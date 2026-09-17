# EventInfo (System API)

Defines an **EventInfo** object, which is used to receive the event details transferred by upgrade event notification. The object contains the **eventId** and **taskBody** fields. **eventId** indicates the event ID, which identifies the event type; **taskBody** indicates the task data, which contains the task status and progress.

Use scenarios: After an event listener is registered by calling **on**, the callback function receives an **EventInfo** object when an event occurs. The real-time status and progress of the upgrade task can be obtained by parsing **eventId** and **taskBody**, which can be used to monitor the upgrade process in real time.

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## eventId

```TypeScript
eventId: EventId
```

Event ID, which identifies the upgrade event type. You can determine the specific event based on **eventId** and take corresponding actions. For example, **EVENT_DOWNLOAD_START** indicates that the download starts, and **EVENT_UPGRADE_SUCCESS** indicates that the upgrade is successful.

Common event types include download events (such as **EVENT_DOWNLOAD_START**), upgrade events (such as **EVENT_UPGRADE_START**), and completion events (such as **EVENT_UPGRADE_SUCCESS** and **EVENT_UPGRADE_FAIL**). You are advised to execute different service logic based on **eventId** in the event callback.

**Type:** [EventId](arkts-basicservices-update-eventid-e-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.

## taskBody

```TypeScript
taskBody: TaskBody
```

Represents task data.

**Type:** [TaskBody](arkts-basicservices-update-taskbody-i-sys.md)

**Since:** 9

**System capability:** SystemCapability.Update.UpdateService

**System API:** This is a system API.
