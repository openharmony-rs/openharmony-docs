# EventResult

EventResult是ArkWeb Kit中用于通知Web组件同层事件消费结果的类。在同层嵌入场景下，应用与Web组件共同暴露在事件响应链中。EventResult允许应用向Web组件声明自身是否消费了触摸或鼠标事件，从而决定Web 组件是否继续处理该事件。当应用设置消费结果为true时，表示应用已消费该事件，Web组件将不再消费；当设置为false时，表示应用不消费该事件，事件将由Web组件消费。EventResult用于设置触摸事件（ TouchType）和鼠标事件（MouseAction，仅限左中右按键）的消费结果，通过MouseButton定 义鼠标按键的类型，适用于应用与Web组件同层交互的事件协调场景。 触摸事件示例代码参考[onNativeEmbedGestureEvent](arkts-arkweb-web-attribute.md#onnativeembedgestureevent)。 鼠标事件示例代码参考[onNativeEmbedMouseEvent](arkts-arkweb-web-attribute.md#onnativeembedmouseevent)。

**起始版本：** 12

<!--Device-unnamed-declare class EventResult--><!--Device-unnamed-declare class EventResult-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { WebNetErrorList } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionAbility, ConnectionInfo } from '@kit.ArkWeb';
import { webNativeMessagingExtensionManager } from '@kit.ArkWeb';
import { webview } from '@kit.ArkWeb';
import { WebNativeMessagingExtensionContext } from '@kit.ArkWeb';
```

## constructor

```TypeScript
constructor()
```

EventResult的构造函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-EventResult-constructor()--><!--Device-EventResult-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## setGestureEventResult

```TypeScript
setGestureEventResult(result: boolean): void
```

设置手势事件消费结果。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-EventResult-setGestureEventResult(result: boolean): void--><!--Device-EventResult-setGestureEventResult(result: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | boolean | 是 | 是否消费该手势事件。 <br>true表示消费该手势事件，false表示不消费该手势事件。 <br>传入null或undefined时为true。 |

## setGestureEventResult

```TypeScript
setGestureEventResult(result: boolean, stopPropagation: boolean): void
```

设置手势事件消费结果和冒泡控制。

**起始版本：** 14

<!--Device-EventResult-setGestureEventResult(result: boolean, stopPropagation: boolean): void--><!--Device-EventResult-setGestureEventResult(result: boolean, stopPropagation: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | boolean | 是 | 是否消费该手势事件。 <br>true表示消费该手势事件，false表示不消费该手势事件。 <br>传入null或undefined时为true。 |
| stopPropagation | boolean | 是 | 是否阻止冒泡，在result为true时生效。 <br>true表示阻止冒泡，false表示不阻止冒泡。 <br>传入null或undefined时为true。 |

## setMouseEventResult

```TypeScript
setMouseEventResult(result: boolean, stopPropagation?: boolean): void
```

设置鼠标事件消费结果和冒泡控制。

**起始版本：** 20

<!--Device-EventResult-setMouseEventResult(result: boolean, stopPropagation?: boolean): void--><!--Device-EventResult-setMouseEventResult(result: boolean, stopPropagation?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | boolean | 是 | 是否消费该鼠标事件。 <br>true表示消费该鼠标事件，false表示不消费该鼠标事件。 <br>传入null或undefined时为true。 |
| stopPropagation | boolean | 否 | 是否阻止冒泡，在result为true时生效。 <br>true表示阻止冒泡，false表示不阻止冒泡。 <br>传入null或undefined时为true。 <br>默认值：true。 |

