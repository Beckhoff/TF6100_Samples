# About these samples

These samples walk you through the step-by-step process of building and deploying a containerized TwinCAT 3.1 XAR runtime environment, including one of our TwinCAT OPC UA products, using Docker on a Beckhoff IPC. By working through these samples, you will basically learn how to:

- Build and configure a TwinCAT XAR container image that includes one of our TwinCAT OPC UA products
- Manage containers using Docker Compose and Makefile-based automation
- Set up secure communication between Engineering and Runtime using ADS-over-MQTT
- Connect the TwinCAT Engineering to a containerized TwinCAT Runtime
- Work with the containerized TwinCAT OPC UA product

Each sample focuses on a different deployment scenario or use case for the corresponding product.
The table below gives an overview of the samples that are currently available.

| Name | Description |
| ----------- | ----------- |
| tcopcuaserver-container-sample | Demonstrates how to deploy XAR Base and server into the same container. |