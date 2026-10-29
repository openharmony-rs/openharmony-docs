# DistributedBundleEnableInfo (System API)

```TypeScript
export interface DistributedBundleEnableInfo
```

Describes the bundle information of an application that enables cross-device collaboration.

**Since:** 20

<!--Device-notificationManager-export interface DistributedBundleEnableInfo--><!--Device-notificationManager-export interface DistributedBundleEnableInfo-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { notificationManager } from '@kit.NotificationKit';
```

## bundleName

```TypeScript
bundleName: string
```

Bundle name.

**Type:** string

**Since:** 20

<!--Device-DistributedBundleEnableInfo-bundleName: string--><!--Device-DistributedBundleEnableInfo-bundleName: string-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## enable

```TypeScript
enable?: boolean
```

Whether [cross-device collaboration](../../../notification/notification-glossary.md#cross-device-collaboration) is supported. The value **true** indicates supported, and **false** indicates not supported. The default value is **false**.

**Type:** boolean

**Since:** 20

<!--Device-DistributedBundleEnableInfo-enable?: boolean--><!--Device-DistributedBundleEnableInfo-enable?: boolean-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## uid

```TypeScript
uid: number
```

UID of the application.

**Type:** number

**Since:** 20

<!--Device-DistributedBundleEnableInfo-uid: int--><!--Device-DistributedBundleEnableInfo-uid: int-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
