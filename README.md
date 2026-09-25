Hotel Data Warehouse System
A university project developed for the course Software Engineering for Database Systems.
The project demonstrates the design and implementation of a complete data warehouse solution for a hotel chain, starting from an operational OLTP database and continuing through ETL processing, dimensional modeling, analytical reporting, and data visualization.
Project Overview
The system is designed to support hotel business analysis based on operational data such as reservations, completed stays, rooms, guests, employees, additional services, and payments.
The project consists of four main parts:
- OLTP database design and implementation
- Data Warehouse dimensional model
- ETL processes
- Analytical SQL reports and visualizations
OLTP Database
The operational database contains the following main entities:
- Cities
- Hotels
- Room types
- Rooms
- Guests
- Employees
- Reservations
- Stays
- Services
- Service usage
- Payments
The database was populated using a combination of:
- manually entered data
- a real dataset for Serbian cities
- generated data created with Mockaroo
- derived data created with SQL scripts to preserve referential and business consistency
The dataset contains thousands of records, including:
- 159 cities
- 100 hotels
- 1,973 rooms
- 5,000 guests
- 500 employees
- 12,000 reservations
- 7,606 completed stays
- 11,363 service usage records
Data Warehouse Design
The Data Warehouse is centered around the bb_fact_stays fact table, where each row represents one completed hotel stay.
The main dimensions are:
- bb_dim_time
- bb_dim_guest
- bb_dim_city
- bb_dim_hotel
- bb_dim_room_type
- bb_dim_room
- bb_dim_employee
The model combines star and snowflake concepts.
Hotel and room type information is accessed through the room dimension, while city information is accessed through the hotel dimension.
Main Measures
The fact table contains measures such as:
- number of nights
- room revenue
- additional service revenue
- total revenue
- discount percentage
- discount value
- number of used services
ETL Process
ETL processes were implemented using Pentaho Data Integration (Spoon).
The ETL workflow includes:
- extracting data from the OLTP database
- cleaning and validating data
- generating surrogate keys
- performing dimension lookups
- generating the time dimension
- calculating derived measures
- aggregating additional service data
- loading dimensions and the central fact table
Implemented transformations include:
- etl_01_dim_city
- etl_02_dim_room_type
- etl_03_dim_time
- etl_04_dim_guest
- etl_05_dim_employee
- etl_06_dim_hotel
- etl_07_dim_room
- etl_08_fact_stays
Materialized View
The project also includes the materialized view:
bb_mv_monthly_hotel_revenue
It stores monthly aggregated hotel performance data, including:
- year and month
- hotel
- city
- number of stays
- total number of nights
- room revenue
- service revenue
- total revenue
The materialized view is used to reduce the need for repeated joins and aggregations in frequently executed analytical queries.
Analytical Reports
The project includes ten analytical business questions:
1. What is the total hotel revenue by month and year?
2. Which hotels generate the highest revenue?
3. Which room types have the highest number of completed stays?
4. What is the average stay duration by hotel and room type?
5. Which countries have the largest number of guests?
6. Which additional hotel services generate the highest revenue?
7. Which five hotels generated the highest revenue in each quarter?
8. How does the number of completed stays change over time?
9. How do revenue and number of nights differ between cities?
10. What is the relationship between discounts and generated revenue?
The reporting layer includes aggregation queries as well as analytical/window functions such as:
- DENSE_RANK()
- LAG()
Visualizations
Selected SQL report results were additionally visualized using charts, including:
- monthly revenue trends
- top hotels by revenue
- stay distribution by room type
- top guest countries
- completed stays over time
Technologies
- Oracle Database
- Oracle SQL
- Oracle SQL Developer
- Pentaho Data Integration / Spoon
- Mockaroo
- LibreOffice
- Google Sheets

Project Structure:
OLTP database
    ↓
ETL processes
    ↓
Data Warehouse
    ↓
Analytical SQL reports
    ↓
Visualizations

Author:
Bogdan Banjac
Faculty of Sciences, University of Novi Sad
Information Technologies
