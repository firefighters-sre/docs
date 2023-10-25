# Firefighters SRE Workshop Platform

### Architecture Components

1. **Kafka (AMQ Streams)**: A distributed streaming platform for building real-time data pipelines. Used for messaging and data streaming between microservices.
2. **Prometheus**: An open-source systems monitoring and alerting toolkit. Collects metrics from configured targets at given intervals, evaluates rule expressions, and can trigger alerts if certain conditions are observed.
3. **Grafana**: An open-source platform for monitoring and observability. Used for visualizing Prometheus metrics.
4. **Jaeger**: An end-to-end distributed tracing tool for monitoring and troubleshooting transactions in complex, distributed systems.

5. **KEDA (Kubernetes Event-Driven Autoscaling)**: Allows for advanced autoscaling, including event-driven scaling. **!OPTIONAL**
6. **Red Hat OpenShift Pipelines**: Provides a Kubernetes-native CI/CD solution based on Tekton, which is part of the CD Foundation. **!OPTIONAL**

### Microservices

1. 🛎️ [**Access Microservice (concierge-app)**](https://github.com/firefighters-sre/concierge-app): Gerencia a entrada e saída de indivíduos do edifício.
2. 🚶‍♂️🔝 [**Mobility Microservice (mobility-app)**](https://github.com/firefighters-sre/mobility-app): Monitora e gerencia a utilização de escadas e elevadores.
3. 🏠 [**Building Microservice (building-app)**](https://github.com/firefighters-sre/building-app): Gerencia informações relacionadas ao edifício, como temperatura, qualidade do ar e ocupação do piso.

### Namespaces

1. **quarkus-dev**: Houses the Quarkus-based microservices.
2. **kafka-streaming**: Dedicated to Kafka components, including brokers and topics.
3. **kafka-logging**: Used for monitoring components like Prometheus and Grafana.
4. **openshift-distributed-tracing**: Dedicated to hosting distributed tracing components for monitoring and troubleshooting microservices-based distributed systems.

## Prerequisites

- OpenShift Cluster (OCP)
- Helm 3.x
- OpenShift CLI (`oc`)

## Quick Start
### Create Namespaces
1. Quarkus Development: Houses the Quarkus microservices.
```bash
oc new-project quarkus-dev
```
2. Kafka Streaming: For Kafka clusters and topics.
```bash
oc new-project kafka-streaming
```
3. Monitoring (Prometheus & Grafana): For logging and monitoring.
```bash
oc new-project kafka-logging
```

### Install Operators
Install the following operators from the OpenShift OperatorHub:
- Red Hat Integration AMQ Streams
- Prometheus Operator **(Note: Install in the kafka-logging namespace)**
- Red Hat OpenShift distributed tracing platform

## Install Helm Charts
1. Clone the repository:
```bash
git clone https://github.com/quarkus-sre/charts
```

Navigate to the charts directory to install these charts:

1. AMQ Streams
```bash
helm template -f amqstreams/values-cluster-with-metrics.yaml amqstreams | oc apply -f-
```
2. Prometheus
```bash
helm template -f prometheus/values.yaml prometheus | oc apply -f-
```
3. Grafana
```bash
helm template -f grafana/values.yaml grafana | oc apply -f-
```
- Configure the Prometheus data source manually in Grafana.
  - **URL**: `http://prometheus-operated:9090`
- Configure the AlertManager data source manually in Grafana.
  - **URL**: `alertmanager:9093`
- Import Grafana dashboards:
  - Strimzi Kafka Exporter Dashboard (grafana-dashboards/kafka-exporter.json)
  - Quarkus SRE Dashboard (grafana-dashboards/sre-quarkus.json)
  
4. Jaeger
```bash
helm template -f jaeger/values.yaml jaeger | oc apply -f-
```

## Validation Steps

1. **AMQ Streams:**
   - Execute the following command to list all Kafka clusters:
     ```bash
     oc get kafka -n kafka-streaming
     ```
   - You should see your Kafka cluster listed.

2. **Prometheus:**
   - Open a web browser and navigate to the URL specified in the Prometheus route. You can obtain the URL by executing:
     ```bash
     oc get route prometheus -n kafka-logging -o jsonpath='{.spec.host}'
     ```
   - Check the targets in Prometheus UI to ensure they are up.

3. **Grafana:**
   - Open a web browser and navigate to the URL specified in the Grafana route. You can obtain the URL by executing:
     ```bash
     oc get route grafana -n kafka-logging -o jsonpath='{.spec.host}'
     ```
   - Login and check that the Prometheus and AlertManager data sources are configured correctly.
   - Validate that the imported dashboards are available and displaying data.

4. **Jaeger:**
   - Open a web browser and navigate to the URL specified in the Jaeger route. You can obtain the URL by executing:
     ```bash
     oc get route jaeger -n openshift-distributed-tracing -o jsonpath='{.spec.host}'
     ```
   - Validate that traces are being collected and displayed.

## Deploying the Applications

To deploy the individual microservices, you'll need to clone their repositories and apply the respective Helm charts located in the `.chart` folders. Here are the steps for each microservice:

### Access Microservice (concierge-app)
1. Clone the repository:
   ```bash
   git clone https://github.com/firefighters-sre/concierge-app.git
   ```
2. Navigate to the cloned directory and deploy the Helm chart:
   ```bash
   cd concierge-app
   helm dependency update .chart
   helm template .chart/ | oc apply -f-
   ```

### Mobility Microservice (mobility-app)
1. Clone the repository:
   ```bash
   git clone https://github.com/firefighters-sre/mobility-app.git
   ```
2. Navigate to the cloned directory and deploy the Helm chart:
   ```bash
   cd mobility-app
   helm dependency update .chart
   helm template .chart/ | oc apply -f-
   ```

### Building Microservice (building-app)
1. Clone the repository:
   ```bash
   git clone https://github.com/firefighters-sre/building-app.git
   ```
2. Navigate to the cloned directory and deploy the Helm chart:
   ```bash
   cd building-app
   helm dependency update .chart
   helm template .chart/ | oc apply -f-
   ```

After deploying the Helm charts, the microservices should be up and running in your Kubernetes cluster. You can verify the deployment status using `kubectl get pods`.

### Configuring PostgreSQL Database for Building Microservice

The Building Microservice (`building-app`) requires a PostgreSQL database for persistent storage. Here's how you can set it up:

#### Deploying PostgreSQL on OpenShift

1. **Create PostgreSQL Deployment**:
   
   OpenShift provides templates to deploy PostgreSQL. You can instantiate one of these templates to deploy a PostgreSQL instance:

   ```bash
   oc new-app postgresql-persistent --param POSTGRESQL_USER=userWPM --param POSTGRESQL_PASSWORD=Oiu5HI4nBLDbYtHo --param POSTGRESQL_DATABASE=firefighters
   ```

2. **Verify Deployment**:

   Check if the PostgreSQL pod is running:

   ```bash
   oc get pods | grep postgresql
   ```

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
