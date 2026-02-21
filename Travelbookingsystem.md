# TRAVELBOOKINGSYSTEM

---

## CREATING DATABASE

```sql

CREATE DATABASE TravelBookingSystem;
USE TravelBookingSystem;
```

---

## CREATE TABLE CUSTOMER

```sql

CREATE TABLE CUSTOMER(
    -> Customer_ID INT PRIMARY KEY AUTO_INCREMENT,
    -> Name VARCHAR(100),
    -> Email VARCHAR(100) UNIQUE,
    -> Phone VARCHAR(15),
    -> Address TEXT,
    -> Password VARCHAR(100));
```

## CREATE TABLE PACKAGE

```sql

CREATE TABLE PACKAGE (
    -> Package_ID INT PRIMARY KEY AUTO_INCREMENT,
    -> Package_Name VARCHAR(100),
    -> Destination VARCHAR(100),
    -> Duration INT,
    ->  Price DECIMAL(10,2),
    -> Description TEXT);
```

## CREATE TABLE AGENT

```sql

CREATE TABLE AGENT(
    -> Agent_ID INT PRIMARY KEY AUTO_INCREMENT,
    ->  Name VARCHAR(100),
    -> Email VARCHAR(100),
    -> Phone VARCHAR(15),
    -> Commission_Percentage DECIMAL(5,2));
```

## CREATE TABLE BOOKING

```sql

CREATE TABLE BOOKING (
    -> Booking_ID INT PRIMARY KEY AUTO_INCREMENT,
    -> Booking_Date DATE,
    -> Travel_Date DATE,
    ->  Customer_ID INT,
    -> Package_ID INT,
    -> Number_of_People INT,
    -> Total_Amount DECIMAL(10,2),
    -> FOREIGN KEY (Customer_ID) REFERENCES Customer(Customer_ID),
    -> FOREIGN KEY (Package_ID) REFERENCES Package(Package_ID));
```

## CREATE TABLE PAYMENT

 ```sql

CREATE TABLE PAYMENT (
    -> Payment_ID INT PRIMARY KEY AUTO_INCREMENT,
    -> Booking_ID INT,
    -> Payment_Date DATE,
    -> Amount DECIMAL(10,2),
    ->  Payment_Method VARCHAR(50),
    -> Payment_Status VARCHAR(50),
    -> FOREIGN KEY (Booking_ID) REFERENCES Booking(Booking_ID));
```

## INSERT VALUES IN CUSTOMER

 ```sql

INSERT INTO Customer 
    -> VALUES('Omika', 'omika@gmail.com', '9876543210', 'Lucknow', '12345'),
    -> ('Shreya', 'shreya@gmail.com', '9876501234', 'Delhi', 'abc123');
```

## INSERT VALUES IN PACKAGE

 ```sql

INSERT INTO Package 
    -> VALUES('Goa Trip', 'Goa', 5, 15000.00, 'Beach vacation package'),
    -> ('Manali Tour', 'Manali', 7, 20000.00, 'Hill station package');
```

## INSERT VALUES IN AGENT

 ```sql

INSERT INTO Agent
    -> VALUES('Rahul', 'rahul@travel.com', '9999999999', 10.00);
```

## INSERT VALUES IN BOOKING

 ```sql

INSERT INTO Booking 
    -> VALUES('2025-02-01', '2025-03-01', 1, 1, 2, 30000.00);
```

## INSERT VALUES IN PAYMENT

 ```sql

INSERT INTO Payment
    -> VALUES(1, '2025-02-02', 30000.00, 'UPI', 'Completed');
```

## VIEW ALL TABLES NAME

 ```sql

SHOW TABLES;

```
## OUTPUT:

```
+-------------------------------+
| Tables_in_travelbookingsystem |
+-------------------------------+
| agent                         |
| booking                       |
| customer                      |
| package                       |
| payment                       |
+-------------------------------+
 ```


## VIEW TABLE CUSTOMER


```sql

 SELECT * FROM CUSTOMER;

```
## OUTPUT:

```
+-------------+--------+------------------+------------+---------+----------+
| Customer_ID | Name   | Email            | Phone      | Address | Password |
+-------------+--------+------------------+------------+---------+----------+
|           1 | Omika  | omika@gmail.com  | 9876543210 | Lucknow | 12345    |
|           2 | Shreya | shreya@gmail.com | 9876501234 | Delhi   | abc123   |
+-------------+--------+------------------+------------+---------+----------+
```


## VIEW TABLE AGENT


 ```sql

SELECT * FROM AGENT;

```
## OUTPUT:

```
+----------+-------+------------------+------------+-----------------------+
| Agent_ID | Name  | Email            | Phone      | Commission_Percentage |
+----------+-------+------------------+------------+-----------------------+
|        1 | Rahul | rahul@travel.com | 9999999999 |                 10.00 |
+----------+-------+------------------+------------+-----------------------+
```

## VIEW TABLE PACKAGE


 ```sql

SELECT * FROM PACKAGE;

```
## OUTPUT:

```
+------------+--------------+-------------+----------+----------+------------------------+
| Package_ID | Package_Name | Destination | Duration | Price    | Description            |
+------------+--------------+-------------+----------+----------+------------------------+
|          1 | Goa Trip     | Goa         |        5 | 15000.00 | Beach vacation package |
|          2 | Manali Tour  | Manali      |        7 | 20000.00 | Hill station package   |
+------------+--------------+-------------+----------+----------+------------------------+
```

## VIEW TABLE PAYMENT 


 ```sql

SELECT * FROM PAYMENT;

```
## OUTPUT:

```
+------------+------------+--------------+----------+----------------+----------------+
| Payment_ID | Booking_ID | Payment_Date | Amount   | Payment_Method | Payment_Status |
+------------+------------+--------------+----------+----------------+----------------+
|          1 |          1 | 2025-02-02   | 30000.00 | UPI            | Completed      |
+------------+------------+--------------+----------+----------------+----------------+
```

## VIEW TABLE BOOKING


 ```sql

SELECT * FROM BOOKING;

```
## OUTPUT:

```
+------------+--------------+-------------+-------------+------------+------------------+--------------+
| Booking_ID | Booking_Date | Travel_Date | Customer_ID | Package_ID | Number_of_People | Total_Amount |
+------------+--------------+-------------+-------------+------------+------------------+--------------+
|          1 | 2025-02-01   | 2025-03-01  |           1 |          1 |                2 |     30000.00 |
+------------+--------------+-------------+-------------+------------+------------------+--------------+
1 row in set (0.001 sec)
