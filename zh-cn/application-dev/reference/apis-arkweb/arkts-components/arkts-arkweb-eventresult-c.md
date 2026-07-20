# EventResult

通知Web组件同层事件消费结果，支持的事件：[触摸事件的类型](../../apis-arkui/arkts-apis/arkts-arkui-touchtype-e.md)和[鼠标事件的类型](../../apis-arkui/arkts-apis/arkts-arkui-mouseaction-e.md)，鼠标仅支持[左中右按键](../../apis-arkui/arkts-apis/arkts-arkui-mousebutton-e.md)。

如果应用不消费该事件，则应设置消费结果为false，事件将会被Web组件消费；反之如果应用消费了该事件，则应将消费结果设置为true，Web组件将不消费该事件。若应用设置消费结果不符合以上使用规格，将产生与开发者预期不匹配的现象。

触摸事件示例代码参考[onNativeEmbedGestureEvent事件](web:WebAttribute.onNativeEmbedGestureEvent)。

鼠标事件示例代码参考[onNativeEmbedMouseEvent事件](web:WebAttribute.onNativeEmbedMouseEvent)。

**起始版本：** 12

<!--Device-unnamed-declare class EventResult--><!--Device-unnamed-declare class EventResult-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

EventResult的构造函数。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-EventResult-constructor()--><!--Device-EventResult-constructor()-End-->

**系统能力：** SystemCapability.Web.Webview.Core

<a id="setgestureeventresult"></a>
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
| result | boolean | 是 | 是否消费该手势事件。<br>true表示消费该手势事件，false表示不消费该手势事件。<br>传入null或undefined时为true。 |

<a id="setgestureeventresult-1"></a>
## setGestureEventResult

```TypeScript
setGestureEventResult(result: boolean, stopPropagation: boolean): void
```

设置手势事件消费结果。

**起始版本：** 14

<!--Device-EventResult-setGestureEventResult(result: boolean, stopPropagation: boolean): void--><!--Device-EventResult-setGestureEventResult(result: boolean, stopPropagation: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | boolean | 是 | 是否消费该手势事件。<br>true表示消费该手势事件，false表示不消费该手势事件。<br>传入null或undefined时为true。 |
| stopPropagation | boolean | 是 | 是否阻止冒泡，在result为true时生效。<br>true表示阻止冒泡，false表示不阻止冒泡。<br>传入null或undefined时为true。 |

<a id="setmouseeventresult"></a>
## setMouseEventResult

```TypeScript
setMouseEventResult(result: boolean, stopPropagation?: boolean): void
```

设置鼠标事件消费结果。

**起始版本：** 20

<!--Device-EventResult-setMouseEventResult(result: boolean, stopPropagation?: boolean): void--><!--Device-EventResult-setMouseEventResult(result: boolean, stopPropagation?: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | boolean | 是 | 是否消费该鼠标事件。<br>true表示消费该鼠标事件，false表示不消费该鼠标事件。<br>传入null或undefined时为true。 |
| stopPropagation | boolean | 否 | 是否阻止冒泡，在result为true时生效。<br>true表示阻止冒泡，false表示不阻止冒泡。<br>传入null或undefined时为true。<br>默认值：true。 |

