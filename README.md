# Healthcare-Data-Analysis-Using-Azure-Databricks
Insights into Patient Demographics and Seasonal Trends

## Project Description
This project leverages Azure Databricks and Power BI to analyze healthcare data, focusing on patient demographics, the prevalence of medical conditions, and seasonal trends in hospital admissions. It aims to provide actionable insights that could help in strategic healthcare planning and operational adjustments according to seasonal demands.

## Data Source
The data comes from a detailed <a href = "https://www.kaggle.com/datasets/prasad22/healthcare-dataset?resource=download"> dataset </a>
 available on Kaggle, encompassing patient information, medical conditions, admission types, and healthcare costs.

## Technologies Used
- Azure Databricks: For data processing and analysis.
- Azure Blob Storage: For secure data storage.
- Power BI: This is used to create interactive visualizations and dashboards.

## Setup and Execution
Mount Azure Blob Storage on Databricks
```python
dbutils.fs.mount(
  source="wasbs://CONTAINER_NAME@STORAGE_ACCOUNT_NAME.blob.core.windows.net",
  mount_point="/mnt/mount1",
  extra_configs={"fs.azure.account.key.healthcarebigdata.blob.core.windows.net": "YOUR_SECRET_KEY"}
)
```
## Load and Prepare the Data
```python
df = spark.read.format("csv").option("header", "true").load("/mnt/mount1/healthcare_dataset.csv")
```
## Seasonal Trends in Hospital Admissions
Categorize hospital admissions by season and type to assess the healthcare demand fluctuations throughout the year.
```python
df.groupBy("Season", "Admission Type").count().show()
```
## Visualizations and Dashboards
Developed Power BI dashboard to visualize and interact with the analysis results

<img width="749" alt="image" src="https://github.com/user-attachments/assets/af4b487e-0484-4245-b2cf-98ad0b44b084">


Shows number of patients for each medical condition by season

<img width="780" alt="image" src="https://github.com/user-attachments/assets/8f6d7302-1cd0-4800-af33-af9e9f4bb6db">

## Insights from Healthcare Data Analysis

### Seasonal Variations in Medical Conditions:
- **Asthma:** Higher case rates in Spring and Summer.
- **Diabetes:** Stable prevalence year-round, slight increase in Summer.
- **Cancer:** Increased incidences during colder months (Winter and Fall).

### Admission Trends:
- **Elective Admissions:** Consistent across all seasons, with a slight uptick in Summer.
- **Emergency Admissions:** Peak during Fall.
- **Urgent Admissions:** Highest in Spring, decreasing through to Summer.

## Impact of the Analysis

- **Resource Allocation:** Optimizes staffing, bed availability, and medical supplies based on predicted seasonal demands.
- **Public Health Interventions:** Supports targeted interventions like asthma awareness in Spring and enhanced oncology support in Winter.
- **Policy Making:** Aids in developing adaptive healthcare policies to ensure efficient patient care throughout the year.

## Contributions to the Project

### Project Roles:
- **Data Acquisition and Integration:** Led the consolidation of datasets into Azure Blob Storage.
- **Data Processing and Analysis:** Utilized Azure Databricks for efficient data processing.
- **Seasonal Analysis Implementation:** Developed algorithms to identify seasonal healthcare trends.
- **Visualization and Reporting:** Created Power BI visualizations to disseminate insights.

### Individual Contributions:
- Developed the complete data pipeline from ingestion to visualization.
- Authored project documentation and analysis reports.
- Conducted training on utilizing data dashboards for healthcare operations.
