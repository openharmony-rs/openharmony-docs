# UpgradeTaskCallback (System API)

```TypeScript
export type UpgradeTaskCallback = (eventInfo: EventInfo) => void
```

Represents an event callback.

@typedef UpgradeTaskCallback [since 9 - 22] @typedef { function } UpgradeTaskCallback [since 23]

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| eventInfo | [EventInfo](arkts-basicservices-update-eventinfo-i-sys.md) | Yes | Event information, including the eventId(eventID) and taskBody(task data) fields. |
