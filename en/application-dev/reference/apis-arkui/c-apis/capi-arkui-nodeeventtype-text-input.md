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

Defines the event triggered when the Enter key of the text input method is pressed.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: Enter key type of the input method.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_CUT

```c
NODE_TEXT_INPUT_ON_CUT
```

**Description**

Defines the event triggered when the cut button on the pasteboard, which displays when the text box is long pressed, is clicked.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text that is cut.</li> </ul>

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

Defines the event triggered when the text selection position changes. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: start position of the text selection area.</li> <li>ArkUI_NodeComponentEvent.data[1].i32: end position of the text selection area.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_EDIT_CHANGE

```c
NODE_TEXT_INPUT_ON_EDIT_CHANGE
```

**Description**

Defines the event triggered when the input status changes. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: true indicates that text input is in progress.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_CONTENT_SIZE_CHANGE

```c
NODE_TEXT_INPUT_ON_CONTENT_SIZE_CHANGE
```

**Description**

textInput This event is triggered when the input content changes.<br> Conditions for triggering this event: When the input content changes. When the event callback occurs, the union type in the event parameter [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains 2 parameters:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].f32: Indicates the width of the text.</li> <li>ArkUI_NodeComponentEvent.data[1].f32: Indicates the height of the text.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_INPUT_FILTER_ERROR

```c
NODE_TEXT_INPUT_ON_INPUT_FILTER_ERROR
```

**Description**

Defines the event triggered when matching with the regular expression specified by <b>NODE_TEXT_INPUT_INPUT_FILTER</b> fails.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: content that is filtered out when regular expression matching fails.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_CONTENT_SCROLL

```c
NODE_TEXT_INPUT_ON_CONTENT_SCROLL
```

**Description**

This callback is triggered when the text content is scrolled.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: Indicates the horizontal offset of the text in the content area.</li> <li>ArkUI_NodeComponentEvent.data[1].i32: Indicates the vertical coordinate offset of the text in the content area.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_WILL_INSERT

```c
NODE_TEXT_INPUT_ON_WILL_INSERT = 7009
```

**Description**

Defines the event triggered when text is about to be entered.<br> **The event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md).**<br><ul> <li>value.f32: position of the text, with the index of 0; obtained using OH_ArkUI_NodeEvent_GetNumberValue.</li> <li>buffer: string value of the text, with the index of 0; obtained using OH_ArkUI_NodeEvent_GetStringValue.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_DID_INSERT

```c
NODE_TEXT_INPUT_ON_DID_INSERT = 7010
```

**Description**

Defines the event triggered when text is entered.<br> **The event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md).**<br><ul> <li>value.f32: position of the text, with the index of 0; obtained using OH_ArkUI_NodeEvent_GetNumberValue.</li> <li>buffer: string value of the text, with the index of 0; obtained using OH_ArkUI_NodeEvent_GetStringValue.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_WILL_DELETE

```c
NODE_TEXT_INPUT_ON_WILL_DELETE = 7011
```

**Description**

Defines the event triggered when text is about to be deleted.<br> **The event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md).**<br><ul> <li>value.f32: position of the text to delete, with the index of 0; obtained using OH_ArkUI_NodeEvent_GetNumberValue.</li> <li>value.i32: direction for deleting the text, with the index of 1; obtained using OH_ArkUI_NodeEvent_GetNumberValue. The value 0 indicates backward-delete, and 1 indicates forward-delete.</li> <li>buffer: string value of the text, with the index of 0; obtained using OH_ArkUI_NodeEvent_GetStringValue.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_DID_DELETE

```c
NODE_TEXT_INPUT_ON_DID_DELETE = 7012
```

**Description**

Defines the event triggered when text is deleted.<br> **The event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md).**<br><ul> <li>value.f32: position of the text deleted, with the index of 0; obtained using OH_ArkUI_NodeEvent_GetNumberValue.</li> <li>value.i32: direction for deleting the text, with the index of 1; obtained using OH_ArkUI_NodeEvent_GetNumberValue. The value 0 indicates backward-delete, and 1 indicates forward-delete.</li> <li>buffer: string value of the text, with the index of 0; obtained using OH_ArkUI_NodeEvent_GetStringValue.</li> </ul>

**Since**: 12

### NODE_TEXT_INPUT_ON_CHANGE_WITH_PREVIEW_TEXT

```c
NODE_TEXT_INPUT_ON_CHANGE_WITH_PREVIEW_TEXT = 7013
```

**Description**

Defines the event triggered when content (including preview text) changes in the <b>TextInput</b> component.<br> When the event callback occurs, the union type [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md). **[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters:**<br><ul> <li>ArkUI_TextChangeEvent.pStr: content in the TextInput component.</li> <li>ArkUI_TextChangeEvent.pExtendStr: content of the preview text in the TextInput component. ArkUI_TextChangeEvent.number: start position of the preview text in the TextInput component.</li> </ul>

**Since**: 15

### NODE_TEXT_INPUT_ON_WILL_CHANGE

```c
NODE_TEXT_INPUT_ON_WILL_CHANGE = 7014
```

**Description**

Defines the event triggered before content changes<br> When the event callback occurs, the union type [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md). **[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters:**<br><ul> <li>ArkUI_TextChangeEvent.pStr: content in the TextInput component.</li> <li>ArkUI_TextChangeEvent.pExtendStr: content of the preview text in the TextInput component. ArkUI_TextChangeEvent.number: start position of the preview text in the TextInput component.</li> </ul>

**Since**: 20

### NODE_TEXT_INPUT_ON_COPY

```c
NODE_TEXT_INPUT_ON_COPY = 7015
```

**Description**

Defines the event triggered when the copy button on the pasteboard, which displays when text is selected, is clicked. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text that is copied.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_INPUT_ON_WILL_COPY

```c
NODE_TEXT_INPUT_ON_WILL_COPY = 7016
```

**Description**

Defines the event triggered before copying text. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text that is copied.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_INPUT_ON_WILL_CUT

```c
NODE_TEXT_INPUT_ON_WILL_CUT = 7017
```

**Description**

Defines the event triggered before cutting text. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text that is cut.</li> </ul>

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

Defines the event triggered when the text selection position changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: start position of the text selection area.</li> <li>ArkUI_NodeComponentEvent.data[1].i32: end position of the text selection area.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_INPUT_FILTER_ERROR

```c
NODE_TEXT_AREA_ON_INPUT_FILTER_ERROR
```

**Description**

Defines the event triggered when matching with the regular expression specified by <b>NODE_TEXT_AREA_INPUT_FILTER</b> fails.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: content that is filtered out when regular expression matching fails.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_CONTENT_SCROLL

```c
NODE_TEXT_AREA_ON_CONTENT_SCROLL
```

**Description**

This callback is triggered when the text content is scrolled.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: Indicates the horizontal offset of the text in the content area.</li> <li>ArkUI_NodeComponentEvent.data[1].i32: Indicates the vertical coordinate offset of the text in the content area.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_EDIT_CHANGE

```c
NODE_TEXT_AREA_ON_EDIT_CHANGE
```

**Description**

Defines the event triggered when the input status changes.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: true indicates that text input is in progress.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_SUBMIT

```c
NODE_TEXT_AREA_ON_SUBMIT
```

**Description**

Defines the event triggered when the Enter key on the keyboard is pressed for the multi-line text box.<br> This event is not triggered when <b>keyType</b> is <b>ARKUI_ENTER_KEY_TYPE_NEW_LINE</b>. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains one parameter:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32: type of the Enter key.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_CONTENT_SIZE_CHANGE

```c
NODE_TEXT_AREA_ON_CONTENT_SIZE_CHANGE
```

**Description**

textArea This event is triggered when the input content changes.<br> Conditions for triggering this event: When the input content changes. When the event callback occurs, the union type in the event parameter [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains 2 parameters:**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].f32: Indicates the width of the text.</li> <li>ArkUI_NodeComponentEvent.data[1].f32: Indicates the height of the text.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_WILL_INSERT

```c
NODE_TEXT_AREA_ON_WILL_INSERT = 8008
```

**Description**

Defines the event triggered when text is about to be entered.<br> **The event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md).**<br><ul> <li>value.f32: position of the text, with the index of 0; obtained using OH_ArkUI_NodeEvent_GetNumberValue.</li> <li>buffer: string value of the text, with the index of 0; obtained using OH_ArkUI_NodeEvent_GetStringValue.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_DID_INSERT

```c
NODE_TEXT_AREA_ON_DID_INSERT = 8009
```

**Description**

Defines the event triggered when text is entered.<br> **The event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md).**<br><ul> <li>value.f32: position of the text, with the index of 0; obtained using OH_ArkUI_NodeEvent_GetNumberValue.</li> <li>buffer: string value of the text, with the index of 0; obtained using OH_ArkUI_NodeEvent_GetStringValue.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_WILL_DELETE

```c
NODE_TEXT_AREA_ON_WILL_DELETE = 8010
```

**Description**

Defines the event triggered when text is about to be deleted.<br> **The event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md).**<br><ul> <li>value.f32: position of the text to delete, with the index of 0; obtained using OH_ArkUI_NodeEvent_GetNumberValue.</li> <li>value.i32: direction for deleting the text, with the index of 1; obtained using OH_ArkUI_NodeEvent_GetNumberValue. The value 0 indicates backward-delete, and 1 indicates forward-delete.</li> <li>buffer: string value of the text, with the index of 0; obtained using OH_ArkUI_NodeEvent_GetStringValue.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_DID_DELETE

```c
NODE_TEXT_AREA_ON_DID_DELETE = 8011
```

**Description**

Defines the event triggered when text is deleted.<br> **The event parameter is [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md).**<br><ul> <li>value.f32: position of the text deleted, with the index of 0; obtained using OH_ArkUI_NodeEvent_GetNumberValue.</li> <li>value.i32: direction for deleting the text, with the index of 1; obtained using OH_ArkUI_NodeEvent_GetNumberValue. The value 0 indicates backward-delete, and 1 indicates forward-delete.</li> <li>buffer: string value of the text, with the index of 0; obtained using OH_ArkUI_NodeEvent_GetStringValue.</li> </ul>

**Since**: 12

### NODE_TEXT_AREA_ON_CHANGE_WITH_PREVIEW_TEXT

```c
NODE_TEXT_AREA_ON_CHANGE_WITH_PREVIEW_TEXT = 8012
```

**Description**

Defines the event triggered when content (including preview text) changes in the <b>TextArea</b> component.<br> When the event callback occurs, the union type [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md). **[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters:**<br><ul> <li>ArkUI_TextChangeEvent.pStr: content in the TextArea component.</li> <li>ArkUI_TextChangeEvent.pExtendStr: content of the preview text in the TextArea component. ArkUI_TextChangeEvent.number: start position of the preview text in the TextArea component.</li> </ul>

**Since**: 15

### NODE_TEXT_AREA_ON_WILL_CHANGE

```c
NODE_TEXT_AREA_ON_WILL_CHANGE = 8013
```

**Description**

Defines the event triggered before content changes.<br> When the event callback occurs, the union type [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) is [ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md). **[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md) contains the following parameters:**<br><ul> <li>ArkUI_TextChangeEvent.pStr: content in the TextArea component.</li> <li>ArkUI_TextChangeEvent.pExtendStr: content of the preview text in the TextArea component. ArkUI_TextChangeEvent.number: start position of the preview text in the TextArea component.</li> </ul>

**Since**: 20

### NODE_TEXT_AREA_ON_COPY

```c
NODE_TEXT_AREA_ON_COPY = 8014
```

**Description**

Defines the event triggered when the copy button on the pasteboard, which displays when the text box is long pressed, is clicked. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text that is copied.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_AREA_ON_WILL_COPY

```c
NODE_TEXT_AREA_ON_WILL_COPY = 8015
```

**Description**

Defines the event triggered before copying text.<br> When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text that is copied.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_AREA_ON_CUT

```c
NODE_TEXT_AREA_ON_CUT = 8016
```

**Description**

Defines the event triggered when the cut button on the pasteboard, which displays when the text box is long pressed, is clicked. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text that is cut.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_AREA_ON_WILL_CUT

```c
NODE_TEXT_AREA_ON_WILL_CUT = 8017
```

**Description**

Defines the event triggered before cutting text. When the event callback occurs, the union type in the [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text that is cut.</li> </ul>

**Since**: 26.0.0


