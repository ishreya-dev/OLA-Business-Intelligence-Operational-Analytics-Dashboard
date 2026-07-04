# SQL Analysis

## Overview

SQL was used to explore operational ride-booking data, generate business metrics, and answer key analytical questions before building the Power BI dashboard.

The analysis focuses on operational efficiency, customer behavior, revenue performance, service quality, and business reporting.

---

# Business Objectives

The SQL analysis was performed to:

- Measure booking performance
- Analyze revenue generation
- Evaluate customer behavior
- Understand cancellation patterns
- Measure service quality
- Support Business Intelligence reporting

---

# Business Questions Solved

| Category | Business Question |
|-----------|-------------------|
| Operations | How many rides were successfully completed? |
| Revenue | What is the total revenue generated? |
| Customer | Who are the highest-value customers? |
| Vehicle | Which vehicle types perform best? |
| Ratings | What are the average customer and driver ratings? |
| Payment | Which payment methods are most frequently used? |
| Operations | What are the primary cancellation reasons? |
| Service | Which rides were incomplete and why? |

---

# Analytical Queries

---

## 1. Successful Ride Analysis

### Business Question

How many rides were successfully completed?

### SQL

```sql
CREATE VIEW Successful_Bookings AS
SELECT *
FROM bookings
WHERE Booking_Status = 'Success';
```

---

## 2. Vehicle Performance

### Business Question

What is the average ride distance for each vehicle category?

### SQL

```sql
CREATE VIEW Ride_Distance AS
SELECT
Vehicle_Type,
AVG(Ride_Distance) AS Average_Distance
FROM bookings
GROUP BY Vehicle_Type;
```

---

## 3. Customer Analytics

### Business Question

Which customers completed the highest number of bookings?

### SQL

```sql
CREATE VIEW Top_5_Customers AS
SELECT
Customer_ID,
COUNT(*) AS Total_Rides
FROM bookings
GROUP BY Customer_ID
ORDER BY Total_Rides DESC
LIMIT 5;
```

---

## 4. Revenue Analysis

### Business Question

What is the total revenue generated from successful rides?

### SQL

```sql
CREATE VIEW Total_Revenue AS
SELECT
SUM(Booking_Value) AS Revenue
FROM bookings
WHERE Booking_Status='Success';
```

---

## 5. Driver Performance

### Business Question

What are the highest and lowest driver ratings for Prime Sedan rides?

### SQL

```sql
CREATE VIEW Driver_Rating AS
SELECT
MAX(Driver_Ratings) AS Highest_Rating,
MIN(Driver_Ratings) AS Lowest_Rating
FROM bookings
WHERE Vehicle_Type='Prime Sedan';
```

---

## 6. Customer Satisfaction

### Business Question

What is the average customer rating by vehicle type?

### SQL

```sql
CREATE VIEW Customer_Rating AS
SELECT
Vehicle_Type,
AVG(Customer_Rating) AS Average_Rating
FROM bookings
GROUP BY Vehicle_Type;
```

---

## 7. Payment Analysis

### Business Question

How many rides were paid using UPI?

### SQL

```sql
CREATE VIEW UPI_Rides AS
SELECT *
FROM bookings
WHERE Payment_Method='UPI';
```

---

## 8. Cancellation Analysis

### Business Question

How many rides were cancelled because of driver-related issues?

### SQL

```sql
CREATE VIEW Driver_Cancellations AS
SELECT
COUNT(*) AS Cancelled_Rides
FROM bookings
WHERE cancelled_Rides_by_Driver='Personal & Car related issue';
```

---

## 9. Incomplete Ride Analysis

### Business Question

Which rides were incomplete?

### SQL

```sql
CREATE VIEW Incomplete_Rides AS
SELECT
Booking_ID,
Incomplete_Rides_Reason
FROM bookings
WHERE Incomplete_Rides='Yes';
```

---

# SQL Concepts Demonstrated

## Data Retrieval

- SELECT
- WHERE
- LIMIT

---

## Data Aggregation

- COUNT()
- SUM()
- AVG()
- MAX()
- MIN()

---

## Grouping

- GROUP BY

---

## Sorting

- ORDER BY

---

## Views

- CREATE VIEW

---

# Business Insights Generated

The SQL analysis identified several operational and business trends:

- Successful rides generate the majority of revenue.
- Customer cancellations significantly impact ride completion.
- Digital payment methods are widely adopted.
- Premium vehicle categories contribute higher booking values.
- Customer satisfaction remains consistently positive.

---

# Role of SQL in the BI Pipeline

```mermaid
flowchart LR

A[Operational Dataset]

-->

B[SQL Analysis]

-->

C[Business Metrics]

-->

D[Power BI]

-->

E[Executive Dashboard]

-->

F[Business Decisions]
```

---

# Skills Demonstrated

- SQL Query Writing
- Data Exploration
- Business Analytics
- KPI Calculation
- Data Aggregation
- Business Reporting
- Operational Analytics
- Revenue Analysis
- Customer Analytics