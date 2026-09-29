# BundleOption

```TypeScript
export interface BundleOption
```

Describes the **BundleOption** information, that is, the bundle information of an application.

**Since:** 9

<!--Device-unnamed-export interface BundleOption--><!--Device-unnamed-export interface BundleOption-End-->

**System capability:** SystemCapability.Notification.Notification

## bundle

```TypeScript
bundle: string
```

Bundle name of the application.

**Type:** string

**Since:** 9

<!--Device-BundleOption-bundle: string--><!--Device-BundleOption-bundle: string-End-->

**System capability:** SystemCapability.Notification.Notification

## uid

```TypeScript
uid?: number
```

UID of the application, which is obtained from ApplicationInfo. The default value is **0**. This parameter is mandatory in application clone scenarios.

**Type:** number

**Since:** 9

<!--Device-BundleOption-uid?: int--><!--Device-BundleOption-uid?: int-End-->

**System capability:** SystemCapability.Notification.Notification
