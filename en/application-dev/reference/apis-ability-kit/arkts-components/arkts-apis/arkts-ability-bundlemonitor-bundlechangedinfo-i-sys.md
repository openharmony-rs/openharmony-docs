# BundleChangedInfo (System API)

```TypeScript
interface BundleChangedInfo
```

This module defines the result information of monitoring install, update and uninstall.

@typedef BundleChangedInfo

**Since:** 9

<!--Device-bundleMonitor-interface BundleChangedInfo--><!--Device-bundleMonitor-interface BundleChangedInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { bundleMonitor } from '@kit.AbilityKit';
```

## appIndex

```TypeScript
readonly appIndex: number
```

The app index of clone app

**Type:** number

**Since:** 12

<!--Device-BundleChangedInfo-readonly appIndex: int--><!--Device-BundleChangedInfo-readonly appIndex: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## bundleName

```TypeScript
readonly bundleName: string
```

The bundle name

**Type:** string

**Since:** 9

<!--Device-BundleChangedInfo-readonly bundleName: string--><!--Device-BundleChangedInfo-readonly bundleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## userId

```TypeScript
readonly userId: number
```

The user id

**Type:** number

**Since:** 9

<!--Device-BundleChangedInfo-readonly userId: int--><!--Device-BundleChangedInfo-readonly userId: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
