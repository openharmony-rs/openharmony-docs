# AIPageInteraction
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhu-sheng-le-->
<!--Designer: @yyyiye-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

从API版本26.0.0开始，`AIPageInteraction`定义[executeAIPageCommand](./arkts-apis-webview-WebviewController.md#executeaipagecommand)支持的页面交互类JSON命令协议，包括点击、聚焦、输入文本、发送键盘事件等元素级输入操作，以及页面滚动、下拉选项选中、文件上传、缩放控制等会改变页面状态的操作。调用该接口前，应用需要将命令对象序列化为JSON字符串。

> **说明：**
>
> - `command`必须为JSON对象字符串。
> - `method`字段取值区分大小写，需使用[命令总览](#命令总览)中列出的取值。
> - 返回值为JSON字符串，不同命令的返回格式不同。返回格式列为[CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult)的命令请参见AIPageResult；返回格式列为[返回格式](#返回格式)的命令请参见本页返回格式章节。应用可通过`JSON.parse`解析后使用。
> - 命令无法分发或无结果返回时，接口可能返回空字符串；命令执行阶段失败时，以对应命令章节说明的返回格式为准。
> - 查询类命令请参见[AIPageCommand](./arkts-apis-webview-AIPageCommand.md)。

## 命令总览

| method | 功能 | 入参格式 | 返回格式 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| [click](#click) | 点击目标元素 | [ClickCommand](#clickcommand) | [返回格式](#返回格式) | 使目标元素响应点击事件(click event)，不关注是否产生真实的鼠标事件(mouse event)。 |
| [focus](#focus) | 使目标元素获取焦点 | [FocusCommand](#focuscommand) | [返回格式](#返回格式) | 将焦点移动到目标元素，使其可以接收键盘输入等后续交互。 |
| [cursor_position](#cursor_position) | 获取当前文本插入符位置 | 无 | [CursorPositionResult](#cursorpositionresult) | 获取当前页面中文本插入符（caret）的位置，坐标相对于Web组件。 |
| [type](#type) | 向目标元素输入文本 | [TypeCommand](#typecommand) | [返回格式](#返回格式) | 在目标元素指定位置插入文本，支持先清空后输入。若目标元素未获取焦点，先获取焦点再输入。 |
| [send_keys](#send_keys) | 发送键盘事件 | [SendKeysCommand](#sendkeyscommand) | [返回格式](#返回格式) | 向前端发送键盘事件，支持功能键、数字键、字母键、符号键、编辑键、导航键、修饰键及组合键。 |
| [dispatchMouseEvent](#dispatchmouseevent) | 注入鼠标事件 | [DispatchMouseEventCommand](#dispatchmouseeventcommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | 按视口坐标注入鼠标事件。 |
| [dispatchKeyEvent](#dispatchkeyevent) | 注入键盘事件 | [DispatchKeyEventCommand](#dispatchkeyeventcommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | 注入键盘事件。 |
| [input](#input) | 设置输入框内容 | [InputCommand](#inputcommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | 设置指定`input`元素的值。 |
| [scroll](#scroll命令) | 页面滚动 | [ScrollCommand](#scrollcommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | 根据坐标点或节点标识滚动页面。 |
| [select](#select) | 选中下拉选项 | [SelectCommand](#selectcommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | 选中指定的`<select>`元素选项。 |
| [uploadFile](#uploadfile) | 文件上传 | [UploadFileCommand](#uploadfilecommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | 设置`<input type='file'>`标签的文件列表。 |
| [setZoomLevel](#setzoomlevel) | 设置网页缩放比例 | [SetZoomLevelCommand](#setzoomlevelcommand) | [CommandResult](./arkts-apis-webview-AIPageResult.md#commandresult) | 设置当前网页的缩放比例，等价于CTRL+Wheel缩放。 |

## 通用目标元素定位

`click`、`focus`、`type`命令需要通过目标元素定位参数指定操作对象，支持以下两种互斥方式：

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| xpath | string | 目标元素的XPath，可通过[getFullDom](./arkts-apis-webview-AIPageCommand.md#getfulldom)或[getLiteDom](./arkts-apis-webview-AIPageCommand.md#getlitedom)返回的`xpath`字段获取。 |
| nodeid | string | 目标元素的节点标识，可通过[getFullDom](./arkts-apis-webview-AIPageCommand.md#getfulldom)或[getLiteDom](./arkts-apis-webview-AIPageCommand.md#getlitedom)返回的`id`字段获取。该值由frame标识、文档作用域标识和DOM节点标识组合编码。 |

> **说明：**
>
> - `xpath`与`nodeid`互斥，均传入时以`nodeid`为准。

## 返回格式

### 成功

操作类命令（click、focus、type、send_keys）成功时返回：

```json
{
  "code": 10,
  "message": "success"
}
```

查询类命令（cursor_position）成功时返回结果对象，参见各命令说明。

### 失败

返回格式列为本节[返回格式](#返回格式)的命令失败时返回包含`code`和`error`字段的JSON。以下以`click`命令未提供`params`字段为例：

```json
{
  "code": 420,
  "error": "click/focus params not found"
}
```

错误码取值参见[命令执行结果码说明](./arkts-apis-webview-AIPageResult.md#命令执行结果码说明)。

## click

点击目标元素，使其响应点击事件(click event)。该命令仅使目标元素响应点击事件(click event)，不关注是否产生真实的鼠标事件(mouse event)。

### ClickCommand

通过XPath定位目标元素：

```json
{
  "method": "click",
  "params": {
    "xpath": "/html[1]/body[1]/button[1]"
  }
}
```

通过节点标识定位目标元素：

```json
{
  "method": "click",
  "params": {
    "nodeid": "frameToken|documentToken|12"
  }
}
```

### 入参说明

| 参数 | 子参数 | 参数项 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | 是 | 命令名称，固定为`click`。 |
| params | - | - | Object | 是 | 命令参数。 |
| params | - | xpath | string | 否 | 目标元素的XPath。`xpath`与`nodeid`互斥，均传入时以`nodeid`为准。 |
| params | - | nodeid | string | 否 | 目标元素的节点标识。`xpath`与`nodeid`互斥，均传入时以`nodeid`为准。 |

> **说明：**
>
> - `params`中必须包含`xpath`或`nodeid`中的一个，用于定位目标元素。

### 返回说明

命令执行成功时返回`{"code":10,"message":"success"}`；失败时返回错误码JSON，常见错误码见下表：

| 错误码 | 触发条件 |
| ---- | ---- |
| 420 | 未提供`params`字段 |
| 421 | 未提供`xpath`/`nodeid`或其值为空字符串 |
| 422 | 定位字段解析后为空 |
| 423 | Web实例不可用，请确认Web组件已正确加载并关联到有效的Web实例 |
| 424 | 未找到目标元素 |

### 请求示例

```json
{
  "method": "click",
  "params": {
    "xpath": "/html[1]/body[1]/button[1]"
  }
}
```

### 返回示例

成功：

```json
{
  "code": 10,
  "message": "success"
}
```

失败：

`420`（未提供`params`字段）：

```json
{
  "code": 420,
  "error": "click/focus params not found"
}
```

`421`（未提供`xpath`/`nodeid`或其值为空字符串）：

```json
{
  "code": 421,
  "error": "click/focus nodeid not found"
}
```

`422`（定位字段解析后为空）：

```json
{
  "code": 422,
  "error": "click/focus nodeid is empty"
}
```

`423`（Web实例不可用）：

```json
{
  "code": 423,
  "error": "click/focus delegate not initialized"
}
```

`424`（未找到目标元素）：

```json
{
  "code": 424,
  "error": "click/focus element not exist"
}
```

## focus

使目标元素获取焦点。

### FocusCommand

通过XPath定位目标元素：

```json
{
  "method": "focus",
  "params": {
    "xpath": "/html[1]/body[1]/input[1]"
  }
}
```

通过节点标识定位目标元素：

```json
{
  "method": "focus",
  "params": {
    "nodeid": "frameToken|documentToken|12"
  }
}
```

### 入参说明

| 参数 | 子参数 | 参数项 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | 是 | 命令名称，固定为`focus`。 |
| params | - | - | Object | 是 | 命令参数。 |
| params | - | xpath | string | 否 | 目标元素的XPath。`xpath`与`nodeid`互斥，均传入时以`nodeid`为准。 |
| params | - | nodeid | string | 否 | 目标元素的节点标识。`xpath`与`nodeid`互斥，均传入时以`nodeid`为准。 |

> **说明：**
>
> - `params`中必须包含`xpath`或`nodeid`中的一个，用于定位目标元素。

### 返回说明

命令执行成功时返回`{"code":10,"message":"success"}`；失败时返回错误码JSON，错误码与[click](#返回说明-1)一致（420-424）。

### 请求示例

```json
{
  "method": "focus",
  "params": {
    "nodeid": "frameToken|documentToken|12"
  }
}
```

### 返回示例

成功：

```json
{
  "code": 10,
  "message": "success"
}
```

失败（错误码与click一致）：

`420`（未提供`params`字段）：

```json
{
  "code": 420,
  "error": "click/focus params not found"
}
```

`421`（未提供`xpath`/`nodeid`或其值为空字符串）：

```json
{
  "code": 421,
  "error": "click/focus nodeid not found"
}
```

`422`（定位字段解析后为空）：

```json
{
  "code": 422,
  "error": "click/focus nodeid is empty"
}
```

`423`（Web实例不可用）：

```json
{
  "code": 423,
  "error": "click/focus delegate not initialized"
}
```

`424`（未找到目标元素）：

```json
{
  "code": 424,
  "error": "click/focus element not exist"
}
```

## cursor_position

获取当前页面中文本插入符（caret）的位置，返回的坐标为相对于Web组件左上角的偏移量。

### 请求说明

该命令不需要`params`参数。

### CursorPositionResult

```json
{
  "result": {
    "x": 100,
    "y": 200
  }
}
```

### 返回说明

| 字段 | 子字段 | 类型 | 说明 |
| ---- | ---- | ---- | ---- |
| result | - | Object | 文本插入符位置信息。 |
| result | x | number | 文本插入符的x坐标，相对于Web组件。 |
| result | y | number | 文本插入符的y坐标，相对于Web组件。 |

> **说明：**
>
> - 坐标相对于Web组件的位置，非页面绝对坐标。
> - 失败时返回错误码JSON，常见错误码：400（输入功能不可用）、401（未知的命令名称）、402（输入法未绑定）。

### 请求示例

```json
{
  "method": "cursor_position"
}
```

### 返回示例

成功：

```json
{
  "result": {
    "x": 100,
    "y": 200
  }
}
```

失败：

`400`（输入功能不可用，找不到输入法处理器）：

```json
{
  "code": 400,
  "error": "method not found"
}
```

`401`（未知的命令名称，`method`字段取值无法识别）：

```json
{
  "code": 401,
  "error": "unknown method"
}
```

`402`（输入法未绑定）：

```json
{
  "code": 402,
  "error": "input method not bound"
}
```

## type

向目标元素输入文本。支持在目标元素的指定位置插入文本，支持先清空后输入。若目标元素未获取焦点，会先使其获取焦点再输入。

### TypeCommand

```json
{
  "method": "type",
  "params": {
    "xpath": "/html[1]/body[1]/input[1]",
    "text": "需要输入的文本",
    "index": 0,
    "clear": false
  }
}
```

### 入参说明

| 参数 | 子参数 | 参数项 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | 是 | 命令名称，固定为`type`。 |
| params | - | - | Object | 是 | 命令参数。 |
| params | - | xpath | string | 否 | 目标元素的XPath。`xpath`与`nodeid`互斥，均传入时以`nodeid`为准。 |
| params | - | nodeid | string | 否 | 目标元素的节点标识。`xpath`与`nodeid`互斥，均传入时以`nodeid`为准。 |
| params | - | text | string | 是 | 需要输入的文本内容。 |
| params | - | index | number | 否 | 文本插入位置，从0开始。当输入框内已有文本长度小于`index`时，在末尾追加。默认值为0。 |
| params | - | clear | boolean | 否 | 是否在输入前先清空目标元素中的已有文本。默认值为false。 |

> **说明：**
>
> - `params`中必须包含`xpath`或`nodeid`中的一个，用于定位目标元素。
> - 若目标元素未获取焦点，会先使其获取焦点再执行输入操作。
> - `index`为0时表示在已有文本的最前面插入。
> - 当`clear`为`true`时，会先清空目标元素中的全部文本，再在`index`位置插入`text`。

### 返回说明

命令执行成功时返回`{"code":10,"message":"success"}`；失败时返回错误码JSON，常见错误码见下表：

| 错误码 | 触发条件 |
| ---- | ---- |
| 440 | 未提供`params`字段 |
| 441 | 未提供`xpath`/`nodeid` |
| 442 | 未提供`text`参数 |
| 443 | 提供了`xpath`但值为空 |
| 444 | Web实例不可用，请确认Web组件已正确加载并关联到有效的Web实例 |
| 445 | 未找到目标元素 |

### 请求示例

```json
{
  "method": "type",
  "params": {
    "xpath": "/html[1]/body[1]/input[1]",
    "text": "Hello World",
    "index": 0,
    "clear": false
  }
}
```

### 返回示例

成功：

```json
{
  "code": 10,
  "message": "success"
}
```

失败：

`440`（未提供`params`字段）：

```json
{
  "code": 440,
  "error": "type params not found"
}
```

`441`（未提供`xpath`/`nodeid`）：

```json
{
  "code": 441,
  "error": "type nodeid not found"
}
```

`442`（未提供`text`参数）：

```json
{
  "code": 442,
  "error": "type text not found"
}
```

`443`（提供了`xpath`但值为空）：

```json
{
  "code": 443,
  "error": "type xpath is empty"
}
```

`444`（Web实例不可用）：

```json
{
  "code": 444,
  "error": "type delegate not initialized"
}
```

`445`（未找到目标元素）：

```json
{
  "code": 445,
  "error": "type element not exist"
}
```

## send_keys

向前端发送键盘事件，支持单键与组合键。

### SendKeysCommand

单键：

```json
{
  "method": "send_keys",
  "params": {
    "key": "Enter"
  }
}
```

组合键（修饰键+键，用`+`连接）：

```json
{
  "method": "send_keys",
  "params": {
    "key": "Control+c"
  }
}
```

### 入参说明

| 参数 | 子参数 | 参数项 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | 是 | 命令名称，固定为`send_keys`。 |
| params | - | - | Object | 是 | 命令参数。 |
| params | - | key | string | 是 | 需要发送的按键名称，取值请参见[send_keys的params.key字段取值说明](#send_keys的paramskey字段取值说明)。支持`修饰键+键`形式的组合键（如`Control+c`）。发送字母时大小写敏感。 |

> **说明：**
>
> - 发送字母时大小写敏感，例如`KeyA`和`Keya`表示不同的按键。
> - 组合键格式为`修饰键+键`，例如`Control+c`、`Shift+ArrowLeft`。

### send_keys的params.key字段取值说明

| 分类 | 支持的按键 |
| ---- | ---- |
| 功能键 | F1、F2、F3、F4、F5、F6、F7、F8、F9、F10、F11、F12 |
| 数字键 | Digit0、Digit1、Digit2、Digit3、Digit4、Digit5、Digit6、Digit7、Digit8、Digit9 |
| 字母键 | KeyA ~ KeyZ、Keya ~ Keyz（大小写敏感） |
| 符号键 | Backquote、Minus、Equal、Backslash |
| 编辑键 | Backspace、Tab、Delete、Insert、Enter、Escape |
| 导航键 | ArrowDown、ArrowUp、ArrowLeft、ArrowRight、Home、End、PageUp、PageDown |
| 修饰键 | Shift、Control、Alt、ShiftLeft |
| 组合键 | `修饰键+键`，如`Control+c`、`Shift+ArrowLeft` |

### 返回说明

命令执行成功时返回`{"code":10,"message":"success"}`；失败时返回错误码JSON，常见错误码见下表：

| 错误码 | 触发条件 |
| ---- | ---- |
| 460 | 未提供`params`字段 |
| 461 | 未提供`key`字段 |
| 462 | `key`为空字符串或无有效按键 |
| 463 | `key`值无法识别（未知按键名） |

### 请求示例

```json
{
  "method": "send_keys",
  "params": {
    "key": "PageDown"
  }
}
```

### 返回示例

成功：

```json
{
  "code": 10,
  "message": "success"
}
```

失败：

`460`（未提供`params`字段）：

```json
{
  "code": 460,
  "error": "send_keys params not found"
}
```

`461`（未提供`key`字段）：

```json
{
  "code": 461,
  "error": "send_keys keys not found"
}
```

`462`（`key`为空字符串或无有效按键）：

```json
{
  "code": 462,
  "error": "send_keys no valid keys"
}
```

`463`（`key`值无法识别）：

```json
{
  "code": 463,
  "error": "send_keys unknown main key"
}
```

## dispatchMouseEvent

按视口坐标注入鼠标事件。

### DispatchMouseEventCommand

```json
{
  "method": "dispatchMouseEvent",
  "params": {
    "type": "mouseWheel",
    "x": 500,
    "y": 300,
    "deltaX": 0,
    "deltaY": 100,
    "pointerType": "mouse"
  }
}
```

### 入参说明

| 参数 | 子参数 | 参数项 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | 是 | 命令名称，固定为`dispatchMouseEvent`。 |
| params | - | - | Object | 是 | 命令参数。 |
| params | type | - | string | 是 | 鼠标事件类型，支持`mousePressed`、`mouseReleased`、`mouseMoved`和`mouseWheel`。 |
| params | x | - | number | 是 | 视口x坐标。 |
| params | y | - | number | 是 | 视口y坐标。 |
| params | button | - | string | 否 | 鼠标按键，支持`none`、`left`、`middle`、`right`、`back`和`forward`。 |
| params | clickCount | - | number | 否 | 点击次数，必须为整数。 |
| params | deltaX | - | number | 否 | 横向滚动距离，常用于`mouseWheel`。 |
| params | deltaY | - | number | 否 | 纵向滚动距离，常用于`mouseWheel`。 |
| params | pointerType | - | string | 否 | 指针类型。当前仅支持`mouse`；不传入时按`mouse`处理。 |
| params | timestamp | - | number | 否 | 事件时间戳。 |
| params | modifiers | - | number | 否 | 键盘修饰键位掩码，必须为整数。 |
| params | buttons | - | number | 否 | 事件触发时处于按下状态的鼠标按键位掩码，必须为整数。不传入时该字段按0处理，位值说明见下表。 |
| params | force | - | number | 否 | 按压力度。 |
| params | tangentialPressure | - | number | 否 | 切向压力。 |
| params | tiltX | - | number | 否 | 指针相对x轴倾斜角。 |
| params | tiltY | - | number | 否 | 指针相对y轴倾斜角。 |
| params | twist | - | number | 否 | 指针旋转角，必须为整数。 |

`buttons`各位值如下：

| 位值 | 按键状态 |
| ---- | ---- |
| 0 | 没有鼠标按键处于按下状态。 |
| 1 | 左键处于按下状态。 |
| 2 | 右键处于按下状态。 |
| 4 | 中键处于按下状态。 |
| 8 | 后退键处于按下状态。 |
| 16 | 前进键处于按下状态。 |

多个按键同时处于按下状态时，将对应位值按位或。例如，`3`表示左键和右键同时处于按下状态，`5`表示左键和中键同时处于按下状态。`buttons`表示事件触发时所有处于按下状态的按键，`button`表示本次事件对应的单个按键。当前实现只读取上述5个按键位，不额外校验掩码范围；其他位不会映射为鼠标按键状态。

> **说明：**
>
> - `type`、`x`或`y`缺失时，返回参数缺失结果。
> - 字段类型错误、`type`取值不支持、`button`取值不支持、`pointerType`不是`mouse`时，返回参数错误结果。
> - 入参说明中列出的字段为当前实现会校验并下发的公开参数。参数是否产生可观察页面行为，取决于事件类型、目标元素状态以及页面脚本/浏览器输入链路对该字段的处理。
> - 未在入参说明中列出的字段不作为该命令的公开参数。

### 返回说明

命令执行成功时返回`{"code":10,"message":"success"}`。

失败结果如下：

| 错误码 | 触发条件 |
| ---- | ---- |
| 110 | `params`缺失或不是Object。 |
| 132 | browser或browser host为空。 |
| 350 | 鼠标事件命令下发失败。 |
| 391 | 缺少必填参数，或`type`为空字符串。 |
| 392 | 除391所述情况外，入参说明中所列字段的类型或取值不符合约束；其中`pointerType`仅支持`mouse`。 |

### 返回示例

成功时返回：

```json
{
  "code": 10,
  "message": "success"
}
```

参数错误时返回：

```json
{
  "code": 392,
  "message": "pointerType must be mouse"
}
```

## dispatchKeyEvent

注入键盘事件。

### DispatchKeyEventCommand

```json
{
  "method": "dispatchKeyEvent",
  "params": {
    "type": "keyDown",
    "key": "A",
    "code": "KeyA",
    "windowsVirtualKeyCode": 65
  }
}
```

### 入参说明

| 参数 | 子参数 | 参数项 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | 是 | 命令名称，固定为`dispatchKeyEvent`。 |
| params | - | - | Object | 是 | 命令参数。 |
| params | type | - | string | 是 | 键盘事件类型，支持`keyDown`、`keyUp`、`rawKeyDown`和`char`。 |
| params | text | - | string | 否 | 事件生成的文本。 |
| params | unmodifiedText | - | string | 否 | 不包含修饰键影响的文本。 |
| params | key | - | string | 否 | 按键值。 |
| params | code | - | string | 否 | 物理按键编码。 |
| params | timestamp | - | number | 否 | 事件时间戳。 |
| params | modifiers | - | number | 否 | 键盘修饰键位掩码，必须为整数。 |
| params | windowsVirtualKeyCode | - | number | 否 | 兼容虚拟键码，用于描述逻辑按键，必须为整数。 |
| params | nativeVirtualKeyCode | - | number | 否 | 平台原生虚拟键码，必须为整数。 |
| params | location | - | number | 否 | 按键位置，必须为整数。 |
| params | autoRepeat | - | boolean | 否 | 是否为自动重复按键。 |
| params | isKeypad | - | boolean | 否 | 是否来自数字键盘。 |
| params | isSystemKey | - | boolean | 否 | 是否为系统按键。 |
| params | isForwarded | - | boolean | 否 | 是否为转发事件。 |
| params | commands | - | Array\<string> | 否 | 编辑命令列表。 |

> **说明：**
>
> - `type`缺失时，返回参数缺失结果。
> - 字段类型错误或`type`取值不支持时，返回参数错误结果。
> - 入参说明中列出的字段为当前实现会校验并下发的公开参数。参数是否产生可观察页面行为，取决于事件类型、目标元素状态以及页面脚本/浏览器输入链路对该字段的处理。
> - 未在入参说明中列出的字段不作为该命令的公开参数。

### 返回说明

命令执行成功时返回`{"code":10,"message":"success"}`。

失败结果如下：

| 错误码 | 触发条件 |
| ---- | ---- |
| 110 | `params`缺失或不是Object。 |
| 132 | browser或browser host为空。 |
| 350 | 键盘事件命令下发失败。 |
| 391 | `type`缺失或为空字符串。 |
| 392 | 除391所述情况外，入参说明中所列字段的类型或取值不符合约束；`commands`不是数组或包含非string成员也属于该错误。 |

### 返回示例

成功时返回：

```json
{
  "code": 10,
  "message": "success"
}
```

参数错误时返回：

```json
{
  "code": 392,
  "message": "invalid key event type"
}
```

## input

设置指定`input`元素的值。该命令会替换输入框当前内容，不会在原内容后追加。

### InputCommand

通过XPath定位目标输入框：

```json
{
  "method": "input",
  "params": {
    "xpath": "//input[@id='username']",
    "type": "text",
    "value": "ArkWeb"
  }
}
```

通过节点标识定位目标输入框：

```json
{
  "method": "input",
  "params": {
    "id": "frameToken|documentToken|12",
    "type": "text",
    "value": "ArkWeb"
  }
}
```

### 入参说明

| 参数 | 子参数 | 参数项 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | 是 | 命令名称，固定为`input`。 |
| params | - | - | Object | 是 | 命令参数。 |
| params | xpath | - | string | 否 | 目标`input`元素的XPath。与`id`二选一。 |
| params | id | - | string | 否 | [getFullDom](./arkts-apis-webview-AIPageCommand.md#getfulldom)或[getLiteDom](./arkts-apis-webview-AIPageCommand.md#getlitedom)返回的节点标识。与`xpath`二选一。该值不是HTML `id`属性。 |
| params | type | - | string | 是 | 输入框类型。支持`default`、`text`、`password`、`email`、`url`、`tel`、`search`、`number`、`date`、`datetime-local`、`month`、`range`、`time`和`week`。 |
| params | value | - | string | 是 | 要设置的新值。 |

> **说明：**
>
> - `id`和`xpath`必须二选一，不能同时传入。
> - `type`为`default`时，不按传入类型与目标输入框实际类型做精确匹配，但目标元素仍必须是可设置字符串值的`input`元素。
> - `type`不为`default`时，传入类型必须与目标输入框实际类型匹配。
> - `value`必须满足目标输入框类型的值格式要求。

### 返回说明

命令执行成功时返回`{"code":10,"message":"success"}`。

失败结果如下：

| 错误码 | 触发条件 |
| ---- | ---- |
| 11 | 输入命令执行超时，或renderer侧执行对象不可用。 |
| 110 | `params`缺失或不是Object。 |
| 131 | XPath未匹配到元素，或节点标识对应的frame、文档或DOM节点已失效。 |
| 132 | browser或browser host为空。 |
| 160 | main frame无效、frame未就绪或renderer通信通道未就绪。 |
| 161 | 定位到的目标元素不是`input`元素。 |
| 201 | `value`已传入，但不是string。 |
| 202 | `type`是非空字符串但不在支持范围，或目标`input`元素的实际类型不支持设置字符串值。 |
| 203 | `value`不满足目标`input`元素实际类型的值格式要求。 |
| 204 | `type`不是`default`，且与目标`input`元素的实际类型不一致。 |
| 391 | 缺少定位参数、`type`或`value`；`type`为空字符串也属于该错误。 |
| 392 | 除391所述情况外，定位参数的类型、组合或格式不符合入参说明，或`type`不是string。 |

### 返回示例

成功时返回：

```json
{
  "code": 10,
  "message": "success"
}
```

传入不支持的输入框类型时返回：

```json
{
  "code": 202,
  "message": "unsupported input type"
}
```

`id`和`xpath`同时传入时返回：

```json
{
  "code": 392,
  "message": "id and xpath are mutually exclusive"
}
```

## scroll命令

按视口坐标或节点标识滚动页面。使用节点标识时，命令会以目标元素位置执行滚动。

### ScrollCommand

```json
{
  "method": "scroll",
  "params": {
    "x": 400,
    "y": 200,
    "deltaX": 0,
    "deltaY": -200,
    "speed": 1000
  }
}
```

通过节点标识滚动：

```json
{
  "method": "scroll",
  "params": {
    "id": "frameToken|documentToken|12",
    "deltaY": -200
  }
}
```

### 入参说明

| 参数 | 子参数 | 参数项 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | 是 | 命令名称，固定为`scroll`。 |
| params | - | - | Object | 是 | 命令参数。 |
| params | - | id | string | 否 | [getFullDom](./arkts-apis-webview-AIPageCommand.md#getfulldom)或[getLiteDom](./arkts-apis-webview-AIPageCommand.md#getlitedom)返回的节点标识。与`x`、`y`二选一。传入`id`时不能同时传入`x`或`y`。该值不是HTML `id`属性。 |
| params | - | x | number | 否 | 与`id`二选一。wheel事件触发的鼠标X坐标。视口坐标系，左上角为原点(0, 0)，向右递增，单位为CSS像素。缺失时返回`{"code":391}`。若该坐标落在可滚动元素内部，则滚动该元素；若落在页面空白区域，则滚动页面根。 |
| params | - | y | number | 否 | 与`id`二选一。wheel事件触发的鼠标Y坐标。视口坐标系，左上角为原点(0, 0)，向下递增，单位为CSS像素。缺失时返回`{"code":391}`。若该坐标落在可滚动元素内部，则滚动该元素；若落在页面空白区域，则滚动页面根。 |
| params | - | deltaX | number | 否 | 水平方向wheel事件增量。负值使页面向右滚动（显示右侧内容，即`scrollLeft`增大），正值使页面向左滚动（显示左侧内容，即`scrollLeft`减小）。单位为CSS像素。不传入时默认为0（不发生水平滚动）。 |
| params | - | deltaY | number | 否 | 垂直方向wheel事件增量。负值使页面向下滚动（显示下方内容，即`scrollTop`增大），正值使页面向上滚动（显示上方内容，即`scrollTop`减小）。单位为CSS像素。不传入时默认为0（不发生垂直滚动）。 |
| params | - | speed | number | 否 | 滚动速度，必须为整数。取值范围[-2147483648, 2147483647]：负值立刻到达目标位置，无滚动动画；0返回`{"code":392}`；正值按指定速度进行滚动动画。不传入时默认为800。 |

> **说明：**
>
> - `id`与`x`、`y`互斥。
> - 未传入`id`时，必须同时传入`x`和`y`。
> - `scroll`命令为即发即忘模式，命令发送成功后立即返回结果，不等待手势执行完成。
> - 连续发送的滚动命令由Chromium手势控制器排队顺序执行，不会丢失命令。
> - 最终滚动距离可能因浮点数舍入存在微小偏差（通常小于1像素）。

### 返回说明

命令执行成功时返回`{"code":10,"message":"success"}`；失败时返回错误码JSON，常见错误码见下表：

| 错误码 | 触发条件 |
| ---- | ---- |
| 110 | `params`字段非JSON对象 |
| 130 | 通过`id`解析目标元素位置超时 |
| 131 | 通过`id`解析目标元素位置失败、元素不存在或元素无有效矩形 |
| 132 | browser或host为空，通常表示Web实例不可用 |
| 350 | 滚动命令下发失败 |
| 391 | 未传入`id`时缺少必要参数`x`或`y` |
| 392 | `id`无效、`x`/`y`/`deltaX`/`deltaY`/`speed`取值或类型无效（如`speed=0`），或`id`与`x`/`y`同时传入 |

### 请求示例

```json
{
  "method": "scroll",
  "params": {
    "x": 180,
    "y": 320,
    "deltaY": -300
  }
}
```

通过节点标识滚动：

```json
{
  "method": "scroll",
  "params": {
    "id": "frameToken|documentToken|12",
    "deltaY": -300
  }
}
```

### 返回示例

成功：

```json
{
  "code": 10,
  "message": "success"
}
```

失败：

`391`（未传入`id`且未传入坐标）：

```json
{
  "code": 391,
  "message": "missing id or x/y"
}
```

`391`（坐标通路缺少必要参数`x`或`y`）：

```json
{
  "code": 391,
  "message": "missing x or y"
}
```

`392`（`speed`取值或类型无效，例如`speed=0`）：

```json
{
  "code": 392,
  "message": "invalid param: speed"
}
```

`id`与坐标同时传入时返回：

```json
{
  "code": 392,
  "message": "id is mutually exclusive with x/y"
}
```

## select

选中指定的`<select>`元素选项。通过XPath或节点标识定位`<select>`元素，按索引或值选中`<option>`元素。

### SelectCommand

```json
{
  "method": "select",
  "params": {
    "xpath": "//select[@id='country']",
    "indexes": [2]
  }
}
```

通过节点标识定位select元素：

```json
{
  "method": "select",
  "params": {
    "id": "frameToken|documentToken|12",
    "values": ["us"]
  }
}
```

### 入参说明

| 参数 | 子参数 | 参数项 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | 是 | 命令名称，固定为`select`。 |
| params | - | - | Object | 是 | 命令参数。 |
| params | - | xpath | string | 否 | XPath 1.0定位表达式，取首个匹配节点。与`id`二选一。 |
| params | - | id | string | 否 | [getFullDom](./arkts-apis-webview-AIPageCommand.md#getfulldom)或[getLiteDom](./arkts-apis-webview-AIPageCommand.md#getlitedom)返回的节点标识。与`xpath`二选一。该值不是HTML `id`属性。 |
| params | - | indexes | Array\<number\> | 否 | `<option>`子元素的索引列表，数组项必须为整数，从0开始计数，按DOM顺序对应`<select>`下的`<option>`子元素（不含`<optgroup>`层级偏移）。与`values`至少提供一个，两者均未提供时返回`{"code":251}`。与`values`同时提供时`indexes`优先。 |
| params | - | values | Array\<string\> | 否 | `<option>`元素的`value`属性值列表。遍历`<select>`的所有`<option>`子元素，比对`option.value`与传入值。与`indexes`至少提供一个，两者均未提供时返回`{"code":251}`。与`indexes`同时提供时`indexes`优先。 |

> **说明：**
>
> - `id`和`xpath`必须二选一，不能同时传入。
> - `indexes`或`values`数组中类型不匹配的成员会被忽略。
> - XPath表达式无效或未匹配到目标元素时，按目标元素不存在处理。
> - 选中的option包含被禁用项时，返回`{"code":255}`。
> - 多选元素（`<select multiple>`）可传入多个索引；单选元素传入多个索引时返回错误。

### 返回说明

命令执行成功时返回`{"code":10,"message":"success"}`；失败时返回错误码JSON，常见错误码见下表：

| 错误码 | 触发条件 |
| ---- | ---- |
| 110 | `params`字段非JSON对象 |
| 115 | 未提供`id`或`xpath`定位参数 |
| 131 | 目标元素不存在 |
| 132 | browser或host为空，通常表示Web实例不可用 |
| 161 | 目标元素不是`<select>`元素 |
| 251 | `indexes`和`values`均未提供、不是数组或解析后无有效项 |
| 252 | `indexes`索引越界（小于0或大于等于option数量） |
| 253 | `values`中的值在option列表中无匹配项 |
| 254 | 单选`<select>`传入多个索引 |
| 255 | 选中的option被禁用 |
| 256 | `<select>`元素无option子元素 |
| 392 | `id`和`xpath`同时传入，或`id`/`xpath`字段不是string或为空字符串 |

### 请求示例

```json
{
  "method": "select",
  "params": {
    "xpath": "//select[@id='country']",
    "indexes": [1, 3]
  }
}
```

通过节点标识选择选项：

```json
{
  "method": "select",
  "params": {
    "id": "frameToken|documentToken|12",
    "values": ["us"]
  }
}
```

### 返回示例

成功：

```json
{
  "code": 10,
  "message": "success"
}
```

失败：

`115`（未提供`id`或`xpath`定位参数）：

```json
{
  "code": 115,
  "message": "missing or empty xpath"
}
```

`392`（`xpath`为空字符串）：

```json
{
  "code": 392,
  "message": "invalid id or xpath"
}
```

`131`（目标元素不存在）：

```json
{
  "code": 131,
  "message": "select command failed"
}
```

`161`（目标元素不是`<select>`元素）：

```json
{
  "code": 161,
  "message": "select command failed"
}
```

`251`（`indexes`和`values`均未提供）：

```json
{
  "code": 251,
  "message": "both indexes and values are empty"
}
```

`252`（索引越界）：

```json
{
  "code": 252,
  "message": "select command failed"
}
```

`255`（选中的option被禁用）：

```json
{
  "code": 255,
  "message": "select command failed"
}
```

`id`和`xpath`同时传入时返回：

```json
{
  "code": 392,
  "message": "id and xpath are mutually exclusive"
}
```

## uploadFile

为input[type=file]元素设置文件路径。通过XPath定位元素，支持设置单个或多个文件路径。

### UploadFileCommand

```json
{
  "method": "uploadFile",
  "params": {
    "xpath": "//input[@type='file']",
    "files": ["/data/local/tmp/test.pdf"]
  }
}
```

### 入参说明

| 参数 | 子参数 | 参数项 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | 是 | 命令名称，固定为`uploadFile`。 |
| params | - | - | Object | 是 | 命令参数。 |
| params | - | xpath | string | 是 | XPath 1.0定位表达式，取首个匹配节点。缺失或为空字符串时返回`{"code":391}`。 |
| params | - | files | Array\<string\> | 是 | 文件绝对路径列表。路径经过规范化处理。缺失或为空数组时返回`{"code":372}`。数组元素须为非空字符串，空字符串返回`{"code":371}`。 |

> **说明：**
>
> - 文件路径经过规范化处理（解析符号链接）。路径无法解析时返回`{"code":370,"message":"failed to resolve file path: <path>"}`。
> - 路径存在性和可读性为非阻塞警告，不影响命令执行。警告信息附加在`message`字段中，格式为`"success; warnings: <path>: <reason>"`。
> - `xpath`匹配到非`input[type=file]`元素时，上传被拒绝，返回`{"code":352,"message":"upload target is not file input"}`。

### 返回说明

命令执行成功时返回`{"code":10,"message":"success"}`（存在非阻塞警告时`message`字段追加警告信息）；失败时返回错误码JSON，常见错误码见下表：

| 错误码 | 触发条件 |
| ---- | ---- |
| 110 | `params`字段非JSON对象 |
| 131 | `xpath`匹配的元素不存在，或DOM搜索无结果 |
| 132 | browser或host为空，通常表示Web实例不可用 |
| 350 | 文件上传命令下发失败 |
| 351 | 文件上传通道初始化失败 |
| 352 | 文件上传执行失败（含`xpath`匹配到非`<input type='file'>`元素时上传被拒绝） |
| 353 | 元素搜索响应解析失败 |
| 370 | 文件路径无法解析（含路径遍历组件`..`） |
| 371 | 文件路径为空字符串 |
| 372 | 文件列表为空或未提供 |
| 391 | 缺少`xpath`或为空字符串 |

### 请求示例

```json
{
  "method": "uploadFile",
  "params": {
    "xpath": "//input[@type='file' and @name='upload']",
    "files": ["/data/local/tmp/file1.pdf", "/data/local/tmp/file2.pdf"]
  }
}
```

### 返回示例

成功时：

```json
{
  "code": 10,
  "message": "success"
}
```

成功但含警告时：

```json
{
  "code": 10,
  "message": "success; warnings: /path/file.pdf: path does not exist"
}
```

失败：

`131`（`xpath`匹配的元素不存在）：

```json
{
  "code": 131,
  "message": "element not found"
}
```

`352`（`xpath`匹配到非`<input type='file'>`元素）：

```json
{
  "code": 352,
  "message": "upload target is not file input"
}
```

`370`（文件路径无法解析）：

```json
{
  "code": 370,
  "message": "failed to resolve file path: /data/local/tmp/missing.pdf"
}
```

`371`（文件路径为空字符串）：

```json
{
  "code": 371,
  "message": "file path is empty"
}
```

`372`（文件列表为空或未提供）：

```json
{
  "code": 372,
  "message": "files list is empty"
}
```

`391`（缺少`xpath`或为空字符串）：

```json
{
  "code": 391,
  "message": "missing param: xpath"
}
```

## setZoomLevel

设置当前网页的缩放比例。命令等价于用户手动CTRL+Wheel缩放，整体缩放网页（CSS page zoom）。缩放比例会持久化到Chromium HostZoomMap，与手动缩放共享存储。

### SetZoomLevelCommand

```json
{
  "method": "setZoomLevel",
  "params": {
    "zoomLevel": 1.5
  }
}
```

### 入参说明

| 参数 | 子参数 | 参数项 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | 是 | 命令名称，固定为`setZoomLevel`。 |
| params | - | - | Object | 是 | 命令参数。 |
| params | - | zoomLevel | number | 是 | 网页缩放比例。1.0表示100%（原始大小），2.0表示200%，0.5表示50%。取值范围[0.25, 5.0]。 |

> **说明：**
>
> - 当应用通过[zoomControlAccess](./arkts-basic-components-web-attributes.md#zoomcontrolaccess22)禁用缩放时，本命令返回`{"code":482}`。
> - `zoomLevel`为非数字类型（字符串、数组、对象、null）时，统一按缺少字段处理，返回`{"code":391}`。
> - NaN/Infinity/-Infinity不是合法JSON数值，会在JSON解析阶段被拒绝，不会进入本命令。

### 返回说明

命令执行成功时返回`{"code":10,"message":"success"}`；失败时返回错误码JSON，常见错误码见下表：

| 错误码 | 触发条件 |
| ---- | ---- |
| 110 | `params`字段非JSON对象 |
| 132 | browser或host为空，通常表示Web实例不可用 |
| 391 | 缺少`zoomLevel`或为非数字类型（字符串、数组、对象、null） |
| 480 | 取值超出范围`[0.25, 5.0]`，页面缩放比例未改变 |
| 481 | 取值非法如负数、零或NaN，页面缩放比例未改变 |
| 482 | 应用禁用了缩放控制（`zoomControlAccess=false`），页面缩放比例未改变 |

### 测试页面

```html
<!-- index.html -->
<!DOCTYPE html>
<html>
  <body>
    <h1>Zoom Level Demo</h1>
    <p>当前缩放比例可通过getZoomLevel查询，通过setZoomLevel修改。</p>
  </body>
</html>
```

### 请求示例

```json
{
  "method": "setZoomLevel",
  "params": {
    "zoomLevel": 1.5
  }
}
```

### 返回示例

成功时（页面放大至150%）：

```json
{
  "code": 10,
  "message": "success"
}
```

失败：

`391`（缺少`zoomLevel`或为非数字类型）：

```json
{
  "code": 391,
  "message": "missing param: zoomLevel"
}
```

`480`（取值超出范围`[0.25, 5.0]`，页面缩放比例未改变）：

```json
{
  "code": 480,
  "message": "zoom level out of range"
}
```

`481`（取值非法如负数或零，页面缩放比例未改变）：

```json
{
  "code": 481,
  "message": "zoom level invalid"
}
```

`482`（应用禁用了缩放控制，页面缩放比例未改变）：

```json
{
  "code": 482,
  "message": "zoom control is disabled"
}
```
