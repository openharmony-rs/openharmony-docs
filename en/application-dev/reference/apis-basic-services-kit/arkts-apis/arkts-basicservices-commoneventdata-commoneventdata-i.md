# CommonEventData

Describes the data of a common event. The **CommonEventData** module is used to carry the common event data received by subscribers in common event subscription scenarios. The data includes the event name, publisher bundle name, code, data, and additional parameters. This module is applicable to scenarios where apps subscribe to and process common events and parse the data carried in the events.

**Since:** 7

**System capability:** SystemCapability.Notification.CommonEvent

## bundleName

```TypeScript
bundleName?: string
```

Bundle name of the common event publisher. The default value is an empty string.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

## code

```TypeScript
code?: number
```

Common event data received by the subscriber. The value of this field is the same as that of the **code** field in CommonEventPublishData when the publisher uses [commonEventManager.publish](arkts-basicservices-commoneventmanager-publish-f.md) to publish a common event. The value ranges from –2147483648 to 2147483647. The default value is **0**.

**Type:** number

**Default:** 0

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

## data

```TypeScript
data?: string
```

Common event data received by the subscriber. The data size cannot exceed 64 KB. The value of this field is the same as that of the **data** field in CommonEventPublishData when the publisher uses [commonEventManager.publish](arkts-basicservices-commoneventmanager-publish-f.md) to publish a common event.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

## event

```TypeScript
event: string
```

Name of the common event that is being received.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

## parameters

```TypeScript
parameters?: { [key: string]: any }
```

Additional information about the common event received by the subscriber. The value of this field is the same as that of the **parameters** field in CommonEventPublishData when the publisher uses [commonEventManager.publish](arkts-basicservices-commoneventmanager-publish-f.md) to publish a common event.

**Type:** { [key: string]: any }

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent
