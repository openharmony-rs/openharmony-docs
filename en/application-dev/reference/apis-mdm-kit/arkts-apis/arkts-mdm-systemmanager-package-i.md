# Package

Represents the details about a system update package.

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## fd

```TypeScript
fd?: number
```

File descriptor (FD) of the system update package. Currently, you cannot pass in **path** only. The **fd** parameter must also be passed in.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## path

```TypeScript
path: string
```

Path of the system update package. If **fd** is specified, pass in the update package name here.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## type

```TypeScript
type: PackageType
```

Type of the system update package.

**Type:** [PackageType](arkts-mdm-systemmanager-packagetype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
