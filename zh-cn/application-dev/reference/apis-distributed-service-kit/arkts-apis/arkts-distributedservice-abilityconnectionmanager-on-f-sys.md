# on（系统接口）

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

<a id="on"></a>
## on('receiveImage')

```TypeScript
function on(type: 'receiveImage', sessionId: number,
        callback: Callback<EventCallbackInfo>): void
```

Registers receiveImage event.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function on(type: 'receiveImage', sessionId: number,
        callback: Callback<EventCallbackInfo>): void--><!--Device-abilityConnectionManager-function on(type: 'receiveImage', sessionId: number,
        callback: Callback<EventCallbackInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'receiveImage' | 是 | Registration Type, 'receiveImage'. |
| sessionId | number | 是 | Ability connection Session id. |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;EventCallbackInfo&gt; | 是 | Used to handle ('receiveImage') command. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**示例：**

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


<a id="on-1"></a>
## on('collaborateEvent')

```TypeScript
function on(type: 'collaborateEvent', sessionId: number,
        callback: Callback<CollaborateEventInfo>): void
```

Registers collaborateEvent event.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function on(type: 'collaborateEvent', sessionId: number,
        callback: Callback<CollaborateEventInfo>): void--><!--Device-abilityConnectionManager-function on(type: 'collaborateEvent', sessionId: number,
        callback: Callback<CollaborateEventInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'collaborateEvent' | 是 | Registration Type, 'collaborateEvent'. |
| sessionId | number | 是 | Ability connection Session id. |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;CollaborateEventInfo&gt; | 是 | Called when an error event comes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**示例：**

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


<a id="on-2"></a>
## on('collaborateEvent')

```TypeScript
function on(type: 'collaborateEvent', sessionId: number,
        callback: Callback<CollaborateEventInfo>): void
```

Registers collaborateEvent event.

**起始版本：** 18

<!--Device-abilityConnectionManager-function on(type: 'collaborateEvent', sessionId: number,
        callback: Callback<CollaborateEventInfo>): void--><!--Device-abilityConnectionManager-function on(type: 'collaborateEvent', sessionId: number,
        callback: Callback<CollaborateEventInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'collaborateEvent' | 是 | Registration Type, 'collaborateEvent'. |
| sessionId | number | 是 | Ability connection Session id. |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;CollaborateEventInfo&gt; | 是 | Called when an error event comes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例：**

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

