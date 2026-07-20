# sendEvent

## 导入模块

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
```

<a id="sendevent"></a>
## sendEvent

```TypeScript
function sendEvent(event: EventInfo, callback: AsyncCallback<void>): void
```

发送无障碍事件，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [sendAccessibilityEvent(event:](arkts-accessibility-accessibility-sendaccessibilityevent-f.md#sendaccessibilityevent-1)

<!--Device-accessibility-function sendEvent(event: EventInfo, callback: AsyncCallback<void>): void--><!--Device-accessibility-function sendEvent(event: EventInfo, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [EventInfo](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-update-eventinfo-i-sys.md) | 是 | 辅助事件对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，如果发送无障碍事件失败，则 AsyncCallback中err有数据返回。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendEvent(eventInfo, (err: BusinessError) => {
  if (err) {
    console.error(`failed to sendEvent, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
});

```


<a id="sendevent-1"></a>
## sendEvent

```TypeScript
function sendEvent(event: EventInfo): Promise<void>
```

发送无障碍事件，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [sendAccessibilityEvent(event:](arkts-accessibility-accessibility-sendaccessibilityevent-f.md#sendaccessibilityevent-1)

<!--Device-accessibility-function sendEvent(event: EventInfo): Promise<void>--><!--Device-accessibility-function sendEvent(event: EventInfo): Promise<void>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [EventInfo](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-update-eventinfo-i-sys.md) | 是 | 无障碍事件对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**示例：**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendEvent(eventInfo).then(() => {
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
}).catch((err: BusinessError) => {
  console.error(`failed to sendEvent, Code is ${err.code}, message is ${err.message}`);
});

```

