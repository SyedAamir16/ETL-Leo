# ETL-Leo

AWS Glue PySpark ETL pipeline for Leo antenna purchase data.

## Architecture

```text
PostgreSQL -> AWS Glue PySpark -> S3 (Parquet) -> Glue Catalog -> Redshift
                                       |
                                  CloudWatch
```

## Layout

- `src/main.py`: Glue entry point
- `src/jobs/leo_antenna_etl.py`: ETL implementation
- `src/tests/test_transformations.py`: unit tests
- `infrastructure/cloudformation.yaml`: AWS resources
- `config/job_parameters.json`: documented job parameters

## Expected source columns

- `order_id` (primary key)
- `customer_id`
- `antenna_model`
- `quantity`
- `unit_price`
- `purchase_date`
- `updated_at`

Override `SOURCE_TABLE`, `PRIMARY_KEY`, and `UPDATED_AT_COLUMN` in Glue job parameters.
