# onCollaborateEvent（系统接口）

## onCollaborateEvent

```TypeScript
function onCollaborateEvent(sessionId: int,
        callback: Callback<CollaborateEventInfo>): void
```

Registers collaborateEvent event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function onCollaborateEvent(sessionId: int,        callback: Callback<CollaborateEventInfo>): void--><!--Device-abilityConnectionManager-function onCollaborateEvent(sessionId: int,        callback: Callback<CollaborateEventInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | int | 是 | Ability connection Session id. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[CollaborateEventInfo](arkts-distributedservice-abilityconnectionmanager-collaborateeventinfo-i.md)&gt; | 是 | Called when an error event comes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |

## 示例

```TypeScript
import abilityConnectionManager from '@ohos.distributedsched.abilityConnectionManager';
import { hilog } from '@kit.PerformanceAnalysisKit';

let sessionId = 100;
abilityConnectionManager.onCollaborateEvent(sessionId, (callbackInfo) => {
  hilog.info(0x0000, 'testTag', 'session collaborateEvent, eventType is', callbackInfo.eventType);
});
```

