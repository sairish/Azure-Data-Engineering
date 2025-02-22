# Azure Data Engineering

#### I'm thrilled to share details about a recent Azure Data Engineering project I worked on, focused on building a robust and scalable data platform using the Medallion Architecture.

#### This project includes several key components:

1. **Data Sources:** We ingested batch data from diverse sources, including HTTPS endpoints and SQL databases.
2. **Azure Data Factory (ADF):** We used ADF to create pipelines for the continuous ingestion of data into Azure Data Lake Storage Gen2 (ADLS Gen2). This initial landing zone in ADLS Gen2 served as our Bronze layer, storing the raw data in CSV format.
3. **Data Processing in Azure Databricks:**  Leveraging the power of Apache Spark, we processed and transformed the Bronze layer data within Azure Databricks.  Importantly, we converted the CSV files to Parquet format for optimized performance during processing. This transformed data was then stored in another ADLS Gen2 location, acting as our Silver layer.
4. **Data Warehousing with Azure Synapse Analytics:**  The Silver layer data was then ingested into Azure Synapse Analytics, our data warehousing solution.  This formed the Gold layer, providing a curated and optimized dataset for analysis.
5. **Data Visualization with Power BI:**  Finally, we connected Power BI to Azure Synapse Analytics to create interactive dashboards, enabling business users to gain valuable insights from the data.

## Project Architecture


![](https://github.com/sairish/Azure-Data-Engineering/blob/main/Architecture%20Diagrams/Azure%20ArchitectureGif.gif)

This platform is built upon the Medallion Architecture, a proven approach for constructing scalable and maintainable data lakes.
## So What is a medallion architecture?
A medallion architecture is a data design pattern used to logically organize data in a lakehouse, with the goal of incrementally and progressively improving the structure and quality of data as it flows through each layer of the architecture (from Bronze ⇒ Silver ⇒ Gold layer tables).\
**The Bronze layer**, acts as the raw data lake \
**The Silver layer**, contains cleansed and transformed data\
**The Gold layer**, is a curated data warehouse optimized for analysis and reporting. \
This layered approach offers several key benefits, including ensuring data quality through progressive refinement, enabling efficient data processing by separating concerns, and simplifying data governance through a structured approach.

![Medallion Architecture](https://github.com/sairish/Azure-Data-Engineering/blob/main/Support%20Images/Meallion%20Architecture.png)

## Dats Source ER Diagram


![](https://github.com/sairish/Azure-Data-Engineering/blob/main/Data%20Source/Ecomm%20Dataset%20ER%20Diagram.png)
