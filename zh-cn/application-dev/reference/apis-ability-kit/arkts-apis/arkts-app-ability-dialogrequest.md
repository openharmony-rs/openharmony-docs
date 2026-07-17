# @ohos.app.ability.dialogRequest

dialogRequest模块用于处理模态弹框的能力，包括获取RequestInfo（用于绑定模态弹框）、获取RequestCallback（用于设置结果）。

模态弹框是指一个系统弹框，该弹框会拦截弹框之下的页面的鼠标、键盘、触屏等事件。销毁该弹框后，才能对页面进行操作。

> **说明：**  
>  
> - 本模块接口可以在ServiceExtensionAbility下使用，如果ServiceExtensionAbility实现了模态弹框，则可以使用本模块的接口获取请求方的RequestInfo、RequestCallback并  
> 返回请求结果。

**起始版本：** 9

<!--Device-unnamed-declare namespace dialogRequest--><!--Device-unnamed-declare namespace dialogRequest-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { dialogRequest } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getRequestCallback](arkts-ability-dialogrequest-getrequestcallback-f.md#getrequestcallback-1) | 从Want中获取请求方的RequestCallback。 |
| [getRequestInfo](arkts-ability-dialogrequest-getrequestinfo-f.md#getrequestinfo-1) | 从Want中获取请求方的RequestInfo。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [RequestCallback](arkts-ability-dialogrequest-requestcallback-i.md) | 用于设置模态弹框请求结果的callback接口。 |
| [RequestInfo](arkts-ability-dialogrequest-requestinfo-i.md) | 表示发起方请求信息，作为窗口绑定模态弹框的入参。 |
| [RequestResult](arkts-ability-dialogrequest-requestresult-i.md) | 模态弹框请求结果，包含结果码ResultCode和请求结果ResultWant。 |
| [WindowRect](arkts-ability-dialogrequest-windowrect-i.md) | 表示模态弹框的属性。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ResultCode](arkts-ability-dialogrequest-resultcode-e.md) | 模态弹框请求结果码。 |

