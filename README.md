# S3 to Databricks Delta Table Pipeline

This project demonstrates how to set up a data pipeline that processes documents from an S3 bucket and loads them into a Databricks Delta table using Unstructured's platform. The pipeline includes document processing, chunking, and embedding generation.

## Overview

The pipeline performs the following steps:
1. Connects to an S3 bucket containing source documents
2. Processes and chunks the documents using Unstructured's platform
3. Generates embeddings using Azure OpenAI's text-embedding-3-small model
4. Loads the processed data into a Databricks Delta table

## Prerequisites

Before running this pipeline, ensure you have:

1. **Unstructured Platform Access**
   - An account on Unstructured's platform
   - API key for authentication


2. **AWS S3**
   - Access to an S3 bucket containing source documents
   - AWS credentials with appropriate permissions

3. **Databricks**
   - Access to a Databricks workspace
   - Service principal credentials
   - Catalog and schema where the data will be stored

## Setup Instructions

1. **Install Dependencies**
   ```bash
   pip install unstructured-client
   ```

2. **Configure Environment Variables**
   Create a `.env` file with the following variables:
   ```
   UNSTRUCTURED_API_KEY=your_api_key
   AZURE_OPENAI_API_KEY=your_azure_openai_key
   AWS_ACCESS_KEY_ID=your_aws_access_key
   AWS_SECRET_ACCESS_KEY=your_aws_secret_key
   DATABRICKS_HOST=your_databricks_host
   DATABRICKS_TOKEN=your_databricks_token
   ```

3. **Update Configuration**
   In the notebook, update the following parameters:
   - S3 bucket name and prefix
   - Databricks catalog and schema
   - Table name (optional)
   - Embedding model configuration

4. **Run the Pipeline**
   - Open the `S3_to_DatabricksVolume.ipynb` notebook
   - Execute cells in sequence
   - Monitor the workflow execution through the polling mechanism

## Workflow Components

The pipeline consists of the following main components:

1. **Source Connector**: S3 bucket containing source documents
2. **Processor**: Document processing and chunking
3. **Embedder**: Azure OpenAI text embedding generation
4. **Destination Connector**: Databricks Delta table

## Output

Upon successful execution:
- Processed documents are stored in the specified Databricks Delta table
- If no table name is provided, Unstructured creates one with a name starting with "u"
- The table is initially accessible only to the service principal
- Additional permissions may need to be granted for user access

## Troubleshooting

1. **Authentication Issues**
   - Verify all API keys and credentials are correct
   - Check permissions for S3 bucket and Databricks workspace

2. **Workflow Execution**
   - Monitor the job status through the polling mechanism
   - Check logs for any error messages
   - Verify the Databricks table creation and data loading

3. **Data Access**
   - Ensure proper permissions are granted to access the Databricks table
   - Verify the table exists in the specified catalog and schema

## Support

For additional support or questions:
- Refer to Unstructured's documentation
- Contact your Databricks administrator