# ArkUI_NodeAttributeType (Information Display Component Attribute)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side for information display components including **LoadingProgress** and **Progress**.

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
| .value[0].u32 | Foreground color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

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
| .value[0].i32 | Whether to show the loading animation. **true** to show; **false** otherwise. The default value is **true**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the loading animation is shown. The value **1** means that the loading animation is shown, and **0** means the opposite.|

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
| .value[0].f32 | Current value of the progress indicator.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Current value of the progress indicator.|

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
| .value[0].f32 | Total value of the progress indicator.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].f32 | Total value of the progress indicator.|

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
| .value[0].u32 | Color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

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
| .value[0].i32 | Type of the progress indicator, specified using the [ArkUI_ProgressType](capi-native-type-h.md#arkui_progresstype) enum. The default value is **ARKUI_PROGRESS_TYPE_LINEAR**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Type of the progress indicator, specified using the [ArkUI_ProgressType](capi-native-type-h.md#arkui_progresstype) enum.|

## NODE_PROGRESS_LINEAR_STYLE

```c
NODE_PROGRESS_LINEAR_STYLE = 10004
```

Linear progress indicator style. This attribute can be set, reset, and obtained as required through APIs. Note that the settings are effective only if the progress indicator type is linear.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 15


**Parameters**

| Name| Description|
| -- | -- |
| .object | [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md) object that defines the component style.|

**Returns**

| Type| Description|
| -- | -- |
| .object | [ArkUI_ProgressLinearStyleOption](capi-arkui-nativemodule-arkui-progresslinearstyleoption.md) object that obtains the component style.|
