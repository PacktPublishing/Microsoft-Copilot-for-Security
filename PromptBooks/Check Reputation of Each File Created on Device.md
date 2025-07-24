# Check Reputation of Each File Created on Device

**Description**: Identify all files created on the device during the incident timeframe and leverage MDTI to check the reputation of those files through their hash values.

**Required Input**: device_name, start_time, end_time

**Promptbook prompts**:


1. 
 ```
Can you run the following KQL query to list files created and their hash value? Note contains in the KQL query is case insensitive. Here is the KQL query: let STime = <start_time>; let ETime = <end_time>; DeviceFileEvents | extend StartTime = datetime(STime) | extend EndTime = datetime(ETime) | where Timestamp between (StartTime .. EndTime) | where DeviceName contains "<device_name>" | where ActionType == "FileCreated" | summarize by FileName, SHA256
 ```
2.  
 ```
Using the MDTI plugin, can you check the reputation of each file based on its file hash value
 ```
