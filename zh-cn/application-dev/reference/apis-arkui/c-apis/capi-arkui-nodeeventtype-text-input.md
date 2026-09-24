# 文本输入

## 概述

Enumerates the event types supported by the NativeNode component.

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_TEXT_INPUT_ON_CHANGE

```c
NODE_TEXT_INPUT_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_INPUT
```

**描述：**

TextInput输入内容发生变化时触发该事件。<br> 触发该事件的条件：输入内容发生变化时。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。 **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)中包含1个参数：**<br><ul> <li>ArkUI_StringAsyncEvent.pStr：输入的文本内容。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_ON_SUBMIT

```c
NODE_TEXT_INPUT_ON_SUBMIT
```

**描述：**

TextInput按下输入法回车键触发该事件。<br> 触发该事件的条件：按下输入法回车键。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32：输入法回车键类型。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_ON_CUT

```c
NODE_TEXT_INPUT_ON_CUT
```

**描述：**

长按输入框内部区域弹出剪贴板后，点击剪切板剪切按钮，触发该回调。<br> 触发该事件的条件：长按输入框内部区域弹出剪贴板后，点击剪切板剪切按钮。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。 **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)中包含1个参数：**<br><ul> <li>ArkUI_StringAsyncEvent.pStr：剪切的文本内容。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_ON_PASTE

```c
NODE_TEXT_INPUT_ON_PASTE
```

**描述：**

长按输入框内部区域弹出剪贴板后，点击剪切板粘贴按钮，触发该回调。<br> 触发该事件的条件：长按输入框内部区域弹出剪贴板后，点击剪切板粘贴按钮。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。 **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)中包含1个参数：**<br><ul> <li>ArkUI_StringAsyncEvent.pStr：粘贴的文本内容。</li> </ul><br> 从API版本26.0.0开始，回调函数可以返回是否允许粘贴。

**起始版本：** 12

### NODE_TEXT_INPUT_ON_TEXT_SELECTION_CHANGE

```c
NODE_TEXT_INPUT_ON_TEXT_SELECTION_CHANGE
```

**描述：**

文本选择的位置发生变化时，触发该回调。<br> 触发该事件的条件：文本选择的位置发生变化时。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32：表示所选文本的起始位置。</li> <li>ArkUI_NodeComponentEvent.data[1].i32：表示所选文本的结束位置。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_ON_EDIT_CHANGE

```c
NODE_TEXT_INPUT_ON_EDIT_CHANGE
```

**描述：**

输入状态变化时，触发该回调。<br> 触发该事件的条件：输入状态变化时。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32：true表示正在输入。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_ON_CONTENT_SIZE_CHANGE

```c
NODE_TEXT_INPUT_ON_CONTENT_SIZE_CHANGE
```

**描述：**

TextInput输入内容发生变化时触发该事件。<br> 触发该事件的条件：输入内容发生变化时。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].f32：表示文本的宽度。</li> <li>ArkUI_NodeComponentEvent.data[1].f32：表示文本的高度。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_ON_INPUT_FILTER_ERROR

```c
NODE_TEXT_INPUT_ON_INPUT_FILTER_ERROR
```

**描述：**

设置NODE_TEXT_INPUT_INPUT_FILTER，正则匹配失败时触发。<br> 触发该事件的条件：正则匹配失败时。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。 **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)中包含1个参数：**<br><ul> <li>ArkUI_StringAsyncEvent.pStr：表示正则匹配失败时，被过滤的内容。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_ON_CONTENT_SCROLL

```c
NODE_TEXT_INPUT_ON_CONTENT_SCROLL
```

**描述：**

文本内容滚动时，触发该回调。<br> 触发该事件的条件：文本内容滚动时。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32：表示文本在内容区的横坐标偏移。</li> <li>ArkUI_NodeComponentEvent.data[1].i32：表示文本在内容区的纵坐标偏移。</li> </ul>

**起始版本：** 12

### NODE_TEXT_INPUT_ON_WILL_INSERT

```c
NODE_TEXT_INPUT_ON_WILL_INSERT = 7009
```

**描述：**

定义在将要输入时，触发回调的枚举值。<br> 事件回调发生时，事件参数为[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为0的value.f32：插入的值的位置信息。 通过[OH_ArkUI_NodeEvent_GetStringValue](capi-native-node-h.md#oh_arkui_nodeevent_getstringvalue)获取到index为0的buffer字符串：插入的值。

**起始版本：** 12

### NODE_TEXT_INPUT_ON_DID_INSERT

```c
NODE_TEXT_INPUT_ON_DID_INSERT = 7010
```

**描述：**

定义在输入完成时，触发回调的枚举值。<br> 事件回调发生时，事件参数为[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为0的value.f32：插入的值的位置信息。 通过[OH_ArkUI_NodeEvent_GetStringValue](capi-native-node-h.md#oh_arkui_nodeevent_getstringvalue)获取到index为0的buffer字符串：插入的值。

**起始版本：** 12

### NODE_TEXT_INPUT_ON_WILL_DELETE

```c
NODE_TEXT_INPUT_ON_WILL_DELETE = 7011
```

**描述：**

定义在将要删除时，触发回调的枚举值。<br> 事件回调发生时，事件参数为[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为0的value.f32：删除的值的位置信息。 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为1的value.i32：删除值的方向，0为向后删除，1为向前删除。 通过[OH_ArkUI_NodeEvent_GetStringValue](capi-native-node-h.md#oh_arkui_nodeevent_getstringvalue)获取到index为0的buffer字符串：删除的值。

**起始版本：** 12

### NODE_TEXT_INPUT_ON_DID_DELETE

```c
NODE_TEXT_INPUT_ON_DID_DELETE = 7012
```

**描述：**

定义在删除完成时，触发回调的枚举值。<br> 事件回调发生时，事件参数为[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为0的value.f32：删除的值的位置信息。 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为1的value.i32：删除值的方向，0为向后删除，1为向前删除。 通过[OH_ArkUI_NodeEvent_GetStringValue](capi-native-node-h.md#oh_arkui_nodeevent_getstringvalue)获取到index为0的buffer字符串：删除的值。

**起始版本：** 12

### NODE_TEXT_INPUT_ON_CHANGE_WITH_PREVIEW_TEXT

```c
NODE_TEXT_INPUT_ON_CHANGE_WITH_PREVIEW_TEXT = 7013
```

**描述：**

定义TextInput组件在内容改变时（包含预上屏内容），触发回调的枚举值。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md)。 **[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md)包含参数：**<br><ul> <li>ArkUI_TextChangeEvent.pStr：TextInput的内容。</li> <li>ArkUI_TextChangeEvent.pExtendStr：TextInput的预上屏内容。</li> <li>ArkUI_TextChangeEvent.number：TextInput的预上屏起始位置。</li> </ul>

**起始版本：** 15

### NODE_TEXT_INPUT_ON_WILL_CHANGE

```c
NODE_TEXT_INPUT_ON_WILL_CHANGE = 7014
```

**描述：**

定义TextInput组件在内容将要改变时（包含预上屏内容），触发回调的枚举值。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md)。 **[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md)包含参数：**<br><ul> <li>ArkUI_TextChangeEvent.pStr：TextInput的内容。</li> <li>ArkUI_TextChangeEvent.pExtendStr：TextInput的预上屏内容。</li> <li>ArkUI_TextChangeEvent.number：TextInput的预上屏起始位置。</li> </ul>

**起始版本：** 20

### NODE_TEXT_INPUT_ON_COPY

```c
NODE_TEXT_INPUT_ON_COPY = 7015
```

**描述：**

定义当用户点击文本选择时显示的剪贴板上的复制按钮所触发的事件。 当事件回调发生时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。 **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)包含一个参数：**<br><ul> <li>ArkUI_StringAsyncEvent.pStr：复制的文本。</li> </ul>

**起始版本：** 26.0.0

### NODE_TEXT_INPUT_ON_WILL_COPY

```c
NODE_TEXT_INPUT_ON_WILL_COPY = 7016
```

**描述：**

定义复制文本前触发的事件。 当事件回调发生时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。 **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)包含一个参数：**<br><ul> <li>ArkUI_StringAsyncEvent.pStr：复制的文本。</li> </ul>

**起始版本：** 26.0.0

### NODE_TEXT_INPUT_ON_WILL_CUT

```c
NODE_TEXT_INPUT_ON_WILL_CUT = 7017
```

**描述：**

定义剪切文本前触发的事件。 当事件回调发生时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。 **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)包含一个参数：**<br><ul> <li>ArkUI_StringAsyncEvent.pStr：被剪切的文本。</li> </ul>

**起始版本：** 26.0.0

### NODE_TEXT_AREA_ON_CHANGE

```c
NODE_TEXT_AREA_ON_CHANGE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_TEXT_AREA
```

**描述：**

输入内容发生变化时，触发该回调。<br> 触发该事件的条件：输入内容发生变化时。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。 **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)中包含1个参数：**<br><ul> <li>ArkUI_StringAsyncEvent.pStr：当前输入的文本内容。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_ON_PASTE

```c
NODE_TEXT_AREA_ON_PASTE
```

**描述：**

长按输入框内部区域弹出剪贴板后，点击剪切板粘贴按钮，触发该回调。<br> 触发该事件的条件：长按输入框内部区域弹出剪贴板后，点击剪切板粘贴按钮。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。 **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)中包含1个参数：**<br><ul> <li>ArkUI_StringAsyncEvent.pStr：粘贴的文本内容。</li> </ul><br> 从API版本26.0.0开始，回调函数可以返回是否允许粘贴。

**起始版本：** 12

### NODE_TEXT_AREA_ON_TEXT_SELECTION_CHANGE

```c
NODE_TEXT_AREA_ON_TEXT_SELECTION_CHANGE
```

**描述：**

文本选择的位置发生变化时，触发该回调。<br> 触发该事件的条件：文本选择的位置发生变化时。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32：表示所选文本的起始位置。</li> <li>ArkUI_NodeComponentEvent.data[1].i32：表示所选文本的结束位置。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_ON_INPUT_FILTER_ERROR

```c
NODE_TEXT_AREA_ON_INPUT_FILTER_ERROR
```

**描述：**

设置NODE_TEXT_AREA_INPUT_FILTER，正则匹配失败时触发。<br> 触发该事件的条件：正则匹配失败时。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。 **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)中包含1个参数：**<br><ul> <li>ArkUI_StringAsyncEvent.pStr：表示正则匹配失败时，被过滤的内容。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_ON_CONTENT_SCROLL

```c
NODE_TEXT_AREA_ON_CONTENT_SCROLL
```

**描述：**

文本内容滚动时，触发该回调。<br> 触发该事件的条件：文本内容滚动时。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32：表示文本在内容区的横坐标偏移。</li> <li>ArkUI_NodeComponentEvent.data[1].i32：表示文本在内容区的纵坐标偏移。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_ON_EDIT_CHANGE

```c
NODE_TEXT_AREA_ON_EDIT_CHANGE
```

**描述：**

输入状态变化时，触发该回调。<br> 触发该事件的条件：输入状态变化时。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32：true表示正在输入。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_ON_SUBMIT

```c
NODE_TEXT_AREA_ON_SUBMIT
```

**描述：**

TextArea按下输入法回车键触发该事件。<br> 触发该事件的条件：按下输入法回车键。keyType为ARKUI_ENTER_KEY_TYPE_NEW_LINE时不触发 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含1个参数：**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].i32：输入法回车键类型。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_ON_CONTENT_SIZE_CHANGE

```c
NODE_TEXT_AREA_ON_CONTENT_SIZE_CHANGE
```

**描述：**

TextArea输入内容发生变化时触发该事件。<br> 触发该事件的条件：输入内容发生变化时。 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)。 **[ArkUI_NodeComponentEvent](capi-arkui-nativemodule-arkui-nodecomponentevent.md)中包含2个参数：**<br><ul> <li>ArkUI_NodeComponentEvent.data[0].f32：表示文本的宽度。</li> <li>ArkUI_NodeComponentEvent.data[1].f32：表示文本的高度。</li> </ul>

**起始版本：** 12

### NODE_TEXT_AREA_ON_WILL_INSERT

```c
NODE_TEXT_AREA_ON_WILL_INSERT = 8008
```

**描述：**

定义在将要输入时，触发回调的枚举值。<br> 事件回调发生时，事件参数为[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为0的value.f32：插入的值的位置信息。 通过[OH_ArkUI_NodeEvent_GetStringValue](capi-native-node-h.md#oh_arkui_nodeevent_getstringvalue)获取到index为0的buffer字符串：插入的值。

**起始版本：** 12

### NODE_TEXT_AREA_ON_DID_INSERT

```c
NODE_TEXT_AREA_ON_DID_INSERT = 8009
```

**描述：**

定义在输入完成时，触发回调的枚举值。<br> 事件回调发生时，事件参数为[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为0的value.f32：插入的值的位置信息。 通过[OH_ArkUI_NodeEvent_GetStringValue](capi-native-node-h.md#oh_arkui_nodeevent_getstringvalue)获取到index为0的buffer字符串：插入的值。

**起始版本：** 12

### NODE_TEXT_AREA_ON_WILL_DELETE

```c
NODE_TEXT_AREA_ON_WILL_DELETE = 8010
```

**描述：**

定义在将要删除时，触发回调的枚举值。<br> 事件回调发生时，事件参数为[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为0的value.f32：删除的值的位置信息。 通过[OH_ArkUI_NodeEvent_GetNumberValue](capi-native-node-h.md#oh_arkui_nodeevent_getnumbervalue)获取到index为1的value.i32：删除值的方向，0为向后删除，1为向前删除。 通过[OH_ArkUI_NodeEvent_GetStringValue](capi-native-node-h.md#oh_arkui_nodeevent_getstringvalue)获取到index为0的buffer字符串：删除的值。

**起始版本：** 12

### NODE_TEXT_AREA_ON_DID_DELETE

```c
NODE_TEXT_AREA_ON_DID_DELETE = 8011
```

**描述：**

定义在删除完成时，触发回调的枚举值。<br> 事件回调发生时，事件参数为[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)。 通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为0的value.f32：删除的值的位置信息。 通过OH_ArkUI_NodeEvent_GetNumberValue获取到index为1的value.i32：删除值的方向，0为向后删除，1为向前删除。 通过OH_ArkUI_NodeEvent_GetStringValue获取到index为0的buffer字符串：删除的值。

**起始版本：** 12

### NODE_TEXT_AREA_ON_CHANGE_WITH_PREVIEW_TEXT

```c
NODE_TEXT_AREA_ON_CHANGE_WITH_PREVIEW_TEXT = 8012
```

**描述：**

定义TextArea组件在内容改变时（包含预上屏内容），触发回调的枚举值。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md)。 **[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md)包含参数：**<br><ul> <li>ArkUI_TextChangeEvent.pStr：TextArea的内容。</li> <li>ArkUI_TextChangeEvent.pExtendStr：TextArea的预上屏内容。</li> <li>ArkUI_TextChangeEvent.number：TextArea的预上屏起始位置。</li> </ul>

**起始版本：** 15

### NODE_TEXT_AREA_ON_WILL_CHANGE

```c
NODE_TEXT_AREA_ON_WILL_CHANGE = 8013
```

**描述：**

定义TextArea组件在内容将要改变时（包含预上屏内容），触发回调的枚举值。<br> 事件回调发生时，事件参数[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md)。 **[ArkUI_TextChangeEvent](capi-arkui-nativemodule-arkui-textchangeevent.md)包含参数：**<br><ul> <li>ArkUI_TextChangeEvent.pStr：TextArea的内容。</li> <li>ArkUI_TextChangeEvent.pExtendStr：TextArea的预上屏内容。</li> <li>ArkUI_TextChangeEvent.number：TextArea的预上屏起始位置。</li> </ul>

**起始版本：** 20

### NODE_TEXT_AREA_ON_COPY

```c
NODE_TEXT_AREA_ON_COPY = 8014
```

**描述：**

定义长按输入框文本弹出菜单后点击复制按钮触发的事件。 当事件回调发生时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合类型为 [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。 [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)包含一个参数： <b>ArkUI_StringAsyncEvent.pStr</b>：复制的文本。

**起始版本：** 26.0.0

### NODE_TEXT_AREA_ON_WILL_COPY

```c
NODE_TEXT_AREA_ON_WILL_COPY = 8015
```

**描述：**

定义复制文本前触发的事件。 当事件回调发生时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。 **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)包含一个参数：**<br><ul> <li>ArkUI_StringAsyncEvent.pStr：复制的文本。</li> </ul>

**起始版本：** 26.0.0

### NODE_TEXT_AREA_ON_CUT

```c
NODE_TEXT_AREA_ON_CUT = 8016
```

**描述：**

定义长按输入框文本弹出菜单后点击剪切按钮触发的事件。 当事件回调发生时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合类型为 [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。 [ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)包含一个参数： <b>ArkUI_StringAsyncEvent.pStr</b>：剪切后的文本。

**起始版本：** 26.0.0

### NODE_TEXT_AREA_ON_WILL_CUT

```c
NODE_TEXT_AREA_ON_WILL_CUT = 8017
```

**描述：**

定义剪切文本前触发的事件。 当事件回调发生时，[ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md)对象中的联合体类型为[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)。 **[ArkUI_StringAsyncEvent](capi-arkui-nativemodule-arkui-stringasyncevent.md)包含一个参数：**<br><ul> <li>ArkUI_StringAsyncEvent.pStr：被剪切的文本。</li> </ul>

**起始版本：** 26.0.0


