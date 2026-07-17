# on

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## on('connect')

```TypeScript
function on(type: 'connect', sessionId: number,
        callback: Callback<EventCallbackInfo>): void
```

注册connect事件的回调监听。使用callback异步回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function on(type: 'connect', sessionId: number,
        callback: Callback<EventCallbackInfo>): void--><!--Device-abilityConnectionManager-function on(type: 'connect', sessionId: number,
        callback: Callback<EventCallbackInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'connect' | 是 | 事件回调类型，支持的事件为'connect'，完成[abilityConnectionManager.connect()](arkts-distributedservice-abilityconnectionmanager-connect-f.md#connect-1)调用，触发该事件。 |
| sessionId | number | 是 | 创建的协同会话ID。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<EventCallbackInfo> | 是 | 注册的回调函数。 |

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
abilityConnectionManager.on("connect", sessionId,(callbackInfo) => {
  hilog.info(0x0000, 'testTag', 'session connect, sessionId is', callbackInfo.sessionId);
});


```


## on('disconnect')

```TypeScript
function on(type: 'disconnect', sessionId: number,
        callback: Callback<EventCallbackInfo>): void
```

注册disconnect事件的回调监听。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function on(type: 'disconnect', sessionId: number,
        callback: Callback<EventCallbackInfo>): void--><!--Device-abilityConnectionManager-function on(type: 'disconnect', sessionId: number,
        callback: Callback<EventCallbackInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'disconnect' | 是 | 事件回调类型，支持的事件为'disconnect'，完成[abilityConnectionManager.disconnect()](arkts-distributedservice-abilityconnectionmanager-disconnect-f.md#disconnect-1)调用，触发该事件。 |
| sessionId | number | 是 | 创建的协同会话ID。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<EventCallbackInfo> | 是 | 注册的回调函数。 |

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
abilityConnectionManager.on("disconnect", sessionId,(callbackInfo) => {
  hilog.info(0x0000, 'testTag', 'session disconnect, sessionId is', callbackInfo.sessionId);
});


```


## on('receiveMessage')

```TypeScript
function on(type: 'receiveMessage', sessionId: number,
        callback: Callback<EventCallbackInfo>): void
```

注册receiveMessage事件的回调监听。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function on(type: 'receiveMessage', sessionId: number,
        callback: Callback<EventCallbackInfo>): void--><!--Device-abilityConnectionManager-function on(type: 'receiveMessage', sessionId: number,
        callback: Callback<EventCallbackInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'receiveMessage' | 是 | 事件回调类型，支持的事件为'receiveMessage'，完成[abilityConnectionManager.sendMessage()](arkts-distributedservice-abilityconnectionmanager-sendmessage-f.md#sendmessage-1)调用，触发该事件。 |
| sessionId | number | 是 | 创建的协同会话ID。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<EventCallbackInfo> | 是 | 注册的回调函数。 |

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
abilityConnectionManager.on("receiveMessage", sessionId,(callbackInfo) => {
  hilog.info(0x0000, 'testTag', 'receiveMessage, sessionId is', callbackInfo.sessionId);
});


```


## on('receiveData')

```TypeScript
function on(type: 'receiveData', sessionId: number,
        callback: Callback<EventCallbackInfo>): void
```

注册receiveData事件的回调监听。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function on(type: 'receiveData', sessionId: number,
        callback: Callback<EventCallbackInfo>): void--><!--Device-abilityConnectionManager-function on(type: 'receiveData', sessionId: number,
        callback: Callback<EventCallbackInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'receiveData' | 是 | 事件回调类型，支持的事件为'receiveData'，完成[abilityConnectionManager.sendData()](arkts-distributedservice-abilityconnectionmanager-senddata-f.md#senddata-1)调用，触发该事件。 |
| sessionId | number | 是 | 创建的协同会话ID。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<EventCallbackInfo> | 是 | 注册的回调函数。 |

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
abilityConnectionManager.on("receiveData", sessionId,(callbackInfo) => {
  hilog.info(0x0000, 'testTag', 'receiveData, sessionId is', callbackInfo.sessionId);
});


```

