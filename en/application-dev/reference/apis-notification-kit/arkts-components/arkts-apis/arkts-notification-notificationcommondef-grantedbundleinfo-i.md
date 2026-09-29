# GrantedBundleInfo

```TypeScript
export interface GrantedBundleInfo
```

Describes the authorized bundle information.

**Since:** 22

<!--Device-unnamed-export interface GrantedBundleInfo--><!--Device-unnamed-export interface GrantedBundleInfo-End-->

**System capability:** SystemCapability.Notification.Notification

## appIndex

```TypeScript
readonly appIndex: number
```

Index of an application clone, which takes effect only for application clones. The value is obtained from the **appIndex** of ApplicationInfo.

**Type:** number

**Since:** 22

<!--Device-GrantedBundleInfo-readonly appIndex: int--><!--Device-GrantedBundleInfo-readonly appIndex: int-End-->

**System capability:** SystemCapability.Notification.Notification

## appName

```TypeScript
readonly appName?: string
```

Application name, which is obtained from the **label** of ApplicationInfo.

**Type:** string

**Since:** 22

<!--Device-GrantedBundleInfo-readonly appName?: string--><!--Device-GrantedBundleInfo-readonly appName?: string-End-->

**System capability:** SystemCapability.Notification.Notification

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 22

<!--Device-GrantedBundleInfo-bundleName: string--><!--Device-GrantedBundleInfo-bundleName: string-End-->

**System capability:** SystemCapability.Notification.Notification
