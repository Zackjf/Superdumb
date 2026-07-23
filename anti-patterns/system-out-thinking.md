# System-Out Thinking

Building pages around data models instead of user tasks.

## What It Looks Like

You have a database with Users, Orders, and Products tables. The AI builds you
a Users page, an Orders page, and a Products page. The nav bar reads like a
database diagram. Every page is a CRUD table with columns matching the schema.

```
Sidebar:
  - Users
  - Orders
  - Products
  - Invoices
  - Shipments
  - Inventory
```

The user who needs to "fulfill an order" now has to visit Orders to find the
order, Products to check stock, Shipments to create a label, and Invoices to
send the bill. Four pages for one job.

## Why It Happens

AI agents read your schema, see entities, and map each one to a page. It's the
shortest path from data model to working UI. One table = one page = done.

## Why It's Bad

Users don't think in tables. They think in tasks: "Ship this order." "Refund
this customer." "Restock this item." A schema-mirror UI forces them to hold the
data model in their head and manually stitch pages together.

## What to Do Instead

Start from tasks, not tables. Ask: what does the user need to *do*? Build
pages around those workflows, pulling from whatever tables are needed.

### Before

```
/users          -> list of users
/orders         -> list of orders
/products       -> list of products
/shipments      -> list of shipments
```

### After

```
/fulfillment    -> open orders + stock status + shipping actions, all in one view
/customers      -> customer profile with their orders, returns, and messages
/catalog        -> products with stock levels, pricing, and supplier info together
```

The database still has separate tables. The UI doesn't have to mirror them.
A single "Fulfillment" screen can query Orders, Products, Shipments, and
Invoices behind the scenes and present one coherent workflow.

### The Test

Look at your nav bar. If it reads like a list of database tables, you've built
a system-out UI. If it reads like a list of things a person would say they need
to do today, you're closer to right.
