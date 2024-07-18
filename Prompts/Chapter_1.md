```
Based on MDTI, Microsoft Defender Threat Intelligence, can you describe in detail one of the ways attackers can move laterally within the organization? Please be specific on the TTPs.
```
---
```
Can you run the following KQL query then examine its output, especially the process command line output, to look for any encoded command line? Here is the KQL query: DeviceProcessEvents I where Timestamp between (datetime(2024-06-25) . datetime(2024-06-27)) I where InitiatingProcessFileName contains "powershell.exe" and FileName contains "schtasks.exe and DeviceName contains "avoriaz- win10e I project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, FileName, ProcessCommandLine
```
---
