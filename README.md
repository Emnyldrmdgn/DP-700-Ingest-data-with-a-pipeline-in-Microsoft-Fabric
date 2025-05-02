# DP-700-Ingest-data-with-a-pipeline-in-Microsoft-Fabric
By combining the pipeline and Spark capabilities in Fabric, you can implement complex data ingestion logic that copies data from external sources into the OneLake storage on which the lakehouse is based, and then uses Spark code to perform custom data transformations before loading it into tables for analysis.

This guide explains how to ingest data from an external source into a Lakehouse using a pipeline in Microsoft Fabric. The process includes extracting the data, loading it into OneLake storage, and optionally transforming it with Apache Spark.


## 📌 Objective
This project demonstrates how to implement a data ingestion pipeline in Microsoft Fabric to automate the process of copying data from an external source into a lakehouse. The data is then transformed using Apache Spark and stored in a table for analysis.

## 🧰 Prerequisites
- Access to Microsoft Fabric (Trial, Premium, or Fabric capacity workspace)
- A Microsoft account with Fabric access

## 🗂️ Steps

### 1. Create a Workspace
- Go to the Microsoft Fabric homepage: https://app.fabric.microsoft.com/
- From the left menu, select **Workspaces** > **+ New workspace**
- Name your workspace and ensure it uses a Fabric-supported license

### 2. Create a Lakehouse
- In your workspace, select **Create > Lakehouse** and give it a unique name
- In the **Files** section of the lakehouse, create a subfolder named `new_data`

### 3. Create a Data Pipeline
- From the lakehouse homepage, click **Get Data > New data pipeline**
- Use the **Copy Data assistant** to configure the pipeline:
  - Source type: HTTP
  - URL: `https://raw.githubusercontent.com/MicrosoftLearning/dp-data/main/sales.csv`
  - Destination: `Files/new_data/sales.csv`

### 4. Create and Configure a Notebook
- From the lakehouse homepage, select **Open notebook > New notebook**
- Replace the default cell with the following parameter cell:
  ```python
  table_name = "sales"

### 5. Modify the Pipeline to Include Notebook Execution
Add a Delete Data activity before the Copy Data step to clean up existing CSVs in new_data

Add a Notebook activity after the Copy Data step:

Notebook: Load Sales

Base parameter: table_name = "new_sales"![fabriclab4_5_5](https://github.com/user-attachments/assets/45237061-1c35-42bc-9420-68c813bc9389)
![fabriclab4_5_4](https://github.com/user-attachments/assets/6cd0fdee-ab0e-4767-a4bd-609ab4096d99)


### 6. Verify Results
Open your lakehouse and refresh the Tables section

Confirm that a new table named new_sales is created

Preview the ingested and transformed data
![fabriclab4_5_3](https://github.com/user-attachments/assets/91ba8f06-836b-46d7-868a-98fea61d7f9f)

### 🧹 Clean Up
When finished, you can delete the workspace:

Open the workspace settings

Scroll down and select Remove this workspace

Confirm deletion

### Screenshots

![fabriclab4](https://github.com/user-attachments/assets/234594de-97d9-441d-b0a2-c872c9d63a4f)
![fabriclab4_2](https://github.com/user-attachments/assets/854201e9-a373-49bf-8b6f-dd06ec3c2653)
![fabriclab4_3](https://github.com/user-attachments/assets/7a2b3e1a-d9c7-474c-85fb-8c36a13b7968)
![fabriclab4_4](https://github.com/user-attachments/assets/c9fc5eaf-cb0b-4d82-99a4-22c882651724)
![fabriclab4_5](https://github.com/user-attachments/assets/c99a5c6e-6677-43af-ad1b-47155425cb47)
![fabriclab4_5_1](https://github.com/user-attachments/assets/4ffa87e5-9068-49f4-9d6e-dabf2e53de39)
![fabriclab4_5_2](https://github.com/user-attachments/assets/2c172d71-e69d-43d0-a669-4b52353a2645)
![fabriclab4_5_3](https://github.com/user-attachments/assets/ff2fff02-62c1-4f17-b50a-7b54fe242c5c)
![fabriclab4_5_4](https://github.com/user-attachments/assets/4a6e4314-672a-4329-aa6b-d916d85da858)
![fabriclab4_5_5](https://github.com/user-attachments/assets/1a5b1bf2-cc4c-4ec2-ae5c-e8897b9fe634)
![fabriclab4_5_6](https://github.com/user-attachments/assets/d0e426d8-26aa-4531-bd60-1dd0788d2120)
![fabriclab4_5_7](https://github.com/user-attachments/assets/6124b61d-80f6-4aff-a2d9-ca638b22d9aa)
![fabriclab4_6](https://github.com/user-attachments/assets/2301c32b-e5da-44f7-87c5-2dd37527f81c)
