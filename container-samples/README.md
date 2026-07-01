# About these samples
These samples walk you through the process of building and deploying a containerized TwinCAT 3.1 XAR runtime environment that includes one of the TwinCAT OPC UA products. By working through them, you will learn how to build a TwinCAT XAR container image, manage the containers with Docker Compose and Makefile automation, set up ADS-over-MQTT communication, and connect TwinCAT Engineering to a containerized runtime.

## Overview
The table below gives an overview of the container sample folders that are currently available.

| Name | Description | Start here |
| --- | --- | --- |
| tcopcuaserver-container-sample | Deploys XAR Base and the TwinCAT OPC UA Server in the same container. | [tcopcuaserver-container-sample/README.md](tcopcuaserver-container-sample/README.md) |
| tcopcuaclientpubsub-container-sample | Deploys XAR Base and the TwinCAT OPC UA Client and Pub/Sub in the same container. | [tcopcuaclientpubsub-container-sample/README.md](tcopcuaclientpubsub-container-sample/README.md) |

## What this sample demonstrates
- Build and configure a TwinCAT XAR container image that includes one of the TwinCAT OPC UA products.
- Manage containers using Docker Compose and Makefile-based automation.
- Set up secure communication between Engineering and Runtime using ADS-over-MQTT.
- Connect TwinCAT Engineering to a containerized TwinCAT runtime.
- Work with the containerized TwinCAT OPC UA product in a repeatable way.

## Prerequisites
- A supported Beckhoff IPC with Beckhoff Real-Time Linux installed.
- Access to the Beckhoff package server.
- Docker Engine on Debian.
- The `make` and `tcsysconf` tools installed on the host.
- A valid TwinCAT license for the OPC UA product used by the sample you want to run.

## Getting Started
1. Open the README in the sample folder you want to run and follow that folder-specific setup.
2. Copy the sample folder to your Beckhoff Real-Time Linux host and work with it over SSH.
3. Build the image, configure the firewall rules required by the sample, and start the containers with Docker Compose.
4. Copy the `mqtt.xml` route file to your TwinCAT Engineering system, then restart or re-config the TwinCAT System Service.

## Notes & Troubleshooting
- Make sure container IP addresses and AMS Net IDs do not conflict with other samples already running on the host.
- If you already have Mosquitto or another runtime container running, adjust the Docker Compose file accordingly.
- When building the image, replace the placeholder myBeckhoff credentials in the relevant `apt-config` file.
- If the runtime does not appear in TwinCAT Engineering, verify the ADS-over-MQTT route file and the host firewall rules.

## Support
Should you have any questions regarding the provided sample code, please contact your local Beckhoff support team. Contact information can be found on the official Beckhoff website at https://www.beckhoff.com/contact/.