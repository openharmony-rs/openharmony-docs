# Text Input

## Overview

Enumerates the event types supported by the NativeNode component.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TEXT_INPUT_ON_CHANGE

```c
NODE_TEXT_INPUT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_INPUT
```

**Description**

Defines the event triggered when the text input content changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text input.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_SUBMIT

```c
NODE_TEXT_INPUT_ON_SUBMIT
```

**Description**

Event triggered when the **Enter** key on the keyboard is pressed for the **TextInput** component.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameter:**<br><ul> <li>**ArkUI_NodeComponentEvent.data[0].i32**: type of the **Enter** key.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_CUT

```c
NODE_TEXT_INPUT_ON_CUT
```

**Description**

Event triggered when the cut button on the clipboard, which displays when the text box is long pressed, is clicked.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameter:**<br><ul> <li>**ArkUI_StringAsyncEvent.pStr**: text to be cut.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_PASTE

```c
NODE_TEXT_INPUT_ON_PASTE
```

**Description**

Defines the event triggered when the paste button on the pasteboard, which displays when the text box is long pressed, is clicked.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text that is pasted.</li> </ul><br> Since 26.0.0, the callback can return whether the paste is allowed.

**Since**: 12

### NODE_TEXT_INPUT_ON_TEXT_SELECTION_CHANGE

```c
NODE_TEXT_INPUT_ON_TEXT_SELECTION_CHANGE
```

**Description**

Event triggered when the text selection position changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:**<br><ul> <li>**ArkUI_NodeComponentEvent.data[0].i32**: start position of the text selection range.</li> <li>**ArkUI_NodeComponentEvent.data[1].i32**: end position of the text selection range.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_EDIT_CHANGE

```c
NODE_TEXT_INPUT_ON_EDIT_CHANGE
```

**Description**

Event triggered when the input state changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameter:**<br><ul> <li>**ArkUI_NodeComponentEvent.data[0].i32**: **true** indicates that text input is in progress.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_CONTENT_SIZE_CHANGE

```c
NODE_TEXT_INPUT_ON_CONTENT_SIZE_CHANGE
```

**Description**

Event triggered when the text input content changes in the **TextInput** component.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:**<br><ul> <li>**ArkUI_NodeComponentEvent.data[0].f32**: width of the text.</li> <li>**ArkUI_NodeComponentEvent.data[1].f32**: height of the text.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_INPUT_FILTER_ERROR

```c
NODE_TEXT_INPUT_ON_INPUT_FILTER_ERROR
```

**Description**

Event triggered when matching with the regular expression specified by **NODE_TEXT_INPUT_INPUT_FILTER** fails.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameter:**<br><ul> <li>**ArkUI_StringAsyncEvent.pStr**: content that is filtered out when regular expression matching fails.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_CONTENT_SCROLL

```c
NODE_TEXT_INPUT_ON_CONTENT_SCROLL
```

**Description**

Event triggered when the text content is scrolled.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:**<br><ul> <li>**ArkUI_NodeComponentEvent.data[0].i32**: offset in the x-coordinate of the text in the content area.</li> <li>**ArkUI_NodeComponentEvent.data[1].i32**: offset in the y-coordinate of the text in the content area.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_WILL_INSERT

```c
NODE_TEXT_INPUT_ON_WILL_INSERT = 7009
```

**Description**

Event triggered when text is about to be entered.<br> When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). <ul> <li>value.f32 at index 0: position of the text to be inserted; obtained using <b>OH_ArkUI_NodeEvent_GetNumberValue</b>.</li> <li>buffer at index 0: text to be inserted; obtained using <b>OH_ArkUI_NodeEvent_GetStringValue</b>.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_DID_INSERT

```c
NODE_TEXT_INPUT_ON_DID_INSERT = 7010
```

**Description**

Event triggered when input is completed.<br> When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). <ul> <li>value.f32 at index 0: position of the text inserted; obtained using <b>OH_ArkUI_NodeEvent_GetNumberValue</b>.</li> <li>buffer at index 0: inserted text; obtained using <b>OH_ArkUI_NodeEvent_GetStringValue</b>.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_WILL_DELETE

```c
NODE_TEXT_INPUT_ON_WILL_DELETE = 7011
```

**Description**

Event triggered when text is about to be deleted.<br> When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). <ul> <li>value.f32 at index 0: position of the text to be deleted; obtained using <b>OH_ArkUI_NodeEvent_GetNumberValue</b>.</li> <li>value.i32: direction for deleting the text, with the index of <b>1</b>; obtained using <b>OH_ArkUI_NodeEvent_GetNumberValue</b>. The value <b>0</b> indicates backward-delete, and <b>1</b> indicates forward-delete.</li> <li>buffer at index 0: text to be deleted; obtained using <b>OH_ArkUI_NodeEvent_GetStringValue</b>.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_DID_DELETE

```c
NODE_TEXT_INPUT_ON_DID_DELETE = 7012
```

**Description**

Event triggered when deletion is completed.<br> When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). <ul> <li>value.f32 at index 0: position of the text deleted; obtained using <b>OH_ArkUI_NodeEvent_GetNumberValue</b>.</li> <li>value.i32: direction for deleting the text, with the index of <b>1</b>; obtained using <b>OH_ArkUI_NodeEvent_GetNumberValue</b>. The value <b>0</b> indicates backward-delete, and <b>1</b> indicates forward-delete.</li> <li>buffer at index 0: deleted text; obtained using <b>OH_ArkUI_NodeEvent_GetStringValue</b>.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_CHANGE_WITH_PREVIEW_TEXT

```c
NODE_TEXT_INPUT_ON_CHANGE_WITH_PREVIEW_TEXT = 7013
```

**Description**

Event triggered when content (including preview text) changes in the <b>TextInput</b> component.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md). **[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters:**<br><ul> <li>**ArkUI_TextChangeEvent.pStr**: content in the <b>TextInput</b> component.</li> <li>**ArkUI_TextChangeEvent.pExtendStr**: content of the preview text in the <b>TextInput</b> component.</li> <li>**ArkUI_TextChangeEvent.number**: start position of the preview text in the <b>TextInput</b> component.</li> </ul>

**Since**: 15

### NODE_TEXT_INPUT_ON_WILL_CHANGE

```c
NODE_TEXT_INPUT_ON_WILL_CHANGE = 7014
```

**Description**

Event triggered when content (including preview text) is about to change in the <b>TextInput</b> component.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md). **[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters:**<br><ul> <li>**ArkUI_TextChangeEvent.pStr**: content in the <b>TextInput</b> component.</li> <li>**ArkUI_TextChangeEvent.pExtendStr**: content of the preview text in the <b>TextInput</b> component.</li> <li>**ArkUI_TextChangeEvent.number**: start position of the preview text in the <b>TextInput</b> component.</li> </ul>

**Since**: 20

### NODE_TEXT_INPUT_ON_COPY

```c
NODE_TEXT_INPUT_ON_COPY = 7015
```

**Description**

Event triggered when the copy button on the clipboard, which displays when the user clicks text selection, is clicked.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameter:**<br><ul> <li>**ArkUI_StringAsyncEvent.pStr**: text to be copied.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_INPUT_ON_WILL_COPY

```c
NODE_TEXT_INPUT_ON_WILL_COPY = 7016
```

**Description**

Event triggered before text is copied.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameter:**<br><ul> <li>**ArkUI_StringAsyncEvent.pStr**: text to be copied.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_INPUT_ON_WILL_CUT

```c
NODE_TEXT_INPUT_ON_WILL_CUT = 7017
```

**Description**

Event triggered before text is cut.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameter:**<br><ul> <li>**ArkUI_StringAsyncEvent.pStr**: text to be cut.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_AREA_ON_CHANGE

```c
NODE_TEXT_AREA_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_AREA
```

**Description**

Defines the event triggered when the input in the text box changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text entered.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_PASTE

```c
NODE_TEXT_AREA_ON_PASTE
```

**Description**

Defines the event triggered when the paste button on the pasteboard, which displays when the text box is long pressed, is clicked.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text that is pasted.</li> </ul><br> Since 26.0.0, the callback can return whether the paste is allowed.

**Since**: 12

### NODE_TEXT_AREA_ON_TEXT_SELECTION_CHANGE

```c
NODE_TEXT_AREA_ON_TEXT_SELECTION_CHANGE
```

**Description**

Event triggered when the text selection position changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:**<br><ul> <li>**ArkUI_NodeComponentEvent.data[0].i32**: start position of the text selection range.</li> <li>**ArkUI_NodeComponentEvent.data[1].i32**: end position of the text selection range.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_INPUT_FILTER_ERROR

```c
NODE_TEXT_AREA_ON_INPUT_FILTER_ERROR
```

**Description**

Event triggered when matching with the regular expression specified by **NODE_TEXT_AREA_INPUT_FILTER** fails.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameter:**<br><ul> <li>**ArkUI_StringAsyncEvent.pStr**: content that is filtered out when regular expression matching fails.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_CONTENT_SCROLL

```c
NODE_TEXT_AREA_ON_CONTENT_SCROLL
```

**Description**

Event triggered when the text content is scrolled.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:**<br><ul> <li>**ArkUI_NodeComponentEvent.data[0].i32**: offset in the x-coordinate of the text in the content area.</li> <li>**ArkUI_NodeComponentEvent.data[1].i32**: offset in the y-coordinate of the text in the content area.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_EDIT_CHANGE

```c
NODE_TEXT_AREA_ON_EDIT_CHANGE
```

**Description**

Event triggered when the input state changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameter:**<br><ul> <li>**ArkUI_NodeComponentEvent.data[0].i32**: **true** indicates that text input is in progress.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_SUBMIT

```c
NODE_TEXT_AREA_ON_SUBMIT
```

**Description**

Event triggered when the **Enter** key on the keyboard is pressed for the **TextArea** component. It is not triggered when **keyType** is **ARKUI_ENTER_KEY_TYPE_NEW_LINE**.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameter:**<br><ul> <li>**ArkUI_NodeComponentEvent.data[0].i32**: type of the **Enter** key.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_CONTENT_SIZE_CHANGE

```c
NODE_TEXT_AREA_ON_CONTENT_SIZE_CHANGE
```

**Description**

Event triggered when the text input content changes in the **TextArea** component.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains the following parameters:**<br><ul> <li>**ArkUI_NodeComponentEvent.data[0].f32**: width of the text.</li> <li>**ArkUI_NodeComponentEvent.data[1].f32**: height of the text.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_WILL_INSERT

```c
NODE_TEXT_AREA_ON_WILL_INSERT = 8008
```

**Description**

Event triggered when text is about to be entered.<br> When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). <ul> <li>value.f32: position of the text to be inserted, with the index of <b>0</b>; obtained using <b>OH_ArkUI_NodeEvent_GetNumberValue</b>.</li> <li>buffer: string value of the text to be inserted, with the index of <b>0</b>; obtained using <b>OH_ArkUI_NodeEvent_GetStringValue</b>.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_DID_INSERT

```c
NODE_TEXT_AREA_ON_DID_INSERT = 8009
```

**Description**

Event triggered when input is completed.<br> When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). <ul> <li>value.f32: position of the text inserted, with the index of <b>0</b>; obtained using <b>OH_ArkUI_NodeEvent_GetNumberValue</b>.</li> <li>buffer: string value of the inserted text, with the index of <b>0</b>; obtained using <b>OH_ArkUI_NodeEvent_GetStringValue</b>.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_WILL_DELETE

```c
NODE_TEXT_AREA_ON_WILL_DELETE = 8010
```

**Description**

Event triggered when text is about to be deleted.<br> When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). <ul> <li>value.f32: position of the text to be deleted, with the index of <b>0</b>; obtained using <b>OH_ArkUI_NodeEvent_GetNumberValue</b>.</li> <li>value.i32: direction for deleting the text, with the index of <b>1</b>; obtained using <b>OH_ArkUI_NodeEvent_GetNumberValue</b>. The value <b>0</b> indicates backward-delete, and <b>1</b> indicates forward-delete.</li> <li>buffer: string value of the text to be deleted, with the index of <b>0</b>; obtained using <b>OH_ArkUI_NodeEvent_GetStringValue</b>.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_DID_DELETE

```c
NODE_TEXT_AREA_ON_DID_DELETE = 8011
```

**Description**

Event triggered when deletion is completed.<br> When the event callback occurs, the event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md). <ul> <li>value.f32: position of the text deleted, with the index of <b>0</b>; obtained using <b>OH_ArkUI_NodeEvent_GetNumberValue</b>.</li> <li>value.i32: direction for deleting the text, with the index of <b>1</b>; obtained using <b>OH_ArkUI_NodeEvent_GetNumberValue</b>. The value <b>0</b> indicates backward-delete, and <b>1</b> indicates forward-delete.</li> <li>buffer: string value of the deleted text, with the index of <b>0</b>; obtained using <b>OH_ArkUI_NodeEvent_GetStringValue</b>.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_CHANGE_WITH_PREVIEW_TEXT

```c
NODE_TEXT_AREA_ON_CHANGE_WITH_PREVIEW_TEXT = 8012
```

**Description**

Event triggered when content (including preview text) changes in the <b>TextArea</b> component.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md). **[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters:**<br><ul> <li>**ArkUI_TextChangeEvent.pStr**: content in the <b>TextArea</b> component.</li> <li>**ArkUI_TextChangeEvent.pExtendStr**: content of the preview text in the <b>TextArea</b> component.</li> <li>**ArkUI_TextChangeEvent.number**: start position of the preview text in the <b>TextArea</b> component.</li> </ul>

**Since**: 15

### NODE_TEXT_AREA_ON_WILL_CHANGE

```c
NODE_TEXT_AREA_ON_WILL_CHANGE = 8013
```

**Description**

Event triggered when content (including preview text) is about to change in the <b>TextArea</b> component.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md). **[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters:**<br><ul> <li>**ArkUI_TextChangeEvent.pStr**: content in the <b>TextArea</b> component.</li> <li>**ArkUI_TextChangeEvent.pExtendStr**: content of the preview text in the <b>TextArea</b> component.</li> <li>**ArkUI_TextChangeEvent.number**: start position of the preview text in the <b>TextArea</b> component.</li> </ul>

**Since**: 20

### NODE_TEXT_AREA_ON_COPY

```c
NODE_TEXT_AREA_ON_COPY = 8014
```

**Description**

Event triggered when the copy button on the clipboard, which displays when the text box is long pressed, is clicked. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text to be copied.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_AREA_ON_WILL_COPY

```c
NODE_TEXT_AREA_ON_WILL_COPY = 8015
```

**Description**

Event triggered before text is copied. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text to be copied.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_AREA_ON_CUT

```c
NODE_TEXT_AREA_ON_CUT = 8016
```

**Description**

Event triggered when the cut button on the clipboard, which displays when the internal area of the text box is long pressed, is clicked. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text to be cut.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_AREA_ON_WILL_CUT

```c
NODE_TEXT_AREA_ON_WILL_CUT = 8017
```

**Description**

Event triggered before text is cut. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains the following parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text to be cut.</li> </ul>

**Since**: 26.0.0


