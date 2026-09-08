# Common Event Callbacks
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=828befee530895124aaf1637c9402999a598c883 translatedAt=2026-09-01T11:59:03.124Z -->

>**NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## UICommonEvent
Used to set the basic event callbacks of a component, covering events such as click, touch, show/hide, key, focus, floating, component area change, and visible area change. When the input parameter is undefined, the corresponding event callback is reset. This is suitable for scenarios where the basic event processing logic of a component is configured and cleared in a centralized manner.
### setOnClick

setOnClick(callback: Callback\<ClickEvent> \| undefined): void

Sets the callback for the [click event](./ts-universal-events-click.md). When callback is undefined, the callback for the click event is reset.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback | [Callback](./ts-types.md#callback12)\<[ClickEvent](./ts-universal-events-click.md#clickevent)> \| undefined | Yes | Callback function for the click event. The signature is (event: ClickEvent) => void, used in the component to receive the click event object when a click event is triggered. |

### setOnTouch

setOnTouch(callback: Callback\<TouchEvent> \| undefined): void

Sets the callback for the [touch event](./ts-universal-events-touch.md). When callback is undefined, the callback for the touch event is reset.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback | [Callback](./ts-types.md#callback12)\<[TouchEvent](./ts-universal-events-touch.md#touchevent)> \| undefined | Yes | Callback function for the touch event. The signature is (event: TouchEvent) => void. It is used in the component to receive the touch event object when the touch event is triggered. |


### setOnAppear

setOnAppear(callback: Callback\<void> \| undefined): void

Sets the callback for the [onAppear](./ts-universal-events-show-hide.md#onappear) mount and display event. When callback is undefined, the callback for the mount and display event is reset.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback | [Callback](./ts-types.md#callback12)\<void> \| undefined | Yes | Callback for the mount and display event. The signature is () => void. Triggered when the component is mounted and displayed. |


### setOnDisappear

setOnDisappear(callback: Callback\<void> \| undefined): void

Sets the callback for the [onDisappear](./ts-universal-events-show-hide.md#ondisappear) unmount and disappear event. When callback is undefined, the callback for the unmount and disappear event is reset.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback | [Callback](./ts-types.md#callback12)\<void> \| undefined | Yes | Callback invoked when the component unmounts and disappears. The signature is () => void. It is triggered when the component unmounts and disappears. |

### setOnKeyEvent

setOnKeyEvent(callback: Callback\<KeyEvent> \| undefined): void

Sets the callback for the [key event](./ts-universal-events-key.md). When callback is undefined, resets the callback for the key event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback | [Callback](./ts-types.md#callback12)\<[KeyEvent](./ts-universal-events-key.md#keyevent)>  \| undefined | Yes | Callback function for the key event. The signature is (event: KeyEvent) => void, used to receive the key event object when the component triggers the key event. |

### setOnFocus

setOnFocus(callback: Callback\<void> \| undefined): void

Sets the callback for the [onFocus](./ts-universal-focus-event.md#onfocus) focus event. When callback is undefined, resets the callback for the focus event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback | [Callback](./ts-types.md#callback12)\<void> \| undefined | Yes | Callback invoked when the component gains focus. The signature is () => void. |

### setOnBlur

setOnBlur(callback: Callback\<void> \| undefined): void

Sets the callback for the [onBlur](./ts-universal-focus-event.md#onblur) blur event. When callback is undefined, resets the callback for the blur event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback | [Callback](./ts-types.md#callback12)\<void> \| undefined | Yes | Callback function for the blur event. The signature is () => void. It is triggered when the component loses focus. |

### setOnHover

setOnHover(callback: HoverCallback \| undefined): void

Sets the callback for the [onHover](./ts-universal-events-hover.md#onhover) floating event. When callback is undefined, resets the callback for the floating event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback | [HoverCallback](#hovercallback)  \| undefined | Yes | Callback for the floating event, with the signature (isHover: boolean, event: HoverEvent) => void, used to receive the floating state and event object when the component enters or exits the floating state. |

### setOnMouse

setOnMouse(callback: Callback\<MouseEvent> \| undefined): void

Sets the callback for the [onMouse](./ts-universal-mouse-key.md#onmouse) mouse event. When callback is undefined, resets the callback for the mouse event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback | [Callback](./ts-types.md#callback12)\<[MouseEvent](./ts-universal-mouse-key.md#mouseevent)>   \| undefined | Yes | Callback function for the mouse event. The signature is (event: MouseEvent) => void. It is used in the component to receive the mouse event object when the mouse event is triggered. |

### setOnSizeChange

setOnSizeChange(callback: SizeChangeCallback \| undefined): void

Sets the callback for the [onSizeChange](./ts-universal-component-size-change-event.md#onsizechange) component area change event. When callback is undefined, resets the callback for the component area change event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback | [SizeChangeCallback](./ts-universal-component-size-change-event.md#sizechangecallback)   \| undefined | Yes | Callback for the component area change event. The signature is (oldValue: SizeOptions, newValue: SizeOptions) => void, used to receive the size information before and after the change when the component area size changes. Here, oldValue indicates the size information before the change, and newValue indicates the size information after the change. |

### setOnVisibleAreaApproximateChange

setOnVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback \| undefined): void

Sets the callback for the [onVisibleAreaChange](./ts-universal-component-visible-area-change-event.md#onvisibleareachange) visible area change event with a limited callback interval. When event is undefined, resets the callback for the visible area change event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| options | [VisibleAreaEventOptions](./ts-universal-component-visible-area-change-event.md#visibleareaeventoptions12) | Yes | Configuration parameters of the visible area change event, used to set the visible area ratio threshold and the expected update interval. The visible area callback threshold of this API includes 0 by default. The event callback is triggered when the ratio of the visible area of the component to its own area approaches the threshold that actually takes effect. |
| event | [VisibleAreaChangeCallback](./ts-universal-component-visible-area-change-event.md#visibleareachangecallback12)   \| undefined | Yes | Callback function of the visible area change event. Its signature is (isExpanding: boolean, currentRatio: number) => void. This callback is triggered when the ratio of the visible area of the component to its own area approaches the threshold set in options. isExpanding indicates whether the visible area ratio is increasing, and currentRatio indicates the current ratio of the visible area to the component's own area. When set to undefined, resets the callback for the visible area change event. |

>**NOTE**
>
>This API differs from [onVisibleAreaChange](./ts-universal-component-visible-area-change-event.md#onvisibleareachange) in the following ways: onVisibleAreaChange calculates the visible area ratio in every frame, which may increase system power consumption as the number of registered nodes grows. This API reduces the frequency of visible area ratio calculation, and the calculation interval is determined by the expectedUpdateInterval parameter of [VisibleAreaEventOptions](./ts-universal-component-visible-area-change-event.md#visibleareaeventoptions12).
>
> The visible area callback threshold of this API includes 0 by default. For example, if the developer sets the callback threshold to [0.5], the effective threshold is [0.0, 0.5].

## HoverCallback

type HoverCallback = (isHover: boolean, event: HoverEvent)=> void

Callback type for the hover event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name           | Type           | Mandatory        | Description                                      |
| ------------- | ---------------------- |---------------------| --------------------------------------- |
| isHover | boolean | Yes | Whether the component is in the floating state. The value **true** indicates that it is in the floating state, and **false** indicates the opposite. |
| event | [HoverEvent](./ts-universal-events-hover.md#hoverevent10) | Yes | Mouse or stylus floating event object, which provides event information such as the floating position coordinates. |