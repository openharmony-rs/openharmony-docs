# on_scrollEvent

## 导入模块

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## on('scrollEvent')

```TypeScript
export function on(type: 'scrollEvent', options: ObserverOptions, callback: Callback<ScrollEventInfo>): void
```

Registers a callback function to be called when the scroll event start or stop.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function on(type: 'scrollEvent', options: ObserverOptions, callback: Callback<ScrollEventInfo>): void--><!--Device-uiObserver-export function on(type: 'scrollEvent', options: ObserverOptions, callback: Callback<ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to listen for. Must be 'scrollEvent'. |
| options | ObserverOptions | 是 | The options object. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md)&gt; | 是 | The callback function to be called when the scroll event start or stop. |


## on('scrollEvent')

```TypeScript
export function on(type: 'scrollEvent', callback: Callback<ScrollEventInfo>): void
```

Registers a callback function to be called when the scroll event start or stop.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-uiObserver-export function on(type: 'scrollEvent', callback: Callback<ScrollEventInfo>): void--><!--Device-uiObserver-export function on(type: 'scrollEvent', callback: Callback<ScrollEventInfo>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'scrollEvent' | 是 | The type of event to listen for. Must be 'scrollEvent'. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ScrollEventInfo](arkts-arkui-uiobserver-scrolleventinfo-i.md)&gt; | 是 | The callback function to be called when the scroll event start or stop. |

