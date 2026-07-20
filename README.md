# SmartLibrary Database Management System

A relational database project for a university library management system, built with **Microsoft SQL Server** and visualized with **Power BI**. The system models the full lifecycle of a library's operations: cataloging books, managing members and staff, tracking borrow/return transactions, and calculating overdue fines.

## Overview

SmartLibrary simulates a real academic library (modeled on university faculties such as Computers and Information, Science, Engineering, Medicine, and Commerce) with:

- **62 books** across 10 categories, linked to authors and publishers
- **180 physical copies** tracked individually with availability status
- **50 registered members** (students) and **5 librarians** working different shifts
- **200 borrow transactions** with realistic on-time, late, and still-outstanding return patterns
- **Automatically generated fines** for late returns, with paid/unpaid status tracking

## Database Schema

The schema is fully normalized and enforces referential integrity through primary/foreign keys and check constraints.

| Table | Description |
|---|---|
| `Categories` | Book subject categories (e.g., Computer Science, Literature, Philosophy) |
| `Publishers` | Publishing houses |
| `Authors` | Book authors |
| `Books` | Core book catalog (title, ISBN, page count, publication date) |
| `Book_Authors` | Many-to-many link between books and authors |
| `BookCopies` | Individual physical copies of each book, with status (`Available`, `Borrowed`, `Damaged`) |
| `Members` | Library members (students), with faculty affiliation |
| `Librarians` | Library staff, assigned to `Morning`, `Evening`, or `Night` shifts |
| `BorrowTransactions` | Borrow/return records linking a copy, a member, and a librarian |
| `Fines` | Late-return fines linked to transactions, with payment status |

## Views

Four views simplify reporting and analysis on top of the raw schema:

- **`vw_BorrowHistory`** — full borrow history joined with member, book, and librarian details
- **`vw_BookAvailability`** — per-book copy counts, split by available and borrowed
- **`vw_Fines`** — fine details joined with member and transaction info
- **`vw_BookStatistics`** — borrow count per book, used for popularity analysis

## Business Queries

The project includes 25+ analytical SQL queries covering common library reporting needs, including:

- Top 10 most-borrowed books and most active members
- Books that have never been borrowed
- Currently overdue books
- Total fines collected vs. outstanding
- Borrowing trends by category and by month
- Publisher with the largest collection in the library
- Core SQL techniques demonstrated: `JOIN`, `GROUP BY` / `HAVING`, `LIKE`, `BETWEEN`, subqueries, and aggregate functions

## Project Files

| File | Description |
|---|---|
| `SQLQuery1.sql` | Database and table creation (schema + constraints) |
| `SQLQuery2.sql` | Initial data seeding (categories, publishers, authors, sample books, members, transactions) |
| `SQLQuery3.sql` | View definitions |
| `SQLQuery4.sql` | 25 business/reporting queries |
| `SQLQuery5.sql` | Extended data generation (remaining books, copies, members, and transactions via loops to reach full scale) |
| `SQL_Project_Final.pbix` | Power BI dashboard built on the database views |

## Tech Stack

- **Microsoft SQL Server / T-SQL**
- **Power BI** for dashboarding and visualization

## How to Run

1. Open the scripts in **SQL Server Management Studio (SSMS)**.
2. Run `SQLQuery1.sql` to create the `SmartLibrary` database and schema.
3. Run `SQLQuery2.sql` to seed the initial dataset.
4. Run `SQLQuery3.sql` to create the reporting views.
5. Run `SQLQuery5.sql` to generate the extended dataset (additional books, copies, members, and transactions).
6. Run `SQLQuery4.sql` to explore the business reports.
7. Open `SQL_Project_Final.pbix` in Power BI Desktop, connected to the `SmartLibrary` database, to view the interactive dashboard.
