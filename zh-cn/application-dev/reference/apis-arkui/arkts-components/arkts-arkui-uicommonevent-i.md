# UICommonEvent

用于设置基础事件回调。方法入参为undefined的时候，重置对应的事件回调。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## setOnAppear

```TypeScript
setOnAppear(callback: Callback<void> | undefined): void
```

设置[onAppear](arkts-arkui-commonmethod-c.md#onappear)挂载显示事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;void&gt; \| undefined | 是 | 挂载显示事件的回调函数。 |

## setOnBlur

```TypeScript
setOnBlur(callback: Callback<void> | undefined): void
```

设置[onBlur](arkts-arkui-commonmethod-c.md#onblur)失焦事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;void&gt; \| undefined | 是 | 失焦事件的回调。 |

## setOnClick

```TypeScript
setOnClick(callback: Callback<ClickEvent> | undefined): void
```

设置点击事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;[ClickEvent](arkts-arkui-clickevent-i.md)&gt; \| undefined | 是 | 点击事件的回调函数。 |

## setOnDisappear

```TypeScript
setOnDisappear(callback: Callback<void> | undefined): void
```

设置[onDisAppear](arkts-arkui-commonmethod-c.md#ondisappear)卸载消失事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;void&gt; \| undefined | 是 | 卸载消失事件的回调。 |

## setOnFocus

```TypeScript
setOnFocus(callback: Callback<void> | undefined): void
```

设置[onFocus](arkts-arkui-commonmethod-c.md#onfocus)获焦事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;void&gt; \| undefined | 是 | 获焦事件的回调。 |

## setOnHover

```TypeScript
setOnHover(callback: HoverCallback | undefined): void
```

设置[onHover](arkts-arkui-commonmethod-c.md#onhover)悬浮事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [HoverCallback](arkts-arkui-hovercallback-t.md) \| undefined | 是 | 悬浮事件的回调函数。 |

## setOnKeyEvent

```TypeScript
setOnKeyEvent(callback: Callback<KeyEvent> | undefined): void
```

设置按键事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;[KeyEvent](arkts-arkui-keyevent-i.md)&gt; \| undefined | 是 | 按键事件的回调函数。 |

## setOnMouse

```TypeScript
setOnMouse(callback: Callback<MouseEvent> | undefined): void
```

设置[onMouse](arkts-arkui-commonmethod-c.md#onmouse)鼠标事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;[MouseEvent](arkts-arkui-mouseevent-i.md)&gt; \| undefined | 是 | 鼠标事件的回调函数。 |

## setOnSizeChange

```TypeScript
setOnSizeChange(callback: SizeChangeCallback | undefined): void
```

设置[onSizeChange](arkts-arkui-commonmethod-c.md#onsizechange)组件区域变化事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [SizeChangeCallback](arkts-arkui-sizechangecallback-t.md) \| undefined | 是 | 组件区域变化事件的回调函数。 |

## setOnTouch

```TypeScript
setOnTouch(callback: Callback<TouchEvent> | undefined): void
```

设置触摸事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;[TouchEvent](arkts-arkui-touchevent-i.md)&gt; \| undefined | 是 | 触摸事件的回调函数。 |

## setOnVisibleAreaApproximateChange

```TypeScript
setOnVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): void
```

设置限制回调间隔的 [onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange) 可见区域变化事件的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [VisibleAreaEventOptions](arkts-arkui-visibleareaeventoptions-i.md) | 是 | 可见区域变化相关的参数。 |
| event | [VisibleAreaChangeCallback](arkts-arkui-visibleareachangecallback-t.md) \| undefined | 是 | 可见区域变化事件的回调函数。当组件可见面积与自身面积的比值接近options中设置的阈值时触发该回调。 |
