# PatchInfo

```TypeScript
interface PatchInfo
```

设备补丁信息。

**起始版本：** 26.1.0

<!--Device-deviceInfo-interface PatchInfo--><!--Device-deviceInfo-interface PatchInfo-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { deviceInfo } from '@kit.MDMKit';
```

## accountName

```TypeScript
accountName: string
```

补丁安装程序的用户名。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PatchInfo-accountName: string--><!--Device-PatchInfo-accountName: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## description

```TypeScript
description: PatchDescription
```

补丁说明。

**类型：** [PatchDescription](arkts-mdm-deviceinfo-patchdescription-i.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PatchInfo-description: PatchDescription--><!--Device-PatchInfo-description: PatchDescription-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## installTime

```TypeScript
installTime: number
```

安装时间戳。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PatchInfo-installTime: number--><!--Device-PatchInfo-installTime: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## name

```TypeScript
name: string
```

补丁名称。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PatchInfo-name: string--><!--Device-PatchInfo-name: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager
