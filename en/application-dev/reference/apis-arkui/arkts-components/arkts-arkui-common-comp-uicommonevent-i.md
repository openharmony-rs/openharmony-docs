# UICommonEvent

```TypeScript
declare interface UICommonEvent
```

Used to set the basic event callbacks of a component, covering events such as click, touch, show/hide, key, focus, floating, component area change, and visible area change. When the input parameter is undefined, the corresponding event callback is reset. This is suitable for scenarios where the basic event processing logic of a component is configured and cleared in a centralized manner.

**Since:** 12

<!--Device-unnamed-declare interface UICommonEvent--><!--Device-unnamed-declare interface UICommonEvent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setOnAppear

```TypeScript
setOnAppear(callback: Callback<void> | undefined): void
```

Sets the callback for the [onAppear](arkts-arkui-common-comp-commonmethod-c.md#onappear) mount and display event. When **callback** is undefined, the callback for the mount and display event is reset.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UICommonEvent-setOnAppear(callback: Callback<void> | undefined): void--><!--Device-UICommonEvent-setOnAppear(callback: Callback<void> | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;void&gt; &#124; undefined | Yes | Callback for the mount and display event. The signature is () =&gt; void. Triggered when the component is mounted and displayed. |

## setOnBlur

```TypeScript
setOnBlur(callback: Callback<void> | undefined): void
```

Sets the callback for the [onBlur](arkts-arkui-common-comp-commonmethod-c.md#onblur) blur event. When **callback** is undefined, resets the callback for the blur event.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UICommonEvent-setOnBlur(callback: Callback<void> | undefined): void--><!--Device-UICommonEvent-setOnBlur(callback: Callback<void> | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;void&gt; &#124; undefined | Yes | Callback function for the blur event. The signature is () =&gt; void. It is triggered when the component loses focus. |

## setOnClick

```TypeScript
setOnClick(callback: Callback<ClickEvent> | undefined): void
```

Sets the callback for the [click event](arkts-arkui-common-comp-commonmethod-c.md#onclick1). When **callback** is undefined, the callback for the click event is reset.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UICommonEvent-setOnClick(callback: Callback<ClickEvent> | undefined): void--><!--Device-UICommonEvent-setOnClick(callback: Callback<ClickEvent> | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[ClickEvent](arkts-arkui-common-comp-clickevent-i.md)&gt; &#124; undefined | Yes | Callback function for the click event. The signature is (event: ClickEvent) =&gt; void, used in the component to receive the click event object when a click event is triggered. |

## setOnDisappear

```TypeScript
setOnDisappear(callback: Callback<void> | undefined): void
```

Sets the callback for the [onDisAppear](arkts-arkui-common-comp-commonmethod-c.md#ondisappear) unmount and disappear event. When **callback** is undefined, the callback for the unmount and disappear event is reset.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UICommonEvent-setOnDisappear(callback: Callback<void> | undefined): void--><!--Device-UICommonEvent-setOnDisappear(callback: Callback<void> | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;void&gt; &#124; undefined | Yes | Callback invoked when the component unmounts and disappears. The signature is () =&gt; void. It is triggered when the component unmounts and disappears. |

## setOnFocus

```TypeScript
setOnFocus(callback: Callback<void> | undefined): void
```

Sets the callback for the [onFocus](arkts-arkui-common-comp-commonmethod-c.md#onfocus) focus event. When **callback** is undefined, resets the callback for the focus event.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UICommonEvent-setOnFocus(callback: Callback<void> | undefined): void--><!--Device-UICommonEvent-setOnFocus(callback: Callback<void> | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;void&gt; &#124; undefined | Yes | Callback invoked when the component gains focus. The signature is () =&gt; void. |

## setOnHover

```TypeScript
setOnHover(callback: HoverCallback | undefined): void
```

Sets the callback for the [onHover](arkts-arkui-common-comp-commonmethod-c.md#onhover) floating event. When **callback** is undefined, resets the callback for the floating event.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UICommonEvent-setOnHover(callback: HoverCallback | undefined): void--><!--Device-UICommonEvent-setOnHover(callback: HoverCallback | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [HoverCallback](arkts-arkui-common-comp-hovercallback-t.md) &#124; undefined | Yes | Callback for the floating event, with the signature (isHover: boolean, event: HoverEvent) =&gt; void, used to receive the floating state and event object when the component enters or exits the floating state. |

## setOnKeyEvent

```TypeScript
setOnKeyEvent(callback: Callback<KeyEvent> | undefined): void
```

Sets the callback for the key event. When **callback** is undefined, resets the callback for the key event.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UICommonEvent-setOnKeyEvent(callback: Callback<KeyEvent> | undefined): void--><!--Device-UICommonEvent-setOnKeyEvent(callback: Callback<KeyEvent> | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[KeyEvent](arkts-arkui-common-comp-keyevent-i.md)&gt; &#124; undefined | Yes | Callback function for the key event. The signature is (event: KeyEvent) =&gt; void, used to receive the key event object when the component triggers the key event. |

## setOnMouse

```TypeScript
setOnMouse(callback: Callback<MouseEvent> | undefined): void
```

Sets the callback for the [onMouse](arkts-arkui-common-comp-commonmethod-c.md#onmouse) mouse event. When **callback** is undefined, resets the callback for the mouse event.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UICommonEvent-setOnMouse(callback: Callback<MouseEvent> | undefined): void--><!--Device-UICommonEvent-setOnMouse(callback: Callback<MouseEvent> | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[MouseEvent](arkts-arkui-common-comp-mouseevent-i.md)&gt; &#124; undefined | Yes | Callback function for the mouse event. The signature is (event: MouseEvent) =&gt; void. It is used in the component to receive the mouse event object when the mouse event is triggered. |

## setOnSizeChange

```TypeScript
setOnSizeChange(callback: SizeChangeCallback | undefined): void
```

Sets the callback for the [onSizeChange](arkts-arkui-common-comp-commonmethod-c.md#onsizechange) component area change event. When **callback** is undefined, resets the callback for the component area change event.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UICommonEvent-setOnSizeChange(callback: SizeChangeCallback | undefined): void--><!--Device-UICommonEvent-setOnSizeChange(callback: SizeChangeCallback | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [SizeChangeCallback](arkts-arkui-common-comp-sizechangecallback-t.md) &#124; undefined | Yes | Callback for the component area change event. The signature is (oldValue: SizeOptions, newValue: SizeOptions) =&gt; void, used to receive the size information before and after the change when the component area size changes. Here, **oldValue** indicates the size information before the change, and **newValue** indicates the size information after the change. |

## setOnTouch

```TypeScript
setOnTouch(callback: Callback<TouchEvent> | undefined): void
```

Sets the callback for the [touch event](arkts-arkui-common-comp-commonmethod-c.md#ontouch). When **callback** is undefined, the callback for the touch event is reset.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UICommonEvent-setOnTouch(callback: Callback<TouchEvent> | undefined): void--><!--Device-UICommonEvent-setOnTouch(callback: Callback<TouchEvent> | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[TouchEvent](arkts-arkui-common-comp-touchevent-i.md)&gt; &#124; undefined | Yes | Callback function for the touch event. The signature is (event: TouchEvent) =&gt; void. It is used in the component to receive the touch event object when the touch event is triggered. |

## setOnVisibleAreaApproximateChange

```TypeScript
setOnVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): void
```

Sets the callback for the [onVisibleAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onvisibleareachange1) visible area change event with a limited callback interval. When **event** is undefined, resets the callback for the visible area change event.

> **NOTE:** 
> 
> This API differs from **onVisibleAreaChange** in the following ways: **onVisibleAreaChange** calculates the
> visible area ratio in every frame, which may increase system power consumption as the number of registered
> nodes grows. This API reduces the frequency of visible area ratio calculation, and the calculation interval is
> determined by the **expectedUpdateInterval** parameter of [VisibleAreaEventOptions](arkts-arkui-common-comp-visibleareaeventoptions-i.md).
> 
> The visible area callback threshold of this API includes 0 by default. For example, if the developer sets the
> callback threshold to [0.5], the effective threshold is [0.0, 0.5].

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-UICommonEvent-setOnVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): void--><!--Device-UICommonEvent-setOnVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [VisibleAreaEventOptions](arkts-arkui-common-comp-visibleareaeventoptions-i.md) | Yes | Configuration parameters of the visible area change event, used to set the visible area ratio threshold and the expected update interval. The visible area callback threshold of this API includes 0 by default. The event callback is triggered when the ratio of the visible area of the component to its own area approaches the threshold that actually takes effect. |
| event | [VisibleAreaChangeCallback](arkts-arkui-common-comp-visibleareachangecallback-t.md) &#124; undefined | Yes | Callback function of the visible area change event. Its signature is (isExpanding: boolean, currentRatio: number) =&gt; void. This callback is triggered when the ratio of the visible area of the component to its own area approaches the threshold set in **options**. **isExpanding** indicates whether the visible area ratio is increasing, and **currentRatio** indicates the current ratio of the visible area to the component's own area. When set to undefined, resets the callback for the visible area change event. |
