```
Can you tell me more about DefenseEvasion: a process was injected with potentially malicious code on 'mb-winclient' (Windows10), involving the files 'ContosoADFSadmincreds.ps1', 'Midnight161.ps1'
```
---
```
Can you describe in detail about the technique used by attackers to execute arbitrary code in the address space of a separate live process.
```
---
```
Can you run the following KQL then examine its output? Please pay extra attention to the process command line and initiating process command line to look for any suspicious events. Here is the KQL query: DeviceProcessEvents | where Timestamp >= datetime(2024-08-06T17:15:00Z) and Timestamp <= datetime(2024-08-06T17:18:00Z) | where DeviceName contains "mb-winclient"
```
---
```
Can you run the following KQL then examine its output? Please pay extra attention to the process command line and initiating process command line to look for 'csc.exe' (C# compiler) was used to compile code. Then display the relevant event here. Here is the KQL query: DeviceProcessEvents | where Timestamp >= datetime(2024-08-06T17:15:00Z) and Timestamp <= datetime(2024-08-06T17:18:00Z) | where DeviceName contains "mb-winclient"
```
---
## Credential Access
```
In your incident summary, you mentioned that "At 2024-08-06 17:17:07 UTC, a suspected DCSync attack (replication of directory services) was detected on 'mb-winclient' (Windows 10), impacting user 'pgustavo'." What's a DCSync attack? Can you provide its TTPs?
```
---
