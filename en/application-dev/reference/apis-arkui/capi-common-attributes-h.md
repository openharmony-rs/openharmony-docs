# common_attributes.h

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @zhou-chaobo-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=a982f9d9be2aa48466f66955fc58f87c03f60f05 translatedAt=2026-08-21T04:12:38.593Z pushedAt=2026-08-21T08:03:48.726Z -->

## Overview

Defines the types of common attributes and events of **NativeModule**, used to support the configuration of common component attributes and event handling, making it easier for native developers to manage component behavior in a unified manner.

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
| [ArkUI_ResponseRegionSupportedTool](#arkui_responseregionsupportedtool)                         | ArkUI_ResponseRegionSupportedTool             | Enumerates the input tool types supported for response region configuration.                         |
| [ArkUI_RawInputEventType](#arkui_rawinputeventtype) | ArkUI_RawInputEventType | Enumerates the types of raw input events.|

### Functions

| Name| Description|
| -- | -- |
| [ArkUI_SnapshotOptions* OH_ArkUI_CreateSnapshotOptions()](#oh_arkui_createsnapshotoptions) | Creates a snapshot option object, which must be released using [OH_ArkUI_DestroySnapshotOptions](#oh_arkui_destroysnapshotoptions) when no longer in use.|
| [void OH_ArkUI_DestroySnapshotOptions(ArkUI_SnapshotOptions* snapshotOptions)](#oh_arkui_destroysnapshotoptions) | Destroys the snapshot option object.|
| [int32_t OH_ArkUI_SnapshotOptions_SetScale(ArkUI_SnapshotOptions* snapshotOptions, float scale)](#oh_arkui_snapshotoptions_setscale) | Sets the scale property in the snapshot options.|
| [int32_t OH_ArkUI_SnapshotOptions_SetColorMode(ArkUI_SnapshotOptions* snapshotOptions, int32_t colorSpace, bool isAuto)](#oh_arkui_snapshotoptions_setcolormode) | Sets the color space in the screenshot options.|
| [int32_t OH_ArkUI_SnapshotOptions_SetDynamicRangeMode(ArkUI_SnapshotOptions* snapshotOptions, int32_t dynamicRangeMode, bool isAuto)](#oh_arkui_snapshotoptions_setdynamicrangemode) | Sets the dynamic range mode in the screenshot options.|
| [ArkUI_VisibleAreaEventOptions* OH_ArkUI_VisibleAreaEventOptions_Create()](#oh_arkui_visibleareaeventoptions_create) | Creates an instance of the parameters for visible area change events. This API is used in scenarios such as list scrolling exposure statistics, lazy loading of images or videos, and triggering business logic when a component enters or leaves the screen. After successful creation, you must first complete the related parameter configuration and listener usage, and call [OH_ArkUI_VisibleAreaEventOptions_Dispose](#oh_arkui_visibleareaeventoptions_dispose) to release the parameter object after use. After calling **Dispose**, you must not continue to use the parameter object. |
| [void OH_ArkUI_VisibleAreaEventOptions_Dispose(ArkUI_VisibleAreaEventOptions* option)](#oh_arkui_visibleareaeventoptions_dispose) | Disposes of the instance of the parameters for visible area change events.|
| [int32_t OH_ArkUI_VisibleAreaEventOptions_SetRatios(ArkUI_VisibleAreaEventOptions* option, float* value, int32_t size)](#oh_arkui_visibleareaeventoptions_setratios) | Sets the threshold array used to determine the change in the visible ratio of a component. This API is applicable to scenarios such as exposure statistics, staged loading of components, and controlling media playback based on the visible ratio. |
| [int32_t OH_ArkUI_VisibleAreaEventOptions_SetExpectedUpdateInterval(ArkUI_VisibleAreaEventOptions *option, int32_t value)](#oh_arkui_visibleareaeventoptions_setexpectedupdateinterval) | Sets the expected update interval. This API is used to control the update frequency of the visible area ratio. A smaller interval is suitable for scenarios that require timely awareness of visible area changes, but increases computational overhead. A larger interval is suitable for scenarios that do not require high real-time performance and need to reduce computational overhead. |
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
| ARKUI_HIT_TEST_MODE_BLOCK_DESCENDANTS = 5 | Neither the node itself nor any of its descendant nodes responds to the hit test. It does not affect the hit test of ancestor nodes.<br>**Since:** 20                     |

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
| ARKUI_HOVER_EFFECT_SCALE = 1 | Scale effect. |
| ARKUI_HOVER_EFFECT_HIGHLIGHT = 2 | Highlight effect. |
| ARKUI_HOVER_EFFECT_NONE = 3 | No effect. |

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
| UI_STATE_HOVERED = 1 << 4 | Hovered state.<br/>**Since:** 26 |

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

### ArkUI_RawInputEventType

```c
enum ArkUI_RawInputEventType
```

**Description**

Enumerates the types of raw input events.

**Since:** 26.0.0

| Value| Description|
| -- | -- |
| ARKUI_RAW_INPUT_EVENT_TYPE_TOUCH = 0 | Touch event.|
| ARKUI_RAW_INPUT_EVENT_TYPE_MOUSE = 1 | Mouse event.|

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
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* | Pointer to the created screenshot option object. If the API returns a null pointer, the creation fails, possibly because the address space is full. |

### OH_ArkUI_DestroySnapshotOptions()

```c
void OH_ArkUI_DestroySnapshotOptions(ArkUI_SnapshotOptions* snapshotOptions)
```

**Description**

Destroys the screenshot option object created by [OH_ArkUI_CreateSnapshotOptions](#oh_arkui_createsnapshotoptions).

**Since:** 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* snapshotOptions | Pointer to the screenshot option object to be destroyed, used to release the screenshot option object created by [OH_ArkUI_CreateSnapshotOptions](#oh_arkui_createsnapshotoptions). |

### OH_ArkUI_SnapshotOptions_SetScale()

```c
int32_t OH_ArkUI_SnapshotOptions_SetScale(ArkUI_SnapshotOptions* snapshotOptions, float scale)
```

**Description**

Set the scale attribute in screenshot options, which is used to control the scale factor of the generated screenshot.

**Since:** 15

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* snapshotOptions | Pointer to the screenshot option object. Before using this parameter, create a valid screenshot option object through [OH_ArkUI_CreateSnapshotOptions](#oh_arkui_createsnapshotoptions) to set the scale attribute of the screenshot. |
| float scale | Scale factor of the screenshot. The value is a floating-point number greater than 0, and the default value is **1.0**. |

**Returns**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Possible causes: The **snapshotOptions** parameter is null, or the **scale** value does not match the API requirements. To solve this issue, pass a valid screenshot option object pointer and ensure that the value of **scale** is a floating-point number greater than 0. |

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
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* snapshotOptions | Pointer to the screenshot option object. Before using this parameter, call [OH_ArkUI_CreateSnapshotOptions](#oh_arkui_createsnapshotoptions) to create a valid screenshot option object to set the color space of the screenshot. |
| int32_t colorSpace | Color space used for the screenshot.<br>If you know the color space used by the component to be captured, you can specify it through the **colorSpace** parameter and set **isAuto** to **false** to achieve the expected screenshot effect.<br>The supported values are as follows: **3** (Display P3, suitable for scenarios where Display P3 content needs to be retained), **4** (SRGB, suitable for common display devices and compatibility-first scenarios), and **27** (DISPLAY BT2020, suitable for scenarios where the target device supports the BT2020 color gamut).<br>Default value: **4**<br>This parameter takes effect only when **isAuto** is set to **false**. |
| bool isAuto | Whether the system automatically determines the color space to be used.<br>**true**: The system automatically determines the color space to be used. If the color space used by the component is uncertain, you are advised to set **isAuto** to **true** so that the system can automatically determine the color space to be used.<br>**false**: The color space type set through the **colorSpace** field is used for screenshot.<br>Default value: **false**|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Possible causes: The **snapshotOptions** parameter is null, or the **colorSpace** value is not supported. To solve this issue, pass a valid screenshot option object pointer and ensure that the **colorSpace** value is a supported color space. |

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
| [ArkUI_SnapshotOptions](capi-arkui-nativemodule-arkui-snapshotoptions.md)* snapshotOptions | Pointer to the screenshot option object. Before using this parameter, create a valid screenshot option object through [OH_ArkUI_CreateSnapshotOptions](#oh_arkui_createsnapshotoptions) to set the dynamic range mode of the screenshot. |
| int32_t dynamicRangeMode | Dynamic range mode used for the screenshot.<br>If you know the dynamic range mode used by the screenshot object, you can specify it through the **dynamicRangeMode** parameter and set **isAuto** to **false** to achieve the expected screenshot effect.<br>The value can be an enumerated value of [ArkUI_DynamicRangeMode](capi-image-h.md#arkui_dynamicrangemode): **ARKUI_DYNAMIC_RANGE_MODE_HIGH** applies to devices that support HDR display and HDR content, **ARKUI_DYNAMIC_RANGE_MODE_CONSTRAINT** applies to scenarios that require SDR compatibility, and **ARKUI_DYNAMIC_RANGE_MODE_STANDARD** applies to common display devices.<br>Default value: **ARKUI_DYNAMIC_RANGE_MODE_STANDARD**<br>This parameter takes effect only when **isAuto** is set to **false**. |
| bool isAuto | Whether the system automatically determines the dynamic range mode to be used.<br>**true**: The system automatically determines the dynamic range mode to be used. If the dynamic range mode used by the component is uncertain, you are advised to set **isAuto** to **true** so that the system can automatically determine the dynamic range mode to be used.<br>**false**: The dynamic range mode set by the **dynamicRangeMode** field is used for screenshot.<br>Default value: **false**|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Possible causes: The **snapshotOptions** parameter is null, or the **dynamicRangeMode** value is not supported. To solve this issue, pass a valid screenshot option object pointer and ensure that **dynamicRangeMode** is set to a supported dynamic range mode. |

### OH_ArkUI_VisibleAreaEventOptions_Create()

```c
ArkUI_VisibleAreaEventOptions* OH_ArkUI_VisibleAreaEventOptions_Create()
```

**Description**

Creates an instance of the parameters for visible area change events. This API is used in scenarios such as list scrolling exposure statistics, lazy loading of images or videos, and triggering business logic when a component enters or leaves the screen. After successful creation, you must first complete the related parameter configuration such as the visible ratio threshold and update interval through related APIs, and then use the parameter object to register the visible area change listener. The system calculates the component visible ratio based on the configured parameters and triggers the corresponding listener event. After use, call [OH_ArkUI_VisibleAreaEventOptions_Dispose](#oh_arkui_visibleareaeventoptions_dispose) to release the parameter object. After **Dispose** is called, the parameter object must not be used again.


**Since:** 17

**Returns**

| Type                                | Description|
|------------------------------------| -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* | Pointer to the parameter object of the visible area change listener. If the API returns a null pointer, the creation fails. |

### OH_ArkUI_VisibleAreaEventOptions_Dispose()

```c
void OH_ArkUI_VisibleAreaEventOptions_Dispose(ArkUI_VisibleAreaEventOptions* option)
```

**Description**

Disposes of the instance of the parameters for visible area change events. The parameter object must be created by [OH_ArkUI_VisibleAreaEventOptions_Create](#oh_arkui_visibleareaeventoptions_create), and must not be used after **Dispose** is called.

**Since:** 17

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Pointer to the parameter object to be disposed of. |

### OH_ArkUI_VisibleAreaEventOptions_SetRatios()

```c
int32_t OH_ArkUI_VisibleAreaEventOptions_SetRatios(ArkUI_VisibleAreaEventOptions* option, float* value, int32_t size)
```

**Description**

Sets the threshold array used to determine the change in the visible ratio of a component. This API is applicable to scenarios such as exposure statistics, staged loading of components, and controlling media playback based on the visible ratio.

**Since:** 17

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Pointer to the instance of visible area change event parameters. Before using this parameter, create a valid parameter instance through [OH_ArkUI_VisibleAreaEventOptions_Create](#oh_arkui_visibleareaeventoptions_create). |
| float* value | Pointer to the threshold array. Each element represents the ratio of the visible area of the component to the area of the component itself. By default, only the area within the parent component is calculated. When **measureFromViewport** is set to **true** and **NODE_CLIP** of the parent component is set to **false**, the part of the component beyond the parent component area is also counted into the visible area. The value range of each threshold is [0.0, 1.0]: a value close to 0.0 is suitable for listening to the scenario where the component just enters the visible area, a value close to 0.5 is suitable for listening to the scenario where most of the component is visible, and a value close to 1.0 is suitable for listening to the scenario where the component is fully or almost fully visible. Select the threshold based on the service requirement for the visibility of the component. If the threshold you set exceeds this range, the actual value **0.0** or **1.0** is used. |
| int32_t size | Number of elements in the threshold array, used to specify the number of thresholds passed by the **value** parameter. The value must be a non-negative integer and must be consistent with the actual number of threshold elements passed by the **value** parameter. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Possible causes: The **option** or **value** parameter is null, or the **size** value does not meet the API requirements. To solve this issue, pass a valid parameter pointer and ensure that the **size** value is valid. |

### OH_ArkUI_VisibleAreaEventOptions_SetExpectedUpdateInterval()

```c
int32_t OH_ArkUI_VisibleAreaEventOptions_SetExpectedUpdateInterval(ArkUI_VisibleAreaEventOptions *option, int32_t value)
```

**Description**

Sets the expected update interval. This API is used to control the update frequency of the visible area ratio. A smaller interval is suitable for scenarios that require timely awareness of visible area changes, but increases computational overhead. A larger interval is suitable for scenarios that do not require high real-time performance and need to reduce computational overhead.

**Since:** 17

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md) *option | Pointer to the instance of visible area change event parameters. Before using this parameter, create a valid parameter instance through [OH_ArkUI_VisibleAreaEventOptions_Create](#oh_arkui_visibleareaeventoptions_create). |
| int32_t value | Expected update interval, in ms. This parameter is used to control the calculation frequency of the visible area ratio. The value must be a non-negative integer. The default value is 1000 ms, which is used when this parameter is not set. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Possible causes: The **option** parameter is null or the **value** parameter does not meet the API requirements. To solve this issue, pass a valid parameter instance and ensure that **value** is valid. |

### OH_ArkUI_VisibleAreaEventOptions_SetMeasureFromViewport()

```c
int32_t OH_ArkUI_VisibleAreaEventOptions_SetMeasureFromViewport(ArkUI_VisibleAreaEventOptions* option, bool measureFromViewport)
```

**Description**

Sets the visible area calculation mode. In scenarios involving scrolling containers, clipping containers, or allowing child components to extend beyond the parent component display, you can select the calculation mode based on whether the actually visible portion within the viewport needs to be included in exposure and visibility determination.

**Since:** 22

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Pointer to the instance of visible area change event parameters. Before using this parameter, create a valid parameter instance through [OH_ArkUI_VisibleAreaEventOptions_Create](#oh_arkui_visibleareaeventoptions_create). |
| bool measureFromViewport | Visible area calculation mode.<br>When **measureFromViewport** is set to **true**, the system considers the **NODE_CLIP** attribute of the parent component when calculating the visible area of a component: if **NODE_CLIP** of the parent component is set to **false**, the area of the component beyond the parent component is also counted into the visible area; if **NODE_CLIP** of the parent component is set to **true**, the area of the component beyond the parent component is clipped and not counted into the visible area. When **measureFromViewport** is set to **false**, the system does not consider the **NODE_CLIP** attribute and directly treats the part of the component beyond the parent component as the invisible area.<br>Default value: **false** |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br>         Possible cause: The **option** parameter is null. To solve this issue, pass a valid instance of visible area change event parameters. |

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
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Pointer to the instance of visible area change event parameters. Before using this parameter, create a valid parameter instance through [OH_ArkUI_VisibleAreaEventOptions_Create](#oh_arkui_visibleareaeventoptions_create). |
| float* value | Pointer to the buffer used to receive the threshold array, where each element indicates the ratio of the visible area of the component to the area of the component itself, with a value range of [0.0, 1.0]. The array capacity is specified by the **size** parameter. |
| int32_t* size | Pointer to the size of the threshold array. Before the call, it is used to pass the capacity of the buffer specified by **value**. After the call succeeds, it is used to return the actual number of elements in the threshold array. |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Result code.<br> Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the operation is successful.<br> Returns [ARKUI_ERROR_CODE_PARAM_INVALID](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if a parameter error occurs.<br> Returns [ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR](capi-arkui-nativemodule-arkui-error-code-h.md#arkui_errorcode) if the array size is insufficient.<br> Possible causes: The **option**, **value**, or **size** parameter is null. To solve this issue, pass a valid parameter pointer and ensure that the buffer specified by **value** has sufficient capacity. If the capacity is insufficient, **ARKUI_ERROR_CODE_BUFFER_SIZE_ERROR** is returned. |

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
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Pointer to the instance of visible area change event parameters. Before using this parameter, create a valid parameter instance through [OH_ArkUI_VisibleAreaEventOptions_Create](#oh_arkui_visibleareaeventoptions_create). |

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Expected update interval, in ms. Default value: 1000 ms. |

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
| [ArkUI_VisibleAreaEventOptions](capi-arkui-nativemodule-arkui-visibleareaeventoptions.md)* option | Pointer to the instance of visible area change event parameters. Before using this parameter, create a valid parameter instance through [OH_ArkUI_VisibleAreaEventOptions_Create](#oh_arkui_visibleareaeventoptions_create). |

**Returns**

| Type| Description|
| -- | -- |
| bool | Visible area calculation mode.<br>**true**: The calculation takes the parent component's **NODE_CLIP** attribute into account. If the parent component's **NODE_CLIP** attribute is **false**: Child components can render beyond the parent component's bounds, and the out-of-bounds area is counted as part of the visible area. If the parent component's **NODE_CLIP** attribute is **true**: Child components are clipped to the parent component's bounds, and the out-of-bounds area is treated as invisible. **false**: The area beyond the parent component's bounds is directly treated as invisible, ignoring the parent component's **NODE_CLIP** attribute.<br>Default value: **false**|