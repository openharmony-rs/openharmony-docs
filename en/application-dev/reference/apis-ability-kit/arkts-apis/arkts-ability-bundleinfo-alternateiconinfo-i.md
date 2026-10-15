# AlternateIconInfo

```TypeScript
export interface AlternateIconInfo
```

Describes the app backup icon information.

**Since:** 26.0.0

<!--Device-unnamed-export interface AlternateIconInfo--><!--Device-unnamed-export interface AlternateIconInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## enabled

```TypeScript
readonly enabled: boolean
```

Whether the backup icon is enabled.

true: The current backup icon is enabled.

false: The current backup icon is not enabled.

NOTE

An app can enable at most one backup icon.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AlternateIconInfo-readonly enabled: boolean--><!--Device-AlternateIconInfo-readonly enabled: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## iconId

```TypeScript
readonly iconId: number
```

Resource ID of the backup icon, which is automatically generated during compilation and build based on the icon configured in the app.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AlternateIconInfo-readonly iconId: long--><!--Device-AlternateIconInfo-readonly iconId: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## iconName

```TypeScript
readonly iconName: string
```

Name of the backup icon.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AlternateIconInfo-readonly iconName: string--><!--Device-AlternateIconInfo-readonly iconName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
