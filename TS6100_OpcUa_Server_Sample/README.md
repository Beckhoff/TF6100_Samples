# TS6100 OPC UA Server Sample

## Overview
This TwinCAT 2 PLCopen OPC UA sample shows how to publish PLC data through an OPC UA server. The project is intended to demonstrate how variables can be shared from a TwinCAT 2 PLC project.

## What this sample demonstrates
- Publishing PLC variables and data structures through OPC UA
- Exposing server-side data that a client can browse and read
- Demonstrating how an OPC UA server project can be organized in TwinCAT 2
- Showing how PLC comments and symbol definitions can be used to share data

## Prerequisites
- TwinCAT 2 System Manager and PLC-Control engineering environment
- TwinCAT OPC UA Server for TwinCAT 2 Setup installed
- An OPC UA client for testing the sample server
- The required OPC UA runtime/license components for your TwinCAT 2 installation
- A trusted server certificate if the OPC UA endpoint uses secure communication

## Getting Started
1. Open the PLC project [TS6100_OpcUa_Server_Sample.pro](TS6100_OpcUa_Server_Sample.pro).
2. Build and download the project to your TwinCAT 2 target.
3. Start the PLC runtime and ensure the OPC UA server portion is active.
4. Connect an OPC UA client and browse the published nodes.
5. If the server uses secure communication, trust its certificate before reconnecting.

## Notes & Troubleshooting
- The sample was added as a TwinCAT 2 PLC sample and is intended for PLCopen OPC UA workflows.
- If the server is not reachable, check the PLC runtime state and target connection first.
- If your client reports a certificate error, trust the server certificate and retry the connection.
- If nodes do not appear as expected, verify that the PLC project was downloaded and started successfully.

## Support
For questions about this sample, contact your local Beckhoff support team. Contact information is available on the official Beckhoff website at https://www.beckhoff.com/contact/.