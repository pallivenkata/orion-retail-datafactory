
Orion Retail Full Enterprise Project (ADF) - Package
Generated: 2025-11-17T16:17:41.129311Z

This package contains ADF JSON artifacts (skeletons) to import into your ADF Git repo.
Paths inside ZIP correspond to the Git factory layout expected by Azure Data Factory Git mode:

factory/
  linkedService/
  dataset/
  pipeline/
  factory.json
  publish_config.json
  README_Orion_Project.txt

IMPORTANT: Replace placeholders after import:
 - Storage account key in LS_Blob_Orion.json (YOUR_STORAGE_KEY)
 - Databricks token in LS_Databricks_Orion.json (DATABRICKS_TOKEN_PLACEHOLDER)
 - Any SQL credentials if you want to change them (or move secrets to Key Vault and update LS_KeyVault_Orion.json)
 - Update connection names if your environment uses different server names

IMPORT FLOW (Recommended using Git integration):
1) Connect your ADF to this GitHub repo (Manage -> Git configuration)
2) Ensure repository root points to /factory (we used /factory)
3) In GitHub push the entire 'factory' folder's contents (datasets, linkedService, pipeline, factory.json)
4) In ADF Studio (Author) you'll see the pipelines/datasets/linked services loaded from Git
5) Click 'Publish' to create adf_publish branch and deploy to live Data Factory
6) Update Linked Services secrets and test pipelines (Debug)

TEST SCENARIOS:
 - Upload sample files to blob: processed/csv/<yyyy-MM-dd>/Sales.csv etc.
 - Run PL_Day04_Recursive_ProcessedToStaging (Debug) to stage files to SQL staging tables
 - Run PL_SCD2_Upsert to test SCD2 merge (Databricks notebook must be provided)
 - Test PL_Incremental_Watermark: configure watermark table and run

SECURITY NOTE:
 - Rotate SQL password after import if embedded
 - Ideally store secrets in Key Vault and reference them from Linked Services

If you want, I will now:
 - Push these artifacts into your GitHub repo for you (requires repo permission)
 - Or guide you to upload them (I recommend manual commit or drag-drop for learning)
