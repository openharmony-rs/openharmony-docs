# 文本显示

## 概述

Enumerates the event types supported by the NativeNode component.

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_TEXT_ON_DETECT_RESULT_UPDATE

```c
NODE_TEXT_ON_DETECT_RESULT_UPDATE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT
```

**描述：**

文本设置TextDataDetectorConfig且识别成功时，触发onDetectResultUpdate回调。<br> 触发该事件的条件：文本设置TextDataDetectorConfig且识别成功后。 事件回调发生时，事件参数{@link ArkUI_NodeEvent}对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。<br>**[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)中包含1个参数：**<br><ul> <li>ArkUI_StringAsyncEvent.pStr：表示文本识别的结果，Json格式。</li> </ul>

**起始版本：** 12

### NODE_TEXT_SPAN_ON_LONG_PRESS

```c
NODE_TEXT_SPAN_ON_LONG_PRESS = 1001
```

**描述：**

Span组件长按事件。<br> 组件被长按时触发此回调。 事件回调发生时，可从事件参数{@link ArkUI_NodeEvent}对象中获取{@link ArkUI_UIInputEvent}。

**起始版本：** 20

### NODE_TEXT_ON_TEXT_SELECTION_CHANGE

```c
NODE_TEXT_ON_TEXT_SELECTION_CHANGE = 1002
```

**描述：**

定义文本选择位置改变时触发的事件。 当事件回调发生时，{@link ArkUI_NodeEvent}对象中的联合体类型为 [ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。<br>[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)包含两个参数：<br><b>ArkUI_NodeComponentEvent.data[0].i32</b>：文本选择区域的起始位置。<br><b>ArkUI_NodeComponentEvent.data[1].i32</b>：文本选择区域的结束位置。

**起始版本：** 26.0.0

### NODE_TEXT_ON_COPY

```c
NODE_TEXT_ON_COPY = 1003
```

**描述：**

定义长按输入框时显示的剪贴板上的复制按钮被点击时触发的事件。<br> 当事件回调发生时，{@link ArkUI_NodeEvent}对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。 <br>**[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)包含一个参数：**<br><ul> <li>ArkUI_StringAsyncEvent.pStr：复制的文本。</li> </ul>

**起始版本：** 26.0.0

### NODE_TEXT_ON_WILL_COPY

```c
NODE_TEXT_ON_WILL_COPY = 1004
```

**描述：**

定义复制文本前触发的事件。<br> 当事件回调发生时，{@link ArkUI_NodeEvent}对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。 <br>**[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)包含一个参数：**<br><ul> <li>ArkUI_StringAsyncEvent.pStr：复制的文本。</li> </ul>

**起始版本：** 26.0.0


