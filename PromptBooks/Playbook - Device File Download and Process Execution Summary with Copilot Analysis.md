# Playbook - Device File Download and Process Execution Summary with Copilot Analysis 

**Description**: Identify file download events and get a summary of the device process execution, then request Security Copilot to analyze the results.

**Required Input**: start_time, end_time, device_name

**Promptbook prompts**:

1. 
 ```
Can you run the following KQL query to report file download activities? Here is the KQL query: let STime = <start_time>; let ETime = <end_time>; DeviceFileEvents | extend StartTime = datetime(STime) | extend EndTime = datetime(ETime) | where Timestamp between (StartTime .. EndTime) | where DeviceName contains "<device_name>" | where isnotempty(FileOriginUrl) and ActionType == "FileCreated" | project Timestamp, DeviceName, FileName, FolderPath, FileOriginUrl, InitiatingProcessFileName, InitiatingProcessAccountName, InitiatingProcessCommandLine | sort by Timestamp desc
 ```
2.  
 ```
Can you run the following KQL query to report process execution summary? Here is the KQL query: let STime = <start_time>; let ETime = <end_time>; DeviceProcessEvents | extend StartTime = datetime(STime) | extend EndTime = datetime(ETime) | where Timestamp between (StartTime .. EndTime) | where DeviceName contains "<device_name>" | extend ProcessName = FileName, ProcessPath = FolderPath | summarize Count = count() by ProcessName, ProcessPath, AccountName | sort by ProcessName asc
 ```
 3. 
 ```
Using the Generic plugin, review the previous output on process execution summary to identify any process that is not commonly used by users but are more commonly used by attackers
 ```
