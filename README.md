# Parcel Master: Distributed Parcel Delivery Database

A distributed database project in Oracle PL/SQL for a parcel delivery service. Data is split between a
**site** database and a **server** database that talk to each other through a database link.

## Structure
| Folder | File | What it does |
|---|---|---|
| `SITE` | `DBSITE.sql` | Creates the site tables: `PRODUCT`, `CLIENT`, `SERVICEINFO`, `SERVICEINFO2`, `SUPPLIER`, `TRANSACTIONINFO` |
| `SITE` | `SITE.sql` | Function that calculates the delivery cost from the service and parcel weight, and a procedure that updates delivery status |
| `SITE` | `AVAIL.sql` | Package that checks whether a product type is available |
| `SITE` | `TRANSACTION.sql` | Procedure that lists delivered products with their suppliers |
| `SERVER` | `DBSERVER.sql` | Creates the server-side service table and inserts products and clients entered by the user |
| `SERVER` | `AVAIL.sql` | Package that searches product availability across the site through the `site1` database link |

## Tech
Oracle Database, PL/SQL (packages, procedures, functions), SQL*Plus, database links.

## Run
1. Create two Oracle users or databases (site and server) and a database link named `site1` from the
   server to the site.
2. Run `SITE/DBSITE.sql` on the site, then `SERVER/DBSERVER.sql` on the server.
3. Run the other scripts in SQL*Plus (`@SITE.sql`, `@AVAIL.sql`, `@TRANSACTION.sql`) and follow the prompts.
