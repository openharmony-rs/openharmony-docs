# EmbeddedComponent

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_EMBEDDED_COMPONENT_WANT

```c
NODE_EMBEDDED_COMPONENT_WANT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_EMBEDDED_COMPONENT
```

**Description**

Defines the want used to start EmbeddedUIExtensionAbility. This attribute can be set as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: The want of EmbeddedComponent, with parameter type {@AbilityBase_Want}.</li> <li>The default value is <b>nullptr</b>.</li> </ul>

**Since**: 20

### NODE_EMBEDDED_COMPONENT_OPTION

```c
NODE_EMBEDDED_COMPONENT_OPTION
```

**Description**

Runtime option of **EmbeddedComponent**, which is used to control the UI display behavior of the EmbeddedAbility. This attribute can be set.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: List of options for **EmbeddedComponent**. The parameter type is [ArkUI_EmbeddedComponentOption](capi-arkui-nativemodule-arkui-embeddedcomponentoption.md). The default value is **nullptr**.</li> </ul>

**Since**: 20


