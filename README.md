# Azure Data Engineering Project
## Building a Scalable Data Platform with the Medallion Architecture on Azure
#### I'm thrilled to share details about a recent Azure Data Engineering project I worked on, focused on building a robust and scalable data platform using the Medallion Architecture.

This project focused on building a complete data platform on **Azure** to ingest and process **e-commerce data** for insightful analysis.  Using the **Medallion Architecture**, I ingested data from various sources into a Bronze layer in **ADLS Gen2**, transformed it in **Databricks** and stored it in a Silver layer, and finally loaded it into a **Synapse data warehouse** (Gold layer) for **Power BI** reporting.  This end-to-end process enabled efficient data analysis and visualization, ultimately providing valuable insights into e-commerce performance.

## Project Architecture


![Project Architecture](https://github.com/sairish/Azure-Data-Engineering/blob/main/Architecture%20Diagrams/Azure%20ArchitectureGif.gif)

This platform is built upon the Medallion Architecture, a proven approach for constructing scalable and maintainable data lakes.
## So What is a medallion architecture?
A medallion architecture is a data design pattern used to logically organize data in a lakehouse, with the goal of incrementally and progressively improving the structure and quality of data as it flows through each layer of the architecture (from Bronze ⇒ Silver ⇒ Gold layer tables).\
**The Bronze layer**, acts as the raw data lake \
**The Silver layer**, contains cleansed and transformed data\
**The Gold layer**, is a curated data warehouse optimized for analysis and reporting. \
This layered approach offers several key benefits, including ensuring data quality through progressive refinement, enabling efficient data processing by separating concerns, and simplifying data governance through a structured approach.

![Medallion Architecture](https://github.com/sairish/Azure-Data-Engineering/blob/main/Support%20Images/Meallion%20Architecture.png)

For this project, I leveraged the following Azure services:

*   **Azure Data Factory (ADF):**  ADF served as the orchestration engine for my data pipelines.  It allowed me to create and manage the workflows for ingesting data from various sources into the Bronze layer of my data lake.  I used ADF to connect to HTTPS endpoints and SQL databases, extract data, and load it into ADLS Gen2.

*   **Azure Data Lake Storage Gen2 (ADLS Gen2):** ADLS Gen2 acted as the foundation of my data lake.  It provided a scalable and cost-effective storage solution for both raw and processed data.  I used ADLS Gen2 to store the data in the Bronze and Silver layers, taking advantage of its hierarchical namespace and integration with other Azure services.

*   **Azure Databricks:** Databricks, a unified analytics platform powered by Apache Spark, was instrumental in processing and transforming the data. I used Databricks to read data from the Bronze layer in ADLS Gen2, perform data cleansing and transformations using Python and Spark, and then write the processed data to the Silver layer in ADLS Gen2.  A key aspect of this stage was converting the data to Parquet format for optimized performance.

*   **Azure Synapse Analytics:**  Synapse Analytics served as my data warehouse.  I used Synapse to ingest data from the Silver layer in ADLS Gen2 and create a curated data warehouse (Gold layer) optimized for analytical queries and reporting.  This involved designing a star schema and implementing efficient data loading processes.

*   **Power BI:** Power BI was used for data visualization and reporting. I connected Power BI to the Azure Synapse Analytics data warehouse to create interactive dashboards and reports, providing business users with valuable insights derived from the data.



## Dats Source ER Diagram


![Dats Source ER Diagram](https://github.com/sairish/Azure-Data-Engineering/blob/main/Data%20Source/Ecomm%20Dataset%20ER%20Diagram.png)

## Project Details:

*   **Data Ingestion (Bronze Layer):**
    *   Ingested batch data from diverse sources, including HTTPS endpoints (e.g., product catalogs, customer reviews) and SQL databases (e.g., transactional data, inventory).
    *   Utilized **Azure Data Factory (ADF)** to create and manage data pipelines for continuous ingestion.
    *   Landed raw data in CSV format into **Azure Data Lake Storage Gen2 (ADLS Gen2)**, designated as the Bronze layer.

*   **Data Transformation (Silver Layer):**
    *   Leveraged **Azure Databricks** and **Apache Spark** for data processing and transformation.
    *   Read data from the Bronze layer in ADLS Gen2.
    *   Performed data cleaning, standardization, and enrichment (e.g., handling missing values, data type conversions, joining data from different sources).
    *   Converted the data from CSV to **Parquet format** for optimized storage and query performance.
    *   Stored the transformed data in ADLS Gen2, designated as the Silver layer.

*   **Data Warehousing (Gold Layer):**
    *   Utilized **Azure Synapse Analytics** as the data warehouse.
    *   Ingested data from the Silver layer in ADLS Gen2 into Synapse.
    *   Designed and implemented a **star schema** optimized for analytical queries.
    *   Created tables, views, and stored procedures to support reporting and analysis.

*   **Data Visualization and Reporting:**
    *   Connected **Power BI** to the Azure Synapse Analytics data warehouse.
    *   Developed interactive dashboards and reports to visualize key metrics and provide business insights.
    *   Enabled users to explore the data and gain actionable intelligence.

## Optimization Techniques Used:

*   **Parquet Format:** Converting data to Parquet in Databricks significantly improved query performance in Synapse due to its columnar storage and efficient compression.
*   **Data Partitioning:** Proper partitioning of data in Databricks and Synapse based on relevant criteria (e.g., date, region) optimized data processing and query execution by reducing the amount of data scanned.
*   **Spark Optimization:** Tuning Spark configurations, such as executor memory, driver memory, and number of executors, ensured efficient resource utilization and minimized processing time. This included careful consideration of shuffle operations and data skew.
*   **ADF Pipeline Optimization:** Optimizing ADF pipelines, including concurrency settings, data flow configurations, and appropriate use of activities like Copy Data and Data Flows, ensured seamless and efficient data ingestion.
*   **Synapse Performance Tuning:** Optimized Synapse performance through techniques like proper indexing (e.g., clustered columnstore indexes), distribution strategies, and materialized views where appropriate.

## Snippet of the project:

**Data Piepline:**
![Data Pipeline](https://github.com/sairish/Azure-Data-Engineering/blob/main/Support%20Images/Data%20Pipeline.png)

**ADLS Storage:**
![ADLS Storage](https://github.com/sairish/Azure-Data-Engineering/blob/main/Support%20Images/Storage%20Layer.png)

**Azure Synapse:**
![Azure Synapse](https://github.com/sairish/Azure-Data-Engineering/blob/main/Support%20Images/Azure%20Synapse.png)
