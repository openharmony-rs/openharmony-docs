# Text Display

## Overview

Enumerates the event types supported by the NativeNode component.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_TEXT_ON_DETECT_RESULT_UPDATE

```c
NODE_TEXT_ON_DETECT_RESULT_UPDATE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT
```

**Description**

Triggers onDetectResultUpdate callback when the text is set to TextDataDetectorConfig and recognized successfully.<br> Trigger this event when TextDataDetectorConfig is set and recognized successfully. When the event callback occurs, the event parameter{@link ArkUI_NodeEvent}The union type in the object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md).<br>**[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)contains 1 parameter**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: Indicates the result of text recognition, in Json format.</li> </ul>

**Since**: 12

### NODE_TEXT_SPAN_ON_LONG_PRESS

```c
NODE_TEXT_SPAN_ON_LONG_PRESS = 1001
```

**Description**

Defines the long press event for span.<br> The event is triggered when the span is long pressed. When the event callback occurs, the {@link ArkUI_NodeEvent} object can be obtained from the<br>{@link ArkUI_UIInputEvent} object.

**Since**: 20

### NODE_TEXT_ON_TEXT_SELECTION_CHANGE

```c
NODE_TEXT_ON_TEXT_SELECTION_CHANGE = 1002
```

**Description**

Defines the event triggered when the text selection position changes. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md). <br>**[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md) contains two parameters:**<br><ul><br><li>ArkUI_NodeComponentEvent.data[0].i32: start position of the text selection area.</li><br><li>ArkUI_NodeComponentEvent.data[1].i32: end position of the text selection area.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_ON_COPY

```c
NODE_TEXT_ON_COPY = 1003
```

**Description**

Defines the event triggered when the copy button on the pasteboard, which displays when the text box is long pressed, is clicked. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br>**[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text that is copied.</li> </ul>

**Since**: 26.0.0

### NODE_TEXT_ON_WILL_COPY

```c
NODE_TEXT_ON_WILL_COPY = 1004
```

**Description**

Defines the event triggered before copying text. When the event callback occurs, the union type in the {@link ArkUI_NodeEvent} object is [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md). <br>**[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md) contains one parameter:**<br><ul> <li>ArkUI_StringAsyncEvent.pStr: text that is copied.</li> </ul>

**Since**: 26.0.0


