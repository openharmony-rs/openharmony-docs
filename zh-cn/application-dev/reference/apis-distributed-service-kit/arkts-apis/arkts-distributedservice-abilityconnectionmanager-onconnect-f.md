# onConnect

## onConnect

```TypeScript
function onConnect(sessionId: int,
        callback: Callback<EventCallbackInfo>): void
```

Registers connect event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function onConnect(sessionId: int,        callback: Callback<EventCallbackInfo>): void--><!--Device-abilityConnectionManager-function onConnect(sessionId: int,        callback: Callback<EventCallbackInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | int | 是 | Ability connection Session id. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[EventCallbackInfo](arkts-distributedservice-abilityconnectionmanager-eventcallbackinfo-i.md)&gt; | 是 | Used to handle ('connect') command. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

## 示例

```TypeScript
import abilityConnectionManager from '@ohos.distributedsched.abilityConnectionManager';
import hilog from '@ohos.hilog';

let sessionId = 100;
abilityConnectionManager.onDisconnect(sessionId,(callbackInfo) => {
  hilog.info(0x0000, 'testTag', 'session disconnect, sessionId is', callbackInfo.sessionId);
});
```

