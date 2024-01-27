# Spark-kafka-Project-Global-Alliance-Bank-SBDL
The Project is SBDL – Spark bulk data load Application.project addresses the data distribution challenges faced by a multinational bank in disseminating accurate entity data from its Master Data Management (MDM) platform to downstream systems efficiently.

# Project Name L Global Alliance Bank SBDL using Kafka

## Project Overview

This repository contains the source code and documentation for the "Global Alliance Bank SBDL using Kafka" project. The project involves building a scalable data pipeline between the Master Data Management (MDM) platform of Global Alliance Bank and Apache Kafka for downstream systems.

## Table of Contents

- [Introduction](#introduction)
- [Project Background](#project-background)
- [Scope](#scope)
- [Data Sources](#data-sources)
- [Requirements](#requirements)
- [Data Processing and Transformation](#data-processing-and-transformation)
- [Spark Application Development](#spark-application-development)
- [Testing](#testing)
- [Performance Optimization](#performance-optimization)
- [CI/CD Pipeline Setup](#cicd-pipeline-setup)
- [Documentation](#documentation)
- [Getting Started](#getting-started)
- [Contributing](#contributing)
- [License](#license)

## Introduction

Global Alliance Bank SBDL (Scalable Batch Data Loading) using Kafka is a project designed to create a robust data pipeline for synchronizing master data within the bank's enterprise. The project leverages Apache Kafka for efficient and scalable data transfer between the MDM platform and downstream systems.

## Project Background

Large multinational banks often face challenges in managing and sharing accurate entity data across various lines of business and systems. The MDM platform serves as a central data management solution, and this project focuses on optimizing data transfer from MDM to downstream systems using Kafka.

## Scope

The project scope includes:
- Reading entity data from MDM stored in Hive tables.
- Processing and transforming data according to business requirements.
- Sending prepared entity data to Apache Kafka topics.
- Implementation of a batch data flow pipeline with customizable synchronization frequencies.

## Data Sources

The MDM platform exports entity data to Hive tables daily. The project utilizes the exported data from these tables for further processing.

## Requirements

The detailed project requirements, including data structures, transformations, and business logic, are documented in the [Requirements Document](./docs/requirements.md).


## Architecture

The project leverages Apache Kafka as a central message broker to facilitate communication between the MDM system and downstream applications. Data is exported from the MDM platform to Hadoop Hive tables, and the Spark application processes and transforms the data before publishing it to Kafka topics.

![Project Architecture](docs/images/architecture.png)

## Requirements

- Java 8 or later
- Apache Spark
- Apache Kafka
- Hadoop Hive
- ...

## Data Processing Pipeline

### Entity-Specific Transformations

The project performs entity-specific transformations, including data cleansing, enrichment, and formatting. Each entity has its transformation logic defined in the Spark application.

### Spark Application Development

#### Implementation

The Spark application is developed to read entity data from Hive tables, process it according to the transformation requirements, and publish the prepared data to Kafka topics.

#### Testing

Unit testing is implemented for the Spark application, ensuring the correctness of the transformation logic. Integration testing is also performed with the Kafka cluster to validate end-to-end functionality.

## Usage

1. Clone the repository:

    ```bash
    git clone https://github.com/yourusername/global-alliance-bank-sbdl-kafka.git
    cd global-alliance-bank-sbdl-kafka
    ```

2. Build the Spark application:

    ```bash
    ./build.sh
    ```

3. Run the Spark application:

    ```bash
    spark-submit --class com.example.Main --master local[2] target/global-alliance-bank-sbdl-kafka.jar
    ```

## Data Processing and Transformation

Entity-specific transformations are applied to cleanse, enrich, and format the data. The [Data Processing Requirements Document](./docs/data-processing-requirements.md) outlines the specific transformations for each entity.

## Spark Application Development

The Spark application is developed using PySpark. The [Spark Application Code](./src/spark_app.py) is organized and follows best practices for modular design and code reuse.

## Testing

The testing procedures, including unit testing and integration testing with the Kafka cluster, are documented in the [Testing Document](./docs/testing.md).

## Performance Optimization

Guidelines for estimating required resources, recommending Spark job configurations, and optimizing performance are detailed in the [Performance Optimization Document](./docs/performance-optimization.md).

## CI/CD Pipeline Setup

The setup procedures for the CI/CD pipeline, collaboration with the DevOps team, and testing automation are outlined in the [CI/CD Pipeline Setup Document](./docs/cicd-pipeline-setup.md).

## Documentation

Additional documentation, including user instructions, code documentation, and performance tuning recommendations, can be found in the [Documentation Folder](./docs/).

## Getting Started

Follow the steps in the [Getting Started Guide](./docs/getting-started.md) to set up and run the Spark application.

## Contributing

If you'd like to contribute to the project, please follow the [Contribution Guidelines](./CONTRIBUTING.md).

## License

This project is licensed under the [MIT License](./LICENSE).
