# UpdatePackageInfo

```TypeScript
export interface UpdatePackageInfo
```

Represents information about the system update packages.

**Since:** 12

<!--Device-systemManager-export interface UpdatePackageInfo--><!--Device-systemManager-export interface UpdatePackageInfo-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## authInfo

```TypeScript
authInfo?: string
```

Authentication information of the system update package.

**Type:** string

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

<!--Device-UpdatePackageInfo-authInfo?: string--><!--Device-UpdatePackageInfo-authInfo?: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## description

```TypeScript
description?: PackageDescription
```

Description of the system update packages.

**Type:** [PackageDescription](arkts-mdm-systemmanager-packagedescription-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-UpdatePackageInfo-description?: PackageDescription--><!--Device-UpdatePackageInfo-description?: PackageDescription-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## packages

```TypeScript
packages: Array<Package>
```

Details about the system update packages.

**Type:** Array&lt;[Package](arkts-mdm-systemmanager-package-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-UpdatePackageInfo-packages: Array<Package>--><!--Device-UpdatePackageInfo-packages: Array<Package>-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## version

```TypeScript
version: string
```

Version of the system update package.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-UpdatePackageInfo-version: string--><!--Device-UpdatePackageInfo-version: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
