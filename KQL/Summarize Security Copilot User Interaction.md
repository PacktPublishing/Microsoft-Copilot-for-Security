# Summarize Security Copilot User Interaction

## Description
This query allows you to categorize and quantify user CopilotInteraction events according to the specific Security Copilot environments in which they occurred.

## Query
```kql
// Summarize Security Copilot User Interaction
CloudAppEvents
| extend AppId = parse_json(RawEventData)["AppIdentity"] 
| where AppId == "Copilot.Security.SecurityCopilot"
| extend EventType = tostring(parse_json(RawEventData)["Operation"])
| where EventType == "CopilotInteraction"
| extend UserIP = tostring(parse_json(RawEventData)["ClientIP"])
| extend Time= tostring(parse_json(RawEventData)["CreationTime"])
| extend User = tostring(parse_json(RawEventData)["UserId"])
| extend Events = parse_json(RawEventData)["CopilotEventData"]
| extend Event = tostring(parse_json(Events)["Contexts"])
| extend CopilotExperience = tostring(parse_json(Events)["AppHost"])
| summarize UserInteractionCount = count() by User, EventType, CopilotExperience
| sort by User asc, CopilotExperience asc 
```