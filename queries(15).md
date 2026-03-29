 # 📘 SQL Queries with Explanation and Output

---

## 1. Show all records from Customer table
```sql
 SELECT * FROM CUSTOMER;
+-------------+--------+------------------+------------+---------+----------+
| customer_ID | Name   | Email            | Phone      | Address | Password |
+-------------+--------+------------------+------------+---------+----------+
|           1 | Omika  | omika@gmail.com  | 9876543210 | Lucknow | 12345    |
|           2 | Shreya | shreya@gmail.com | 9876501234 | Delhi   | abc123   |
+-------------+--------+------------------+------------+---------+----------+
2 rows in set (0.001 sec)
```

## 2. Show packages with price greater than 15000`
```sql
 SELECT * FROM Package
    -> WHERE Price > 15000;
+------------+--------------+-------------+----------+----------+----------------------+
| Package_ID | Package_Name | Destination | Duration | Price    | Description          |
+------------+--------------+-------------+----------+----------+----------------------+
|          2 | Manali Tour  | Manali      |        7 | 20000.00 | Hill station package |
+------------+--------------+-------------+----------+----------+----------------------+
1 row in set (0.001 sec)
```
## 3.Show booking details with customer name and total amount``
```sql

 SELECT Booking.Booking_ID, Customer.Name, Booking.Travel_Date, Booking.Total_Amount FROM Booking
    -> JOIN Customer ON Booking.Customer_ID = Customer.Customer_ID;
+------------+-------+-------------+--------------+
| Booking_ID | Name  | Travel_Date | Total_Amount |
+------------+-------+-------------+--------------+
|          1 | Omika | 2025-03-01  |     30000.00 |
+------------+-------+-------------+--------------+
1 row in set (0.002 sec)
```
## 4.Show booking details with package name and destination
```sql
SELECT Booking.Booking_ID, Package.Package_Name, Package.Destination
    -> FROM Booking
    -> JOIN Package ON Booking.Package_ID = Package.Package_ID;
+------------+--------------+-------------+
| Booking_ID | Package_Name | Destination |
+------------+--------------+-------------+
|          1 | Goa Trip     | Goa         |
+------------+--------------+-------------+
1 row in set (0.001 sec)
```
## 5. Show agent name who handled booking
```sql
 SELECT Booking.Booking_ID, Agent.Name AS Agent_Name FROM Booking JOIN Agent ON Booking.Agent_ID = Agent.Agent_ID;
+------------+------------+
| Booking_ID | Agent_Name |
+------------+------------+
|          1 | Rahul      |
+------------+------------+
1 row in set (0.001 sec)
```
## 6. Show complete booking details (Customer + Package + Agent)
```sql
 SELECT
    ->  Booking.Booking_ID,
    ->  Customer.Name AS Customer_Name,
    ->  Package.Package_Name,
    ->  Agent.Name AS Agent_Name,
    ->  Booking.Total_Amount
    -> FROM Booking
    -> JOIN Customer ON Booking.Customer_ID = Customer.Customer_ID
    -> JOIN Package ON Booking.Package_ID = Package.Package_ID
    -> JOIN Agent ON Booking.Agent_ID = Agent.Agent_ID;
+------------+---------------+--------------+------------+--------------+
| Booking_ID | Customer_Name | Package_Name | Agent_Name | Total_Amount |
+------------+---------------+--------------+------------+--------------+
|          1 | Omika         | Goa Trip     | Rahul      |     30000.00 |
+------------+---------------+--------------+------------+--------------+
1 row in set (0.002 sec)
```
## 7.Count total number of customers
```sql
 SELECT COUNT(*) AS Total_Customers FROM Customer;
+-----------------+
| Total_Customers |
+-----------------+
|               2 |
+-----------------+
1 row in set (0.001 sec)
```
## 8.Calculate total revenue
```sql
 SELECT SUM(Total_Amount) AS Total_Revenue FROM Booking;
+---------------+
| Total_Revenue |
+---------------+
|      30000.00 |
+---------------+
1 row in set (0.001 sec)
```
## 9.Find average package price
```sql
SELECT AVG(Price) AS Average_Price FROM Package;
+---------------+
| Average_Price |
+---------------+
|  17500.000000 |
+---------------+
1 row in set (0.001 sec)
```
## 10. Count bookings per customer
```sql
SELECT Customer_ID, COUNT(*) AS Total_Bookings FROM Booking GROUP BY Customer_ID;
+-------------+----------------+
| Customer_ID | Total_Bookings |
+-------------+----------------+
|           1 |              1 |
+-------------+----------------+
1 row in set (0.001 sec)
```
##  11. Show payment details
```sql
SELECT Payment.Payment_ID, Payment.Booking_ID, Payment.Amount, Payment.Payment_Status FROM Payment;
+------------+------------+----------+----------------+
| Payment_ID | Booking_ID | Amount   | Payment_Status |
+------------+------------+----------+----------------+
|          1 |          1 | 30000.00 | Completed      |
+------------+------------+----------+----------------+
1 row in set (0.001 sec)
```
## 12. Show customer who booked Goa Trip
```sql
 SELECT Customer.Name
    -> FROM Customer
    -> JOIN Booking ON Customer.Customer_ID = Booking.Customer_ID
    -> JOIN Package ON Booking.Package_ID = Package.Package_ID
    -> WHERE Package.Package_Name = 'Goa Trip';
+-------+
| Name  |
+-------+
| Omika |
+-------+
1 row in set (0.001 sec)
```
## 13. Show bookings with more than 1 person
```sql
 SELECT * FROM Booking
    -> WHERE Number_of_People > 1;
+------------+--------------+-------------+-------------+------------+----------+------------------+--------------+
| booking_ID | Booking_Date | Travel_Date | Customer_ID | Package_ID | Agent_ID | Number_of_People | Total_Amount |
+------------+--------------+-------------+-------------+------------+----------+------------------+--------------+
|          1 | 2025-02-01   | 2025-03-01  |           1 |          1 |        1 |                2 |     30000.00 |
+------------+--------------+-------------+-------------+------------+----------+------------------+--------------+
1 row in set (0.001 sec)
```
## 14. Show highest payment 
```sql
SELECT MAX(Amount) AS Highest_Payment FROM Payment;
+-----------------+
| Highest_Payment |
+-----------------+
|        30000.00 |
+-----------------+
1 row in set (0.001 sec)
```
## 15. Show completed payments
```sql
 SELECT * FROM Payment
    -> WHERE Payment_Status = 'Completed';
+------------+------------+--------------+----------+----------------+----------------+
| Payment_ID | Booking_ID | Payment_Date | Amount   | Payment_Method | Payment_Status |
+------------+------------+--------------+----------+----------------+----------------+
|          1 |          1 | 2025-02-02   | 30000.00 | UPI            | Completed      |
+------------+------------+--------------+----------+----------------+----------------+
1 row in set (0.001 sec)

