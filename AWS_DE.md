### AWS Data Engineering Project – End-to-End Explanation

As an AWS Data Engineer, my role involves designing, developing, deploying and maintaining end-to-end data pipelines using AWS services such as S3, Lambda, Glue, EMR, MWAA, Athena and Redshift.

On a daily basis, upstream source systems ingest data into Amazon S3, which acts as our landing and raw storage layer.

Whenever a new file arrives in S3, an S3 event notification triggers an AWS Lambda function. The Lambda function performs initial validations, such as checking the file name, file extension, file format and required metadata. Once the validation is successful, it triggers the corresponding Airflow DAG through the MWAA REST API.

In MWAA, we define DAGs to orchestrate the complete ETL workflow, including task dependencies, retries, monitoring and failure handling.

As part of the workflow, we use AWS Glue Crawlers to discover the source schema and register the metadata in the Glue Data Catalog. For subsequent daily loads with an unchanged schema, we reuse the existing catalog metadata rather than running crawlers unnecessarily.

For data processing, we use AWS Glue ETL jobs with PySpark. We also use Amazon EMR for large-scale or complex Spark processing workloads, depending on the processing requirements.

Within our PySpark scripts, we implement business transformation logic such as joins, aggregations, duplicate removal, null handling, data validation and incremental processing.

After the initial transformations, we write the validated and cleansed datasets into the Silver layer in S3, generally using Parquet format.

From the Silver layer, we perform further business-level transformations and aggregations to create the Gold layer. This includes preparing business-ready datasets with appropriate dimensions, metrics and measures for downstream reporting and analytics.

We then load the curated datasets into Amazon Redshift using staging tables and incremental loading strategies, including appropriate deduplication and merge logic to maintain data consistency.

Additionally, we use Amazon Athena to query datasets directly from S3 using the Glue Data Catalog. This helps us perform ad hoc analysis and validate the processed datasets without necessarily loading them into Redshift.

Finally, we monitor pipeline execution through Airflow, CloudWatch and job logs, investigate failures, optimize Spark performance and ensure reliable data delivery to downstream consumers.


DQ Checks:
We implement data validations at each layer of the Medallion Architecture, with different validation objectives.

In the Bronze layer, we focus mainly on ingestion-level validations, such as file availability, file format, file size, duplicate file detection and basic schema checks. We preserve the original source data for traceability.

In the Silver layer, we perform data quality and cleansing operations using PySpark. This includes null handling, duplicate removal, data type validation, business key validation, referential integrity checks and handling invalid records. We separate invalid records into a quarantine location rather than silently dropping them.

In the Gold layer, we focus on business-level validations. We validate aggregations, transaction counts, financial totals, dimension and fact relationships, and business KPIs. We also perform reconciliation between Silver and Gold datasets to ensure that the business metrics are accurate.

We orchestrate these validation activities through MWAA, capture validation metrics and use CloudWatch for monitoring and alerting. If critical validations fail, we prevent the affected dataset from being published to downstream consumers.



### PayPal – Merchant Payment Analytics Platform

I worked on a merchant-oriented payment analytics platform where our objective was to consolidate payment-related data and provide merchant-level business insights for reporting and analytics.

We worked with multiple datasets, including merchant master data, payment transactions, refunds, settlement records, and disputes. These datasets helped business teams analyze merchant payment performance, transaction success rates, refund trends, settlement amounts, and chargeback activity.

Data was received from upstream systems and ingested into Google Cloud Storage. We used Cloud Composer (Apache Airflow) to orchestrate the end-to-end data pipeline and manage dependencies between different processing tasks.

We used Dataproc with PySpark to perform distributed data processing. Our transformations included schema validation, data cleansing, null handling, duplicate removal, joins, and aggregations.

We joined payment transactions with merchant master data using merchant ID and integrated refund and dispute information using transaction IDs. We also processed settlement records to calculate gross amounts, transaction fees, and net settlement amounts.

We followed a Bronze, Silver, and Gold architecture. The Bronze layer stored raw source data, the Silver layer contained cleansed and standardized datasets, and the Gold layer contained business-ready merchant-level reporting datasets.

In the Gold layer, we created merchant-level metrics such as total payment volume, successful and failed transactions, payment success rate, total refunds, net payment volume, and settlement summaries.

We stored the processed datasets in Parquet format in GCS and loaded the curated datasets into BigQuery using incremental processing.

The downstream BI and business teams used these BigQuery tables to build dashboards and analyze merchant performance across different countries, business categories, and reporting periods.

We also handled duplicate records, late-arriving transactions, data-quality validations, and pipeline failures to maintain data consistency and reliability.
