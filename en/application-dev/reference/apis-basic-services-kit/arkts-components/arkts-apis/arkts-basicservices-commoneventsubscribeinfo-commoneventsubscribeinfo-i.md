# CommonEventSubscribeInfo

```TypeScript
export interface CommonEventSubscribeInfo
```

This module provides APIs for providing subscriber information. It allows you to configure parameters such as the subscribed common event type, publisher permission, publisher device ID, user ID, and subscription priority. This module is applicable to scenarios where an app needs to subscribe to system common events or custom common events and requires refined control over event sources.

> **NOTE:** 
> 
> After users subscribing to custom common events, any application can send potential
> malicious common events to subscribers. The **publisherPermission** and
> **publisherBundleName** parameters of this module can be used to restrict the publisher
> scope of common events.

**Since:** 7

**System capability:** SystemCapability.Notification.CommonEvent

## events

```TypeScript
events: Array<string>
```

Common events to subscribe to.

**Type:** Array&lt;string&gt;

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

## priority

```TypeScript
priority?: number
```

Subscriber priority. A larger value indicates a higher priority, and the subscriber with a higher priority receives ordered public events first. The value ranges from –100 to 1000. If the value exceeds the upper or lower limit, the upper or lower limit is used. The default value is **0**.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

## publisherBundleName

```TypeScript
publisherBundleName?: string
```

Bundle name of the publisher to be subscribed to. This parameter is used to restrict the subscriber to receive only public events published by the publisher with the specified bundle name. If this parameter is not set, the subscriber can receive all public events published by the app.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

## publisherDeviceId

```TypeScript
publisherDeviceId?: string
```

Device ID, which is used to restrict the subscriber to receive only public events published by the specified device. Use [@ohos.deviceInfo](arkts-basicservices-deviceinfo.md) to obtain the UDID as the device ID of the publisher. Not supported currently.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

## publisherPermission

```TypeScript
publisherPermission?: string
```

Permission of the publisher. The value is an array of permission names defined by the system. This parameter specifies that the subscriber can only receive the common events from publishers with this permission. If this parameter is left empty, the subscriber can receive common events from all publishers.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent

## userId

```TypeScript
userId?: number
```

User ID, which is used to restrict the subscriber to receive only public events related to the specified user ID. If this parameter is not specified, the default value, which is the ID of the current user, will be used. The value must be an existing user ID in the system. Use [getOsAccountLocalId](arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) to obtain the system user ID and use it as the user ID of the publisher.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.CommonEvent
