EDA on COVID-19 India & World Data

Notebooks also available on Kaggle:

India: https://www.kaggle.com/ankitrathi/eda-on-covid-19-india-patient-database

World: https://www.kaggle.com/ankitrathi/eda-on-covid-19-world-data-by-jhu-csse


Table: api_requests
Columns:
- request_id (PK, serial): Unique identifier for each API request
- request_type (varchar): Type of the API request
- request_category (varchar): Category of the API request
- request_parameters (jsonb): Flexible parameters for the API request
- response_parameters (jsonb): Flexible parameters for the API response
- status (varchar): Status of the request (e.g., pending, completed, failed)
- timestamp (timestamp): Timestamp of the API request

Table: data_store_configurations
Columns:
- configuration_id (PK, serial): Unique identifier for each data store configuration
- request_category (varchar): Category of the request for which the configuration applies
- source_configurations (jsonb): Flexible configurations for the data source (e.g., connection details)
- destination_configurations (jsonb): Flexible configurations for the data destination (e.g., connection details)

Table: request_processing
Columns:
- processing_id (PK, serial): Unique identifier for each processing operation
- request_id (FK): Foreign key referencing the api_requests table
- operation_type (varchar): Type of processing operation (e.g., read, write, reconcile)
- operation_status (varchar): Status of the processing operation (e.g., success, failure)
- operation_details (jsonb): Flexible details about the processing operation
- source_configuration_id (FK): Foreign key referencing the data_store_configurations table for source
- destination_configuration_id (FK): Foreign key referencing the data_store_configurations table for destination
- timestamp (timestamp): Timestamp of the processing operation

Table: reconciliation
Columns:
- reconciliation_id (PK, serial): Unique identifier for each reconciliation record
- processing_id (FK): Foreign key referencing the request_processing table
- source_details (jsonb): Details about the source files (e.g., size, count, hash keys)
- destination_details (jsonb): Details about the destination files (e.g., size, count, hash keys)
- timestamp (timestamp): Timestamp of the reconciliation process

