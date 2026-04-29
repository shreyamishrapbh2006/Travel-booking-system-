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
    -> Password VARCHAR(225));
```

## CREATE TABLE PACKAGE

```sql

CREATE TABLE PACKAGE (
    -> Package_ID INT PRIMARY KEY AUTO_INCREMENT,
    -> Package_Name VARCHAR(100),
    -> Destination VARCHAR(100),
    -> Duration INT,
    -> Price DECIMAL(10,2),
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
    -> Customer_ID INT,
    -> Package_ID INT,
    -> Agent_ID INT,
    -> Number_of_People INT,
    -> Total_Amount DECIMAL(10,2),
    -> FOREIGN KEY (Customer_ID) REFERENCES Customer(Customer_ID),
    -> FOREIGN KEY (Package_ID) REFERENCES Package(Package_ID),
    -> FOREIGN KEY (Agent_ID) REFERENCES Agent(Agent_ID));
```

## CREATE TABLE PAYMENT

 ```sql

CREATE TABLE PAYMENT (
    -> Payment_ID INT PRIMARY KEY AUTO_INCREMENT,
    -> Booking_ID INT,
    -> Payment_Date DATE,
    -> Amount DECIMAL(10,2),
    ->  Payment_Method VARCHAR(50),
    -> Payment_Status ENUM('Pending','Completed','Failed'),
    -> FOREIGN KEY (Booking_ID) REFERENCES Booking(Booking_ID));
```

## INSERT VALUES IN CUSTOMER

 ```sql

INSERT INTO Customer(Name, Email, Phone, Address, Password)
    -> VALUES('Pooja','pooja@gmail.com','9876540001','Noida','p123'),
-> ('Rohit','rohit@gmail.com','9876540002','Delhi','r123'),
-> ('Sneha','sneha@gmail.com','9876540003','Mumbai','s123'),
-> ('Arjun','arjun@gmail.com','9876540004','Pune','a123'),
-> ('Neel','neel@gmail.com','9876540005','Chandigarh','n123');
```

## INSERT VALUES IN PACKAGE

 ```sql

INSERT INTO Package(Package_Name, Destination, Duration, Price, Description) 
    -> VALUES('Shimla Trip','Shimla',5,14000,'Hill station tour'),
-> ('Kashmir Tour','Kashmir',7,25000,'Snow paradise'),
-> ('Ooty Package','Ooty',6,17000,'Nature tour'),
-> ('Darjeeling Trip','Darjeeling',5,16000,'Tea gardens'),
-> ('Rajasthan Tour','Rajasthan',8,22000,'Desert safari');
```

## INSERT VALUES IN AGENT

 ```sql

INSERT INTO Agent(Name, Email, Phone, Commission_Percentage)
    -> VALUES('Simran','simran@travel.com','9000000001',9.00),
-> ('Vikas','vikas@travel.com','9000000002',11.00),
-> ('Ankit','ankit@travel.com','9000000003',10.00),
-> ('Priya','priya@travel.com','9000000004',12.00),
-> ('Deepak','deepak@travel.com','9000000005',8.50);
```

## INSERT VALUES IN BOOKING

 ```sql

INSERT INTO Booking(Booking_Date, Travel_Date, Customer_ID, Package_ID, Agent_ID, Number_of_People, Total_Amount)
   -> VALUES('2025-03-05','2025-04-05',3,2,1,2,40000),
-> ('2025-03-12','2025-04-12',4,3,2,3,51000),
-> ('2025-03-20','2025-04-20',5,4,3,1,16000),
-> ('2025-04-01','2025-05-01',6,5,4,4,88000),
-> ('2025-04-10','2025-05-10',7,6,5,2,44000);
```

## INSERT VALUES IN PAYMENT

 ```sql

INSERT INTO Payment(Booking_ID, Payment_Date, Amount, Payment_Method, Payment_Status)
    -> VALUES(2,'2025-03-06',40000,'UPI','Completed'),
-> (3,'2025-03-13',51000,'Card','Completed'),
-> (4,'2025-03-21',16000,'Cash','Pending'),
-> (5,'2025-04-02',88000,'Net Banking','Completed'),
-> (6,'2025-04-11',44000,'UPI','Failed');
```
