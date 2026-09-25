# Hotel Data Warehouse System

University project for the course **Software Engineering for Database Systems**.

The project presents a complete Data Warehouse solution for a hotel chain, including an OLTP database, ETL processes, dimensional modeling, analytical SQL reports, and data visualizations.

## Main Features

- OLTP database for hotels, rooms, guests, reservations, stays, services, and payments
- Data Warehouse with fact and dimension tables
- ETL processes implemented in **Pentaho Data Integration**
- Surrogate keys and dimension lookups
- Materialized view for monthly hotel revenue
- Analytical SQL reports using aggregation and window functions
- Data visualizations based on report results

## Dataset

The database contains:

- 159 cities
- 100 hotels
- 1,973 rooms
- 5,000 guests
- 12,000 reservations
- 7,606 completed stays
- 11,363 service usage records

Data was created using a combination of real data, Mockaroo-generated data, and SQL-generated records.

## Data Warehouse

The central fact table is:

`bb_fact_stays`

Main dimensions:

- `bb_dim_time`
- `bb_dim_guest`
- `bb_dim_city`
- `bb_dim_hotel`
- `bb_dim_room_type`
- `bb_dim_room`
- `bb_dim_employee`

The model combines **star** and **snowflake** concepts.

## ETL

ETL processes include:

- data extraction and cleaning
- surrogate key generation
- dimension lookups
- time dimension generation
- calculation of revenue and stay measures
- loading dimension and fact tables

## Reports

The project includes analytical reports for:

- revenue by month and year
- top hotels by revenue
- most used room types
- average stay duration
- guest countries
- additional service revenue
- top hotels by quarter
- monthly stay trends
- revenue by city
- relationship between discounts and revenue

Window functions such as `DENSE_RANK()` and `LAG()` are also used.

## Technologies

- Oracle Database
- Oracle SQL / SQL Developer
- Pentaho Data Integration (Spoon)
- Mockaroo
- Google Sheets
- LibreOffice

## Project Flow

```text
OLTP Database
      ↓
ETL Processes
      ↓
Data Warehouse
      ↓
Analytical Reports
      ↓
Visualizations
