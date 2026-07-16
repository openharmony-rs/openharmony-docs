# ArkUI_NodeAttributeType (Others)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @wangyang2022-->
<!--Designer: @piggyguy; @wangyang2022-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side, including component interaction, focus obtaining, off-screen rendering, and tap distance.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## NODE_ENABLED

```c
NODE_ENABLED = 6
```

Interactivity attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the component can interact with users. The value **1** indicates that the component can interact with users, and **0** indicates the opposite.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the component can interact with users. The value **1** indicates that the component can interact with users, and **0** indicates the opposite.|

## NODE_FOCUSABLE

```c
NODE_FOCUSABLE = 39
```

Focus attribute, which can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the component is focusable. The value **1** indicates that the component is focusable, and **0** indicates the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the component is focusable. The value **1** indicates that the component is focusable, and **0** indicates the opposite.|

## NODE_RENDER_GROUP

```c
NODE_RENDER_GROUP = 80
```

Whether the component and its child components are rendered off the screen and then drawn together with its parent. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the component and its child components are rendered off the screen and then drawn together with its parent. The value **1** means that the component and its child components are rendered off the screen and then drawn together with its parent, and **0** means the opposite. The default value is **0**.|

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the component and its child components are rendered off the screen and then drawn together with its parent. The value **1** means that the component and its child components are rendered off the screen and then drawn together with its parent, and **0** means the opposite.|

## NODE_CLICK_DISTANCE

```c
NODE_CLICK_DISTANCE = 97
```

Moving distance limit for the component-bound click gesture. This attribute can be set as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].f32 | Allowed moving distance of a finger, in vp.|

## NODE_ALLOW_FORCE_DARK

```c
NODE_ALLOW_FORCE_DARK = 108
```

Whether to enable color inversion of a component. This attribute can be set, reset, and obtained as required through APIs.<br>
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute is as follows.<br>

**Since**: 21


**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether to enable color inversion. The value 1 indicates to enable color inversion, and **0** indicates the opposite.|
