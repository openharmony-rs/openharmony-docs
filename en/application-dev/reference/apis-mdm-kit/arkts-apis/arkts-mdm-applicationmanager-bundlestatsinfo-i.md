# BundleStatsInfo

```TypeScript
interface BundleStatsInfo
```

Application bundle statistics.

**Since:** 26.0.0

<!--Device-applicationManager-interface BundleStatsInfo--><!--Device-applicationManager-interface BundleStatsInfo-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## abilityInFgTotalTime

```TypeScript
abilityInFgTotalTime: number
```

Total duration that the ability runs in the foreground, in milliseconds.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleStatsInfo-abilityInFgTotalTime: number--><!--Device-BundleStatsInfo-abilityInFgTotalTime: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## appIndex

```TypeScript
appIndex: number
```

Index of the application clone. The value is an integer greater than or equal to 0. You can call [getAppCloneIdentity](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getappcloneidentity-f.md) of @ ohos.bundle.bundleManager to obtain the index.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleStatsInfo-appIndex: number--><!--Device-BundleStatsInfo-appIndex: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleStatsInfo-bundleName: string--><!--Device-BundleStatsInfo-bundleName: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
