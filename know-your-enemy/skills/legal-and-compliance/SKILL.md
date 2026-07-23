---
name: legal-and-compliance
description: "Research what legal pages, disclaimers, and compliance requirements a website needs based on its country and industry. AI agents never add these on their own. A dental clinic in Venezuela needs different legal pages than a SaaS in the US or an e-commerce store in the EU. Use whenever building a website to determine what legal/regulatory pages are required."
---

# Legal & Compliance

AI agents never add legal pages unless told to. But a real business website needs them — and the requirements vary dramatically by country and industry. A dental clinic in Venezuela has different obligations than a fintech in the UK or an e-commerce store in Germany.

This skill researches and produces a list of required and recommended legal pages, disclaimers, and compliance measures for the specific business + country combination.

## What to Research

### 1. Country-Level Data Protection Laws

Every country has data protection rules that affect websites collecting personal information (which is basically every website with a contact form).

| Region | Law | Key requirement for websites |
|---|---|---|
| EU/EEA | GDPR | Cookie consent banner, privacy policy, data processing agreement, right to erasure |
| UK | UK GDPR + PECR | Same as EU GDPR + specific cookie rules |
| Brazil | LGPD | Privacy policy, consent for data collection, DPO appointment for some businesses |
| US (California) | CCPA/CPRA | "Do Not Sell My Info" link, privacy policy with specific disclosures |
| US (general) | No federal law | Privacy policy still strongly recommended, FTC enforcement |
| Canada | PIPEDA | Privacy policy, meaningful consent |
| Venezuela | LOPD (limited enforcement) | Privacy policy recommended, not strictly enforced online |
| Mexico | LFPDPPP | Privacy notice (aviso de privacidad) required |
| Argentina | PDPL | Privacy policy, data registration with authority |
| Chile | Ley 19.628 | Privacy policy, consent |
| Colombia | Ley 1581 | Privacy policy, authorization for data treatment |

**Action:** Search for the current data protection law in the target country. Note what website-level compliance is required. When in doubt, default to: include a privacy policy page.

### 2. Cookie Consent

| Region | Requirement |
|---|---|
| EU/EEA/UK | Active consent banner BEFORE setting non-essential cookies. Must allow granular choice. |
| Brazil | Consent required, banner recommended |
| US | No federal requirement (California requires opt-out for some data) |
| Latin America (general) | Generally not required by law, but increasingly expected |

**Action:** If the site targets EU/UK users or uses analytics/tracking cookies, include a cookie consent banner. If the site is a local business in Latin America targeting local customers, a cookie banner is optional but a privacy policy is still needed.

### 3. Industry-Specific Requirements

| Industry | Common requirements |
|---|---|
| **Medical/Dental** | Professional license number display, health information disclaimers ("not a substitute for professional advice"), patient privacy (HIPAA in US, equivalent locally), before/after photo consent |
| **Legal** | Bar association membership, disclaimer that website content is not legal advice, jurisdiction statement |
| **Financial** | Regulatory registration numbers, risk disclaimers, FINRA/FCA compliance statements |
| **E-commerce** | Return/refund policy, shipping policy, terms of sale, consumer protection compliance |
| **Real estate** | License numbers, fair housing disclaimer (US), agency disclosures |
| **Food/Restaurant** | Allergen information (EU), health department scores (varies) |
| **Education** | Accreditation display, non-discrimination policy |
| **SaaS** | Terms of service, acceptable use policy, SLA, data processing agreement |

**Action:** Research what the specific industry requires in the target country. Check what legal pages the competitors (from the site visit phase) actually have.

### 4. Accessibility

| Region | Requirement |
|---|---|
| US | ADA compliance (increasingly enforced for websites) |
| EU | European Accessibility Act (2025+) |
| UK | Equality Act 2010 |
| Canada | AODA (Ontario), ACA (federal) |
| Most other countries | No specific web accessibility law, but best practice |

**Action:** Note whether accessibility compliance is legally required. If yes, include an accessibility statement page and ensure the site meets WCAG 2.1 AA at minimum.

### 5. Professional Licensing Display

Many regulated professions require displaying license/registration information on business materials including websites:

- Doctors/dentists: medical license number, university, specialty board certifications
- Lawyers: bar registration, jurisdiction
- Accountants: CPA license, registration number
- Real estate agents: license number, brokerage
- Contractors: license number, insurance

**Action:** Research whether the profession requires license display in the target country. Check what competitors show.

### 6. Business Registration

Some countries require displaying business registration information on commercial websites:

- EU: many countries require company registration number, VAT number, registered address
- UK: Companies House number, registered office address, VAT number
- Germany: Impressum (legally required, must include: company name, address, managing director, registration number, VAT ID, contact info)
- US: generally not required on website
- Latin America: varies, generally RIF/RUC/NIT numbers recommended but not always required on websites

**Action:** Research whether the target country requires business registration display on websites.

## Output

Produce a legal requirements checklist:

```
LEGAL & COMPLIANCE: Dental Clinic in Caracas, Venezuela

REQUIRED PAGES:
✓ Privacy policy (LOPD — limited enforcement but standard practice)
  - Must cover: what data you collect (form submissions), how you use it,
    how to request deletion
  - Language: Spanish

RECOMMENDED PAGES:
◐ Terms of service (for the appointment request form)
◐ Health information disclaimer ("This website is for informational
   purposes. Consult a professional for diagnosis and treatment.")

REQUIRED DISPLAY:
✓ Professional license number (Colegio de Odontologos registration)
✓ University/credentials of practicing dentists
✓ Business address

NOT REQUIRED (for this market):
✗ Cookie consent banner (no Venezuelan law requires it, site is local)
✗ GDPR compliance (not serving EU customers)
✗ Accessibility statement (no Venezuelan law requires it)
✗ Impressum (German requirement, not applicable)
✗ HIPAA (US requirement, not applicable)

INDUSTRY-SPECIFIC:
- Before/after photos: obtain and display patient consent statement
- Health claims: avoid promising specific outcomes ("guaranteed results")
- Emergency disclaimer: if advertising emergency services, note limitations

COMPETITORS' LEGAL PAGES (from site visits):
- 8 of 15 have a privacy policy
- 3 of 15 have terms of service
- 0 of 15 have cookie consent banners
- 12 of 15 display professional license numbers
- 0 of 15 have accessibility statements
```

## When to Escalate

If the business operates in a heavily regulated industry (healthcare, finance, legal) or targets customers in the EU/UK, **recommend the client consult a lawyer** for compliance review. This research provides a starting point, not legal advice.

Add a note to the brief: "Legal page content should be reviewed by a qualified professional before publication. This research identifies what pages are needed, not the specific language they should contain."
