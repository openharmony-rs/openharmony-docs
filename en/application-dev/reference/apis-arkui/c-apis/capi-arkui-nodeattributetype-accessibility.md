# Accessibility

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_ACCESSIBILITY_GROUP

```c
NODE_ACCESSIBILITY_GROUP
```

**Description**

Sets the accessibility group. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Accessibility group. The value <b>1</b> means that the component and all its child components form an entire selectable component.</li> <li>In this case, the accessibility service will no longer be available for the content of its child components.</li> <li>The value is <b>1</b> or <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Accessibility group. The value <b>1</b> means that the component and all its child components form an entire selectable component.</li> <li>In this case, the accessibility service will no longer be available for the content of its child components.</li> <li>The value is <b>1</b> or <b>0</b>.</li> </ul>

**Since**: 12

### NODE_ACCESSIBILITY_TEXT

```c
NODE_ACCESSIBILITY_TEXT
```

**Description**

Sets the accessibility text. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: accessibility text.</li> </ul>

**Since**: 12

### NODE_ACCESSIBILITY_MODE

```c
NODE_ACCESSIBILITY_MODE
```

**Description**

Sets the accessibility service model. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: accessibility service model. The parameter type is [ArkUI_AccessibilityMode](capi-native-type-h.md#arkui_accessibilitymode).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: accessibility service model. The parameter type is [ArkUI_AccessibilityMode](capi-native-type-h.md#arkui_accessibilitymode).</li> </ul>

**Since**: 12

### NODE_ACCESSIBILITY_DESCRIPTION

```c
NODE_ACCESSIBILITY_DESCRIPTION
```

**Description**

Sets the accessibility description. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: accessibility description.</li> </ul>

**Since**: 12

### NODE_ACCESSIBILITY_ID

```c
NODE_ACCESSIBILITY_ID = 87
```

**Description**

Accessible ID, which can be obtained as required through APIs.<br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Accessible ID.</li> </ul>

**Since**: 12

### NODE_ACCESSIBILITY_ACTIONS

```c
NODE_ACCESSIBILITY_ACTIONS = 88
```

**Description**

Define accessible actions, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: accessible action types, and uses the [ArkUI_AccessibilityActionType](capi-native-type-h.md#arkui_accessibilityactiontype) enumeration value.</li> </ul>

**Since**: 12

### NODE_ACCESSIBILITY_ROLE

```c
NODE_ACCESSIBILITY_ROLE = 89
```

**Description**

Define accessible role, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: accessible role type, and uses the [ArkUI_NodeType](capi-native-node-h.md#arkui_nodetype) enumeration value.</li> </ul>

**Since**: 12

### NODE_ACCESSIBILITY_STATE

```c
NODE_ACCESSIBILITY_STATE = 90
```

**Description**

Define accessible state, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: the parameter type is [ArkUI_AccessibilityState](capi-arkui-nativemodule-arkui-accessibilitystate.md).</li> </ul>

**Since**: 12

### NODE_ACCESSIBILITY_VALUE

```c
NODE_ACCESSIBILITY_VALUE = 91
```

**Description**

Define accessible value, which can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: the parameter type is [ArkUI_AccessibilityValue](capi-arkui-nativemodule-arkui-accessibilityvalue.md).</li> </ul>

**Since**: 12

### NODE_ACCESSIBILITY_NEXT_FOCUS_ID

```c
NODE_ACCESSIBILITY_NEXT_FOCUS_ID = 124
```

**Description**

Defines the next accessibility focus id of current component for accessibility processing to find the next focus component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.string: accessibility next focus ID.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.string: accessibility next focus ID.</li> </ul>

**Since**: 26.0.0

### NODE_ACCESSIBILITY_DEFAULT_FOCUS

```c
NODE_ACCESSIBILITY_DEFAULT_FOCUS = 125
```

**Description**

Sets the accessibility default focus flag for accessibility services to find the default focus component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: Accessibility default focus. The value <b>1</b> means that the component is defined as default focus in accessibility services.</li> <li>The value is <b>1</b> or <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: Accessibility default focus. The value <b>1</b> means that the component is defined as default focus in accessibility services.</li> <li>The value is <b>1</b> or <b>0</b>.</li> </ul>

**Since**: 26.0.0


