# sendDialogResult（系统接口）

## 导入模块

```TypeScript
import { dialogSession } from '@kit.AbilityKit';
```

## sendDialogResult

```TypeScript
function sendDialogResult(dialogSessionId: string, targetWant: Want, isAllowed: boolean): Promise<void>
```

发送用户请求。使用Promise异步回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dialogSessionId | string | 是 | 用户请求会话ID。 |
| targetWant | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 用户请求目标。 |
| isAllowed | boolean | 是 | 是否允许拉起目标Ability。true表示允许，false表示不允许。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
import { dialogSession, Want, UIExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UIExtAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    // want由系统内部指定，dialogSessionId为内置参数
    let dialogSessionId = want?.parameters?.dialogSessionId.toString();

    // 查询DialogSessionInfo
    let dialogSessionInfo: dialogSession.DialogSessionInfo = dialogSession.getDialogSessionInfo(dialogSessionId);

    let isAllow: boolean = true;

    let targetWant: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };

    try {
      dialogSession.sendDialogResult(dialogSessionId, targetWant, isAllow)
        .then((data) => {
          console.info(`sendDialogResult success`);
        }, (err: BusinessError) => {
          console.error(`sendDialogResult error, errorCode: ${err.code}`);
        });
    } catch (err) {
      console.error(`sendDialogResult error, errorCode: ${(err as BusinessError).code}`);
    }
  }
}
```


## sendDialogResult

```TypeScript
function sendDialogResult(dialogSessionId: string, targetWant: Want, isAllowed: boolean, callback: AsyncCallback<void>): void
```

发送用户请求。使用callback异步回调。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dialogSessionId | string | 是 | 用户请求会话ID。 |
| targetWant | [Want](arkts-ability-app-ability-want-want-c.md) | 是 | 用户请求目标。 |
| isAllowed | boolean | 是 | 是否允许拉起目标Ability。true表示允许，false表示不允许。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当发送用户请求成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**

```TypeScript
import { dialogSession, Want, UIExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UIExtAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    // want由系统内部指定，dialogSessionId为内置参数
    let dialogSessionId = want?.parameters?.dialogSessionId.toString();

    // 查询DialogSessionInfo
    let dialogSessionInfo: dialogSession.DialogSessionInfo =
      dialogSession.getDialogSessionInfo(dialogSessionId);

    let isAllow: boolean = true;

    let targetWant: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };

    try {
      dialogSession.sendDialogResult(dialogSessionId, targetWant, isAllow, (err, data) => {
        if (err) {
          console.error(`sendDialogResult error, errorCode: ${err.code}`);
        } else {
          console.info(`sendDialogResult success`);
        }
      });
    } catch (err) {
      console.error(`sendDialogResult error, errorCode: ${(err as BusinessError).code}`);
    }
  }
}
```
