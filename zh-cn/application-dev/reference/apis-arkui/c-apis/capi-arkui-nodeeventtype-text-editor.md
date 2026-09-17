# 富文本

## 概述

Enumerates the event types supported by the NativeNode component.

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_TEXT_EDITOR_ON_SELECTION_CHANGE

```c
NODE_TEXT_EDITOR_ON_SELECTION_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_EDITOR
```

**描述：**

定义TextEditor组件中选区或光标位置发生变化时触发的事件。 <br>事件回调触发时，{@link ArkUI_NodeEvent}对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br><br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含两个参数：<br><br><b>ArkUI_NodeComponentEvent.data[0].i32</b>：选区起始索引。<br><br><b>ArkUI_NodeComponentEvent.data[1].i32</b>：选区结束索引。

**起始版本：** 24

### NODE_TEXT_EDITOR_ON_READY

```c
NODE_TEXT_EDITOR_ON_READY
```

**描述：**

定义TextEditor组件首次初始化完成时触发的事件。 <br>事件回调触发时，{@link ArkUI_NodeEvent}对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。

**起始版本：** 24

### NODE_TEXT_EDITOR_ON_PASTE

```c
NODE_TEXT_EDITOR_ON_PASTE
```

**描述：**

定义TextEditor组件执行粘贴时触发的事件。<br> 系统会根据回调函数返回值判断是否拦截组件的默认行为。 可通过[OH_ArkUI_NodeEvent_SetReturnNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_setreturnnumbervalue)设置返回值。 返回值中索引为0的value.i32表示是否拦截组件的默认行为。 0：不拦截。1：拦截。

**起始版本：** 24

### NODE_TEXT_EDITOR_ON_EDITING_CHANGE

```c
NODE_TEXT_EDITOR_ON_EDITING_CHANGE
```

**描述：**

定义TextEditor组件编辑状态发生变化时触发的事件。 <br>事件回调触发时，{@link ArkUI_NodeEvent}对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br><br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含一个参数：<br><br><b>ArkUI_NodeComponentEvent.data[0].i32</b>：组件的编辑状态。

**起始版本：** 24

### NODE_TEXT_EDITOR_ON_SUBMIT

```c
NODE_TEXT_EDITOR_ON_SUBMIT
```

**描述：**

定义TextEditor组件输入法的回车键被按下时触发的事件。 <br>事件回调触发时，{@link ArkUI_NodeEvent}对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br><br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含一个参数：<br><br><b>ArkUI_NodeComponentEvent.data[0].i32</b>：输入法的回车键类型{@link ArkUI_EnterKeyType}。

**起始版本：** 24

### NODE_TEXT_EDITOR_ON_CUT

```c
NODE_TEXT_EDITOR_ON_CUT
```

**描述：**

定义TextEditor组件执行剪切时触发的事件。<br> 系统会根据回调函数返回值判断是否拦截组件的默认行为。 可通过[OH_ArkUI_NodeEvent_SetReturnNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_setreturnnumbervalue)设置返回值。 返回值中索引为0的value.i32表示是否拦截组件的默认行为。 0：不拦截。1：拦截。

**起始版本：** 24

### NODE_TEXT_EDITOR_ON_COPY

```c
NODE_TEXT_EDITOR_ON_COPY
```

**描述：**

定义TextEditor组件执行复制时触发的事件。<br> 系统会根据回调函数返回值判断是否拦截组件的默认行为。 可通过[OH_ArkUI_NodeEvent_SetReturnNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_setreturnnumbervalue)设置返回值。 返回值中索引为0的value.i32表示是否拦截组件的默认行为。 0：不拦截。1：拦截。

**起始版本：** 24

### NODE_TEXT_EDITOR_ON_WILL_CHANGE

```c
NODE_TEXT_EDITOR_ON_WILL_CHANGE
```

**描述：**

定义TextEditor组件在内容将要改变时触发的事件。 <br>在任何导致文本内容发生变化的操作生效之前会触发该回调，开发者可根据回调事件中的信息决定是否拦截本次内容变更。 <br>当事件回调发生时，可以通过[OH_ArkUI_NodeEvent_GetTextEditorOnWillChangeEvent](capi-native-node-h.md#oh_arkui_nodeevent_gettexteditoronwillchangeevent)从{@link ArkUI_NodeEvent}对象中获得<br>[OH_ArkUI_TextEditorChangeEvent](capi-arkui-nativemodule-oh-arkui-texteditorchangeevent.md)对象。<br><br>使用OH_ArkUI_TextEditorChangeEvent_XXX系列接口可以从该对象中获取更多信息。<br><br>系统会根据回调函数返回值判断当前内容是否允许被更改。<br><br>可通过[OH_ArkUI_NodeEvent_SetReturnNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_setreturnnumbervalue)设置返回值。 <br>返回值中索引为0的value.i32表示当前内容是否允许被更改。<b>0</b>：不允许更改。<b>1</b>：允许更改。

**起始版本：** 24

### NODE_TEXT_EDITOR_ON_DID_CHANGE

```c
NODE_TEXT_EDITOR_ON_DID_CHANGE
```

**描述：**

定义TextEditor组件在内容改变时触发的事件。 <br>事件回调触发时，{@link ArkUI_NodeEvent}对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br><br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含四个参数：<br><br><b>ArkUI_NodeComponentEvent.data[0].i32</b>：文本变化前将要被替换的文本范围的起始索引。<br><br><b>ArkUI_NodeComponentEvent.data[1].i32</b>：文本变化前将要被替换的文本范围的结束索引。<br><br><b>ArkUI_NodeComponentEvent.data[2].i32</b>：文本变化后新增内容的文本范围的起始索引。<br><br><b>ArkUI_NodeComponentEvent.data[3].i32</b>：文本变化后新增内容的文本范围的结束索引。

**起始版本：** 24


