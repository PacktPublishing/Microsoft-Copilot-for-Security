# Playbook - Device File Download and Process Execution Summary with Copilot Analysis (Referencing Plugin Skills) 

**Description**: Report on files downloaded to the device. Then, request Security Copilot to identify any suspicious process executions on this device.

**Required Input**: < Device Name, Start Time, End Time >

1. 
 ```
/ListFilesDownloaded List the files downloaded to device DeviceName from StartTime to EndTime and state where the files were downloaded from.
 ```
2. 
 ```
/ProcessExecutionSummary Can you provide a list of processes executed on device DeviceName from StartTime to EndTime.
 ```
3. 
 ```
Using your previous output, find a list of the users who ran these processes.
 ```
4. 
 ```
Using the Entra plugin, tell me more about these users from your previous output.
 ```
5. 
 ```
Using the generic plugin, based on users' job title and department, can you review the list of processes executed on device DeviceName from your previous output and identify any processes that users typically should not perform given users' role and department? And please include your reasoning, along with the suspicious process path and its execution count.
 ```