# XComponent

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

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

Size of the surface held by the **XComponent** component. This attribute can only be obtained through APIs. If you attempt to modify the size of the surface by using the [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) API, the setting does not take effect.<br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: Width, in px.</li> <li>.value[1].u32: Height, in px.</li> </ul>

**Since**: 12

### NODE_XCOMPONENT_SURFACE_RECT

```c
NODE_XCOMPONENT_SURFACE_RECT
```

**Description**

Display area of the surface held by the **XComponent** component. This attribute can be set and obtained through APIs. It applies to scenarios where a partial area within the **XComponent** component needs to be specified for rendering, such as cropped video display and partial rendering in PiP mode.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: X-coordinate of the surface display area relative to the upper left corner of the **XComponent** component, in px.</li> <li>.value[1].i32: Y-coordinate of the surface display area relative to the upper left corner of the **XComponent** component, in px.</li> <li>.value[2].i32: Width of the surface display area, in px. The value must be a positive integer. The setting does not take effect when 0 or a negative number is passed.</li> <li>.value[3].i32: Height of the surface display area, in px. The value must be a positive integer. The setting does not take effect when 0 or a negative number is passed.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: X-coordinate of the surface display area relative to the upper left corner of the **XComponent** component, in px.</li> <li>.value[1].i32: Y-coordinate of the surface display area relative to the upper left corner of the **XComponent** component, in px.</li> <li>.value[2].i32: Width of the surface display area, in px. The value must be a non-negative integer.</li> <li>.value[3].i32: Height of the surface display area, in px.</li> </ul>

**Since**: 18

### NODE_XCOMPONENT_ENABLE_ANALYZER

```c
NODE_XCOMPONENT_ENABLE_ANALYZER
```

**Description**

Whether to enable the image analyzer for the **XComponent** component. This attribute can be set and obtained as required through APIs. When enabled, content recognition and analysis can be performed on the image displayed in the component. It applies to scenarios such as real-time recognition in camera preview and image content understanding.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Whether to enable the image analyzer. `1` indicates enable the image analyzer, and `0` indicates the opposite. The default value is `0`. Values other than 0 and 1 are treated as `0`.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Whether the image analyzer is enabled. `1` indicates that the image analyzer is supported, and `0` indicates the opposite.</li> </ul>

**Since**: 18

### NODE_XCOMPONENT_BUFFER_QUEUE_SIZE

```c
NODE_XCOMPONENT_BUFFER_QUEUE_SIZE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_XCOMPONENT + 5
```

**Description**

Defines the buffer queue size for the <b><XComponent></b> component. This attribute can be set, reset, and obtained as required through APIs. Only takes effect for XComponent of type SURFACE or TEXTURE.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>value[0].i32: Buffer queue size. The value ranges from 2 to 5. The default value is <b>5</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>value[0].i32: Buffer queue size.</li> </ul>

**Since**: 26.1.0


