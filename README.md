# Azure Data Pipeline with Databricks and Delta Lake  

## Overview  
This repository demonstrates an end-to-end data engineering pipeline leveraging Azure services such as Azure Data Factory, Azure Data Lake, and Databricks. The pipeline handles data ingestion, cleaning, transformation, and staging using Delta Lake for efficient and scalable data processing.  

---

## Pipeline Workflow  

1. **Data Ingestion**  
   - Data is ingested daily from a database into the **raw container** of Azure Data Lake using Azure Data Factory.  
   - Supports incremental ingestion with Day 1, Day 2, and so on.

2. **Data Cleaning and Processing**  
   - Ingested data is read into Databricks notebooks.  
   - Cleaning steps include:
     - Handling missing values.
     - Modifying data types.  
   - Cleaned data is written to the **processed container** in Delta Lake format.  

3. **Data Transformation and Staging**  
   - Processed data is read from the **processed container** in Databricks.  
   - Transformation steps include:
     - Joins.
     - Grouping.  
   - Final transformed data is consolidated and written to the **staged container**.  

4. **Pipeline Automation**  
   - The pipeline is triggered via scheduled triggers in Azure Data Factory.  
   - Ensures seamless daily processing of raw, processed, and staged data.

---

## Features  

- **Scalable Data Processing**: Leverages Azure Data Lake and Databricks for large-scale data processing.  
- **Delta Lake**: Ensures ACID transactions and efficient data storage.  
- **Incremental Load**: Supports day-wise data ingestion.  
- **Automated Pipeline**: End-to-end automation with Azure Data Factory triggers.  

---

## Folder Structure  

```plaintext
📁 azure-data-pipeline-databricks  
├── 📂 raw_data  
│   └── Day1_Data.csv  
│   └── Day2_Data.csv  
├── 📂 notebooks  
│   ├── data_cleaning.ipynb  
│   ├── data_transformation.ipynb  
├── 📂 processed_data  
│   └── consolidated_data.delta  
├── 📂 staged_data  
│   └── final_output.delta  
├── 📂 pipeline  
│   ├── azure_data_factory_pipeline.json  
├── 📜 README.md  
└── 📜 LICENSE


## **How to Use**

1. **Clone the Repository**  
   - Run the following commands in your terminal:  
     ```bash
     git clone https://github.com/saibdp/azure-data-pipeline-databricks.git
     cd azure-data-pipeline-databricks
     ```

2. **Set Up Azure Resources**  
   - Create an Azure Data Lake Storage account.  
   - Create a Databricks workspace.  
   - Set up Azure Data Factory and import the pipeline JSON from the `pipeline` folder.  

3. **Run Databricks Notebooks**  
   - Upload the notebooks from the `notebooks` folder to your Databricks workspace.  
   - Update configurations such as storage account credentials and paths.  

4. **Trigger the Pipeline**  
   - Use Azure Data Factory to trigger the pipeline.  
   - Monitor pipeline execution and data flow.  

---

## **Requirements**  

- Azure Subscription  
- Databricks Workspace  
- Azure Data Factory  
- Python 3.x  
