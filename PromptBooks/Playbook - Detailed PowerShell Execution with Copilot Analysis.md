# Playbook - Detailed PowerShell Execution with Copilot Analysis 

**Description**: This promptbook pulls the detailed PowerShell execution events then asks Security Copilot to analyze them.

**Required Input**: device_name, start_time, end_time

**Promptbook prompts**:

1. 
 ```
/DetailedPowerShellExecution for device <device_name> from <start_time> to <end_time>
 ```
2.  
 ```
Based on your previous output on PowerShell, provide a detailed summary of the PowerShell activities.
 ```
3.  
 ```
Based on your previous output on PowerShell, explain in detail the suspicious PowerShell activities.
 ```
