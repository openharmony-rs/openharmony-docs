# PatchDescription

```TypeScript
interface PatchDescription
```

补丁描述信息。

**起始版本：** 26.1.0

<!--Device-deviceInfo-interface PatchDescription--><!--Device-deviceInfo-interface PatchDescription-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { deviceInfo } from '@kit.MDMKit';
```

## bodies

```TypeScript
bodies: Array<PatchDescriptionBody>
```

说明正文项。

**类型：** Array&lt;[PatchDescriptionBody](arkts-mdm-deviceinfo-patchdescriptionbody-i.md)&gt;

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PatchDescription-bodies: Array<PatchDescriptionBody>--><!--Device-PatchDescription-bodies: Array<PatchDescriptionBody>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## headers

```TypeScript
headers: Array<string>
```

描述标题。

**类型：** Array&lt;string&gt;

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PatchDescription-headers: Array<string>--><!--Device-PatchDescription-headers: Array<string>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager
