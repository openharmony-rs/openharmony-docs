# UICommonEvent

```TypeScript
declare interface UICommonEvent
```

Implements a common event callback. Passing **undefined** as the input parameter resets the corresponding event callback.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setOnAppear

```TypeScript
setOnAppear(callback: Callback<void> | undefined): void
```

Sets the callback for the [onAppear](arkts-arkui-common-comp-commonmethod-c.md#onappear) event.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;void&gt; &#124; undefined | Yes | Callback invoked when the component appears. |

## setOnBlur

```TypeScript
setOnBlur(callback: Callback<void> | undefined): void
```

Sets the callback for the [onBlur](arkts-arkui-common-comp-commonmethod-c.md#onblur) event.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;void&gt; &#124; undefined | Yes | Callback for the blur event. |

## setOnClick

```TypeScript
setOnClick(callback: Callback<ClickEvent> | undefined): void
```

Set the callback for the [click event](arkts-arkui-common-comp-commonmethod-c.md#onclick).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[ClickEvent](arkts-arkui-common-comp-clickevent-i.md)&gt; &#124; undefined | Yes | Callback for the click event. |

## setOnDisappear

```TypeScript
setOnDisappear(callback: Callback<void> | undefined): void
```

Sets the callback for the [onDisAppear](arkts-arkui-common-comp-commonmethod-c.md#ondisappear) event.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;void&gt; &#124; undefined | Yes | Callback invoked when the component disappears. |

## setOnFocus

```TypeScript
setOnFocus(callback: Callback<void> | undefined): void
```

Sets the callback for the [onFocus](arkts-arkui-common-comp-commonmethod-c.md#onfocus) event.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;void&gt; &#124; undefined | Yes | Callback for the focus event. |

## setOnHover

```TypeScript
setOnHover(callback: HoverCallback | undefined): void
```

Sets the callback for the [onHover](arkts-arkui-common-comp-commonmethod-c.md#onhover) event.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [HoverCallback](arkts-arkui-common-comp-hovercallback-t.md) &#124; undefined | Yes | Callback for the hover event. |

## setOnKeyEvent

```TypeScript
setOnKeyEvent(callback: Callback<KeyEvent> | undefined): void
```

Sets the callback for the key event.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[KeyEvent](arkts-arkui-common-comp-keyevent-i.md)&gt; &#124; undefined | Yes | Callback for the key event. |

## setOnMouse

```TypeScript
setOnMouse(callback: Callback<MouseEvent> | undefined): void
```

Sets the callback for the [onMouse](arkts-arkui-common-comp-commonmethod-c.md#onmouse) event.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[MouseEvent](arkts-arkui-common-comp-mouseevent-i.md)&gt; &#124; undefined | Yes | Callback for the mouse event. |

## setOnSizeChange

```TypeScript
setOnSizeChange(callback: SizeChangeCallback | undefined): void
```

Sets the callback for the [onSizeChange](arkts-arkui-common-comp-commonmethod-c.md#onsizechange) event, which is triggered when the component's size changes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [SizeChangeCallback](arkts-arkui-common-comp-sizechangecallback-t.md) &#124; undefined | Yes | Callback invoked when the component's size changes. |

## setOnTouch

```TypeScript
setOnTouch(callback: Callback<TouchEvent> | undefined): void
```

Sets the callback for the [touch event](arkts-arkui-common-comp-commonmethod-c.md#ontouch).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-common-comp-callback-i.md)&lt;[TouchEvent](arkts-arkui-common-comp-touchevent-i.md)&gt; &#124; undefined | Yes | Callback for the touch event. |

## setOnVisibleAreaApproximateChange

```TypeScript
setOnVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): void
```

Sets the callback for the [onVisibleAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onvisibleareachange) visible area change event.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [VisibleAreaEventOptions](arkts-arkui-common-comp-visibleareaeventoptions-i.md) | Yes | Configuration options for visible area change detection. |
| event | [VisibleAreaChangeCallback](arkts-arkui-common-comp-visibleareachangecallback-t.md) &#124; undefined | Yes | Callback invoked when the ratio of the component's visible area to its total area crosses the threshold specified in **options**. |
