# getRequestCallback

## 导入模块

```TypeScript
import { dialogRequest } from '@kit.AbilityKit';
```

## getRequestCallback

```TypeScript
function getRequestCallback(want: Want): RequestCallback
```

从Want中获取请求方的RequestCallback。

> **说明：**  
>  
> 该接口可以在ServiceExtensionAbility下使用，如果ServiceExtensionAbility实现了模态弹框，则能从Want中获取请求方的RequestCallback。其他场景使用该接口，均无法获取返回  
> 值。

**起始版本：** 9

<!--Device-dialogRequest-function getRequestCallback(want: Want): RequestCallback--><!--Device-dialogRequest-function getRequestCallback(want: Want): RequestCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 表示发起方请求弹框时传入的want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RequestCallback](arkts-ability-dialogrequest-requestcallback-i.md) | 请求方RequestCallback，用于设置返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { AbilityConstant, UIAbility, Want, dialogRequest } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    try {
      // 获取请求方的RequestCallback
      let requestCallback = dialogRequest.getRequestCallback(want);
    } catch (err) {
      console.error(`Failed to getRequestCallback. Code: ${err.code}, message: ${err.message}`);
    }
  }
}

```

