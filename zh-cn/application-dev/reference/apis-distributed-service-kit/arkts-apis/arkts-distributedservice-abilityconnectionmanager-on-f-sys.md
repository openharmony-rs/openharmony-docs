# on（系统接口）

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## on('receiveImage')

```TypeScript
function on(type: 'receiveImage', sessionId: number,
        callback: Callback<EventCallbackInfo>): void
```

注册receiveImage事件的回调监听。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'receiveImage' | 是 | 事件注册类型，'receiveImage'。 |
| sessionId | number | 是 | 协同会话ID。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[EventCallbackInfo](arkts-distributedservice-abilityconnectionmanager-eventcallbackinfo-i.md)&gt; | 是 | 用于处理('receiveImage')事件的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// sessionId需通过协同会话创建接口获取
let sessionId = 100;
// 注册receiveImage事件监听
abilityConnectionManager.on('receiveImage', sessionId, (callbackInfo) => {
  hilog.info(0x0000, 'testTag', 'session receiveImage, sessionId is', callbackInfo.sessionId);
});
```


## on('collaborateEvent')

```TypeScript
function on(type: 'collaborateEvent', sessionId: number,
        callback: Callback<CollaborateEventInfo>): void
```

注册collaborateEvent事件的回调监听。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'collaborateEvent' | 是 | 事件注册类型，'collaborateEvent'。 |
| sessionId | number | 是 | 协同会话ID。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CollaborateEventInfo](arkts-distributedservice-abilityconnectionmanager-collaborateeventinfo-i.md)&gt; | 是 | 错误事件回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// sessionId需通过协同会话创建接口获取
let sessionId = 100;
// 注册collaborateEvent事件监听
abilityConnectionManager.on('collaborateEvent', sessionId, (callbackInfo) => {
  hilog.info(0x0000, 'testTag', 'session collaborateEvent, eventType is', callbackInfo.eventType);
});
```
