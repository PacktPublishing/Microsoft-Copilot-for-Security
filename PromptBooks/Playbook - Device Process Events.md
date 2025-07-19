# Playbook - Device Process Events 

**Description**: Identifies file download events, then lists device process execution summary and detailed process execution events.

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
Can you run the following KQL query to report the details of process executions? Here is the KQL query: let STime = <start_time>; let ETime = <end_time>; DeviceProcessEvents | extend StartTime = datetime(STime) | extend EndTime = datetime(ETime) | where Timestamp between (StartTime .. EndTime) | where DeviceName contains "<device_name>" | extend ProcessName = FileName, ProcessPath = FolderPath | project Timestamp, DeviceName, ProcessName, ProcessPath, ProcessCommandLine, InitiatingProcessFileName, InitiatingProcessCommandLine, InitiatingProcessAccountName | sort by Timestamp desc
 ```
