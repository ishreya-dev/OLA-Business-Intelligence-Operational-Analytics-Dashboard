# DAX Measures

## Overview

The Power BI dashboard uses DAX (Data Analysis Expressions) to calculate key business metrics that support operational monitoring, revenue analysis, and executive reporting.

These measures enable dynamic KPI cards, interactive visualizations, and business performance analysis.

---

# Booking KPIs

## Total Bookings

```DAX
Total Bookings =
COUNT(Bookings[Booking_ID])
```

Returns the total number of ride bookings.

---

## Successful Rides

```DAX
Successful Rides =
CALCULATE(
    COUNT(Bookings[Booking_ID]),
    Bookings[Booking_Status] = "Success"
)
```

Returns the number of successfully completed rides.

---

## Success Rate (%)

```DAX
Success Rate % =
DIVIDE(
    [Successful Rides],
    [Total Bookings],
    0
)
```

Measures the percentage of completed bookings.

---

## Cancelled Rides

```DAX
Cancelled Rides =
CALCULATE(
    COUNT(Bookings[Booking_ID]),
    Bookings[Booking_Status] <> "Success"
)
```

Returns the total cancelled rides.

---

## Cancellation Rate (%)

```DAX
Cancellation Rate % =
DIVIDE(
    [Cancelled Rides],
    [Total Bookings],
    0
)
```

Measures the overall cancellation percentage.

---

# Revenue KPIs

## Total Revenue

```DAX
Total Revenue =
SUM(Bookings[Booking_Value])
```

Calculates total booking revenue.

---

## Average Booking Value

```DAX
Average Booking Value =
AVERAGE(Bookings[Booking_Value])
```

Returns the average revenue generated per booking.

---

## Revenue per Successful Ride

```DAX
Revenue per Successful Ride =
DIVIDE(
    [Total Revenue],
    [Successful Rides],
    0
)
```

Measures the average revenue from completed rides.

---

# Customer KPIs

## Total Customers

```DAX
Total Customers =
DISTINCTCOUNT(Bookings[Customer_ID])
```

Counts unique customers.

---

## Average Customer Rating

```DAX
Average Customer Rating =
AVERAGE(Bookings[Customer_Rating])
```

Returns the average customer rating.

---

# Driver KPIs

## Average Driver Rating

```DAX
Average Driver Rating =
AVERAGE(Bookings[Driver_Ratings])
```

Returns the average driver rating.

---

# Operational KPIs

## Average Ride Distance

```DAX
Average Ride Distance =
AVERAGE(Bookings[Ride_Distance])
```

Calculates average trip distance.

---

## Total Ride Distance

```DAX
Total Ride Distance =
SUM(Bookings[Ride_Distance])
```

Returns total distance travelled.

---

# Business Intelligence Measures

## Highest Booking Value

```DAX
Highest Booking Value =
MAX(Bookings[Booking_Value])
```

Returns the maximum booking value.

---

## Lowest Booking Value

```DAX
Lowest Booking Value =
MIN(Bookings[Booking_Value])
```

Returns the minimum booking value.

---

## Average Revenue per Customer

```DAX
Average Revenue per Customer =
DIVIDE(
    [Total Revenue],
    [Total Customers],
    0
)
```

Measures customer value.

---

# Dashboard Usage

The DAX measures are used across the following dashboard modules:

| Dashboard | Measures Used |
|------------|---------------|
| Executive Overview | Total Bookings, Revenue, Success Rate |
| Revenue Analysis | Revenue, Average Booking Value |
| Vehicle Performance | Average Ride Distance |
| Cancellation Analysis | Cancellation Rate |
| Ratings Dashboard | Driver Rating, Customer Rating |

---

# Business Value

These measures provide:

- Executive KPI reporting
- Revenue monitoring
- Customer behavior analysis
- Operational performance tracking
- Service quality evaluation
- Interactive business intelligence dashboards

---

# Future Enhancements

Future versions may include:

- Rolling 30-day averages
- Month-over-Month Growth
- Year-over-Year Growth
- Revenue Forecasting
- Customer Lifetime Value (CLV)
- Driver Performance Score
- Demand Forecast KPIs