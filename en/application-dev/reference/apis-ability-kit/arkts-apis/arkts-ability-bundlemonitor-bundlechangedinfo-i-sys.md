# BundleChangedInfo (System API)

```TypeScript
interface BundleChangedInfo
```

Application Change Information.

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

Index of the application clone whose status changes.

**Type:** number

**Since:** 12

<!--Device-BundleChangedInfo-readonly appIndex: int--><!--Device-BundleChangedInfo-readonly appIndex: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## bundleName

```TypeScript
readonly bundleName: string
```

Name of the bundle whose status changes.

**Type:** string

**Since:** 9

<!--Device-BundleChangedInfo-readonly bundleName: string--><!--Device-BundleChangedInfo-readonly bundleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## userId

```TypeScript
readonly userId: number
```

ID of the user for whom the bundle status changes. You can obtain the ID by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid).

**Type:** number

**Since:** 9

<!--Device-BundleChangedInfo-readonly userId: int--><!--Device-BundleChangedInfo-readonly userId: int-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
