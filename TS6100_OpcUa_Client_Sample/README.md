# TS6100 OPC UA Client Sample

## Overview
This TwinCAT 2 PLCopen OPC UA sample shows how to connect to an OPC UA server from a PLC project and exercise common client-side interactions. The project contains example programs for browsing, connecting, reading and writing.

## What this sample demonstrates
- Opening and closing an OPC UA session from a TwinCAT 2 PLC project
- Browsing a server namespace and reading reference descriptions
- Reading and writing server values through PLCopen OPC UA blocks
- Using a configurable server URL and namespace URI from the PLC project

## Prerequisites
- TwinCAT 2 System Manager and PLC-Control engineering environment
- TwinCAT OPC UA Client for TwinCAT 2 Setup installed
- A reachable OPC UA server for testing the sample
- The required OPC UA runtime/license components for your TwinCAT 2 installation
- A trusted server certificate if the OPC UA endpoint uses secure communication

## Getting Started
1. Open the PLC project [Tc2_PLCopen_OpcUa_Samples.pro](Tc2_PLCopen_OpcUa_Samples.pro).
2. Configure the server URL in the project if your OPC UA server is not running on `opc.tcp://localhost:4840`.
3. Build the project and download it to the TwinCAT 2 target.
4. Start the browse and connect programs first to verify connectivity.
5. Use the write program after the session opens successfully.
6. Trust the server certificate if the first connection is rejected.

## Notes & Troubleshooting
- The sample defaults to `opc.tcp://localhost:4840` and `urn:BeckhoffAutomation:Ua:PLC1`.
- If connection attempts fail, verify the server is running, the endpoint is reachable, and the certificate trust chain is complete.
- If the server uses secure endpoints, trust the certificate before retrying the connection.

## Support
For questions about this sample, contact your local Beckhoff support team. Contact information is available on the official Beckhoff website at https://www.beckhoff.com/contact/.