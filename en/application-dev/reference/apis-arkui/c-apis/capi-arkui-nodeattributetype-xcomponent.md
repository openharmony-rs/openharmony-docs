# XComponent

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_XCOMPONENT_ID

```c
NODE_XCOMPONENT_ID = MAX_NODE_SCOPE_NUM * ARKUI_NODE_XCOMPONENT
```

**Description**

Defines the ID of the <b><XComponent></b> component. This attribute can be set and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: component ID.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: component ID.</li> </ul>

**Since**: 12

### NODE_XCOMPONENT_TYPE

```c
NODE_XCOMPONENT_TYPE
```

**Description**

Specifies the type of the <b>XComponent</b> component. This attribute is read-only. The type of the <b>XComponent</b> component must be explicitly set during creation using[ARKUI_NODE_XCOMPONENT](capi-native-node-h.md#arkui_nodetype) or [ARKUI_NODE_XCOMPONENT_TEXTURE](capi-native-node-h.md#arkui_nodetype), and cannot be modified afterward. Attempting to change the type through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) will cause rendering exceptions.<br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: type [ArkUI_XComponentType](capi-xcomponent-h.md#arkui_xcomponenttype).</li> </ul>

**Since**: 12

### NODE_XCOMPONENT_SURFACE_SIZE

```c
NODE_XCOMPONENT_SURFACE_SIZE
```

**Description**

Specifies the size of the <b>XComponent</b> component. This attribute is read-only. Attempting to modify the size through [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) will have no effect.<br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: width, in px.</li> <li>.value[1].u32: height, in px.</li> </ul>

**Since**: 12

### NODE_XCOMPONENT_SURFACE_RECT

```c
NODE_XCOMPONENT_SURFACE_RECT
```

**Description**

Defines the rectangle information of surface created by the <b><XComponent></b> component. This attribute can be set and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: The horizontal offset of the surface relative to XComponent, in pixels.</li> <li>.value[1].i32: The vertical offset of the surface relative to XComponent, in pixels.</li> <li>.value[2].i32: The width of the surface created by XComponent, in pixels.</li> <li>.value[3].i32: The height of the surface created by XComponent, in pixels.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: The horizontal offset of the surface relative to XComponent, in pixels.</li> <li>.value[1].i32: The vertical offset of the surface relative to XComponent, in pixels.</li> <li>.value[2].i32: The width of the surface created by XComponent, in pixels.</li> <li>.value[3].i32: The height of the surface created by XComponent, in pixels.</li> </ul>

**Since**: 18

### NODE_XCOMPONENT_ENABLE_ANALYZER

```c
NODE_XCOMPONENT_ENABLE_ANALYZER
```

**Description**

Defines whether to enable the AI analyzer for the <b><XComponent></b> component. This attribute can be set and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: The parameter type is 1 or 0.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: The parameter type is 1 or 0.</li> </ul>

**Since**: 18


