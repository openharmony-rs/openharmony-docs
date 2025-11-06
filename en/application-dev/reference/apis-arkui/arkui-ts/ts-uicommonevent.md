# Common Event Callbacks
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->

>**NOTE**
>
>The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## UICommonEvent
Implements a common event callback. If the method parameter is **undefined**, the corresponding event callback is reset.
### setOnClick

setOnClick(callback: Callback\<ClickEvent> | undefined): void

Set the callback for the [click event](./ts-universal-events-click.md).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback  | [Callback](./ts-types.md#callback12)<[ClickEvent](./ts-universal-events-click.md#clickevent)> \| undefined | Yes  | Callback for the click event.|

### setOnTouch

setOnTouch(callback: Callback\<TouchEvent> | undefined): void

Sets the callback for the [touch event](./ts-universal-events-touch.md).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback  | [Callback](./ts-types.md#callback12)<[TouchEvent](./ts-universal-events-touch.md#touchevent)> \| undefined | Yes  | Callback for the touch event.|


### setOnAppear

setOnAppear(callback: Callback\<void> | undefined): void

Sets the callback for the [onAppear](./ts-universal-events-show-hide.md#onappear) event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback  | [Callback](./ts-types.md#callback12)\<void> \| undefined | Yes  | Callback function for the mounting display event.|


### setOnDisappear

setOnDisappear(callback: Callback\<void> | undefined): void

Sets the callback for the [onDisAppear](./ts-universal-events-show-hide.md#ondisappear) event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback  | [Callback](./ts-types.md#callback12)\<void> \| undefined | Yes  | Callback for the unmounting event.|

### setOnKeyEvent

setOnKeyEvent(callback: Callback\<KeyEvent> | undefined): void

Sets the callback for the [key event](./ts-universal-events-key.md).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback  | [Callback](./ts-types.md#callback12)<[KeyEvent](./ts-universal-events-key.md#keyevent)> \| undefined | Yes  | Callback for the key event.|

### setOnFocus

setOnFocus(callback:  Callback\<void> | undefined): void

Sets the callback for the [onFocus](./ts-universal-focus-event.md#onfocus) event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback  | [Callback](./ts-types.md#callback12)\<void> \| undefined | Yes  | Callback for the focus event.|

### setOnBlur

setOnBlur(callback: Callback\<void> | undefined): void

Sets the callback for the [onBlur](./ts-universal-focus-event.md#onblur) event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback  | [Callback](./ts-types.md#callback12)\<void> \| undefined | Yes  | Callback for the blur event.|

### setOnHover

setOnHover(callback: HoverCallback | undefined): void

Sets the callback for the [onHover](./ts-universal-events-hover.md#onhover) event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback  | [HoverCallback](#hovercallback)  \| undefined | Yes  | Callback for the hover event.|

### setOnMouse

setOnMouse(callback: Callback\<MouseEvent> | undefined): void

Sets the callback for the [onMouse](./ts-universal-mouse-key.md#onmouse) event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback  |  [Callback](./ts-types.md#callback12)<[MouseEvent](./ts-universal-mouse-key.md#mouseevent)> \| undefined | Yes  | Callback for the mouse event.|

### setOnSizeChange

setOnSizeChange(callback: SizeChangeCallback | undefined): void

Sets the callback for the [onSizeChange](./ts-universal-component-size-change-event.md#onsizechange) component area change event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback  | [SizeChangeCallback](./ts-universal-component-size-change-event.md#sizechangecallback)   \| undefined | Yes  | Callback for the component area change event.|

### setOnVisibleAreaApproximateChange

setOnVisibleAreaApproximateChange(options: VisibleAreaEventOptions, event: VisibleAreaChangeCallback | undefined): void

Sets the callback for the [onVisibleAreaChange](./ts-universal-component-visible-area-change-event.md#onvisibleareachange) visible area change event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| options  | [VisibleAreaEventOptions](./ts-universal-component-visible-area-change-event.md#visibleareaeventoptions12) | Yes  | Options of visible area changes.|
| event  | [VisibleAreaChangeCallback](./ts-universal-component-visible-area-change-event.md#visibleareachangecallback12)   \| undefined | Yes  | Callback function of the visible area change event. Called when the ratio of the component's visible area to its total area is greater than or less than the threshold.|

>**NOTE**
>
> This API is different from the [onVisibleAreaChange](./ts-universal-component-visible-area-change-event.md#onvisibleareachange) API in the following ways: onVisibleAreaChange calculates the visible area ratio in each frame. If too many nodes are registered, the system power consumption deteriorates. This API reduces the frequency of calculating the visible area ratio. The calculation interval is determined by the expectedUpdateInterval parameter of [VisibleAreaEventOptions](./ts-universal-component-visible-area-change-event.md#visibleareaeventoptions12).
>
> By default, the interval threshold of the visible area change callback includes 0. This means that, if the provided threshold is [0.5], the effective threshold will be [0.0, 0.5].

## HoverCallback

The **HoverCallback** type is used to represent the callback for the hover event.

type HoverCallback = (isHover: boolean, event: HoverEvent)=> void

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name           | Type           | Mandatory        | Description                                      |
| ------------- | ---------------------- |---------------------| --------------------------------------- |
| isHover | boolean |  Yes |Whether the element is in the hover state. true: yes; false: no.|
| event | [HoverEvent](ts-universal-events-hover.md#hoverevent10) |  Yes|  Position coordinates of the hovered mouse or stylus.|
