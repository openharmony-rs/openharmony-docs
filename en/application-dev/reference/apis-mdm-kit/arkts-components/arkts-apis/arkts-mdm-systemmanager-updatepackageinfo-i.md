# UpdatePackageInfo

Represents information about the system update packages.

**Since:** 12

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

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## description

```TypeScript
description?: PackageDescription
```

Description of the system update packages.

**Type:** [PackageDescription](arkts-mdm-systemmanager-packagedescription-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## packages

```TypeScript
packages: Array<Package>
```

Details about the system update packages.

**Type:** Array&lt;[Package](arkts-mdm-systemmanager-package-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## version

```TypeScript
version: string
```

Version of the system update package.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
