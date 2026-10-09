# ArkUI_NodeAttributeType (Information Display Component Attribute)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=00d8471aa555cf6cc5dfeff4258ec5a6b23f56d0 translatedAt=2026-08-25T02:18:35.143Z pushedAt=2026-08-26T06:00:06.767Z -->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side for information display components including **LoadingProgress** and **Progress**. It supports setting the attributes such as the color, animation, progress value, and type, and applies to scenarios where the appearance and behavior of information display components need to be finely controlled at the native layer. Through a unified attribute collection API, you can conveniently implement features such as loading animation control, progress visualization, and style customization.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_LOADING_PROGRESS_COLOR

```c
NODE_LOADING_PROGRESS_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LOADING_PROGRESS = 6000
```

Foreground color of the loading progress bar. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Foreground color, in 0xARGB format. For example, **0xFFFF0000** indicates red. Default value: The color follows the theme color. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Foreground color, in 0xARGB format.|

## NODE_LOADING_PROGRESS_ENABLE_LOADING

```c
NODE_LOADING_PROGRESS_ENABLE_LOADING = 6001
```

Whether to show the loading animation for the **LoadingProgress** component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to show the loading animation. The value **1** indicates to show, and **0** indicates the opposite. The default value is **1**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the loading animation is shown. The value **1** means that the loading animation is shown, and **0** means the opposite. |

## NODE_PROGRESS_VALUE

```c
NODE_PROGRESS_VALUE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_PROGRESS = 10000
```

Current value of the progress indicator. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Current value of the progress indicator. The value range is [0, **total**]. The default value is **0**. If the value is out of range, it is automatically corrected to the boundary value in the valid range. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Current value of the progress indicator. The value range is [0, **total**]. The default value is **0**. |

## NODE_PROGRESS_TOTAL

```c
NODE_PROGRESS_TOTAL = 10001
```

Total value of the progress indicator. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Total value of the progress indicator. The value range is (0, +∞). The default value is **100**. The value must be greater than 0. The setting does not take effect if a value less than or equal to 0 is passed. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Total value of the progress indicator. The value range is (0, +∞). The default value is **100**. |

## NODE_PROGRESS_COLOR

```c
NODE_PROGRESS_COLOR = 10002
```

Color for the progress value on the progress indicator. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].u32 | Color, in 0xARGB format. For example, **0xFFFF0000** indicates red. Default value: The color follows the theme color. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].u32 | Color, in 0xARGB format.|

## NODE_PROGRESS_TYPE

```c
NODE_PROGRESS_TYPE = 10003
```

Type of the progress indicator. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Type of the progress indicator. The value is an enumerated value of [ArkUI_ProgressType](capi-progress-h.md#arkui_progresstype). The default value is **ARKUI_PROGRESS_TYPE_LINEAR**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Type of the progress indicator. |

## NODE_PROGRESS_LINEAR_STYLE

```c
NODE_PROGRESS_LINEAR_STYLE = 10004
```

Linear progress indicator style. This attribute can be set, reset, and obtained as required through APIs. It does not take effect if the progress indicator type is not linear. In this case, set the progress indicator type to **ARKUI_PROGRESS_TYPE_LINEAR** through **NODE_PROGRESS_TYPE** first.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15

**Parameters**

| Name| Description|
| -- | -- |
| .object | [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md) object that defines the component style.|

**Returns**

| Type| Description|
| -- | -- |
| .object | [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md) object that contains the style information of the linear progress indicator. |