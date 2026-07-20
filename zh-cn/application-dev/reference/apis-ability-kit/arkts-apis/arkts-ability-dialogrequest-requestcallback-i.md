# RequestCallback

用于设置模态弹框请求结果的callback接口。

**起始版本：** 9

<!--Device-dialogRequest-export interface RequestCallback--><!--Device-dialogRequest-export interface RequestCallback-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { dialogRequest } from '@kit.AbilityKit';
```

<a id="setrequestresult"></a>
## setRequestResult

```TypeScript
setRequestResult(result: RequestResult): void
```

设置请求结果

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RequestCallback-setRequestResult(result: RequestResult): void--><!--Device-RequestCallback-setRequestResult(result: RequestResult): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | [RequestResult](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-requestresult-i-sys.md) | 是 | 模态弹框请求结果信息。 |

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
      // 从Want中获取请求方的RequestCallback
      let requestCallback = dialogRequest.getRequestCallback(want);
      let myResult: dialogRequest.RequestResult = {
        result : dialogRequest.ResultCode.RESULT_CANCEL,
      };
      // 设置模态弹框的请求结果
      requestCallback.setRequestResult(myResult);
    } catch (err) {
      console.error(`Failed to setRequestResult. Code: ${err.code}, message: ${err.message}`);
    }
  }
}

```

