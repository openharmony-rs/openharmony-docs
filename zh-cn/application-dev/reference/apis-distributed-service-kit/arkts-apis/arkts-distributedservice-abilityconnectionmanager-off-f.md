# off

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## off('connect')

```TypeScript
function off(type: 'connect', sessionId: number,
        callback?: Callback<EventCallbackInfo>): void
```

取消connect事件的回调监听。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function off(type: 'connect', sessionId: number,
        callback?: Callback<EventCallbackInfo>): void--><!--Device-abilityConnectionManager-function off(type: 'connect', sessionId: number,
        callback?: Callback<EventCallbackInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' | 是 | 事件回调类型，支持的事件为'connect'。 |
| sessionId | number | 是 | 创建的协同会话ID。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<EventCallbackInfo> | 否 | 注册的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';

// sessionId需通过createAbilityConnectionSession接口创建并获取，此处仅为示例
let sessionId = 100;
abilityConnectionManager.off("connect", sessionId);


```


## off('disconnect')

```TypeScript
function off(type: 'disconnect', sessionId: number,
        callback?: Callback<EventCallbackInfo>): void
```

取消disconnect事件的回调监听。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function off(type: 'disconnect', sessionId: number,
        callback?: Callback<EventCallbackInfo>): void--><!--Device-abilityConnectionManager-function off(type: 'disconnect', sessionId: number,
        callback?: Callback<EventCallbackInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'disconnect' | 是 | 事件回调类型，支持的事件为'disconnect'。 |
| sessionId | number | 是 | 创建的协同会话ID。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<EventCallbackInfo> | 否 | 注册的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// sessionId需通过createAbilityConnectionSession接口创建并获取，此处仅为示例
let sessionId = 101;
abilityConnectionManager.off("disconnect", sessionId);


```


## off('receiveMessage')

```TypeScript
function off(type: 'receiveMessage', sessionId: number,
        callback?: Callback<EventCallbackInfo>): void
```

取消receiveMessage事件的回调监听。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function off(type: 'receiveMessage', sessionId: number,
        callback?: Callback<EventCallbackInfo>): void--><!--Device-abilityConnectionManager-function off(type: 'receiveMessage', sessionId: number,
        callback?: Callback<EventCallbackInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'receiveMessage' | 是 | 事件回调类型，支持的事件为'receiveMessage'。 |
| sessionId | number | 是 | 创建的协同会话ID。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<EventCallbackInfo> | 否 | 注册的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// sessionId需通过createAbilityConnectionSession接口创建并获取，此处仅为示例
let sessionId = 100;
abilityConnectionManager.off("receiveMessage", sessionId);


```


## off('receiveData')

```TypeScript
function off(type: 'receiveData', sessionId: number,
        callback?: Callback<EventCallbackInfo>): void
```

取消receiveData事件的回调监听。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function off(type: 'receiveData', sessionId: number,
        callback?: Callback<EventCallbackInfo>): void--><!--Device-abilityConnectionManager-function off(type: 'receiveData', sessionId: number,
        callback?: Callback<EventCallbackInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'receiveData' | 是 | 事件回调类型，支持的事件为'receiveData'，完成。 |
| sessionId | number | 是 | 创建的协同会话ID。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<EventCallbackInfo> | 否 | 注册的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// sessionId需通过createAbilityConnectionSession接口创建并获取，此处仅为示例
let sessionId = 100;
abilityConnectionManager.off("receiveData", sessionId);


```

