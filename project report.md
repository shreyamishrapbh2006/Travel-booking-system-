# Travel Booking System - Project Report

##  Introduction
This project is a Travel Booking System developed using SQL. It manages customer details, travel packages, bookings, agents, and payments efficiently.

---
##  Objectives
- To design a database for travel booking
- To reduce data redundancy using normalization
- To implement SQL queries for real-world operations

---
##  ER Diagram
The ER diagram represents entities like Customer, Booking, Package, Agent, and Payment along with their relationships.

(File attached separately)

---
##  Database Tables
The following tables are created:
- Customer
- Package
- Agent
- Booking
- Payment

Each table is connected using primary and foreign keys.

---
##  Normalization
Initially, all data was stored in a single table (UNF), which caused redundancy.

Then:
- 1NF: Removed repeating groups and ensured atomic values
- 2NF: Separated tables based on partial dependencies
- 3NF: Removed transitive dependencies

Final tables are normalized up to 3NF.

---
##  SQL Queries
Various SQL queries are implemented such as:
- SELECT queries
- JOIN operations
- Aggregate functions
- Filtering using WHERE clause

(See Queries.md file)

---
##  Output
The system successfully performs:
- Customer data storage
- Booking management
- Payment tracking
  
---
##  Conclusion
The Travel Booking System works efficiently and avoids redundancy using normalization techniques. It demonstrates practical implementation of DBMS concepts.

---
By Omika Maurya
Shreya Mishra
