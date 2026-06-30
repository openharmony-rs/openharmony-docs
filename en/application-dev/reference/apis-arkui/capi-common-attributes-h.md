# common_attributes.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @zhou-chaobo-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines the types of common attributes and events of **NativeModule**.

**File to include:** <arkui/node_attributes/common_attributes.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample**: <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md) | ArkUI_SnapshotOptions | Defines snapshot options.|
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md) | ArkUI_VisibleAreaEventOptions | Defines the parameters for visible area change events.|

### Enums

| Name                                                                 | typedef Keyword                     | Description                               |
|---------------------------------------------------------------------|---------------------------------|-----------------------------------|
| [ArkUI_HitTestMode](#arkui_hittestmode)                             | ArkUI_HitTestMode               | Enumerates the hit test modes.                       |
| [ArkUI_Visibility](#arkui_visibility)                               | ArkUI_Visibility                | Enumerates the visibility values.                      |
| [ArkUI_HoverEffect](#arkui_hovereffect) | ArkUI_HoverEffect | Enumerates the hover effects when a component is hovered over.|
| [ArkUI_FocusPriority](#arkui_focuspriority) | ArkUI_FocusPriority | Enumerates the priority levels for focus management within the application. These levels determine the sequence in which UI components receive focus during user interaction.|
| [ArkUI_UIState](#arkui_uistate)                                     | ArkUI_UIState                   | Enumerates the UI states of a component, used for handling state-specific styles.              |
| [ArkUI_FocusMove](#arkui_focusmove)                                 | ArkUI_FocusMove                 | Enumerates the focus movement directions.                    |
| [ArkUI_ResponseRegionSupportedTool](#arkui_responseregionsupportedtool)                         | ArkUI_ResponseRegionSupportedTool             | Enumerates the input tool types supported for response region configuration.                        |

### Functions

| Name| Description|
| -- | -- |
| [ArkUI_SnapshotOptions* OH_ArkUI_CreateSnapshotOptions()](#oh_arkui_createsnapshotoptions) | Creates a snapshot option object, which must be released using [OH_ArkUI_DestroySnapshotOptions](#oh_arkui_destroysnapshotoptions) when no longer in use.|
| [void OH_ArkUI_DestroySnapshotOptions(ArkUI_SnapshotOptions* snapshotOptions)](#oh_arkui_destroysnapshotoptions) | Destroys the snapshot option object.|
| [int32_t OH_ArkUI_SnapshotOptions_SetScale(ArkUI_SnapshotOptions* snapshotOptions, float scale)](#oh_arkui_snapshotoptions_setscale) | Sets the scale property in the snapshot options.|
| [int32_t OH_ArkUI_SnapshotOptions_SetColorMode(ArkUI_SnapshotOptions* snapshotOptions, int32_t colorSpace, bool isAuto)](#oh_arkui_snapshotoptions_setcolormode) | Sets the color space in the screenshot options.|
| [int32_t OH_ArkUI_SnapshotOptions_SetDynamicRangeMode(ArkUI_SnapshotOptions* snapshotOptions, int32_t dynamicRangeMode, bool isAuto)](#oh_arkui_snapshotoptions_setdynamicrangemode) | Sets the dynamic range mode in the screenshot options.|
| [ArkUI_VisibleAreaEventOptions* OH_ArkUI_VisibleAreaEventOptions_Create()](#oh_arkui_visibleareaeventoptions_create) | Creates an instance of the parameters for visible area change events.|
| [void OH_ArkUI_VisibleAreaEventOptions_Dispose(ArkUI_VisibleAreaEventOptions* option)](#oh_arkui_visibleareaeventoptions_dispose) | Disposes of the instance of the parameters for visible area change events.|
| [int32_t OH_ArkUI_VisibleAreaEventOptions_SetRatios(ArkUI_VisibleAreaEventOptions* option, float* value, int32_t size)](#oh_arkui_visibleareaeventoptions_setratios) | Sets the threshold ratios for visible area changes.|
| [int32_t OH_ArkUI_VisibleAreaEventOptions_SetExpectedUpdateInterval(ArkUI_VisibleAreaEventOptions *option, int32_t value)](#oh_arkui_visibleareaeventoptions_setexpectedupdateinterval) | Sets the expected update interval for visible area changes.|
| [int32_t OH_ArkUI_VisibleAreaEventOptions_SetMeasureFromViewport(ArkUI_VisibleAreaEventOptions *option, bool measureFromViewport)](#oh_arkui_visibleareaeventoptions_setmeasurefromviewport) | Sets the visible area calculation mode.|
| [int32_t OH_ArkUI_VisibleAreaEventOptions_GetRatios(ArkUI_VisibleAreaEventOptions* option, float* value, int32_t* size)](#oh_arkui_visibleareaeventoptions_getratios) | Obtains the threshold ratios for visible area changes.|
| [int32_t OH_ArkUI_VisibleAreaEventOptions_GetExpectedUpdateInterval(ArkUI_VisibleAreaEventOptions* option)](#oh_arkui_visibleareaeventoptions_getexpectedupdateinterval) | Obtains the expected update interval for visible area changes.|
| [bool OH_ArkUI_VisibleAreaEventOptions_GetMeasureFromViewport(ArkUI_VisibleAreaEventOptions* option)](#oh_arkui_visibleareaeventoptions_getmeasurefromviewport) | Obtains the visible area calculation mode.|

## Enum Description

### ArkUI_HitTestMode

```c
enum ArkUI_HitTestMode
```

**Description**


Enumerates the hit test modes.

**Since:** 12

| Value| Description                                                    |
| -- |--------------------------------------------------------|
| ARKUI_HIT_TEST_MODE_DEFAULT = 0 | Default hit test mode. The node itself and its child nodes respond to the hit test, but block the hit test of sibling nodes. It does not affect the hit test of ancestor nodes.                                             |
| ARKUI_HIT_TEST_MODE_BLOCK = 1 | The node itself responds to the hit test and blocks the hit test of child nodes, sibling nodes, and ancestor nodes.                                             |
| ARKUI_HIT_TEST_MODE_TRANSPARENT = 2 | Both the node itself and its child nodes respond to the hit test and do not block the hit test of sibling nodes and ancestor nodes.                                        |
| ARKUI_HIT_TEST_MODE_NONE = 3 | The node itself does not respond to the hit test and does not block the hit test of child nodes, sibling nodes, and ancestor nodes.                                            |
| ARKUI_HIT_TEST_MODE_BLOCK_HIERARCHY = 4 | The node itself and its child nodes respond to the hit test, preventing all sibling nodes and parent nodes with lower priority from participating in the hit test.<br>**Since:** 20|
| ARKUI_HIT_TEST_MODE_BLOCK_DESCENDANTS = 5 | The node itself does not respond to the hit test, and all its descendants (children, grandchildren, and more) also do not respond to the hit test. It does not affect the hit test of ancestor nodes.<br>**Since:** 20                    |

### ArkUI_Visibility

```c
enum ArkUI_Visibility
```

**Description**


Enumerates the visibility values.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_VISIBILITY_VISIBLE = 0 | The component is visible.|
| ARKUI_VISIBILITY_HIDDEN = 1 | The component is hidden, and a placeholder is used for it in the layout.|
| ARKUI_VISIBILITY_NONE = 2 | The component is hidden. It is not involved in the layout, and no placeholder is used for it.|

### ArkUI_HoverEffect

```c
enum ArkUI_HoverEffect
```

**Description**


Enumerates the hover effects when a component is hovered over.

**Since:** 23

| Value| Description|
| -- | -- |
| ARKUI_HOVER_EFFECT_AUTO = 0 | Default effect.|
| ARKUI_HOVER_EFFECT_SCALE  | Scale effect.|
| ARKUI_HOVER_EFFECT_HIGHLIGHT  | Highlight effect.|
| ARKUI_HOVER_EFFECT_NONE  | No effect.|

### ArkUI_FocusPriority

```c
enum ArkUI_FocusPriority
```

**Description**


Enumerates the priority levels for focus management within the application. These levels determine the sequence in which UI components receive focus during user interaction.

**Since:** 23

| Value| Description|
| -- | -- |
| ARKUI_FOCUS_PRIORITY_AUTO  = 0 | Default priority.|
| ARKUI_FOCUS_PRIORITY_PRIOR = 2000   | Priority that indicates the component is prioritized in the container.|
| ARKUI_FOCUS_PRIORITY_PREVIOUS = 3000   | Priority of a previously focused node in the container.|

### ArkUI_UIState

```c
enum ArkUI_UIState
```

**Description**


Enumerates the UI states of a component, used for handling state-specific styles.

**Since:** 20

| Value| Description|
| -- | -- |
| UI_STATE_NORMAL = 0 | Normal state.|
| UI_STATE_PRESSED = 1 << 0 | Pressed state.|
| UI_STATE_FOCUSED = 1 << 1 | Focused state.|
| UI_STATE_DISABLED = 1 << 2 | Disabled state.|
| UI_STATE_SELECTED = 1 << 3 | Selected state. This state is supported only by specific component types: **Checkbox**, **Radio**, **Toggle**, **List**, **Grid**, and **MenuItem**.|
| UI_STATE_HOVERED = 1 << 4 | Hovered state.<br>**Since:** 26.0.0|

### ArkUI_FocusMove

```c
enum ArkUI_FocusMove
```

**Description**

Enumerates the focus movement directions.

**Since:** 18

| Value| Description|
| -- | -- |
| ARKUI_FOCUS_MOVE_FORWARD = 0 | Move focus forward.|
| ARKUI_FOCUS_MOVE_BACKWARD = 1 | Move focus backward.|
| ARKUI_FOCUS_MOVE_UP = 2 | Move focus up.|
| ARKUI_FOCUS_MOVE_DOWN = 3 | Move focus down.|
| ARKUI_FOCUS_MOVE_LEFT = 4 | Move focus left.|
| ARKUI_FOCUS_MOVE_RIGHT = 5 | Move focus right.|

### ArkUI_ResponseRegionSupportedTool

```c
enum ArkUI_ResponseRegionSupportedTool
```

**Description**


Enumerates the input tool types supported for response region configuration.

**Since:** 23

| Value| Description|
| -- | -- |
| ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_ALL  = 0 | All.|
| ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_FINGER  = 1  | Finger.|
| ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_PEN  = 2  | Stylus.|
| ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_MOUSE  = 3  | Mouse.|

## Function Description

### OH_ArkUI_CreateSnapshotOptions()

```c
ArkUI_SnapshotOptions* OH_ArkUI_CreateSnapshotOptions()
```

**Description**


Creates a snapshot option object, which must be released using [OH_ArkUI_DestroySnapshotOptions](#oh_arkui_destroysnapshotoptions) when no longer in use.

**Since:** 15

**Returns**

| Type                        | Description|
|----------------------------| -- |
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* | Pointer to the created snapshot option object. If a null pointer is returned, creation failed, possibly due to insufficient memory.|

### OH_ArkUI_DestroySnapshotOptions()

```c
void OH_ArkUI_DestroySnapshotOptions(ArkUI_SnapshotOptions* snapshotOptions)
```

**Description**

Destroys the snapshot option object.

**Since:** 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* snapshotOptions | Pointer to the screenshot option array.|

### OH_ArkUI_SnapshotOptions_SetScale()

```c
int32_t OH_ArkUI_SnapshotOptions_SetScale(ArkUI_SnapshotOptions* snapshotOptions, float scale)
```

**Description**

Sets the scale property in the snapshot options.

**Since:** 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* snapshotOptions | Pointer to the screenshot option array.|
| float scale | Scale factor.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         A possible cause is that mandatory parameters are left unspecified.|
### OH_ArkUI_SnapshotOptions_SetColorMode()

``` C++
int32_t OH_ArkUI_SnapshotOptions_SetColorMode(ArkUI_SnapshotOptions* snapshotOptions, int32_t colorSpace, bool isAuto)
```

**Description**

Sets the color space in the screenshot options.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* snapshotOptions | Pointer to the screenshot option array.|
| int32_t colorSpace | Color space used for the screenshot.<br>If the target component's color space is known, specify it through **colorSpace** and set **isAuto** to **false** to achieve optimal snapshot quality.<br>The supported values are as follows: **3** (Display P3), **4** (SRGB), and **27** (DISPLAY BT2020).<br>Default value: **4**<br>This parameter takes effect only when **isAuto** is set to **false**.|
| bool isAuto | Whether the system automatically determines the color space to be used.<br>**true**: The system automatically determines the color space to be used. If the color space used by the component is uncertain, you are advised to set **isAuto** to **true** so that the system can automatically determine the color space to be used.<br>**false**: The color space type set through the **colorSpace** field is used for screenshot.<br>Default value: **false**|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_SnapshotOptions_SetDynamicRangeMode()

``` C++
int32_t OH_ArkUI_SnapshotOptions_SetDynamicRangeMode(ArkUI_SnapshotOptions* snapshotOptions, int32_t dynamicRangeMode, bool isAuto)
```

**Description**

Sets the dynamic range mode in the screenshot options.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* snapshotOptions | Pointer to the screenshot option array.|
| int32_t dynamicRangeMode | Dynamic range mode used for screenshot.<br>If the dynamic range mode used for screenshot is known, you can specify the dynamic range mode using the **dynamicRangeMode** field and set **isAuto** to **false** to achieve the expected snapshot effect.<br>The value can be an enumerated value of [ArkUI_DynamicRangeMode](capi-image-h.md#arkui_dynamicrangemode).<br>Default value: **ARKUI_DYNAMIC_RANGE_MODE_STANDARD**<br>This parameter takes effect only when **isAuto** is set to **false**.|
| bool isAuto | Whether the system automatically determines the dynamic range mode to be used.<br>**true**: whether the system automatically determines the dynamic range mode to be used. If the dynamic range mode used by the component is uncertain, you are advised to set **isAuto** to **true** so that the system can automatically determine the dynamic range mode to be used.<br>**false**: The dynamic range mode set by the **dynamicRangeMode** field is used for screenshot.<br>Default value: **false**|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.|

### OH_ArkUI_VisibleAreaEventOptions_Create()

```c
ArkUI_VisibleAreaEventOptions* OH_ArkUI_VisibleAreaEventOptions_Create()
```

**Description**

Creates an instance of the parameters for visible area change events.

**Since:** 17

**Returns**

| Type                                | Description|
|------------------------------------| -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* | Pointer to the instance of the parameters for visible area change events.|

### OH_ArkUI_VisibleAreaEventOptions_Dispose()

```c
void OH_ArkUI_VisibleAreaEventOptions_Dispose(ArkUI_VisibleAreaEventOptions* option)
```

**Description**

Disposes of the instance of the parameters for visible area change events.

**Since:** 17

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Pointer to the instance of visible area change event parameters to be disposed of.|

### OH_ArkUI_VisibleAreaEventOptions_SetRatios()

```c
int32_t OH_ArkUI_VisibleAreaEventOptions_SetRatios(ArkUI_VisibleAreaEventOptions* option, float* value, int32_t size)
```

**Description**

Sets the threshold ratios for visible area changes.

**Since:** 17

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Pointer to the instance of visible area change event parameters.|
| float* value | Pointer to the array of threshold ratios. Each element represents a ratio of the component's visible area (that is, the area of the component that is visible on screen; only the area within the parent component is counted) to the component's total area. The value range of the threshold is [0.0, 1.0]. If the threshold set exceeds this range, the value **0.0** or **1.0** will be used.|
| int32_t size | Size of the array of threshold ratios.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_VisibleAreaEventOptions_SetExpectedUpdateInterval()

```c
int32_t OH_ArkUI_VisibleAreaEventOptions_SetExpectedUpdateInterval(ArkUI_VisibleAreaEventOptions *option, int32_t value)
```

**Description**

Sets the expected update interval for visible area changes.

**Since:** 17

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md) *option | Pointer to the instance of visible area change event parameters.|
| int32_t value | Expected update interval, in ms. Default value: **1000**.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_VisibleAreaEventOptions_SetMeasureFromViewport()

```c
int32_t OH_ArkUI_VisibleAreaEventOptions_SetMeasureFromViewport(ArkUI_VisibleAreaEventOptions* option, bool measureFromViewport)
```

**Description**

Sets the visible area calculation mode.

**Since:** 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Pointer to the instance of visible area change event parameters.|
| bool measureFromViewport | Visible area calculation mode.<br>**true**: The calculation takes the parent component's **NODE_CLIP** attribute into account. If the parent component's **NODE_CLIP** attribute is **false**: Child components can render beyond the parent component's bounds, and the out-of-bounds area is counted as part of the visible area. If the parent component's **NODE_CLIP** attribute is **true**: Child components are clipped to the parent component's bounds, and the out-of-bounds area is treated as invisible. **false**: The area beyond the parent component's bounds is directly treated as invisible, ignoring the parent component's **NODE_CLIP** attribute.<br>Default value: **false**|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_VisibleAreaEventOptions_GetRatios()

```c
int32_t OH_ArkUI_VisibleAreaEventOptions_GetRatios(ArkUI_VisibleAreaEventOptions* option, float* value, int32_t* size)
```

**Description**

Obtains the threshold ratios for visible area changes.

**Since:** 17

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Pointer to the instance of visible area change event parameters.|
| float* value | Pointer to the array of threshold ratios.|
| int32_t* size | Pointer to the size of the array of threshold ratios.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-native-type-h.md#arkui_errorcode) if a parameter error occurs.<br>         Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-native-type-h.md#arkui_errorcode) if the array size is insufficient.<br>         A possible cause is that mandatory parameters are left unspecified.|

### OH_ArkUI_VisibleAreaEventOptions_GetExpectedUpdateInterval()

```c
int32_t OH_ArkUI_VisibleAreaEventOptions_GetExpectedUpdateInterval(ArkUI_VisibleAreaEventOptions* option)
```

**Description**

Obtains the expected update interval for visible area changes.

**Since:** 17

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Pointer to the instance of visible area change event parameters.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Expected update interval, in ms. Default value: **1000**.|


### OH_ArkUI_VisibleAreaEventOptions_GetMeasureFromViewport()

```c
bool OH_ArkUI_VisibleAreaEventOptions_GetMeasureFromViewport(ArkUI_VisibleAreaEventOptions* option)
```

**Description**

Obtains the visible area calculation mode.

**Since:** 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Pointer to the instance of visible area change event parameters.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Visible area calculation mode.<br>**true**: The calculation takes the parent component's **NODE_CLIP** attribute into account. If the parent component's **NODE_CLIP** attribute is **false**: Child components can render beyond the parent component's bounds, and the out-of-bounds area is counted as part of the visible area. If the parent component's **NODE_CLIP** attribute is **true**: Child components are clipped to the parent component's bounds, and the out-of-bounds area is treated as invisible. **false**: The area beyond the parent component's bounds is directly treated as invisible, ignoring the parent component's **NODE_CLIP** attribute.<br>Default value: **false**|
