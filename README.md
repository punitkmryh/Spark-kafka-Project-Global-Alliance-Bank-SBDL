# Spark-kafka-Project-Global-Alliance-Bank-SBDL
The Project is SBDL – Spark bulk data load Application.project addresses the data distribution challenges faced by a multinational bank in disseminating accurate entity data from its Master Data Management (MDM) platform to downstream systems efficiently.

# Project Name L Global Alliance Bank SBDL using Kafka

# SBDL – Spark Bulk Data Load Application

## Introduction

The SBDL (Spark Bulk Data Load) application addresses the challenges faced by a multinational bank in efficiently disseminating accurate entity data from its Master Data Management (MDM) platform to downstream systems. This capstone project proposes a Kafka-based data pipeline to ensure scalability and efficiency in synchronizing data without overloading the MDM platform.

## Project Background Overview

### Current Challenges

Downstream systems necessitate a local copy of MDM entities for reporting and predictive analytics. The existing API interface is not scalable for multiple downstream systems, prompting the need for a Kafka-based solution.

### Proposed Solution

The project proposes a Spark-based solution that ingests entity data from Hive tables, processes it, and publishes it to Kafka topics. This approach decouples downstream systems from direct connections to the MDM platform, ensuring scalability and ease of synchronization.

## Project Scope

### System Components

- **MDM Platform:** Central repository for entity data.
- **Kafka Cluster:** Scalable and efficient data distribution.
- **Hadoop Cluster with Hive and Spark:** Utilized for data processing and ingestion.

### Data Flow Overview

1. **Data Ingestion:**
   - MDM exports complete entity data to Hive tables daily, maintaining a 7-day history.

2. **Spark Application:**
   - A Spark application processes entity data for a specified load_date.
   - The application is designed for modular processing and adheres to best practices.

3. **Kafka Integration:**
   - Processed entity data is published to Kafka topics for downstream consumption.

4. **Best Practices:**
   - Modular design and code reuse principles are followed.
   - Unit testing ensures the reliability of the Spark application.

## Data Sources

The primary data source is the MDM platform, exporting entity data to Hive tables. The Spark application reads data from these Hive tables based on the specified load_date.

## Requirements

1. **Data Ingestion:**
   - Utilize Hive tables partitioned by load_date.
   - Ingest complete entity data for the specified load_date.

2. **Spark Application:**
   - Accept load_date as an input argument.
   - Read and process entity data from Hive tables.
   - Adhere to modular design and code reuse principles.
   - Publish processed data to Kafka topics.

3. **Kafka Integration:**
   - Establish a connection to the Kafka cluster.
   - Publish processed entity data to relevant Kafka topics.

4. **Best Practices:**
   - Implement modular design and code reuse.
   - Conduct unit testing for code reliability.

## Process and Data Flow

### 1. Data Ingestion Process

- MDM exports complete entity data to Hive tables daily.
- Data is partitioned by load_date.

### 2. Spark Application Process

- Accepts load_date as an input argument.
- Reads entity data from Hive tables for the specified load_date.
- Applies modular processing logic.
- Publishes processed data to Kafka topics.

### 3. Kafka Data Flow

- Downstream systems subscribe to relevant Kafka topics.
- Processed entity data is consumed by downstream systems.

## Best Practices

1. **Modular Design:**
   - Implement a modular structure for the Spark application, allowing easy maintenance and scalability.

2. **Code Reuse:**
   - Encourage the reuse of code components to enhance efficiency and reduce redundancy.

3. **Unit Testing:**
   - Conduct thorough unit testing to ensure the reliability of the Spark application.

## Data Processing Requirements

- **Entity-Specific Transformations:**
  - Detail specific transformations and processing steps for each entity, considering data cleansing, enrichment, and formatting.

## Spark Application Development

### Implementation

- Document the actual implementation of the Spark application, ensuring parameterized execution and adherence to best practices.

### Testing

- Outline testing procedures, including unit testing and any integration testing with the Kafka cluster.

## Performance Optimization

### Resource Estimation

- Provide guidelines for estimating the required resources based on data analysis and workload.

### Job Configuration

- Recommend Spark job configurations for optimal performance.

## CI/CD Pipeline Setup

### Setup Procedures

- Detail the steps taken to set up the CI/CD pipeline, including collaboration with the DevOps team.

### Testing Automation

- Explain how testing procedures are automated in the CI/CD pipeline.

## Documentation

- **User Instructions:**
  - Provide clear instructions on how to use the Spark application, specifying input parameters and expected outputs.

- **Code Documentation:**
  - Include inline comments and documentation within the code for easy comprehension and maintenance.

- **Performance Tuning Recommendations:**
  - Offer recommendations for performance tuning based on the analysis and optimization efforts.


## Getting Started

Follow the steps in the [Getting Started Guide](./docs/getting-started.md) to set up and run the Spark application.

## Contributing

If you'd like to contribute to the project, please follow the [Contribution Guidelines](./CONTRIBUTING.md).

## License

This project is licensed under the [MIT License](./LICENSE).
