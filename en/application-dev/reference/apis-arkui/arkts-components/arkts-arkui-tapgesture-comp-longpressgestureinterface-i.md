# LongPressGestureInterface

```TypeScript
interface LongPressGestureInterface extends GestureInterface<LongPressGestureInterface>
```

**LongPressGesture** is used to trigger a long press gesture. This gesture requires one or more fingers to be held down for a specified duration, which is 500 ms by default and can be adjusted using the **duration** parameter.

> **NOTE:** 
> 
> Since API version 18, on some devices, the system's two-finger long press gesture may take precedence, causing
> the application's two-finger long press gesture to be ineffective.

**Inheritance/Implementation:** LongPressGestureInterface extends GestureInterface<LongPressGestureInterface>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## [[Call]]

```TypeScript
(value?: { fingers?: number; repeat?: boolean; duration?: number }): LongPressGestureInterface
```

Creates a long press gesture. Inherits from [GestureInterface&lt;T&gt;](arkts-arkui-tapgesture-comp-gestureinterface-i.md).

In components that support drag actions by default, such as **Text**, **TextInput**, **TextArea**, **HyperLink**, **Image**, and **RichEditor**, the long press gesture may conflict with the drag action. If this occurs, the event priority is determined as follows:

If the long press duration is less than 500 milliseconds, the system prioritizes the long press event over the drag event.

If the long press duration reaches or exceeds 500 milliseconds, the system prioritizes the drag event over the long press event.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | { fingers?: number; repeat?: boolean; duration?: number } | No | Parameters for the long press gesture.<br> - **fingers**: minimum number of fingers to trigger a long press gesture. The value ranges from 1 to 10. <br>Default value: **1**. <br> - **repeat**: whether to continuously trigger the event callback. The value **true** means to continuously trigger the event callback, and **false** means the opposite.<br>Default value: **false**. <br> - **duration**: minimum hold-down time, in ms.<br>Default value: **500**. |

**Return value:**

| Type | Description |
| --- | --- |
| [LongPressGestureInterface](arkts-arkui-tapgesture-comp-longpressgestureinterface-i.md) |  |

<a id="call-1"></a>

## [[Call]]

```TypeScript
(options?: LongPressGestureHandlerOptions): LongPressGestureInterface
```

Creates a long press gesture. Compared with LongPressGesture)}, this API adds the **isFingerCountLimited** parameter to **options**, which determines whether to enforce the exact number of fingers touching the screen.

In components that support drag actions by default, such as **Text**, **TextInput**, **TextArea**, **HyperLink**, **Image**, and **RichEditor**, the long press gesture may conflict with the drag action. If this occurs, the event priority is determined as follows:

If the long press duration is less than 500 milliseconds, the system prioritizes the long press event over the drag event.

If the long press duration reaches or exceeds 500 milliseconds, the system prioritizes the drag event over the long press event.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [LongPressGestureHandlerOptions](arkts-arkui-tapgesture-comp-longpressgesturehandleroptions-i.md) | No | Parameters of the long press gesture handler. |

**Return value:**

| Type | Description |
| --- | --- |
| [LongPressGestureInterface](arkts-arkui-tapgesture-comp-longpressgestureinterface-i.md) |  |

## onAction

```TypeScript
onAction(event: (event: GestureEvent) => void): LongPressGestureInterface
```

Registers the callback for successful long press gesture recognition.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | Yes | Callback for successful long press gesture recognition. |

**Return value:**

| Type | Description |
| --- | --- |
| [LongPressGestureInterface](arkts-arkui-tapgesture-comp-longpressgestureinterface-i.md) |  |

## onActionCancel

```TypeScript
onActionCancel(event: () => void): LongPressGestureInterface
```

Registers the callback for long press gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful long press gesture recognition. No gesture event information is returned.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback for long press gesture cancellation. |

**Return value:**

| Type | Description |
| --- | --- |
| [LongPressGestureInterface](arkts-arkui-tapgesture-comp-longpressgestureinterface-i.md) |  |

<a id="onactioncancel-1"></a>

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): LongPressGestureInterface
```

Registers the callback for long press gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful long press gesture recognition. Gesture event information is returned.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback for long press gesture cancellation. |

**Return value:**

| Type | Description |
| --- | --- |
| [LongPressGestureInterface](arkts-arkui-tapgesture-comp-longpressgestureinterface-i.md) |  |

## onActionEnd

```TypeScript
onActionEnd(event: (event: GestureEvent) => void): LongPressGestureInterface
```

Registers the callback for long press gesture completion. This callback is triggered when all fingers are lifted after successful recognition.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: GestureEvent) =&gt; void | Yes | Callback for long press gesture completion. |

**Return value:**

| Type | Description |
| --- | --- |
| [LongPressGestureInterface](arkts-arkui-tapgesture-comp-longpressgestureinterface-i.md) |  |
