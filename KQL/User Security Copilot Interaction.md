# User Security Copilot Interaction

## Description
This query retrieves Security Copilot audit log events then filters these events to show only the CopilotInteraction logs.

## Query
```KQL
// User Security Copilot Interaction
| extend AppId = parse_json(RawEventData)["AppIdentity"] 
| where AppId == "Copilot.Security.SecurityCopilot"
| extend EventType = parse_json(RawEventData)["Operation"]
| where EventType == "CopilotInteraction"
| extend UserIP = parse_json(RawEventData)["ClientIP"]
| extend Time= tostring(parse_json(RawEventData)["CreationTime"])
| extend User = parse_json(RawEventData)["UserId"]
| extend Events = parse_json(RawEventData)["CopilotEventData"]
| extend CopilotExperience = parse_json(Events)["AppHost"]
| project Time, User, EventType, CopilotExperience, UserIP, City, CountryCode, ISP
| sort by Time desc 
```
