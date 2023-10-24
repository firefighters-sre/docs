# Roadmap

## M1 - Emergency Response Enhancements

In this phase, the focus is on improving emergency response and evacuation efficiency across all apps.

### Expected Features:
- **SLO/SLA fire incident prevention Automation** to reduce evacuation time (Building App, Concierge App).
- **Elevator Capacity Efficiency** with an objective to operate elevators at no more than 80% capacity during evacuations (Mobility App).
- **Stairs Traffic Flow** management to avoid bottlenecks or overcrowding (Mobility App).
- **Stairs Safety Compliance** to ensure adherence to safety guidelines (Mobility App).
- **Backup Systems for Elevators** to ensure activation within 1 minute of primary system failure (Mobility App).
- **Stairs Lighting and Signage** to maintain 100% uptime during fire incidents (Mobility App).
- **Automated Evacuation Drills** to validate evacuation protocols (Concierge App).
- **Exit Monitoring Automation** to ensure clear exit routes (Concierge App).

## M2 - Performance Monitoring and Scalability

In this phase, the focus is on monitoring the performance of the apps and ensuring scalability.

### Expected Features:
- **Custom Metrics Scaling** based on application-specific metrics (Building App, Concierge App).
- **KEDA** implementation for event-driven autoscaling (Building App, Concierge App).
- **Monitoring** setup for app performance and health, including elevator capacity usage, travel time, and stairs congestion level (Mobility App).
- **Logging** for elevator trips, anomalies, stair access points, and manual overrides (Mobility App).
- **Centralized Logging** for better traceability (Building App, Mobility App, Concierge App).

## M3 - User Experience and Data Management

In this phase, the focus is on improving user experience and managing data efficiently.

### Expected Features:
- **Real-time Floor Count Display** to show people count on each floor (Building App).
- **Integration** with Concierge and Mobility Apps for seamless data flow (Building App).
- **Enhanced Decision Logic** to guide users on whether to take stairs or elevator (Mobility App).
- **Security** implementation and possible authentication mechanisms (Mobility App).
- **Capacity Forecasting** and **Capacity Planning & Resource Provisioning Automation** for efficient resource allocation (Concierge App).

## M4 - Advanced Analytics and Testing

In this phase, the focus is on testing the apps and providing advanced analytics for better decision-making.

### Expected Features:
- **Load Testing** and **Integration Testing** to ensure app scalability and smooth integration with other microservices (Mobility App).
- **Error Budget Automation**, **Throughput SLO**, **Data Accuracy SLO**, and other service level objectives and agreements for better service reliability (Concierge App).

## M5 - Data Retrieval and Management

In this phase, the focus is on ensuring data accuracy and availability, especially during emergencies.

### Expected Features:
- **Data Availability SLO/SLA** with backup and recovery mechanisms (Concierge App).
- **Process Kafka `registration` Topic Events**, **Store/Retrieve Person Information**, and **Automatic Person ID Generation** for better data management (Concierge App).
