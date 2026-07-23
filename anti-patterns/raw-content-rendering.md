# Raw Content Rendering

## What It Looks Like

The user visits a blog post, help article, or CMS-driven page and sees:

```
<h2>Welcome to Our Blog</h2>
<p>We're excited to announce our <strong>new feature</strong> that helps teams...</p>
```

Or they see raw Markdown:

```
## Welcome to Our Blog

We're excited to announce our **new feature** that helps teams...
```

Instead of properly formatted, readable content.

## Why It Happens

Claude (and AI coding agents in general) builds content systems with three components: an editor, a database, and a renderer. The most common failures:

1. **HTML stored, rendered as text.** The content is HTML from a rich-text editor (TipTap, Quill, ProseMirror), stored correctly in the database, but rendered with `{post.content}` (React text interpolation) instead of `dangerouslySetInnerHTML` or a proper renderer. The HTML tags appear as literal text.

2. **HTML rendered without sanitization.** The developer uses `dangerouslySetInnerHTML={{ __html: post.content }}` but never sanitizes the input. This works visually but is an XSS vulnerability. If any content is user-submitted, AI-generated, or imported, malicious scripts can execute.

3. **Markdown stored, no processor used.** Content is written in Markdown but rendered as plain text. The `##` headings, `**bold**`, and `[links](url)` appear as literal characters because no Markdown library (like `react-markdown` or `marked`) is used.

4. **Format mismatch.** The editor says "Markdown" but the renderer expects HTML, or vice versa. The editor produces one format, the renderer consumes another, and the output is mangled.

5. **AI-generated content not sanitized.** An AI generates content that includes HTML fragments, unclosed tags, or formatting artifacts. This is rendered directly without any cleanup.

## Why It's Bad

- **Users see code instead of content.** `<p>` tags, `##` marks, and `**` asterisks are developer syntax. Users think the page is broken.
- **XSS vulnerabilities.** Unsanitized HTML can execute scripts, steal session cookies, redirect users, or inject phishing content.
- **Trust destruction.** A blog with visible HTML tags looks unprofessional and broken. Users leave immediately.
- **SEO damage.** Search engines may index the raw tags as content, harming page quality scores.

## What to Do Instead

1. **Pick one format and stick with it.** If the editor produces HTML (TipTap, Quill), store HTML and render with sanitized `dangerouslySetInnerHTML`. If the editor produces Markdown, store Markdown and render with `react-markdown`.

2. **Always sanitize before rendering.** No exceptions. Use `DOMPurify.sanitize(content)` or `sanitize-html` to strip dangerous elements (`<script>`, `<iframe>`, `onclick`, `onerror`, `javascript:` URLs) before injecting HTML.

3. **Test with adversarial content.** Before shipping any content renderer, paste these into the editor and verify they render safely:
   - `<script>alert('xss')</script>` — must not execute
   - `<img src=x onerror=alert('xss')>` — must not execute
   - `<h1>Normal heading</h1>` — must render as a heading, not as text
   - `## Markdown heading` — must render as a heading (if Markdown) or as literal text (if HTML-only, which is acceptable)
   - `**bold text**` — must render bold (if Markdown) or as literal text (if HTML-only)

4. **Add a preview.** Blog editors and CMS should show content exactly as it will appear on the public page. This catches rendering mismatches before publication.

## The Test

For every page that renders dynamic content (blog posts, help articles, CMS pages, AI-generated text):

1. Does the page use `dangerouslySetInnerHTML`? → Is it sanitized? If no, add sanitization.
2. Does the page use `{content}` text interpolation? → Does the content contain HTML? If yes, switch to a proper renderer.
3. Does the editor label match the renderer? Markdown editor → Markdown renderer. HTML editor → HTML renderer.
4. Paste `<script>alert(1)</script>` into the editor. Does it execute on the public page? If yes, you have an XSS vulnerability.
5. View the public page. Do you see any raw `<tags>`, `##` marks, `**` asterisks, or `[link](url)` syntax? If yes, the renderer is wrong.
