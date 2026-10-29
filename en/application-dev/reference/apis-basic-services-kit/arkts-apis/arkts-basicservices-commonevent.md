# @ohos.commonEvent(Common Event)

The **CommonEvent** module provides capabilities to publish, subscribe to, and unsubscribe from common events, as well as obtain and modify the common event result code and result data.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [commonEventManager](arkts-basicservices-commoneventmanager.md)

<!--Device-unnamed-declare namespace commonEvent--><!--Device-unnamed-declare namespace commonEvent-End-->

**System capability:** SystemCapability.Notification.CommonEvent

## Modules to Import

```TypeScript
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createSubscriber](arkts-basicservices-commonevent-createsubscriber-depr-f.md#createsubscriber-1) | Creates a subscriber. This API uses an asynchronous callback to return the result. |
| [createSubscriber](arkts-basicservices-commonevent-createsubscriber-depr-f.md#createsubscriber-2) | Creates a subscriber. This API uses a promise to return the result. |
| [publish](arkts-basicservices-commonevent-publish-depr-f.md#publish-1) | Publishes a common event with given properties. This API uses an asynchronous callback to return the result. |
| [publish](arkts-basicservices-commonevent-publish-depr-f.md#publish-2) | Publishes a common event with given properties. This API uses an asynchronous callback to return the result. |
| [subscribe](arkts-basicservices-commonevent-subscribe-depr-f.md#subscribe) | Subscribes to common events. This API uses an asynchronous callback to return the result. |
| [unsubscribe](arkts-basicservices-commonevent-unsubscribe-depr-f.md#unsubscribe) | Unsubscribes from common events. This API uses an asynchronous callback to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [publishAsUser](arkts-basicservices-commonevent-publishasuser-depr-f-sys.md#publishasuser-1) | Publishes a common event to a specific user. This API uses an asynchronous callback to return the result. |
| [publishAsUser](arkts-basicservices-commonevent-publishasuser-depr-f-sys.md#publishasuser-2) | Publishes a common event with given properties to a specific user. This API uses an asynchronous callback to return the result. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [Support](arkts-basicservices-commonevent-support-depr-e.md) | [System common events](../../../basic-services/common-event/common-event-glossary.md#system-common-event) refer to events released by system services or system apps. Subscribing to these events requires specific permissions. To publish or subscribe to this type of event, you must follow the event-specific definitions. |
