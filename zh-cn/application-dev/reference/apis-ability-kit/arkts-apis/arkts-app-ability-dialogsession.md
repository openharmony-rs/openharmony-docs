# @ohos.app.ability.dialogSession

dialogSession模块用于支持系统应用弹框功能。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[getDialogSessionInfo](arkts-ability-dialogsession-getdialogsessioninfo-f-sys.md#getDialogSessionInfo-1) | 通过dialogSessionId获取会话信息。<br/> |
| <!--DelRow-->[sendDialogResult](arkts-ability-dialogsession-senddialogresult-f-sys.md#sendDialogResult-1) | 发送用户请求。使用Promise异步回调。<br/> |
| <!--DelRow-->[sendDialogResult](arkts-ability-dialogsession-senddialogresult-f-sys.md#sendDialogResult-2) | 发送用户请求。使用callback异步回调。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[DialogAbilityInfo](arkts-ability-dialogsession-dialogabilityinfo-i-sys.md) | 提供会话组件信息，包括包名、模块名、组件名等信息。<br/> |
| <!--DelRow-->[DialogSessionInfo](arkts-ability-dialogsession-dialogsessioninfo-i-sys.md) | 提供会话信息，包括请求方信息、目标组件信息列表、其他参数。<br/> |

