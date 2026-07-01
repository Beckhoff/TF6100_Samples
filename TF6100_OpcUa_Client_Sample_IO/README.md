# TF6100 OPC UA Client Sample

## Overview
This TwinCAT 3 sample demonstrates how to connect the TwinCAT OPC UA Client I/O device to an OPC UA server and exercise common client-side workflows. The project contains variables, structures and methods from the TwinCAT OPC UA Sample Server.

## What this sample demonstrates
- Establishing an OPC UA session with the TwinCAT OPC UA Client I/O device
- Reading and writing variables
- Calling OPC UA methods with input and output arguments

## Prerequisites
- TwinCAT 3 XAE engineering environment installed on Windows
- A TwinCAT 3 XAR runtime or compatible target system that can run the PLC project
- TF6100 TC3 OPC UA Client workload installation on your target system
- TF6100 OPC UA license for the target runtime
- Network access to the target server, plus a trusted server certificate for secure connections

Please note that the TF6100 TC3 OPC UA Client workload will also install the `TwinCAT OPC UA Sample Server`, which is used by these samples.

## Getting Started
1. Start the `TwinCAT OPC UA Sample Server`, which you can find on the Windows start menu.
2. Open the solution file [TF6100_OpcUa_Client_Sample_IO.sln](TF6100_OpcUa_Client_Sample_IO.sln).
3. Build and activate the project

In this sample project, the TwinCAT OPC UA Sample Server has been added as a "Virtual OPC UA Client" device to the TwinCAT I/O configuration. This device is responsible for setting up OPC UA communication with the server and selecting which nodes to add to the configuration. Each selected node is then represented by a variable on the process image of the device.

![TwinCAT OPC UA Client I/O device](docs/client_ioDevice.png)

By using the code generation feature of the I/O device, PLC code can be automatically generated and added as a global variable list to the PLC project. In this sample project, this step has already been made.

![Generated global variable list](docs/client_codegengvl.png)

The code generation feature can be executed on the settings page of the "Virtual OPC UA Client" device.

![Executing code generation](docs/client_ioDeviceCodeGen.png)

## Reading variables
By using the code generation functionality, variables from the TwinCAT OPC UA Sample Server have been automatically created in `Device_1_Client_1`. These variables are mapped to OPC UA variables on the process image of the "Virtual OPC UA Client" device. The device settings specify the sampling mode (Polling, Subscription) and how fast the variables should be sampled from the server.

When logging in to the PLC application, you will see variable values being updated.

## Writing variables
The `MAIN` program contains a sample that demonstrates how to execute write commands. 

To start cyclic write commands, set variable `bToggleWrite` to TRUE. This will set the process image variable `bWriteEnable` on the virtual OPC UA client device to TRUE in order to allow write commands. Write commands are cyclically send to the server based on the cycle time configured on the virtual OPC UA client device. To stop write commands, set variable `bToggleWrite` to TRUE again.

# Calling methods
The TwinCAT OPC UA Sample Server contains a method that has two input and two output arguments. When calling the method, the input arguments are reflected to the output arguments. 

The method itself is available on the process image of the virtual OPC UA client device, including its input arguments (as output variables) and output arguments (as input variables). A bExecute output variable allows to initiate the method call and different input variables such as bDone, bBusy, bError and nErrorID allow to determine if method execution has completed successfully or with an error.

The `MAIN` program contains a state machine that demonstrates how to execute this method call. To start the method call, set variable `bCallMethod` to TRUE, which will trigger the state machine. The state machine uses the PLC function block instance `Sample_Methods_MyObject_MyMethod` from the generated global variable list to call the method.

## Notes & Troubleshooting
- This sample uses the TwinCAT OPC UA Sample Server, which is installed together with the TF6100 TC3 OPC UA Client workload.
- If you receive ADS Error 6 on one of the OPC UA function block calls, make sure that you have configure the correct AmsNetId of the virtual device as shown under "Getting Started".
- The included code assumes secure OPC UA communication and may require certificate trust on first connect.
- If a client program fails to connect, verify the server URL, runtime state, and license status on the target.
- For method-call samples, make sure the object and method node identifiers match the target server.
- Historical access only works if the target server exposes historized nodes.

## Support
For questions about this sample, contact your local Beckhoff support team. Contact information is available on the official Beckhoff website at https://www.beckhoff.com/contact/.