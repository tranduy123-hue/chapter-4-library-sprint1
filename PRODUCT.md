# Product
<!-- impeccable:product-schema 1 -->
## Platform
web
## Stack
Python 3 standard library, SQLite, HTML/CSS. Implementation choice under the user's instruction to complete the assignment; Python and HTML are explicitly allowed by the assignment.
## Users
Librarian adding books to the library catalog, as specified in chapter 4.
## Product Purpose
Demonstrate Sprint 1: add a book with unique ISBN and calculate overdue fines.
## Capabilities and Constraints
Book fields id, title, author, isbn. Fine 5,000 VND/day; beyond 10 days add 20 percent. No fine for non-positive days. Local demo, no production authentication. Unit tests use AAA. GitHub and Jira provide assignment evidence.
## Operating Context
Assumption: librarian uses a desktop browser in a lit library; form must also work on small screens.
## Evidence on Hand
Four-page chapter 4 PDF in workspace. No supplied brand, member roster or existing code. A/B/C are teaching roles, not invented people.
## Product Principles
Keep entered values on validation failure; explain duplicate ISBN; store real entries; keep the demo dependency-free.