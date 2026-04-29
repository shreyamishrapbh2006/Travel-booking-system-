-- 🔴 UN-NORMALIZED FORM (UNF)
-- All data in one table (redundancy exists)
```sql
CREATE TABLE UNF_BOOKING(
    Customer_Name VARCHAR(100),
    Email VARCHAR(100),
    Phone VARCHAR(15),
    Package_Name VARCHAR(100),
    Destination VARCHAR(100),
    Agent_Name VARCHAR(100),
    Booking_Date DATE,
    Travel_Date DATE,
    No_of_People INT,
    Total_Amount DECIMAL(10,2),
    Payment_Method VARCHAR(50)
);
```

```sql
INSERT INTO UNF_BOOKING VALUES
('Omika','omika@gmail.com','9876543210','Goa Trip','Goa','Rahul','2025-02-01','2025-03-01',2,30000,'UPI'),
('Omika','omika@gmail.com','9876543210','Manali Tour','Manali','Rahul','2025-04-01','2025-05-01',3,60000,'Card'),
('Shreya','shreya@gmail.com','9876501234','Goa Trip','Goa','Rahul','2025-06-01','2025-07-01',1,15000,'Cash');
```

-- 🔴 PROBLEM: Data redundancy (same customer repeated)
```sql
SELECT Customer_Name, COUNT(*)
FROM UNF_BOOKING
GROUP BY Customer_Name;
```

-- 🟡 1NF:
-- Remove repeating groups, ensure atomic values

-- 🟢 2NF:
-- Separate Customer and Package data into different tables

-- 🔵 3NF:
-- Remove transitive dependency (Agent and Payment separated)

-- ✅ FINAL RESULT:
-- CUSTOMER, PACKAGE, AGENT, BOOKING, PAYMENT tables created
-- Database is normalized up to 3NF
