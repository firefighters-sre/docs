## Database Structure

The architecture utilizes PostgreSQL as its primary database, managing multiple tables related to access, building floors, and environmental conditions.

### External Area Database

This database stores information related to the external area of the building, mainly focusing on tracking people's access to the building.

**Tables**:

- **Person**:
  - **id** (primary key): Unique identifier for each person.
  - **name**: The name of the person.
  - **type**: Categorizes the person as a visitor or employee.
  - **contact**: Contact details for the person (could be a phone number or email).

### SQL Script for External Area Database

```sql
CREATE DATABASE externaldb;

-- Switch to the created database
\c externaldb;

-- Create the AccessLog table
CREATE TABLE AccessLog (
    recordId SERIAL PRIMARY KEY,
    personId INT NOT NULL,
    entryTime TIMESTAMP NOT NULL,
    exitTime TIMESTAMP,
    personType VARCHAR(50) CHECK (personType IN ('visitor', 'employee')),
    destination VARCHAR(255)
);

-- Create the Person table
CREATE TABLE Person (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    type VARCHAR(50) CHECK (type IN ('visitor', 'employee')),
    contact VARCHAR(255)
);
```

### Building Database

This database focuses on the internal structure of the building, capturing details about individual floors, environmental conditions, and potential security threats.

**Tables**:

- **FloorData**:
  - **floor_number** (primary key): Denotes the specific floor within the building.
  - **people_count**: Tracks the current number of people on the floor.
  - **structure_quality**: Rates the structural quality on a scale from 1 to 5.
  - **max_people**: Sets a limit for the maximum number of people allowed on the floor.
  - **o2_level**: Measures the current oxygen level on the floor.
  - **co2_level**: Monitors the carbon dioxide level on the floor.

### SQL Script to Create the Database

```sql
CREATE DATABASE buildingdb;

-- Switch to the created database
\c buildingdb;

-- Create the AccessLog table
CREATE TABLE AccessLog (
    recordId SERIAL PRIMARY KEY,
    personId INT NOT NULL,
    entryTime TIMESTAMP NOT NULL,
    exitTime TIMESTAMP,
    personType VARCHAR(50) CHECK (personType IN ('visitor', 'employee')),
    destination VARCHAR(255)
);

-- Create the FloorData table
CREATE TABLE FloorData (
    floor_number INT PRIMARY KEY,
    people_count INT NOT NULL DEFAULT 0,
    structure_quality INT CHECK (structure_quality BETWEEN 1 AND 5) NOT NULL,
    max_people INT NOT NULL,
    o2_level DECIMAL NOT NULL,
    co2_level DECIMAL NOT NULL
);
```

#### Connecting Building Microservice to PostgreSQL

When deploying the Building Microservice (`building-app`), the connection details to PostgreSQL are provided via environment variables. The Helm chart for `building-app` should have these environment variables already defined:

```yaml
env:
  - name: POSTGRESQL_JDBC_URL
    value: 'jdbc:postgresql://postgresql:5432/firefighters'
  - name: POSTGRESQL_USER
    value: userWPM
  - name: POSTGRESQL_PASSWORD
    value: Oiu5HI4nBLDbYtHo
```

With the PostgreSQL database in place and the Building Microservice correctly configured, the microservice will be able to connect to the database upon deployment, ensuring data persistence and relational data management for the application.

**Note**: Ensure proper security practices are followed. The above demonstration uses hardcoded credentials for simplicity. In a real-world scenario, sensitive data like database passwords should be stored securely, for instance, using OpenShift secrets or external secret management tools.

## Configuring HPA, PDB, SLOs, and SLAs

Using the `.chart/values.yaml` file, you can enable or disable various features and configurations for your application.

### Horizontal Pod Autoscaler (HPA)

HPA automatically scales the number of pods in a deployment depending on the CPU or memory usage. To enable HPA:

```yaml
hpa:
  enabled: true
  cpuTarget: 200m
  memTarget: 300Mi
```

### Pod Disruption Budget (PDB)

PDB limits the number of concurrently disrupted pods during voluntary disruptions. To enable PDB:

```yaml
pdb:
  enabled: true
```
### Service Level Objectives (SLOs) and Service Level Agreements (SLAs)

SLOs define a target level of service that you aim to provide, while SLAs are the formalized commitments regarding the level of service. To configure SLOs and SLAs:

```yaml
prometheus:
  slos:
    enabled: true
    severity: warning
  slas:
    enabled: true
    severity: critical
  fireincident:
    slos: true
    slas: false
```

Ensure that the Prometheus ServiceMonitor is enabled to track the SLOs and SLAs:

```yaml
prometheus:
  servicemonitor:
    enabled: true
```