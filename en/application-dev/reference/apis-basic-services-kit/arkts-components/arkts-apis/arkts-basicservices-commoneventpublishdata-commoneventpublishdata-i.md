# CommonEventPublishData

```TypeScript
export interface CommonEventPublishData
```

This module encapsulates the data and attributes carried when a common event is published, including the event data (code/data), subscriber permissions, subscriber bundle name, whether the event is ordered or sticky, and additional parameters. It allows the publisher to precisely control the common event recipients, event delivery sequence, and sticky feature. This module is applicable to scenarios where the recipients need to be specified, custom event data needs to be transferred, and ordered/sticky common events need to be implemented.

> **NOTE:** 
> 
> If there is no restriction, any app can subscribe to common events and read the
> information carried by the event. In this case, sensitive information should not be
> carried in common events. The **subscriberPermissions** and **bundleName** parameters
> of this module can be used to restrict the receiving scope of common events.

**Since:** 7

**System capability:** SystemCapability.Notification.CommonEvent

## bundleName

```TypeScript
bundleName?: string
```

Bundle name of the subscriber, which is used to specify the subscriber to whom the common event is published. This parameter is left empty by default. When this parameter is empty, the bundle name of the subscriber is not specified, and all subscribers can receive the common event.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

## code

```TypeScript
code?: number
```

Common event data transferred by the publisher. The default value is **0**.

**Type:** number

**Default:** 0

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

## data

```TypeScript
data?: string
```

Common event data transferred by the publisher. The value is a string and cannot exceed 64 KB. If the value exceeds the limit, the event fails to be published. This parameter is left empty by default.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

## isOrdered

```TypeScript
isOrdered?: boolean
```

Whether the common event is an ordered one. The default value is **false**.

- **true**: This event is an ordered common event. Based on the priority set by the subscriber, the common event is  
preferentially sent to the subscriber with a higher priority. After the subscriber successfully receives the event, the public event is sent to the subscriber with a lower priority. Subscribers with the same priority receive common events in a random order.  
- **false**: This event is an unordered common event. Whether subscribers receive the event is not considered, and  
the common event which subscribers receive may not comply with the subscription sequence.

**Type:** boolean

**Default:** false

**Since:** 7

**System capability:** SystemCapability.Notification.CommonEvent

## isSticky

```TypeScript
isSticky?: boolean
```

Whether the common event is a sticky one. The default value is **false**.

- **true**: This event is a sticky common event, which allows subscribers to receive common events that have been  
sent before subscription.  
- **false**: This event is not a sticky common event, which allows subscribers to receive common events sent after  
subscription.

Only system applications and system services are allowed to send sticky events.

**Required Permissions**: [ohos.permission.COMMONEVENT_STICKY](../../../security/AccessToken/permissions-for-all.md#ohospermissioncommonevent_sticky)

**Type:** boolean

**Default:** false

**Since:** 7

**Required permissions:** ohos.permission.COMMONEVENT_STICKY

**System capability:** SystemCapability.Notification.CommonEvent

## parameters

```TypeScript
parameters?: { [key: string]: any }
```

Additional information about the common event transferred by the publisher. Custom parameters are configured in a key-value pair format. This parameter is left empty by default.

**Type:** { [key: string]: any }

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

## subscriberPermissions

```TypeScript
subscriberPermissions?: Array<string>
```

Subscriber permissions. Only subscribers with the specified permissions can receive the common event. This parameter is left empty by default. When this parameter is empty, the subscriber permissions are not specified, and all subscribers can receive the common event.

**Type:** Array&lt;string&gt;

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent
