# Other Security Copilot Events Excluding User Interaction

## Description
This query filters for Security Copilot user events other than the CopilotInteraction events.

## Query
```kql
//Other Security Copilot Events Excluding User Interaction
CloudAppEvents
| extend AppId = parse_json(RawEventData)["AppIdentity"] 
| where AppId == "Copilot.Security.SecurityCopilot"
| extend EventType = tostring(parse_json(RawEventData)["Operation"])
| where EventType != "CopilotInteraction"
| extend User = tostring(parse_json(RawEventData)["UserId"])
| extend EventDetail = tostring(parse_json(RawEventData)["CopilotSettingsEventData"])
| project Timestamp, ActionType, User, EventDetail, IPAddress, City, CountryCode, ISP
| sort by Timestamp desc 
```