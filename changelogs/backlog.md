## [v1.0.6]

### Building App
**SLO/SLA fire incident prevention Automation**: Escalate the application to reduce the evacuation time.
**Custom Metrics Scaling**: Implement scaling based on custom application-specific metrics.
**KEDA**:

### Mobility App
**Elevator Capacity Efficiency**:
   - **Objective**: Ensure elevators operate at no more than 80% capacity during evacuations.
   - **Metric**: Track individuals in an elevator during evacuations compared to max capacity.
**Stairs Traffic Flow**:
   - **Objective**: Maintain a steady flow, avoiding bottlenecks or overcrowding.
   - **Metric**: Monitor the rate of individuals entering and exiting stairwells.
**Stairs Safety Compliance**:
   - **Objective**: Ensure stairwell users comply with safety guidelines.
   - **Metric**: Use sensors to detect non-compliance events in stairwells.
**Backup Systems for Elevators**:
   - **Objective**: Activate backup systems within 1 minute of primary system failure.
   - **Metric**: Monitor downtime of primary systems and activation time of backups.
**Stairs Lighting and Signage**:
   - **Objective**: Maintain 100% uptime for emergency lighting and signage during fire incidents.
   - **Metric**: Monitor operational status of lighting and signage in stairwells.

### Concierge App
**SLO/SLA fire incident prevention Automation**:
   - Some task related to these SLOs: Escalate the application to reduce the evacuation time.
**Custom Metrics Scaling**: Implement scaling based on custom application-specific metrics.
**KEDA**:

### Backlog Mobility App
- [ ] **Monitoring**: Set up monitoring tools to keep track of the app's performance and health.
  - [ ] **Elevator Capacity Usage**: Percentage utilization of elevator capacity during trips.
  - [ ] **Elevator Travel Time**: Time taken for elevator trips between floors.
  - [ ] **Stairs Congestion Level**: Measure of how congested the stairs are, possibly based on people count over time.
- [ ] **Logging**: Set up monitoring tools to keep track of the app's performance and health. 
  - [ ] **Elevator Trip Completion**: Log each time the elevator completes a trip, including start and end floors and trip duration.
  - [ ] **Elevator Anomalies**: Log any elevator anomalies or issues, e.g., if it stops unexpectedly.
  - [ ] **Stair Access Points**: Log when stair access points (e.g., doors) are opened and closed.
  - [ ] **Stair Usage Estimate**: Potentially log periodic counts or estimates of people using stairs.
  - [ ] **Manual Overrides**: Log any manual overrides or changes to the mobility system (e.g., shutting down an elevator for maintenance).
- [ ] **Enhanced Decision Logic**: Improve the logic that decides whether a person should take the stairs or elevator.
- [ ] **Security**: Implement security best practices and possibly add authentication mechanisms.
- [ ] **Load Testing**: Conduct performance and load tests to ensure the app's scalability.
- [ ] **Integration Testing**: Conduct tests to ensure smooth integration with other microservices like `concierge-app` and `building-app`.
- [ ] **Centralized Logging**: Integrate with a centralized logging system for better traceability.

### Backlog Building App 
- [ ] **Real-time Floor Count Display**: Implement a feature to provide a real-time display of people count on each floor.
- [ ] **Integration with Concierge and Mobility Apps**: Ensure seamless data flow with the other microservices.
- [ ] **Centralized Logging**: Integrate with a centralized logging system for better traceability.

### Backlog Concierge App
- [ ] **Automated Evacuation Drills**: Schedule and automate periodic fire drills to ensure the readiness of all individuals and validate the effectiveness of evacuation protocols.
- [ ] **Exit Monitoring Automation**: Implement sensors and cameras to monitor exit routes and ensure they remain clear. The system should automatically raise alerts if any blockages or obstructions are detected.
- [ ] **Capacity Forecasting**: Based on the number of individuals in the building, predict potential choke points during evacuation and adjust exit strategies accordingly.
- [ ] **Capacity Planning & Resource Provisioning Automation**: Predict system resource constraints based on metrics (disk usage, memory consumption,CPU utilization) and automate provisioning processes accordingly. 
- [ ] **Exit Accessibility SLO**: Ensure that at least 90% of exits are accessible and clear during a fire incident.
- [ ] **Exit Accessibility SLA**: Regular checks on exit routes to ensure they are clear. If more than 10% of exits are found blocked during a check,  a review of the premises' maintenance protocol will be conducted. 
- [ ] **Data Availability SLO**: Ensure 99.99% uptime for the data retrieval system, especially during emergencies, to provide real-time data on individual whereabouts.
- [ ] **Data Availability SLA**: Implement a backup and recovery mechanism to ensure that data is always available, especially during emergencies. Any downtime beyond 0.01% will require a review of data systems.
- [ ] **Error Budget Automation**: Implement automation routines to monitor and alert on Error Budget consumption. This includes:
  - [ ] Automated reporting on Error Budget consumption.
  - [ ] Proactive alerts when approaching the Error Budget limit.
  - [ ] Triggering automated remediation actions if certain thresholds are crossed (e.g., rolling back a deployment).
  - [ ] Integration with CI/CD pipelines to halt new releases if the Error Budget is exceeded.
- [ ] **Throughput SLO**: Ensure the system handles at least 1000 API requests and processes at least 500 events per second.
- [ ] **Data Accuracy SLO**: Ensure less than 0.01% discrepancy between input events and processed events' data.  
- [ ] **Support Response Time SLA**: Implement a service credit system for failure to meet response times for various priority issues.
- [ ] **Data Recovery SLA**: Implement a service credit for recovery times exceeding 4 hours.
- [ ] **Maintenance Notification SLA**: Implement a service credit for failure to notify about maintenance 72 hours in advance.
- [ ] **Service Restoration SLA**: Implement a service credit for service restoration times exceeding 2 hours..
- [ ] **Stairs**: Add stairs as preferredRoute.
- [ ] **Monitoring**: Set up monitoring tools to keep track of the app's performance and health.
   - [ ] **Current Evacuation Status**: A gauge that can be set to 1 during an active evacuation and 0 otherwise. This helps in easily determining if an evacuation is in progress.
  - [ ] **Evacuation Completion Time**: A timer to measure the total time taken from the start of the evacuation until the building is confirmed empty.
- [ ] **Logging**: Set up monitoring tools to keep track of the app's performance and health.
  - [ ] **Evacuation Start**: A log entry indicating the time and reason (in this case, a fire drill) when the evacuation started.
  - [ ] **Evacuation End**: A log entry indicating the time when the evacuation was completed and the building was empty.
  - [ ] **Any Anomalies**: Log entries capturing any anomalies or issues during the evacuation, such as access system malfunctions, entry/exit bottlenecks, etc.
- [ ] **Centralized Logging**: Integrate with a centralized logging system for better traceability.
- [ ] **Store Access Log**: Save the access log entries into the database under the `AccessLog` table.
- [ ] **Retrieve Access Logs**: Implement functionality to fetch access logs from the `AccessLog` table.
- [ ] **Process Kafka `registration` Topic Events**: Capture and process events from the Kafka topic named `registration`.
- [ ] **Store Person Information**: Save the person's data into the database under the `Person` table.
- [ ] **Automatic Person ID Generation**: For every new person's data, generate a unique identifier automatically.
- [ ] **Retrieve Person Information**: Implement functionality to fetch details about a person from the `Person` table.
- [ ] **Integration with Building and Mobility Apps**: Ensure seamless data flow between the Concierge App and the other microservices.