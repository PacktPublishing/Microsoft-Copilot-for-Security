# Check Reputation of Each Process Ran on Device

**Description**: Gather a list of processes executed on the device around the time of the incident, then use the MDTI plugin to check the reputation of each process based on its file hash value.

**Required Input**: device_name, start_time, end_time

**Promptbook prompts**:


1. 
 ```
Can you run the following KQL query to list processes and their hash value? Note contains in the KQL query is case insensitive. Here is the KQL query: let STime = <start_time>; let ETime = <end_time>; DeviceProcessEvents | extend StartTime = datetime(STime) | extend EndTime = datetime(ETime) | where Timestamp between (StartTime .. EndTime) | where DeviceName contains "<device_name>" | summarize by FileName, SHA256
 ```
2.  
 ```
Using the MDTI plugin, can you check the reputation of each process based on its file hash value
 ```
