# Text Editor

## Overview

Enumerates the event types supported by the NativeNode component.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TEXT_EDITOR_ON_SELECTION_CHANGE

```c
NODE_TEXT_EDITOR_ON_SELECTION_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_EDITOR
```

**Description**

Event triggered when the selection or cursor position in the **TextEditor** component changes. <br>When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: start index of the selection.</li><br><li>ArkUI_NodeComponentEvent.data[1].i32: end index of the selection.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_ON_READY

```c
NODE_TEXT_EDITOR_ON_READY
```

**Description**

Event triggered when the first initialization of the **TextEditor** component is complete. <br>When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).

**Since**: 24

### NODE_TEXT_EDITOR_ON_PASTE

```c
NODE_TEXT_EDITOR_ON_PASTE
```

**Description**

Event triggered when the **TextEditor** component pastes content. <br>The system determines whether to intercept the default behavior of the component based on the return value of the callback function. <br>You can use [OH_ArkUI_NodeEvent_SetReturnNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_setreturnnumbervalue) to set the return value. <br>**value.i32**: whether to intercept the default behavior of the component, with the index of **0**. <br>**0**: not intercept. **1**: intercept.

**Since**: 24

### NODE_TEXT_EDITOR_ON_EDITING_CHANGE

```c
NODE_TEXT_EDITOR_ON_EDITING_CHANGE
```

**Description**

Event triggered when the editing status of the **TextEditor** component changes. <br>When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameter:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: editing status of the component.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_ON_SUBMIT

```c
NODE_TEXT_EDITOR_ON_SUBMIT
```

**Description**

Event triggered when the **Enter** key on the keyboard is pressed for the **TextEditor** component. <br>When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameter:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: type of the Enter key, specified using {@link ArkUI_EnterKeyType}.</li> </ul>

**Since**: 24

### NODE_TEXT_EDITOR_ON_CUT

```c
NODE_TEXT_EDITOR_ON_CUT
```

**Description**

Event triggered when the **TextEditor** component cuts content. <br>The system determines whether to intercept the default behavior of the component based on the return value of the callback function. <br>You can use [OH_ArkUI_NodeEvent_SetReturnNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_setreturnnumbervalue) to set the return value. <br>**value.i32**: whether to intercept the default behavior of the component, with the index of **0**. <br>**0**: not intercept. **1**: intercept.

**Since**: 24

### NODE_TEXT_EDITOR_ON_COPY

```c
NODE_TEXT_EDITOR_ON_COPY
```

**Description**

Event triggered when the **TextEditor** component copies content. <br>The system determines whether to intercept the default behavior of the component based on the return value of the callback function. <br>You can use [OH_ArkUI_NodeEvent_SetReturnNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_setreturnnumbervalue) to set the return value. <br>**value.i32**: whether to intercept the default behavior of the component, with the index of **0**. <br>**0**: not intercept. **1**: intercept.

**Since**: 24

### NODE_TEXT_EDITOR_ON_WILL_CHANGE

```c
NODE_TEXT_EDITOR_ON_WILL_CHANGE
```

**Description**

Event triggered when the **TextEditor** component is about to change the content. <br>This callback is triggered before any operation that causes a text content change takes effect. You can determine whether to intercept the content change based on the information in the callback event. <br>When the event callback occurs, you can obtain the [OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md) object from the<br>{@link ArkUI_NodeEvent} object by calling [OH_ArkUI_NodeEvent_GetTextEditorOnWillChangeEvent](capi-native-node-h.md#oh_arkui_nodeevent_gettexteditoronwillchangeevent).<br><br>Then, you can use the **OH_ArkUI_TextEditorChangeEvent_***XXX* series APIs to obtain more information from<br>this object.<br><br>The system determines whether the current content can be changed based on the return value of the callback<br>function.<br><br>You can use [OH_ArkUI_NodeEvent_SetReturnNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_setreturnnumbervalue) to set the return value. <br>**value.i32** whose **index** is set to **0** indicates whether the current content can be changed. **0**: The content cannot be changed. **1**: The content can be changed.

**Since**: 24

### NODE_TEXT_EDITOR_ON_DID_CHANGE

```c
NODE_TEXT_EDITOR_ON_DID_CHANGE
```

**Description**

Event triggered when the **TextEditor** component changes the content. <br>When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md).<br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: start index of the text range to be replaced before the text changes.</li><br><li>ArkUI_NodeComponentEvent.data[1].i32: end index of the text range to be replaced before the text changes.</li><br><li>ArkUI_NodeComponentEvent.data[2].i32: start index of the text range of the new content after the text changes.</li><br><li>ArkUI_NodeComponentEvent.data[3].i32: end index of the text range of the new content after the text changes.</li> </ul>

**Since**: 24


