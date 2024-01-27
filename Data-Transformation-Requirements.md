# Data Transformation Requirements

## Project Overview

### Objective

The primary goal of this project is to establish a robust and scalable data pipeline to synchronize Master Data Management (MDM) entity data to downstream systems through Kafka. The project focuses on transforming raw entity data stored in Hive tables into a JSON format that adheres to a specific structure and publishing it to relevant Kafka topics.

### Data Sources

#### Entity Structure

The primary entity for this project is the "Account" entity, consisting of data from three primary Hive tables:

1. **Account Table**
   - Fields: active indicator, account id, account start date, legal title one, legal title two, etc.

2. **Parties Table**
   - Fields: party id (primary key), account id (foreign key), etc.

3. **Addresses Table**
   - Fields: address id (primary key), party id (foreign key), address details, etc.

### Transformation Requirements

#### Entity: Account

#### JSON Structure Explanation

![](https://github.com/punitkmryh/Spark-kafka-Project-Global-Alliance-Bank-SBDL/blob/main/img/account-output-sample.png)


1. **Event Header:**
   - eventIdentifier: A dynamically generated UUID for each record.
   - eventType: A fixed string indicating the type of event. For the account entity, it is "SBDL-Contrat."
   - majorSchemaVersion and minorSchemaVersion: Fixed numbers representing the schema version.
   - eventDateTime: Timestamp indicating when the event was generated.

2. **Keys:**
   - An array representing the keys for the entity. In the case of the account entity, a single key field is used: contractIdentifier (account id).

3. **Payload:**
   - Fields are sent as triplets of operation, oldValue, and newValue.
   - For the current project, the operation is always INSERT, and oldValue is always null.
   - Fields include contractIdentifier (account id), contractStartDateTime (account start date), contractTitle (legal titles), partyRelations (party details including addresses), and other simple fields.

Certainly! Let me explain each section of the JSON template:

1. **eventHeader:** This section contains metadata about the event.
   - eventIdentifier: A unique identifier for each record, represented as a UUID.
   - eventType: A fixed string indicating the type of event, in this case, "SBDL-Contract."
   - majorSchemaVersion and minorSchemaVersion: Fixed numbers representing the schema version.
   - eventDateTime: Timestamp indicating when the event was generated.

2. **keys:** This section contains information about the primary key of the entity.
   - keyField: The name of the key field, in this case, "contractIdentifier."
   - keyValue: The actual value of the key, representing the entity ID.

3. **payload:**
   - contractIdentifier:
     - operation: Describes the type of operation, and in this context, it is an INSERT operation.
     - newValue: Contains the actual value of the contract identifier associated with the contract.
   - sourceSystemIdentifier:
     - operation: Specifies the type of operation, and it is an INSERT operation in this case.
     - newValue: Represents the source system identifier associated with the contract.
   - contactStartDateTime:
     - operation: Indicates the type of operation, which is an INSERT operation.
     - newValue: Contains the start date and time of the contract.
   - contractTitle:
     - operation: Specifies the type of operation, and it is an INSERT operation.
     - newValue: An array representing legal titles associated with the contract. Each legal title is represented as a JSON object with a type (contractTitleLineType) and a value (contractTitleLine).
   - taxIdentifier:
     - operation: Describes the type of operation, and it is an INSERT operation.
     - newValue: Contains information about the tax identifier, including the type (taxIdType) and the actual identifier value (taxId).
   - contractBranchCode:
     - operation: Indicates the type of operation, which is an INSERT operation.
     - newValue: Represents the branch code associated with the contract.
   - contractCountry:
     - operation: Specifies the type of operation, and it is an INSERT operation.
     - newValue: Represents the country associated with the contract.
   - partyRelations:
     - An array representing relationships with parties associated with the contract.
     - Each partyRelation is a JSON object with the following fields:
       - partyIdentifier:
         - operation: Describes the type of operation, and it is an INSERT operation.
         - newValue: Represents the ID of the party associated with the contract.
       - partyRelationshipType:
         - operation: Specifies the type of operation, which is an INSERT operation.
         - newValue: Represents the type of relationship with the party.
       - partyRelationStartDateTime:
         - operation: Indicates the type of operation, which is an INSERT operation.
         - newValue: Represents the start date and time of the party's relationship with the contract.
       - partyAddress:
         - operation: Specifies the type of operation, which is an INSERT operation.
         - newValue: Contains address information associated with the party, including address lines, city, postal code, country, and the start date of the address.

Each field within the payload has the structure:
- operation: The type of operation (INSERT).
- oldValue: Null (as we are focusing on INSERT operations).
- newValue: The actual value from the source data.

## High-Level Approach

1. **Read Data from Hive Tables:**
   - Utilize Apache Spark to read data from the Hive tables for the specified load_date. Use Spark SQL for efficient querying.

2. **Transform Data:**
   - Apply entity-specific transformations to merge data from multiple tables.
   - Create a JSON structure following the specified format. Handle complex fields like legal titles and party relations.

3. **Send to Kafka:**
   - Establish a connection to the Kafka cluster using the Kafka Producer API.
   - Publish the processed entity data to relevant Kafka topics. Ensure proper error handling and logging.

## Detailed Transformation Steps

1. **Read Data from Hive Tables**
   - Utilize Spark SQL to perform SQL queries on Hive tables.
   - Read data from the three tables - Accounts, Parties, and Addresses.
   - Apply necessary filters and conditions based on the load_date parameter.

2. **Transform Data**
   - Implement entity-specific transformations.
   - Merge data from the three tables to create a unified entity record.
   - Handle relationships between entities (e.g., account to party relationships).
   - Aggregate and structure data as per the JSON format.

3. **Send to Kafka**
   - Configure Kafka producer settings using Spark configurations.
   - Establish a connection to the Kafka cluster.
   - Publish the transformed entity data to the relevant Kafka topics.
   - Implement error handling and logging for data publishing.

## Conclusion

This detailed document provides a comprehensive understanding of the MDM to Kafka data pipeline project. It includes insights into data sources, transformation requirements, and a step-by-step approach to achieve the project objectives.


