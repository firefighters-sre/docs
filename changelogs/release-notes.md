# Firefighters SRE

## [v1.0.5]

### Building App
**Detail Database Schema**: Elaborate on the `FloorData` table structure.
**Automatic Database Initialization**: Set up `buildingdb` with 5 floors in `FloorData` table, initializing values.

### Mobility App
**SLOs and SLAs**: 
   - **Elevator Response Time SLO**: Ensure response and arrival within 30 seconds during fire incidents.
   - **Stairs Traffic Flow SLO**: Monitor flow to avoid bottlenecks or overcrowding.
   - **High External Redeliveries SLO**: Alert for high external redeliveries.
   - **Elevator Response Time SLA**: Service credit system for exceeding 40 seconds average response time.
   - **Stairs Traffic Flow SLA**: Service credit system if congestion persists for over 15 minutes.

### Concierge App
**Define Estimated Evacuation Time Formula**: Develop formula to predict evacuation time.
**Implement SLOs, SLAs, and Alerts related to fire incident**:
   - **Evacuation Time SLO**: Monitor evacuation time ensuring it's below 1 minute during fire incidents.
   - **Evacuation Time SLA**: Trigger review if average evacuation time exceeds 5 minutes.

## [v1.0.4]

### Building App
**SLO/SLA prevention Automation**:
   - **Automated Scaling**:
      - **Horizontal Pod Autoscaling (HPA)**: Scale the number of running pods based on observed CPU utilization.
   - **Self-Healing Systems**:
      - **Liveness and Readiness Probes**: Check the health of the application and restart unresponsive pods.
      - **PodDisruptionBudget (PDB)**: Ensure high availability during voluntary disruptions.

### Mobility App
**SLO/SLA prevention Automation**:
   - **Automated Scaling**:
      - **Horizontal Pod Autoscaling (HPA)**: Scale the number of running pods based on observed CPU utilization.
   - **Self-Healing Systems**:
      - **Liveness and Readiness Probes**: Check the health of the application and restart unresponsive pods.
      - **PodDisruptionBudget (PDB)**: Ensure high availability during voluntary disruptions.

### Concierge App
**SLO/SLA prevention Automation**:
   - **Automated Scaling**:
      - **Horizontal Pod Autoscaling (HPA)**: Scale the number of running pods based on observed CPU utilization.
   - **Self-Healing Systems**:
      - **Liveness and Readiness Probes**: Check the health of the application and restart unresponsive pods.
      - **PodDisruptionBudget (PDB)**: Ensure high availability during voluntary disruptions.

## [v1.0.3]

### Building App
**Database Connectivity via Environment Vars**: Set up and validate environment variables for the database.
**Helm Chart Creation**: Design and implement a Helm chart for deployments on Kubernetes.
**Implement Basic SLOs, SLAs, and Alerting**:
   - **Availability SLO**: 99.9% uptime over a 10-minute window.
   - **Latency SLO**: API response times under 200ms and event processing times within 500ms.
   - **Error Rate SLO**: Less than 0.1% of all API requests result in errors.

### Mobility App
**Implement Basic SLOs, SLAs, and Alerting**:
   - **Availability SLO**: 99.9% uptime over a 10-minute window.
   - **Latency SLO**: API response times under 200ms and event processing times within 500ms.
   - **Error Rate SLO**: Less than 0.1% of all API requests result in errors.

### Concierge App
**Process Kafka `MoveLog` in `exit` Topic Events**: Process events from the Kafka topic named `exit`.
**Deliver `ExitLog` to Kafka `external` Topic**: Send processed messages to Kafka `external` topic.
**Automatic AccessLog ID Generation**: Generate a unique identifier for every new access log entry.
**API Documentation**: Document all exposed APIs and endpoints.

## [v1.0.2]

### Building App
**Route Documentation**: Document all exposed APIs and endpoints for clarity.
**Health Endpoint Integration**: Integrated `camel-quarkus-microprofile-health` for application monitoring.

### Mobility App
**Route Documentation**: Document all routes for better clarity.
**Health Endpoint Integration**: Integrated `camel-quarkus-microprofile-health` to provide health check endpoints.

### Concierge App
**Process Kafka `MoveLog` in `exit` Topic Events**: Process events from the Kafka topic named `exit`.
**Deliver `ExitLog` to Kafka `external` Topic**: Send processed messages to Kafka `external` topic.
**Automatic AccessLog ID Generation**: Generate a unique identifier for every new access log entry.
**API Documentation**: Document all exposed APIs and endpoints for better clarity.
**Health Endpoint Integration**: Integrated `smallrye-health` to provide health check endpoints.

## [v1.0.1]

### Building App
**Monitoring**: Set up tools to monitor the app's performance and health with various metrics.
**Logging**: Set up monitoring tools to keep track of the app's performance and health.

### Mobility App
**Monitoring**: 
   - **Elevator Usage Count**: Number of times the elevator is used within a time frame.
   - **Elevator Average Wait Time**: Average time people wait for the elevator.
   - **Stairs Usage Count**: Number of times the stairs are used within a time frame.
   - **Total People Moved**: Total number of people moved using either the stairs or the elevator.
   - **Average Movement Time**: Average time taken for a person to move from one point to another.
   - **Mobility Efficiency**: Ratio of people moved to the total number of people waiting or intending to move.
**Logging**:
   - **Elevator Called**: Log each time the elevator is called, including the floor number.
   - **Elevator Trip Completion**: Log each time the elevator completes a trip, including start and end floors and trip duration.
   - **System Alerts**: Log any system alerts or warnings related to mobility.

### Concierge App
**Monitoring**:
   - **Entrance Rate**: Measure the rate of people entering the building.
   - **Exit Rate**: Measure the rate of people exiting the building during evacuation.
**Logging**:
   - **Person Entry**: Log entry every time a person enters the building.
   - **Person Exit**: Log entry every time a person exits the building during evacuation.
**Helm Chart Creation**: Design and implement a Helm chart for deployments on Kubernetes clusters.

## [v1.0]

### Building App
**Process Kafka `stairs` and `elevator` Topic Events**: Capture and process events from the Kafka topics named `stairs` and `elevator`.
**Update Floor Count in Database**: Based on the messages from the topics, update the number of people on each floor in the database.

### Mobility App
**Process Kafka `entrance` Topic Events**: Capture and process events from the Kafka topic named `entrance`.
**Decision Logic**: Implement logic to decide whether a message should be directed to `stairs` or `elevator` topics.

### Concierge App
**Process Kafka `AccesLog` in `lobby` Topic Events**: Capture and process events from the Kafka topic named `lobby`.
**Enhance `MoveLog` with `preferredRoute` Attribute**: Add a preferredRoute attribute to the MoveLog class.
**Deliver `MoveLog` to Kafka `entrance` Topic**: Send processed messages from `lobby` to the Kafka topic named `entrance`.

