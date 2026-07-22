# TemplateStatus（系统接口）

用于描述已注册的伴随设备认证模板的完整状态信息，包括模板ID、数据确认状态、有效性、用户ID、添加时间、支持的业务范围以及关联的设备状态等。

**起始版本：** 23

<!--Device-companionDeviceAuth-interface TemplateStatus--><!--Device-companionDeviceAuth-interface TemplateStatus-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## addedTime

```TypeScript
addedTime: Date
```

模板添加时间。模板创建的时间戳，格式为Unix时间戳，即自1970年1月1日起经过的毫秒数。

**类型：** Date

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TemplateStatus-addedTime: Date--><!--Device-TemplateStatus-addedTime: Date-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## deviceStatus

```TypeScript
deviceStatus: DeviceStatus
```

设备状态信息。与该模板关联的伴随设备的当前状态，包括在线状态、设备名等。

**类型：** DeviceStatus

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TemplateStatus-deviceStatus: DeviceStatus--><!--Device-TemplateStatus-deviceStatus: DeviceStatus-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## enabledBusinessIds

```TypeScript
enabledBusinessIds: number[]
```

支持的业务ID列表。该模板已启用的业务场景范围，可通过[updateEnabledBusinessIds](arkts-userauthentication-companiondeviceauth-updateenabledbusinessids-f-sys.md#updateenabledbusinessids)接口更新。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TemplateStatus-enabledBusinessIds: int[]--><!--Device-TemplateStatus-enabledBusinessIds: int[]-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## isConfirmed

```TypeScript
isConfirmed: boolean
```

数据确认状态。true表示数据是实时数据，已与设备确认同步；false表示数据是缓存数据，可能与设备实际状态存在差异。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TemplateStatus-isConfirmed: boolean--><!--Device-TemplateStatus-isConfirmed: boolean-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## isValid

```TypeScript
isValid: boolean
```

模板有效性。true表示模板有效，可用于认证；false表示模板无效，可能已被删除或失效，无法用于认证。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TemplateStatus-isValid: boolean--><!--Device-TemplateStatus-isValid: boolean-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## localUserId

```TypeScript
localUserId: number
```

本地用户ID。主设备上与该模板关联的用户标识，为大于等于0的正整数。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TemplateStatus-localUserId: int--><!--Device-TemplateStatus-localUserId: int-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## templateId

```TypeScript
templateId: Uint8Array
```

模板ID。伴随设备认证模板的唯一标识，用于在更新业务范围或订阅认证状态时指定目标模板。

**类型：** Uint8Array

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TemplateStatus-templateId: Uint8Array--><!--Device-TemplateStatus-templateId: Uint8Array-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

