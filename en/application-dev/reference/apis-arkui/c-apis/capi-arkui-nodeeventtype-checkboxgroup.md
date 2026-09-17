# CheckboxGroup

## Overview

Enumerates the event types supported by the NativeNode component.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_CHECKBOX_GROUP_EVENT_ON_CHANGE

```c
NODE_CHECKBOX_GROUP_EVENT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_CHECKBOX_GROUP
```

**Description**

Defines the callback triggered when the selected status of the <b>ARKUI_NODE_CHECKBOX_GROOUP</b> or checkbox changes.<br> When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <b>ArkUI_StringAsyncEvent.pStr</b> Name: The names of the selected checkboxes; **Status:**<br><ul> <li>0: All checkboxes are selected.</li> <li>1: Some checkboxes are selected.</li> <li>2: No checkboxes are selected.</li> </ul>

**Since**: 15


