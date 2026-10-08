# Gesture Handler
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9430c77017ca73641537d932a3d7d8a4c99c078b translatedAt=2026-08-28T01:44:21.498Z pushedAt=2026-09-01T02:40:13.259Z -->

Used to set the gestures bound to a component. It supports gesture handlers such as tap, long press, pan, swipe, pinch, rotation, and gesture group, and is suitable for scenarios where gestures need to be dynamically added, removed, or configured for a component. It helps developers manage component gesture interactions in a unified manner. You can use the [UIGestureEvent](./ts-uigestureevent.md#uigestureevent) object to call its APIs to add or remove gestures.

>**NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## GestureHandler\<T>

Defines the base type of a gesture handler, which carries the common configuration capabilities of specific gesture handlers, such as setting the gesture tag and limiting the supported event input sources.

### tag

tag(tag: string): T

Sets the tag of the gesture handler. This is suitable for scenarios where multiple gesture handlers need to be distinguished or managed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory|Description                                       |
| ----  | ------  | ------|---------------------------------- |
| tag   | string  | Yes|Gesture handler tag.|

**Return values**

| Type| Description|
| -------- | -------- |
| T | Current gesture handler object. |

### allowedTypes<sup>14+</sup>

allowedTypes(types: Array\<SourceTool>): T

Sets the event input sources supported by the gesture handler. This is suitable for scenarios where the gesture needs to be limited to responding only to specific input sources such as touch, mouse, or stylus.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory|Description                                       |
| ----  | ------  | ------|---------------------------------- |
| types   | Array\<[SourceTool](ts-gesture-settings.md#sourcetool9)>  | Yes|Supported input source types.|

**Return values**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## BaseHandlerOptions<sup>15+</sup>

Provides the parameters of the basic gesture handler.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name          | Type         | Read-Only| Optional| Description           |
|---------------|---------------|-----|------|----------------|
| isFingerCountLimited | boolean | No| Yes| Whether to enforce the exact number of fingers touching the screen. **true**: Enforce the exact number of fingers touching the screen. **false**: Do not enforce the exact number of fingers touching the screen.<br>Default value: **false**|

## TapGestureHandler

Defines the tap gesture handler object type, which is used to recognize tap interactions on a component. It is suitable for touch scenarios such as single tap, multiple taps, or multi-finger tap, and supports configuring recognition conditions such as the tap count and the number of triggering fingers.

### constructor

constructor(options?: TapGestureHandlerOptions)

Constructor used to create a tap gesture handler instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                        | Mandatory| Description              |
| ------- | ------------------------------------------------------------ | ---- | ------------------ |
| options | [TapGestureHandlerOptions](#tapgesturehandleroptions) | No | Tap gesture handler configuration options. Pass this parameter when you need to customize the number of consecutive taps, the number of fingers that trigger the tap, the finger count check, or the tap gesture movement threshold. If this parameter is not passed, the default tap gesture handler configuration is used, for example, the number of consecutive taps is 1, the number of fingers that trigger the tap is 1, and the number of fingers touching the screen is not checked by default. |

### onAction

onAction(event: Callback\<GestureEvent>): TapGestureHandler

Sets the callback for successful tap gesture recognition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes | Callback invoked when the tap gesture is recognized. The callback parameter is a **GestureEvent** object used to obtain the tap gesture event information. |

**Return values**

| Type| Description|
| -------- | -------- |
| [TapGestureHandler](#tapgesturehandler) | Tap gesture handler object.|

## TapGestureHandlerOptions

Provides the parameters of the tap gesture handler. Inherits from [BaseHandlerOptions](#basehandleroptions15).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                                 | Read-Only| Optional| Description                |
| ------------ | -------------------------------------|------ | ---- | -------------------- |
| count | number | No | Yes | Number of consecutive taps to be recognized. If the value set is less than 1 or is not set, the default value is used.<br>Default value: 1<br>Value range: [0, +∞)<br>**Note:**<br>1. When multiple taps are configured, the timeout between the lift of the last finger of the previous tap and the press of the first finger of the next tap is 300 ms.<br>2. If the distance between the position of the previous tap and the position of the current tap exceeds 60 vp, gesture recognition fails.<br>**Atomic service API:** This API can be used in atomic services since API version 12.|
| fingers | number | No | Yes | Number of fingers that trigger a tap. The minimum is 1 finger, and the maximum is 10 fingers. If the value set is less than 1 or is not set, the default value is used.<br>Default value: **1**<br>**Note:**<br>1. When multiple fingers are configured, if a sufficient number of fingers are not pressed within 300 ms after the first finger is pressed, gesture recognition fails. If a sufficient number of fingers are not lifted within 300 ms after the first finger is lifted, gesture recognition fails.<br>2. When **isFingerCountLimited** is not enabled, if the actual number of tapping fingers exceeds the configured value, gesture recognition succeeds. When **isFingerCountLimited** is enabled, the number of fingers touching the screen must be equal to the configured value; otherwise, gesture recognition fails.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| isFingerCountLimited<sup>15+</sup> | boolean | No | Yes | Whether to check the number of fingers touching the screen. The value **true** indicates checking the number of fingers touching the screen, and **false** indicates not checking the number of fingers touching the screen. If the number of fingers touching the screen is not equal to the configured number of fingers that trigger a tap (that is, the **fingers** parameter), gesture recognition fails.<br>In a multi-tap event (that is, the **count** parameter is greater than 1), the number of fingers in each tap must be equal to the configured number of fingers that trigger a tap; otherwise, gesture recognition fails.<br>Default value: **false**<br>**Atomic service API:** This API can be used in atomic services since API version 15. |
| distanceThreshold<sup>23+</sup> | number | No | Yes | Movement threshold of the tap gesture. If the value set is less than or equal to 0 or is not set, the default value is used.<br>Default value: **2^31-1**<br>Unit: vp<br>Value range: (0, +∞)<br>**Note:**<br>When the movement distance of the finger exceeds the movement threshold preset by the developer, tap recognition fails. If the default threshold is used, tap recognition fails when the finger moves beyond the hot zone of the component.<br>**Atomic service API:** This API can be used in atomic services since API version 23. |

## LongPressGestureHandler

Defines the long press gesture handler object type, which is used to recognize long press interactions on a component. It is suitable for scenarios where an operation is triggered after pressing and holding, and supports configuring recognition conditions such as the number of triggering fingers, the long press duration, whether to trigger continuously, and the movement threshold.

### constructor

constructor(options?: LongPressGestureHandlerOptions)

Constructor used to create a long press gesture handler instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**


| Name | Type                                                        | Mandatory| Description              |
| ------- | ------------------------------------------------------------ | ---- | ------------------ |
| options | [LongPressGestureHandlerOptions](#longpressgesturehandleroptions) | No | Configuration parameters of the long press gesture handler. Pass this parameter when you need to customize the minimum finger count for triggering a long press, whether to trigger continuously, the minimum trigger time, finger count verification, or the maximum movement distance. If this parameter is not passed, the default configuration of the long press gesture handler is used, for example, the trigger finger count is 1, **repeat** is **false**, the minimum time for triggering a long press is 500 ms, and the maximum movement distance is 15 px. |

### onAction

onAction(event: Callback\<GestureEvent>): LongPressGestureHandler

Sets the callback for successful long press gesture recognition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes | Callback invoked when the long press gesture handler recognizes the gesture successfully. The callback parameter is a **GestureEvent** object used to obtain the long press gesture event information. |

**Return values**

| Type| Description|
| -------- | -------- |
| [LongPressGestureHandler](#longpressgesturehandler) | Long press gesture handler object.|

### onActionEnd

onActionEnd(event: Callback\<GestureEvent>): LongPressGestureHandler

Sets the callback for long press gesture recognition completion. This callback is triggered when all fingers are lifted after successful recognition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes | Callback for the end of the long press gesture handler. The callback parameter is a **GestureEvent** object, used to obtain the gesture event information when the long press ends. |

**Return values**

| Type| Description|
| -------- | -------- |
| [LongPressGestureHandler](#longpressgesturehandler) | Long press gesture handler object.|

### onActionCancel

onActionCancel(event: Callback\<void>): LongPressGestureHandler

Sets the callback for long press gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. No gesture event information is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)\<void> | Yes | Callback for the long press gesture handler cancellation event. This callback has no input parameters and does not return gesture event information. |

**Return values**

| Type| Description|
| -------- | -------- |
| [LongPressGestureHandler](#longpressgesturehandler) | Long press gesture handler object.|

### onActionCancel<sup>18+</sup>

onActionCancel(event: Callback\<GestureEvent>): LongPressGestureHandler

Sets the callback for long press gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. Compared with [onActionCancel](#onactioncancel), this API returns gesture event information.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes| Callback invoked when the long press gesture is cancelled. This callback returns gesture event information.|

**Return values**

| Type| Description|
| -------- | -------- |
| [LongPressGestureHandler](#longpressgesturehandler) | Long press gesture handler object.|

## LongPressGestureHandlerOptions

Provides the parameters of the long press gesture handler. Inherits from [BaseHandlerOptions](#basehandleroptions15).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                              | Read-Only   | Optional| Description                |
| ------------ | ---------------------------------|----- | ---- | -------------------- |
| fingers | number | No | Yes | Minimum number of fingers to trigger a long press. When **isFingerCountLimited** is enabled, the number of fingers touching the screen must equal the fingers value; otherwise, gesture recognition fails.<br>Default value: **1**<br>Value range: [1, 10]<br> **NOTE**<br>If the finger moves more than 15 px after being pressed down, the current long press gesture recognition is determined to have failed.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| repeat | boolean | No | Yes | Whether to continuously trigger event callbacks. The value **true** indicates continuous triggering of event callbacks, and **false** indicates the opposite.<br>Default value: **false**<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| duration | number | No | Yes | Minimum duration to trigger a long press, in milliseconds (ms).<br>Default value: **500**<br>**NOTE**<br>Value range: (0, +∞). If the value is set to less than or equal to 0, the default value 500 is used.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| isFingerCountLimited<sup>15+</sup> | boolean | No | Yes | Whether to check the number of fingers touching the screen. The value **true** indicates checking the number of fingers touching the screen, and **false** indicates not checking. If the number of fingers touching the screen is not equal to the minimum number of fingers set to trigger a long press (that is, the **fingers** parameter above), gesture recognition fails.<br>For a gesture that has been successfully recognized, subsequent changes in the number of fingers touching the screen will not trigger the repeat event (if the number of fingers touching the screen returns to the minimum number of fingers set to trigger a long press, the [onAction](ts-basic-gestures-longpressgesture.md#onaction) event can be triggered), but the [onActionEnd](ts-basic-gestures-longpressgesture.md#onactionend) event can be triggered.<br>Default value: **false**<br>**Atomic service API:** This API can be used in atomic services since API version 15. |
| allowableMovement<sup>22+</sup> | number | No | Yes | Maximum movement distance of the gesture recognized by the long press gesture recognizer, in px.<br>Default value: 15<br>Value range: (0, +∞). If the value is set to less than or equal to 0, the default value **15** is used.<br>**Atomic service API:** This API can be used in atomic services since API version 22. |

## PanGestureHandler

Defines the pan gesture handler object type, which is used to recognize drag or slide interactions on a component. It is suitable for scenarios where the state needs to be updated as the finger moves, and supports configuring the number of triggering fingers, the pan direction, the minimum drag distance, and the trigger distance for different input sources.

### constructor

constructor(options?: PanGestureHandlerOptions)

Constructor used to create a pan gesture handler instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**


| Name | Type                                                        | Mandatory| Description              |
| ------- | ------------------------------------------------------------ | ---- | ------------------ |
| options | [PanGestureHandlerOptions](#pangesturehandleroptions) | No | Configuration options of the pan gesture handler. Pass this parameter when you need to customize the minimum number of fingers to trigger dragging, the trigger direction, the minimum drag distance, the minimum drag distance for different input sources, or finger count validation. If this parameter is not passed, the default configuration of the pan gesture handler is used, for example, the number of fingers to trigger is 1, the direction is **PanDirection.All**, the minimum drag distance uses the default value based on the input source, and the number of fingers touching the screen is not checked by default. |

### onActionStart

onActionStart(event: Callback\<GestureEvent>): PanGestureHandler

Sets the callback for successful pan gesture recognition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes | Callback invoked when the pan gesture handler is successfully recognized. The callback parameter is a **GestureEvent** object, which is used to obtain the gesture event information at the start of the pan. |

**Return values**

| Type| Description|
| -------- | -------- |
| [PanGestureHandler](#pangesturehandler) | Pan gesture handler object.|

### onActionUpdate

onActionUpdate(event: Callback\<GestureEvent>): PanGestureHandler

Sets the callback for pan gesture movement updates. The callback is triggered when the pan gesture moves.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes | Callback invoked when the pan gesture handler is updated.<br>When **fingerList** contains multiple fingers, each invocation of this callback updates the position information of only one finger. |

**Return values**

| Type| Description|
| -------- | -------- |
| [PanGestureHandler](#pangesturehandler) | Pan gesture handler object.|

### onActionEnd

onActionEnd(event: Callback\<GestureEvent>): PanGestureHandler

Sets the callback for pan gesture recognition completion. This callback is triggered when all fingers are lifted after successful recognition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes | Callback invoked when the pan gesture ends. The callback parameter is a **GestureEvent** object, used to obtain the gesture event information when the pan gesture ends. |

**Return values**

| Type| Description|
| -------- | -------- |
| [PanGestureHandler](#pangesturehandler) | Pan gesture handler object.|

### onActionCancel

onActionCancel(event: Callback\<void>): PanGestureHandler

Sets the callback for pan gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. No gesture event information is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)\<void> | Yes | Callback for the cancellation of the pan gesture handler. This callback has no input parameters and does not return gesture event information. |

**Return values**

| Type| Description|
| -------- | -------- |
| [PanGestureHandler](#pangesturehandler) | Pan gesture handler object.|

### onActionCancel<sup>18+</sup>

onActionCancel(event: Callback\<GestureEvent>): PanGestureHandler

Sets the callback for pan gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. Compared with [onActionCancel](#onactioncancel-1), this API returns gesture event information.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes| Callback invoked when the pan gesture is cancelled. Gesture event information is returned.|

**Return values**

| Type| Description|
| -------- | -------- |
| [PanGestureHandler](#pangesturehandler) | Pan gesture handler object.|

## PanGestureHandlerOptions

Provides the parameters of the pan gesture handler. Inherits from [BaseHandlerOptions](#basehandleroptions15).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                             | Read-Only| Optional| Description                |
| ------------ | ---------------------------------|----- | ---- | -------------------- |
| fingers | number | No | Yes | Minimum number of fingers required to trigger a drag. The minimum value is 1,&nbsp;and the maximum value is 10.<br>Default value: **1**<br>Value range: [1, 10]<br>**Note:** <br>If the value is less than 1 or not set, it is converted to the default value.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| direction | [PanDirection](./ts-basic-gestures-pangesture.md#pandirection) | No | Yes | Gesture direction that triggers the drag. This enum value supports logical AND (&amp;) and logical OR (\|) operations.<br/>Default value: **PanDirection.All**<br/>**Atomic service API:** This API can be used in atomic services since API version 12. |
| distance | number | No | Yes | Minimum drag distance that triggers a swipe gesture event, in vp.<br>Default value for stylus: 8; default value for other input sources: 5<br>**Note:**<br>When the [Tabs component](ts-container-tabs.md) swipe and this swipe gesture event coexist, set **distance** to **1** to make the drag more sensitive and avoid event disorder.<br>Value range: [0, +∞). If the value is less than 0, the default value is used.<br>Since API version 19, the default value for stylus is 8, in vp.<br>When this field is configured using [gestureModifier](./ts-universal-attributes-gesture-modifier.md#gesturemodifier), the unit is px.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| distanceMap<sup>19+</sup> | Map\<[SourceTool](ts-gesture-settings.md#sourcetool9), number\> | No | Yes | Minimum drag distance that triggers a swipe gesture event for different input sources, in vp.<br>Default value for stylus: **8**; default value for other input sources: **5**<br>**Note:**<br>When the [Tabs component](ts-container-tabs.md) swipe and this swipe gesture event coexist, set the distanceMap value of the corresponding input source to 1 to make the drag more sensitive and avoid event disorder.<br>Value range: [0, +∞). If the value is less than 0, the default value is used.<br>**Atomic service API:** This API can be used in atomic services since API version 19. |

## SwipeGestureHandler

Defines the swipe gesture handler object type, which is used to recognize quick swipe interactions on a component. It is suitable for scenarios where an operation is triggered based on the swipe direction or speed, and supports configuring the number of triggering fingers, the swipe direction, and the minimum speed.

### constructor

constructor(options?: SwipeGestureHandlerOptions)

Constructor used to create a swipe gesture handler instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                        | Mandatory| Description              |
| ------- | ------------------------------------------------------------ | ---- | ------------------ |
| options | [SwipeGestureHandlerOptions](#swipegesturehandleroptions) | No | Configuration options of the swipe gesture handler. Pass this parameter when you need to customize the minimum finger count, swipe direction, minimum recognition speed, or finger count check for triggering a swipe; if not passed, the default configuration of the swipe gesture handler is used, that is, the trigger finger count is 1, the direction is **SwipeDirection.All**, the minimum speed is 100 vp/s, and the number of fingers touching the screen is not checked by default. |

### onAction

onAction(event: Callback\<GestureEvent>): SwipeGestureHandler

Sets the callback for successful swipe gesture recognition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes | Callback invoked when the swipe gesture handler is successfully recognized. The callback parameter is a **GestureEvent** object, used to obtain the swipe gesture event information. |

**Return values**

| Type| Description|
| -------- | -------- |
| [SwipeGestureHandler](#swipegesturehandler) | Swipe gesture handler object.|

## SwipeGestureHandlerOptions

Provides the parameters of the swipe gesture handler. Inherits from [BaseHandlerOptions](#basehandleroptions15).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                                  | Read-Only| Optional| Description                |
| ------------ | -------------------------------------- | ---- | -----|--------------- |
| fingers | number | No | Yes | Minimum number of fingers required to trigger a swipe.<br>Value range: [1, 10]. If the value is out of range, the default value is used.<br>Set this parameter to 1 when a single-finger swipe is sufficient to trigger the action; set it to a value from 2 to 10 when you need to reduce accidental touches and require multi-finger coordination to trigger the swipe.<br>Default value: **1** |
| direction | [SwipeDirection](./ts-basic-gestures-swipegesture.md#swipedirection) | No | Yes | Swipe direction that triggers the swipe gesture. **SwipeDirection.All** applies to scenarios where a swipe in any direction can trigger the action; **SwipeDirection.Horizontal** applies to scenarios where only horizontal swipes are responded to, such as page turning or carousel switching; **SwipeDirection.Vertical** applies to scenarios where only vertical swipes are responded to, such as switching content up and down; **SwipeDirection.None** applies to scenarios where the swipe gesture is not triggered for the time being. If this parameter is not passed, the default value is **SwipeDirection.All**.<br>Default value: **SwipeDirection.All** |
| speed | number | No | Yes | Minimum speed for recognizing a swipe. Set a smaller positive threshold when you need to recognize swipes more sensitively; set a larger threshold when you need to reduce the chance of ordinary pans being misrecognized as swipes. It is recommended to use the default value first and then adjust it based on interaction sensitivity and accidental touch conditions. If this parameter is not passed, the default value is **100vp/s**.<br>Default value: 100vp/s <br>Value range: (0, +∞), unit: vp/s.<br>**NOTE**<br>When the swipe speed is less than or equal to 0, it is converted to the default value. |
| isFingerCountLimited<sup>15+</sup> | boolean | No | Yes | Whether to check the number of fingers touching the screen. The value **true** indicates checking the number of fingers touching the screen, and **false** indicates not checking the number of fingers touching the screen. If the number of touching fingers is not equal to the minimum number of fingers set to trigger the swipe (that is, the **fingers** parameter above), gesture recognition fails.<br>Default value: **false**<br>**Atomic service API:** This API can be used in atomic services since API version 15. |

## PinchGestureHandler

Defines the pinch gesture handler object type, which is used to recognize multi-finger pinch interactions on a component. It is suitable for scaling operation scenarios, and supports configuring recognition conditions such as the number of triggering fingers, the minimum recognition distance, and the finger count limit.

### constructor

constructor(options?: PinchGestureHandlerOptions)

Constructor used to create a pinch gesture handler instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**


| Name | Type                                                        | Mandatory| Description              |
| ------- | ------------------------------------------------------------ | ---- | ------------------ |
| options | [PinchGestureHandlerOptions](#pinchgesturehandleroptions) | No | Configuration parameters of the pinch gesture handler. Pass this parameter when you need to customize the minimum finger count for triggering a pinch, the minimum recognition distance, or the finger count check. If this parameter is not passed, the default configuration of the pinch gesture handler is used, for example, the trigger finger count is 2, the minimum recognition distance is 5 vp, and the finger count on the touch screen is not checked by default. |

### onActionStart

onActionStart(event: Callback\<GestureEvent>): PinchGestureHandler

Sets the callback for successful pinch gesture recognition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes | Callback invoked when the pinch gesture is recognized successfully. The callback parameter is a **GestureEvent** object, used to obtain the gesture event information at the start of the pinch. |

**Return values**

| Type| Description|
| -------- | -------- |
| [PinchGestureHandler](#pinchgesturehandler) | Pinch gesture handler object.|

### onActionUpdate

onActionUpdate(event: Callback\<GestureEvent>): PinchGestureHandler

Sets the callback for pinch gesture movement updates. The callback is triggered when the pinch gesture moves.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes | Callback invoked when the pinch gesture handler is updated. The callback parameter is a **GestureEvent** object, used to obtain the gesture event information during the pinch update. |

**Return values**

| Type| Description|
| -------- | -------- |
| [PinchGestureHandler](#pinchgesturehandler) | Pinch gesture handler object.|

### onActionEnd

onActionEnd(event: Callback\<GestureEvent>): PinchGestureHandler

Sets the callback for pinch gesture recognition completion. This callback is triggered when all fingers are lifted after successful recognition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes | Callback invoked when the pinch gesture handler ends. The callback parameter is a **GestureEvent** object, used to obtain the gesture event information when the pinch ends. |

**Return values**

| Type| Description|
| -------- | -------- |
| [PinchGestureHandler](#pinchgesturehandler) | Pinch gesture handler object.|

### onActionCancel

onActionCancel(event: Callback\<void>): PinchGestureHandler

Sets the callback for pinch gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. No gesture event information is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)\<void> | Yes| Callback invoked when the pinch gesture is cancelled. No gesture event information is returned.|

**Return values**

| Type| Description|
| -------- | -------- |
| [PinchGestureHandler](#pinchgesturehandler) | Pinch gesture handler object.|

### onActionCancel<sup>18+</sup>

onActionCancel(event: Callback\<GestureEvent>): PinchGestureHandler

Sets the callback for pinch gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. Compared with [onActionCancel](#onactioncancel-2), this API returns gesture event information.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes| Callback invoked when the pinch gesture is cancelled. Gesture event information is returned.|

**Return values**

| Type| Description|
| -------- | -------- |
| [PinchGestureHandler](#pinchgesturehandler) | Pinch gesture handler object.|

## PinchGestureHandlerOptions

Provides the parameters of the pinch gesture handler. Inherits from [BaseHandlerOptions](#basehandleroptions15).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                              | Read-Only  | Optional| Description                |
| ------------ | ----------------------------------|---- | ---- | -------------------- |
| fingers | number | No | Yes | Minimum number of fingers that trigger a pinch. The value ranges from 2 to 5.<br>Default value: **2**<br>Value range: [2, 5]<br>If the value is less than 2 or greater than 5, the default value **2** is used.<br>If **isFingerCountLimited** is not enabled, the number of fingers that trigger the gesture can be greater than **fingers**, but only the first **fingers** fingers that touch the screen participate in gesture calculation. If **isFingerCountLimited** is enabled, the number of fingers touching the screen must be equal to **fingers**; otherwise, the gesture will not be recognized. |
| distance | number | No | Yes | Minimum recognition distance, in vp. To recognize a pinch gesture more sensitively, set a smaller positive threshold. To reduce the chance of triggering a pinch due to slight movement or accidental touch, set a larger threshold. You are advised to use the default value first and then adjust it based on the component size and interaction sensitivity. If this parameter is not set, the default value **5** is used.<br>Default value: **5**<br>Value range: (0, +∞)<br>**NOTE**<br>If the recognition distance is less than or equal to 0, the default value is used. |
| isFingerCountLimited<sup>15+</sup> | boolean | No | Yes | Whether to check the number of fingers touching the screen. The value **true** indicates to check the number of fingers touching the screen, and **false** indicates not to check. If the number of fingers touching the screen is not equal to the minimum number of fingers that trigger a pinch (that is, the **fingers** parameter), the gesture will not be recognized. The gesture can be recognized only when the number of fingers touching the screen is equal to the minimum number of fingers that trigger a pinch and the movement distance meets the threshold requirement. (Only the first **fingers** fingers that touch the screen participate in gesture calculation. If any of them is lifted, gesture recognition fails.) For a gesture that has been recognized, changing the number of fingers touching the screen later will not trigger the [onActionUpdate](ts-basic-gestures-pinchgesture.md#onactionupdate) event, but may trigger the [onActionEnd](ts-basic-gestures-pinchgesture.md#onactionend) event.<br>Default value: **false**<br>**Atomic service API:** This API can be used in atomic services since API version 15. |

## RotationGestureHandler

Defines the rotation gesture handler object type, which is used to recognize multi-finger rotation interactions on a component. It is suitable for scenarios where an object needs to be rotated or an angle needs to be adjusted, and supports configuring recognition conditions such as the number of triggering fingers, the minimum angle change, and the finger count limit.

### constructor

constructor(options?: RotationGestureHandlerOptions)

Constructor used to create a rotation gesture handler instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**


| Name | Type                                                        | Mandatory| Description              |
| ------- | ------------------------------------------------------------ | ---- | ------------------ |
| options | [RotationGestureHandlerOptions](#rotationgesturehandleroptions) | No | Rotation gesture handler configuration options. Pass this parameter when you need to customize the minimum number of fingers to trigger rotation, the minimum angle change to trigger the rotation gesture, or the finger count check. If this parameter is not passed, the default configuration of the rotation gesture handler is used, for example, two fingers to trigger, a minimum angle change of 1deg, and no check on the number of fingers touching the screen by default. |

### onActionStart

onActionStart(event: Callback\<GestureEvent>): RotationGestureHandler

Sets the callback for successful rotation gesture recognition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes | Callback invoked when the rotation gesture is recognized. The callback parameter is a **GestureEvent** object, used to obtain the gesture event information at the start of rotation. |

**Return values**

| Type| Description|
| -------- | -------- |
| [RotationGestureHandler](#rotationgesturehandler) | Rotation gesture handler object.|

### onActionUpdate

onActionUpdate(event: Callback\<GestureEvent>): RotationGestureHandler

Sets the callback for rotation gesture movement updates. The callback is triggered when the rotation gesture moves.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes | Callback for the rotation gesture handler update, with the callback parameter being a **GestureEvent** object used to obtain gesture event information during the rotation update. |

**Return values**

| Type| Description|
| -------- | -------- |
| [RotationGestureHandler](#rotationgesturehandler) | Rotation gesture handler object.|

### onActionEnd

onActionEnd(event: Callback\<GestureEvent>): RotationGestureHandler

Sets the callback for rotation gesture recognition completion. This callback is triggered when all fingers are lifted after successful recognition.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes | Callback invoked when the rotation gesture handler ends. The callback parameter is a **GestureEvent** object, which is used to obtain the gesture event information when the rotation ends. |

**Return values**

| Type| Description|
| -------- | -------- |
| [RotationGestureHandler](#rotationgesturehandler) | Rotation gesture handler object.|

### onActionCancel

onActionCancel(event: Callback\<void>): RotationGestureHandler

Sets the callback for rotation gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. No gesture event information is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)\<void> | Yes| Callback invoked when the rotation gesture is cancelled. No gesture event information is returned.|

**Return values**

| Type| Description|
| -------- | -------- |
| [RotationGestureHandler](#rotationgesturehandler) | Rotation gesture handler object.|

### onActionCancel<sup>18+</sup>

onActionCancel(event: Callback\<GestureEvent>): RotationGestureHandler

Sets the callback for rotation gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. Compared with [onActionCancel](#onactioncancel-3), this API returns gesture event information.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)<[GestureEvent](ts-gesture-common.md#gestureevent)> | Yes| Callback invoked when the rotation gesture is cancelled. Gesture event information is returned.|

**Return values**

| Type| Description|
| -------- | -------- |
| [RotationGestureHandler](#rotationgesturehandler) | Rotation gesture handler object.|

## RotationGestureHandlerOptions

Provides the parameters of the rotation gesture handler. Inherits from [BaseHandlerOptions](#basehandleroptions15).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                               |Read-Only  |Optional| Description                |
| ------------ | ---------------------------------|----- | ---- | -------------------- |
| fingers | number | No | Yes | Minimum number of fingers required to trigger rotation. The minimum is 2 and the maximum is 5.<br>Default value: **2**<br>Value range: [2, 5], inclusive. If the value is set to less than 2 or greater than 5, the default value **2** is used.<br>When **isFingerCountLimited** is not enabled, the number of fingers touching the screen can be greater than the value of **fingers** when the gesture is triggered, but only the first two fingers that touch the screen participate in gesture calculation. When **isFingerCountLimited** is enabled, the number of fingers touching the screen must be equal to the value of **fingers**; otherwise, the gesture will not be recognized. |
| angle | number | No | Yes | Minimum angle change, in degrees, required to trigger the rotation gesture. To recognize slight rotations more sensitively, set a smaller positive angle. To reduce accidental touches or respond only to obvious rotations, set a larger angle. It is recommended to use the default value first and then adjust it based on the rotation interaction precision requirements. If this parameter is not set, the default value 1 is used.<br>Default value: **1**<br>Value range: (0, 360]<br>**NOTE**<br>If the angle change is less than or equal to 0 or greater than 360, the default value is used. |
| isFingerCountLimited<sup>15+</sup> | boolean | No | Yes | Whether to check the number of fingers touching the screen. The value **true** indicates to check the number of fingers touching the screen, and **false** indicates not to check. If the number of fingers touching the screen is not equal to the minimum number of fingers set for triggering rotation (that is, the **fingers** parameter), the gesture will not be recognized. The gesture can be recognized successfully only when the number of fingers touching the screen is equal to the minimum number of fingers set for triggering rotation and the rotation angle change reaches the **angle** threshold. If the rotation angle change does not reach the **angle** threshold, the gesture will not be recognized successfully (only the first two fingers that touch the screen participate in gesture calculation; if one of them is lifted, gesture recognition fails).<br>For a gesture that has been recognized successfully, subsequently changing the number of fingers touching the screen does not trigger the [onActionUpdate](ts-basic-gestures-rotationgesture.md#onactionupdate) event, but can trigger the [onActionEnd](ts-basic-gestures-rotationgesture.md#onactionend) event.<br>Default value: false<br>**Atomic service API:** This API can be used in atomic services since API version 15. |

## GestureGroupHandler

Defines the gesture group handler object type, which is used to combine multiple gestures and bind them to a component as a whole. It is suitable for scenarios where the recognition order or concurrency relationship of multiple gestures such as single tap, double tap, and long press needs to be coordinated.

### constructor

constructor(options?: GestureGroupGestureHandlerOptions)

Constructor used to create a gesture group handler instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                        | Mandatory| Description              |
| ------- | ------------------------------------------------------------ | ---- | ------------------ |
| options | [GestureGroupGestureHandlerOptions](#gesturegroupgesturehandleroptions) | No | Configuration options of the gesture group handler. Passed when the combined gesture recognition mode and gesture set need to be set; if not passed, the default configuration of the gesture group handler is used, with the combined gesture recognition mode defaulting to **GestureMode.Sequence** and no gesture set configured. |

### onCancel

onCancel(event: Callback\<void>): GestureGroupHandler

Sets the cancellation callback for the gesture group handler. The callback is triggered when a sequence gesture ([GestureMode](./ts-combined-gestures.md#gesturemode).Sequence) is cancelled.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description                |
| ------ | --------------------------------- | ---- | -------------------- |
| event  | [Callback](./ts-types.md#callback12)\<void> | Yes | Callback for the gesture group handler cancellation, which takes no input parameter and is used to receive a notification after the sequential combined gesture is canceled. |

**Return values**

| Type| Description|
| -------- | -------- |
| [GestureGroupHandler](#gesturegrouphandler) | Current gesture group handler object.|

## GestureGroupGestureHandlerOptions

Provides the parameters of the gesture group handler.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                              | Read-Only   | Optional| Description                |
| ------------ | ---------------------------------|----- | ---- | -------------------- |
| mode    | [GestureMode](./ts-combined-gestures.md#gesturemode)                        | No | No   | Gesture recognition mode of the gesture group. It applies to scenarios where multiple gestures need to be recognized in sequence, in parallel, or mutually exclusively.<br>Default value: **GestureMode.Sequence**      |
| gestures | [GestureHandler](#gesturehandlert)\<[TapGestureHandler](#tapgesturehandler) \| [LongPressGestureHandler](#longpressgesturehandler) \| [PanGestureHandler](#pangesturehandler) \| [SwipeGestureHandler](#swipegesturehandler) \| [PinchGestureHandler](#pinchgesturehandler) \| [RotationGestureHandler](#rotationgesturehandler) \| [GestureGroupHandler](#gesturegrouphandler)>[] | No | No   | Set of gestures to be included in the gesture group.<br>**NOTE**  <br>To add both a single-tap gesture and a double-tap gesture to a component, add two [TapGesture](ts-basic-gestures-tapgesture.md) instances to [GestureGroup](ts-combined-gestures.md), with the double-tap gesture placed before the single-tap gesture. Otherwise, the configuration of adding both single-tap and double-tap gestures does not take effect. |

## GesturePriority

Defines the priority of the bound gesture, which is suitable for scenarios where the response order of gestures needs to be controlled or gesture conflicts need to be handled when multiple gestures are bound at the same time.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value|  Description|
| ------| -- | -------- |
| NORMAL | 0 | Normal priority.|
| PRIORITY | 1 | High priority.|