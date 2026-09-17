# BroadcastEvent

Defines a custom system event. You can use a common event API to obtain the event.

The upload and download SA has the **ohos.permission.SEND_TASK_COMPLETE_EVENT** permission. You can configure the level-2 configuration file to which the metadata of an event points to intercept other event senders.

Use the **CommonEventData** type to transmit data related to common events. The members in **CommonEventData** are different from those described in [CommonEventData](arkts-basicservices-commoneventdata-commoneventdata-i.md). Specifically, **CommonEventData.code** indicates the task status, which is **0x40 COMPLETE** or **0x41 FAILED**, and **CommonEventData.data** indicates the task ID.

<!--Del-->

For details about how to obtain the event configuration and configure the level-2 configuration file, see [Subscribing to Common Events in Static Mode (for System Applications Only)](../../../basic-services/common-event/common-event-static-subscription-sys.md).<!--DelEnd-->

**Since:** 11

**System capability:** SystemCapability.Request.FileTransferAgent

## COMPLETE

```TypeScript
COMPLETE = 'ohos.request.event.COMPLETE'
```

Task completion event. The returned event code can be **0x40** or **0x41**, depending on whether the task is successful or fails.

**Since:** 11

**System capability:** SystemCapability.Request.FileTransferAgent
