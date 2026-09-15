# ArkUI_NodeAttributeType (Others)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @wangyang2022-->
<!--Designer: @piggyguy; @wangyang2022-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=eaca76ddf3e6afb3afe4cc2d803f9aff7c95b81d translatedAt=2026-08-25T02:21:08.010Z pushedAt=2026-08-26T09:16:21.826Z -->

```c
enum ArkUI_NodeAttributeType
```

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side, including component interaction, focus obtaining, off-screen rendering, tap distance, and color inversion. It is applicable to scenarios where fine-grained control of component interaction states, focus management, rendering optimization, and gesture recognition precision is required on the native side, helping you improve the interaction controllability and rendering performance of components.

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
| .value[0].i32 | Whether the component can interact with users. The value **1** indicates that the component can interact with users, and **0** indicates the opposite. The default value is **1**. If the value is less than 0, it does not take effect. If the value is greater than 1, the default value is used. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the component can interact with users. The value **1** indicates that the component can interact with users, and **0** indicates the opposite. |

## NODE_FOCUSABLE

```c
NODE_FOCUSABLE = 39
```

Focus attribute, which controls whether the component can gain focus. It is applicable to scenarios such as keyboard navigation and accessibility assistance. This attribute can be set, reset, and obtained as required through APIs.
The format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute and the format of the return value **ArkUI_AttributeItem** are as follows.<br>

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| .value[0].i32 | Whether the component is focusable. The value **1** indicates that the component is focusable, and **0** indicates the opposite. The default value is **0**. |

**Returns**

| Type| Description|
| -- | -- |
| .value[0].i32 | Whether the component is focusable. The value **1** indicates that the component is focusable, and **0** indicates the opposite. |

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
| .value[0].i32 | Whether the component and its child components are rendered off the screen and then drawn together with its parent. The value **1** means that the component and its child components are rendered off the screen and then drawn together with its parent, and **0** means the opposite. |

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
| .value[0].f32 | Distance threshold within which the finger is allowed to move when a click gesture is recognized, in vp. The value range is [0, +∞). If the value is less than 0, the default value is used. The default value is infinite. A smaller value is suitable for scenarios requiring high click precision, and a larger value is suitable for scenarios requiring high click fault tolerance. |

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