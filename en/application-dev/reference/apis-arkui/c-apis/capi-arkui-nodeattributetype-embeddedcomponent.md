# EmbeddedComponent

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_EMBEDDED_COMPONENT_WANT

```c
NODE_EMBEDDED_COMPONENT_WANT = MAX_NODE_SCOPE_NUM * ARKUI_NODE_EMBEDDED_COMPONENT
```

**Description**

Defines the want used to start EmbeddedAbility. This attribute can be set as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: The want of EmbeddedComponent, with parameter type {@AbilityBase_Want}.</li> <li>The default value is <b>nullptr</b>.</li> </ul>

**Since**: 20

### NODE_EMBEDDED_COMPONENT_OPTION

```c
NODE_EMBEDDED_COMPONENT_OPTION
```

**Description**

Set onError and onTerminated callbacks for EMBEDDED_COMPONENT. This attribute can be set as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: The option for EmbeddedComponent, with parameter type {@ArkUI_EmbeddedComponentOption}.</li> </ul>

**Since**: 20


