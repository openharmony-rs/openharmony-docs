# sendAccessibilityEvent

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
import { accessibility } from '@kit.AccessibilityKit';
import { AccessibilityEventType, AccessibilityAction, FocusMoveResultCode, InjectActionType, AccessibilityFocusScene, FocusRuleType, OperateVirtualNodeResult, AccessibilitySourceType } from '@kit.AccessibilityKit';
import { GesturePath } from '@kit.AccessibilityKit';
import { GesturePoint } from '@kit.AccessibilityKit';
```

## sendAccessibilityEvent

```TypeScript
function sendAccessibilityEvent(event: EventInfo, callback: AsyncCallback<void>): void
```

发送无障碍事件，事件将被分发到系统中已注册且匹配事件类型的辅助应用进行响应。使用callback异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-accessibility-function sendAccessibilityEvent(event: EventInfo, callback: AsyncCallback<void>): void--><!--Device-accessibility-function sendAccessibilityEvent(event: EventInfo, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | EventInfo | 是 | 无障碍事件对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当发送无障碍事件成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to send event. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError | null) => {
  if (err?.code) {
    console.error(`failed to send event, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

ArkTS-Dyn示例：

```TypeScript
@Entry
@Component
struct Index {

  build() {
    Column() {
      // 待聚焦组件添加id属性，id唯一性由使用者保证。
      Button('待聚焦组件').id('click')
    }
  }
}
```

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'requestFocusForAccessibility',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'common',
  customId: 'click' // 对应待聚焦组件id属性值。
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to send event. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

ArkTS-Sta示例：

```TypeScript
@Entry
@Component
struct Index {

  build() {
    Column() {
      // 待聚焦组件添加id属性，id唯一性由使用者保证。
      Button('待聚焦组件').id('click')
    }
  }
}
```

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'requestFocusForAccessibility',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'common',
  customId: 'click' // 对应待聚焦组件id属性值。
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError | null) => {
  if (err?.code) {
    console.error(`failed to send event, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

ArkTS-Dyn示例：

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'announceForAccessibility',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'common',
  textResourceAnnouncedForAccessibility: $r('app.string.ResourceName'),
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to send event. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'announceForAccessibility',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'common',
  textResourceAnnouncedForAccessibility: $r('app.string.ResourceName'),
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError | null) => {
  if (err?.code) {
    console.error(`failed to send event, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in sending event, eventInfo is ${eventInfo}`);
});
```


## sendAccessibilityEvent

```TypeScript
function sendAccessibilityEvent(event: EventInfo): Promise<void>
```

发送无障碍事件，事件将被分发到系统中已注册且匹配事件类型的辅助扩展应用进行响应。使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-accessibility-function sendAccessibilityEvent(event: EventInfo): Promise<void>--><!--Device-accessibility-function sendAccessibilityEvent(event: EventInfo): Promise<void>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | EventInfo | 是 | 无障碍事件对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendAccessibilityEvent(eventInfo).then(() => {
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to send event. Code: ${err.code}, message: ${err.message}`);
});
```

