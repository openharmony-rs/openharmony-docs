# CommonEventSubscribeInfo

```TypeScript
export interface CommonEventSubscribeInfo
```

This module provides APIs for providing subscriber information. It allows you to configure parameters such as the subscribed common event type, publisher permission, publisher device ID, user ID, and subscription priority. This module is applicable to scenarios where an app needs to subscribe to [system common events](../../../basic-services/common-event/common-event-glossary.md#system-common-event) or custom common events and requires refined control over event sources.

> **NOTE:** 
> 
> After users subscribe to custom common events, any app can send potential malicious common events to subscribers.
> Use the **publisherPermission** and **publisherBundleName** parameters of this module to restrict the publishing
> scope of common events.

**Since:** 7

<!--Device-unnamed-export interface CommonEventSubscribeInfo--><!--Device-unnamed-export interface CommonEventSubscribeInfo-End-->

**System capability:** SystemCapability.Notification.CommonEvent

## events

```TypeScript
events: Array<string>
```

Common events to subscribe to.

**Type:** Array&lt;string&gt;

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscribeInfo-events: Array<string>--><!--Device-CommonEventSubscribeInfo-events: Array<string>-End-->

**System capability:** SystemCapability.Notification.CommonEvent

## priority

```TypeScript
priority?: number
```

Subscriber priority. Subscribers with higher priorities receive [ordered common events](../../../basic-services/common-event/common-event-glossary.md#ordered-common-event) first. The value ranges from –100 to 1000. If the value exceeds the upper or lower limit, the upper or lower limit is used. The default value is **0**.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscribeInfo-priority?: int--><!--Device-CommonEventSubscribeInfo-priority?: int-End-->

**System capability:** SystemCapability.Notification.CommonEvent

## publisherBundleName

```TypeScript
publisherBundleName?: string
```

Bundle name of the publisher to be subscribed to. This parameter is used to specify that the subscriber receives only public events published by the publisher with the specified bundle name. If this parameter is not set, the subscriber can receive all public events published by the app. The value can contain a maximum of 254 bytes. Excess content will be truncated.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscribeInfo-publisherBundleName?: string--><!--Device-CommonEventSubscribeInfo-publisherBundleName?: string-End-->

**System capability:** SystemCapability.Notification.CommonEvent

## publisherDeviceId

```TypeScript
publisherDeviceId?: string
```

Device ID, which is used to specify that the subscriber receives only common events published by the specified device. Use [@ohos.deviceInfo](arkts-basicservices-deviceinfo.md) to obtain the UDID as the device ID of the publisher. This feature is not supported currently. The value can contain a maximum of 254 bytes. Excess content will be truncated.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscribeInfo-publisherDeviceId?: string--><!--Device-CommonEventSubscribeInfo-publisherDeviceId?: string-End-->

**System capability:** SystemCapability.Notification.CommonEvent

## publisherPermission

```TypeScript
publisherPermission?: string
```

Permission of the publisher. The value is a permission name defined by the system. This parameter is used to specify that the subscriber receives only common events published by the publisher with this permission. If this parameter is not set, the subscriber can receive common events published by all publishers. The value can contain a maximum of 254 bytes. Excess content will be truncated.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscribeInfo-publisherPermission?: string--><!--Device-CommonEventSubscribeInfo-publisherPermission?: string-End-->

**System capability:** SystemCapability.Notification.CommonEvent

## userId

```TypeScript
userId?: number
```

User ID, which is used to specify that the subscriber receives only common events related to the specified user ID. If this parameter is not specified, the default value, which is the ID of the current user, will be used. The value must be an existing user ID in the system. Use [getOsAccountLocalId](arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) to obtain the system user ID and use it as the user ID of the publisher.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CommonEventSubscribeInfo-userId?: int--><!--Device-CommonEventSubscribeInfo-userId?: int-End-->

**System capability:** SystemCapability.Notification.CommonEvent
