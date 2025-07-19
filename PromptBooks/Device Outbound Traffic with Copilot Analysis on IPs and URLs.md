# Device Outbound Traffic with Copilot Analysis on IPs and URLs

**Description**: Lists public IPs and URLs from the device outbound network events then ask Security Copilot to check IP and URL reputation.

**Required Input**: start_time, end_time, device_name

**Promptbook prompts**:

1. 
 ```
Can you run the following KQL query to report device outbound network events? Here is the KQL query: let STime = <start_time>; let ETime = <end_time>; DeviceNetworkEvents | extend StartTime = datetime(STime) | extend EndTime = datetime(ETime) | where Timestamp between (StartTime .. EndTime) | where DeviceName contains "<device_name>" | where RemoteIPType contains "Public" | summarize NetworkConnectionCount = count() by InitiatingProcessFileName, InitiatingProcessFolderPath, RemoteIP, RemoteUrl, RemotePort, Protocol
 ```
2.  
 ```
Using the MDTI plugin, can you check the reputation of each IP?
 ```
 3.  
 ```
Using the MDTI plugin, can you check the reputation of each URL?
 ```
