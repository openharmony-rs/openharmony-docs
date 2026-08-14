# offConnect

## offConnect

```TypeScript
function offConnect(sessionId: int,
        callback?: Callback<EventCallbackInfo>): void
```

Unregisters connect event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function offConnect(sessionId: int,        callback?: Callback<EventCallbackInfo>): void--><!--Device-abilityConnectionManager-function offConnect(sessionId: int,        callback?: Callback<EventCallbackInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | int | 是 | Ability connection Session id. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[EventCallbackInfo](arkts-distributedservice-abilityconnectionmanager-eventcallbackinfo-i.md)&gt; | 否 | Used to handle ('connect') command. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |

## 示例

```TypeScript
import abilityConnectionManager from '@ohos.distributedsched.abilityConnectionManager';

let sessionId = 100;
abilityConnectionManager.offConnect(sessionId,(callbackInfo) => {});
```

