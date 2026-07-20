# UICommonEvent

用于设置基础事件回调。方法入参为undefined的时候，重置对应的事件回调。

**起始版本：** 12

<!--Device-unnamed-declare interface UICommonEvent--><!--Device-unnamed-declare interface UICommonEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="setonappear"></a>
## setOnAppear

```TypeScript
setOnAppear(callback: Callback<void> | undefined): void
```

设置[onAppear](arkts-arkui-commonmethod-c.md#onappear-1)挂载显示事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UICommonEvent-setOnAppear(callback: Callback<void> | undefined): void--><!--Device-UICommonEvent-setOnAppear(callback: Callback<void> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; \| undefined | 是 | 挂载显示事件的回调函数。 |

<a id="setonblur"></a>
## setOnBlur

```TypeScript
setOnBlur(callback: Callback<void> | undefined): void
```

设置[onBlur](arkts-arkui-commonmethod-c.md#onblur-1)失焦事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UICommonEvent-setOnBlur(callback: Callback<void> | undefined): void--><!--Device-UICommonEvent-setOnBlur(callback: Callback<void> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; \| undefined | 是 | 失焦事件的回调。 |

<a id="setonclick"></a>
## setOnClick

```TypeScript
setOnClick(callback: Callback<ClickEvent> | undefined): void
```

设置[点击事件](arkts-arkui-commonmethod-c.md#onclick-1)的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UICommonEvent-setOnClick(callback: Callback<ClickEvent> | undefined): void--><!--Device-UICommonEvent-setOnClick(callback: Callback<ClickEvent> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ClickEvent&gt; \| undefined | 是 | 点击事件的回调函数。 |

<a id="setondisappear"></a>
## setOnDisappear

```TypeScript
setOnDisappear(callback: Callback<void> | undefined): void
```

设置[onDisAppear](arkts-arkui-commonmethod-c.md#ondisappear-1)卸载消失事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UICommonEvent-setOnDisappear(callback: Callback<void> | undefined): void--><!--Device-UICommonEvent-setOnDisappear(callback: Callback<void> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; \| undefined | 是 | 卸载消失事件的回调。 |

<a id="setonfocus"></a>
## setOnFocus

```TypeScript
setOnFocus(callback: Callback<void> | undefined): void
```

设置[onFocus](arkts-arkui-commonmethod-c.md#onfocus-1)获焦事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UICommonEvent-setOnFocus(callback: Callback<void> | undefined): void--><!--Device-UICommonEvent-setOnFocus(callback: Callback<void> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; \| undefined | 是 | 获焦事件的回调。 |

<a id="setonhover"></a>
## setOnHover

```TypeScript
setOnHover(callback: HoverCallback | undefined): void
```

设置[onHover](arkts-arkui-commonmethod-c.md#onhover-1)悬浮事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UICommonEvent-setOnHover(callback: HoverCallback | undefined): void--><!--Device-UICommonEvent-setOnHover(callback: HoverCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [HoverCallback](arkts-arkui-hovercallback-t.md) \| undefined | 是 | 悬浮事件的回调函数。 |

<a id="setonkeyevent"></a>
## setOnKeyEvent

```TypeScript
setOnKeyEvent(callback: Callback<KeyEvent> | undefined): void
```

设置[按键事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UICommonEvent-setOnKeyEvent(callback: Callback<KeyEvent> | undefined): void--><!--Device-UICommonEvent-setOnKeyEvent(callback: Callback<KeyEvent> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;KeyEvent&gt; \| undefined | 是 | 按键事件的回调函数。 |

<a id="setonmouse"></a>
## setOnMouse

```TypeScript
setOnMouse(callback: Callback<MouseEvent> | undefined): void
```

设置[onMouse](arkts-arkui-commonmethod-c.md#onmouse-1)鼠标事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UICommonEvent-setOnMouse(callback: Callback<MouseEvent> | undefined): void--><!--Device-UICommonEvent-setOnMouse(callback: Callback<MouseEvent> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;MouseEvent&gt; \| undefined | 是 | 鼠标事件的回调函数。 |

<a id="setonsizechange"></a>
## setOnSizeChange

```TypeScript
setOnSizeChange(callback: SizeChangeCallback | undefined): void
```

设置[onSizeChange](arkts-arkui-commonmethod-c.md#onsizechange-1)组件区域变化事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UICommonEvent-setOnSizeChange(callback: SizeChangeCallback | undefined): void--><!--Device-UICommonEvent-setOnSizeChange(callback: SizeChangeCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [SizeChangeCallback](arkts-arkui-sizechangecallback-t.md) \| undefined | 是 | 组件区域变化事件的回调函数。 |

<a id="setontouch"></a>
## setOnTouch

```TypeScript
setOnTouch(callback: Callback<TouchEvent> | undefined): void
```

设置[触摸事件](arkts-arkui-commonmethod-c.md#ontouch-1)的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UICommonEvent-setOnTouch(callback: Callback<TouchEvent> | undefined): void--><!--Device-UICommonEvent-setOnTouch(callback: Callback<TouchEvent> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;TouchEvent&gt; \| undefined | 是 | 触摸事件的回调函数。 |

<a id="setonvisibleareaapproximatechange"></a>
## setOnVisibleAreaApproximateChange

```TypeScript
setOnVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): void
```

设置限制回调间隔的[onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange-1)可见区域变化事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-UICommonEvent-setOnVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): void--><!--Device-UICommonEvent-setOnVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [VisibleAreaEventOptions](arkts-arkui-visibleareaeventoptions-i.md) | 是 | 可见区域变化相关的参数。 |
| event | [VisibleAreaChangeCallback](arkts-arkui-visibleareachangecallback-t.md) \| undefined | 是 | 可见区域变化事件的回调函数。当组件可见面积与自身面积的比值接近options中设置的阈值时触发该回调。 |

