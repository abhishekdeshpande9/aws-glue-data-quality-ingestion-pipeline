# aws-glue-data-quality-ingestion-pipeline
Automated data ingestion and quality pipeline using AWS Glue, Redshift, S3, and EventBridge.

Automated Quality Data Ingestion Pipeline with AWS Glue & Redshift

Overview
This project solves a common data engineering problem:
How do you ingest only new data, validate it before storing, and stay informed  without manually checking logs?

Built using AWS Glue, Redshift, S3, and supporting services, this pipeline handles incremental ingestion, performs data quality checks, routes data accordingly, and sends notifications after each run.

Tech Stack
AWS Glue:	ETL job, job bookmarks, data quality checks
AWS S3: Data lake for raw and rejected data
AWS Redshift: Data warehouse for clean, validated data
AWS SNS: Email notifications
AWS EventBridge: Triggers SNS after job completion

Architecture
Pipeline Flow:
New CSV or Parquet files are dropped into an S3 bucket.
AWS Glue Job with bookmarking picks up only the new files.
Glue Data Quality Ruleset runs validation checks.
Records passing validation are loaded into Redshift.
Failed records are stored in a  separate S3 folder for review.
EventBridge triggers SNS to send notifications after each run.
