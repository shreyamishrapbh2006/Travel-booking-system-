#  SQL Queries with Questions – Travel Booking System

---

## 1. Display all customer details

```sql
SELECT * FROM Customer;
```

---

## 2. Display all travel packages

```sql
SELECT * FROM Package;
```

---

## 3. Display all booking records

```sql
SELECT * FROM Booking;
```

---

## 4. Show customer name and their booking dates

```sql
SELECT c.Name, b.Booking_Date, b.Travel_Date
FROM Booking b
JOIN Customer c ON b.Customer_ID = c.Customer_ID;
```

---

## 5. Show which customer booked which package

```sql
SELECT c.Name, p.Package_Name
FROM Booking b
JOIN Customer c ON b.Customer_ID = c.Customer_ID
JOIN Package p ON b.Package_ID = p.Package_ID;
```

---

## 6. Find packages with price greater than 15000

```sql
SELECT Package_Name, Price
FROM Package
WHERE Price > 15000;
```

---

## 7. Count total number of bookings

```sql
SELECT COUNT(*) AS Total_Bookings
FROM Booking;
```

---

## 8. Calculate total revenue from bookings

```sql
SELECT SUM(Total_Amount) AS Total_Revenue
FROM Booking;
```

---

## 9. Find number of bookings made by each customer

```sql
SELECT c.Name, COUNT(b.Booking_ID) AS Total_Bookings
FROM Customer c
JOIN Booking b ON c.Customer_ID = b.Customer_ID
GROUP BY c.Name;
```

---

## 10. Find customers with more than one booking

```sql
SELECT c.Name, COUNT(*) AS Booking_Count
FROM Booking b
JOIN Customer c ON b.Customer_ID = c.Customer_ID
GROUP BY c.Name
HAVING COUNT(*) > 1;
```

---

## 11. Display all payment details

```sql
SELECT * FROM Payment;
```

---

## 12. Show all completed payments

```sql
SELECT * FROM Payment
WHERE Payment_Status = 'Completed';
```

---

## 13. Show booking ID with payment status

```sql
SELECT b.Booking_ID, p.Payment_Status
FROM Booking b
JOIN Payment p ON b.Booking_ID = p.Booking_ID;
```

---

## 14. Show which agent handled which booking

```sql
SELECT a.Name, b.Booking_ID
FROM Booking b
JOIN Agent a ON b.Agent_ID = a.Agent_ID;
```

---

## 15. Find the most expensive package

```sql
SELECT Package_Name, Price
FROM Package
ORDER BY Price DESC
LIMIT 1;
```

---
