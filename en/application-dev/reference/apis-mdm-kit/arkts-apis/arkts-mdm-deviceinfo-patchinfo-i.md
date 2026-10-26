# PatchInfo

```TypeScript
interface PatchInfo
```

Indicates the device patch information.

**Since:** 26.1.0

<!--Device-deviceInfo-interface PatchInfo--><!--Device-deviceInfo-interface PatchInfo-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { deviceInfo } from '@kit.MDMKit';
```

## accountName

```TypeScript
accountName: string
```

User name of the patch installer.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PatchInfo-accountName: string--><!--Device-PatchInfo-accountName: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## description

```TypeScript
description: PatchDescription
```

Patch description.

**Type:** [PatchDescription](arkts-mdm-deviceinfo-patchdescription-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PatchInfo-description: PatchDescription--><!--Device-PatchInfo-description: PatchDescription-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## installTime

```TypeScript
installTime: number
```

Installation timestamp.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PatchInfo-installTime: number--><!--Device-PatchInfo-installTime: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## name

```TypeScript
name: string
```

Patch name.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PatchInfo-name: string--><!--Device-PatchInfo-name: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
