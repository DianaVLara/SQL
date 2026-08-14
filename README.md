# SQL Portfolio

Hi, I'm Diana — this repository showcases SQL projects I've written to explore, analyze, and answer business questions across a range of real-world datasets. Each project works with a different database and set of questions, and highlights different SQL techniques, from multi-table joins to CTEs and window functions.

## Projects

| Project | Description | Key Techniques |
|---|---|---|
| [Chinook Sales Analytics](<Chinook%20Sales%20Analytics.sql>) | Queries a digital music store database to analyze customers, sales agents, invoices, and top-selling genres. | Multi-table joins, aggregation, `GROUP BY`/`ORDER BY`, filtering |
| [Customer & Order Analytics](<Customer%20&%20Order%20Analytics.sql>) | Analyzes monthly retail order data to surface sales trends, top-selling products, and customer spending patterns by location. | Joins, aggregate functions, `HAVING`, string filtering |
| [Online Sales Analysis](<Online%20Sales%20Analysis.sql>) | Builds a full e-commerce funnel (views → cart → checkout → purchase) in BigQuery to measure conversion rates, time-to-purchase, and revenue per stage. | CTEs, conditional aggregation, `TIMESTAMP_DIFF`, funnel analysis |
| [Covid_Data_Analysis](Covid_Data_Analysis.sql) | Analyzes global COVID-19 case, death, and vaccination data to calculate infection/death rates and rolling vaccination totals by country. | CTEs, window functions, type casting, rolling aggregates |
| [Fortune 500 Analysis](<Fortune%20500%20Analysis.sql>) | Builds and queries a company benefits dataset to compare industries on employee retention, healthcare coverage, and parental leave. | Table design, `CASE` statements, aggregate functions, `HAVING` |
| [Spotify Analytics](<Spotify%20Analytics.sql>) | Loads a Spotify track dataset and explores trends in danceability, popularity, and track length across artists. | Table design, aggregation, `CASE` bucketing, ranking with `LIMIT` |
| [Climate Conference Analysis](<Climate%20Conference%20Analysis.sql>) | Models an event's attendee, hotel, and session data to answer registration and logistics questions. | Joins, self-joins, subqueries |
| [Superstore Database](<Superstore%20Database.sql>) | Builds a small retail inventory database and queries pricing, stock levels, and category statistics. | Table design, aggregate functions, filtering |

## Skills Demonstrated

- Writing complex, multi-table `JOIN`s (inner, left, self-joins)
- Aggregation with `GROUP BY`, `HAVING`, and window functions
- Common Table Expressions (CTEs) for readable, modular queries
- Conditional logic with `CASE` statements
- Designing and populating relational tables with `CREATE TABLE` / `INSERT`
- Querying across SQL environments, including standard SQL and BigQuery

## About

Each project lives in its own `.sql` file and includes the questions being answered alongside the SQL used to answer them. Feel free to explore, and reach out if you have any questions!
