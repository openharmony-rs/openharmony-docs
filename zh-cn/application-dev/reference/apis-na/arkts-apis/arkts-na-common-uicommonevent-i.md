# UICommonEvent

Defines a UICommonEvent which is used to set different common event to target component.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface UICommonEvent--><!--Device-unnamed-export declare interface UICommonEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setOnAppear

```TypeScript
setOnAppear(callback: VoidCallback | undefined): void
```

Set or reset the callback is triggered when a component mounts a display.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UICommonEvent-setOnAppear(callback: VoidCallback | undefined): void--><!--Device-UICommonEvent-setOnAppear(callback: VoidCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) \| undefined | 是 | The callback will be triggered when a component mounts a display. If set undefined will reset the target callback. |

## setOnBlur

```TypeScript
setOnBlur(callback: VoidCallback | undefined): void
```

Set or reset the callback which is triggered when lose focus.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UICommonEvent-setOnBlur(callback: VoidCallback | undefined): void--><!--Device-UICommonEvent-setOnBlur(callback: VoidCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) \| undefined | 是 | The callback will be triggered when a component lose focus. If set undefined will reset the target callback. |

## setOnClick

```TypeScript
setOnClick(callback: Callback<ClickEvent> | undefined): void
```

Set or reset the callback which will be triggered a click event when clicked.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UICommonEvent-setOnClick(callback: Callback<ClickEvent> | undefined): void--><!--Device-UICommonEvent-setOnClick(callback: Callback<ClickEvent> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-na-callback-t.md)&lt;[ClickEvent](arkts-na-common-clickevent-i.md)&gt; \| undefined | 是 | The callback about the click event. If set undefined will reset the target callback. |

## setOnDisappear

```TypeScript
setOnDisappear(callback: VoidCallback | undefined): void
```

Set or reset the callback is triggered when component uninstallation disappears.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UICommonEvent-setOnDisappear(callback: VoidCallback | undefined): void--><!--Device-UICommonEvent-setOnDisappear(callback: VoidCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) \| undefined | 是 | The callback will be triggered when component uninstallation disappears. If set undefined will reset the target callback. |

## setOnFocus

```TypeScript
setOnFocus(callback: VoidCallback | undefined): void
```

Set or reset the callback which is triggered when component get focus.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UICommonEvent-setOnFocus(callback: VoidCallback | undefined): void--><!--Device-UICommonEvent-setOnFocus(callback: VoidCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [VoidCallback](../../apis-arkui/arkts-apis/arkts-arkui-voidcallback-t.md) \| undefined | 是 | The callback will be triggered when a component get focus. If set undefined will reset the target callback. |

## setOnHover

```TypeScript
setOnHover(callback: HoverCallback | undefined): void
```

Set or reset the callback which is triggered when has a hover event.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UICommonEvent-setOnHover(callback: HoverCallback | undefined): void--><!--Device-UICommonEvent-setOnHover(callback: HoverCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [HoverCallback](arkts-na-hovercallback-t.md) \| undefined | 是 | The callback will be triggered when has a hover event. If set undefined will reset the target callback. |

## setOnKeyEvent

```TypeScript
setOnKeyEvent(callback: Callback<KeyEvent> | undefined): void
```

Set or reset the callback is triggered when component has keyboard input.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UICommonEvent-setOnKeyEvent(callback: Callback<KeyEvent> | undefined): void--><!--Device-UICommonEvent-setOnKeyEvent(callback: Callback<KeyEvent> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-na-callback-t.md)&lt;[KeyEvent](arkts-na-common-keyevent-i.md)&gt; \| undefined | 是 | The callback will be triggered when has keyboard input. If set undefined will reset the target callback. |

## setOnMouse

```TypeScript
setOnMouse(callback: Callback<MouseEvent> | undefined): void
```

Set or reset the callback which is triggered when has a mouse event.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UICommonEvent-setOnMouse(callback: Callback<MouseEvent> | undefined): void--><!--Device-UICommonEvent-setOnMouse(callback: Callback<MouseEvent> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-na-callback-t.md)&lt;[MouseEvent](arkts-na-common-mouseevent-i.md)&gt; \| undefined | 是 | The callback will be triggered when has mouse input. If set undefined will reset the target callback. |

## setOnSizeChange

```TypeScript
setOnSizeChange(callback: SizeChangeCallback | undefined): void
```

Sets the callback for the onSizeChange event.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UICommonEvent-setOnSizeChange(callback: SizeChangeCallback | undefined): void--><!--Device-UICommonEvent-setOnSizeChange(callback: SizeChangeCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [SizeChangeCallback](arkts-na-sizechangecallback-t.md) \| undefined | 是 | The callback will be triggered when the size of component changed. If set undefined will reset the target callback. |

## setOnTouch

```TypeScript
setOnTouch(callback: Callback<TouchEvent> | undefined): void
```

Set or reset the callback which will be triggered a touch event when touched.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UICommonEvent-setOnTouch(callback: Callback<TouchEvent> | undefined): void--><!--Device-UICommonEvent-setOnTouch(callback: Callback<TouchEvent> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-na-callback-t.md)&lt;[TouchEvent](arkts-na-common-touchevent-i.md)&gt; \| undefined | 是 | The callback about the touch event. If set undefined will reset the target callback. |

## setOnVisibleAreaApproximateChange

```TypeScript
setOnVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): void
```

Sets the onVisibleAreaChange callback that limits the callback interval.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UICommonEvent-setOnVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): void--><!--Device-UICommonEvent-setOnVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [VisibleAreaEventOptions](arkts-na-common-visibleareaeventoptions-i.md) | 是 | The options for the visibility event. |
| event | [VisibleAreaChangeCallback](arkts-na-visibleareachangecallback-t.md) \| undefined | 是 | The callback will be triggered when the visibleArea of component changed and get close to any number in ratios defined by options. If set undefined will reset the target callback. |

