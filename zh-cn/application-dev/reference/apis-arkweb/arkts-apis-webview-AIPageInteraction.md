# AIPageInteraction
<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhushengle-->
<!--Designer: @yyyiye-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->

从API版本26.0.0开始，`AIPageInteraction`定义[executeAIPageCommand](./arkts-apis-webview-WebviewController.md#executeaipagecommand)支持的页面交互类JSON命令协议，包括点击、聚焦、输入文本、发送键盘事件等操作的入参格式和返回格式。调用该接口前，应用需要将命令对象序列化为JSON字符串。

> **说明：**
>
> - `command`必须为JSON对象字符串。
> - `method`字段取值区分大小写，需使用[命令总览](#命令总览)中列出的取值。
> - 返回值为JSON字符串：成功时操作类命令返回`{"code":10,"message":"success"}`，查询类命令返回结果对象；失败时返回`{"code":<错误码>,"error":"<错误信息>"}`。应用可通过`JSON.parse`解析后使用。
> - 当网页不可用、命令无法执行或无结果返回时，接口返回空字符串。
> - 查询类命令（getFullDom、getLiteDom）请参见[AIPageCommand](./arkts-apis-webview-AIPageCommand.md)。

## 命令总览

| method | 功能 | 入参格式 | 返回格式 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| [click](#click) | 点击目标元素 | [ClickCommand](#clickcommand) | [返回格式](#返回格式) | 使目标元素响应点击事件(click event)，不关注是否产生真实的鼠标事件(mouse event)。 |
| [focus](#focus) | 使目标元素获取焦点 | [FocusCommand](#focuscommand) | [返回格式](#返回格式) | 将焦点移动到目标元素，使其可以接收键盘输入等后续交互。 |
| [cursor_position](#cursor_position) | 获取当前文本插入符位置 | 无 | [CursorPositionResult](#cursorpositionresult) | 获取当前页面中文本插入符（caret）的位置，坐标相对于Web组件。 |
| [type](#type) | 向目标元素输入文本 | [TypeCommand](#typecommand) | [返回格式](#返回格式) | 在目标元素指定位置插入文本，支持先清空后输入。若目标元素未获取焦点，先获取焦点再输入。 |
| [send_keys](#send_keys) | 发送键盘事件 | [SendKeysCommand](#sendkeyscommand) | [返回格式](#返回格式) | 向前端发送键盘事件，支持功能键、数字键、字母键、符号键、编辑键、导航键、修饰键及组合键。 |

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

任意命令失败时返回：

```json
{
  "code": <错误码>,
  "error": "<错误信息>"
}
```

错误码取值参见[错误码](#错误码)。

## 错误码

输入法模块错误码范围（400-479）：

### 通用错误（400-419）

| 错误码 | 枚举名 | 错误信息 | 适用范围 |
| ---- | ---- | ---- | ---- |
| 400 | INPUT_METHOD_NOT_FOUND | method not found | 全局 |
| 401 | INPUT_METHOD_UNKNOWN | unknown method | 全局 |
| 402 | INPUT_METHOD_NOT_BOUND | input method not bound | cursor_position |

### 点击/聚焦命令错误（420-439）

| 错误码 | 枚举名 | 错误信息 | 适用范围 |
| ---- | ---- | ---- | ---- |
| 420 | INPUT_CLICK_PARAMS_MISSING | click params not found | click、focus |
| 421 | INPUT_CLICK_NODEID_MISSING | click nodeid not found | click、focus |
| 422 | INPUT_CLICK_NODEID_EMPTY | click nodeid is empty | click、focus |
| 423 | INPUT_CLICK_DELEGATE_NULL | click delegate not initialized | click、focus |
| 424 | INPUT_CLICK_ELEMENT_NOT_FOUND | click element not exist | click、focus |

### 输入命令错误（440-459）

| 错误码 | 枚举名 | 错误信息 | 适用范围 |
| ---- | ---- | ---- | ---- |
| 440 | INPUT_TYPE_PARAMS_MISSING | type params not found | type |
| 441 | INPUT_TYPE_NODEID_MISSING | type nodeid not found | type |
| 442 | INPUT_TYPE_TEXT_MISSING | type text not found | type |
| 443 | INPUT_TYPE_XPATH_EMPTY | type xpath is empty | type |
| 444 | INPUT_TYPE_DELEGATE_NULL | type delegate not initialized | type |
| 445 | INPUT_TYPE_ELEMENT_NOT_FOUND | type element not exist | type |

### 发送按键命令错误（460-479）

| 错误码 | 枚举名 | 错误信息 | 适用范围 |
| ---- | ---- | ---- | ---- |
| 460 | INPUT_SEND_KEYS_PARAMS_MISSING | send_keys params not found | send_keys |
| 461 | INPUT_SEND_KEYS_KEY_MISSING | send_keys keys not found | send_keys |
| 462 | INPUT_SEND_KEYS_NO_VALID_KEYS | send_keys no valid keys | send_keys |
| 463 | INPUT_SEND_KEYS_UNKNOWN_KEY | send_keys unknown main key | send_keys |

> **说明：**
>
> - 元素定位字段缺失与为空的区分：未提供定位字段、或其值为空字符串，均返回对应命令的`*_NODEID_MISSING`（如421/441）；提供了`xpath`但值为空，返回`*_XPATH_EMPTY`（如443）。
> - send_keys的`key`字段：未提供`key`字段返回461；`key`为空字符串返回462；`key`值无法识别返回463。

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

420（未提供`params`字段）：

```json
{
  "code": 420,
  "error": "click params not found"
}
```

421（未提供`xpath`/`nodeid`或其值为空字符串）：

```json
{
  "code": 421,
  "error": "click nodeid not found"
}
```

422（定位字段解析后为空）：

```json
{
  "code": 422,
  "error": "click nodeid is empty"
}
```

423（Web实例不可用）：

```json
{
  "code": 423,
  "error": "click delegate not initialized"
}
```

424（未找到目标元素）：

```json
{
  "code": 424,
  "error": "click element not exist"
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

420（未提供`params`字段）：

```json
{
  "code": 420,
  "error": "click params not found"
}
```

421（未提供`xpath`/`nodeid`或其值为空字符串）：

```json
{
  "code": 421,
  "error": "click nodeid not found"
}
```

422（定位字段解析后为空）：

```json
{
  "code": 422,
  "error": "click nodeid is empty"
}
```

423（Web实例不可用）：

```json
{
  "code": 423,
  "error": "click delegate not initialized"
}
```

424（未找到目标元素）：

```json
{
  "code": 424,
  "error": "click element not exist"
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

400（输入功能不可用，找不到输入法处理器）：

```json
{
  "code": 400,
  "error": "method not found"
}
```

401（未知的命令名称，`method`字段取值无法识别）：

```json
{
  "code": 401,
  "error": "unknown method"
}
```

402（输入法未绑定）：

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

440（未提供`params`字段）：

```json
{
  "code": 440,
  "error": "type params not found"
}
```

441（未提供`xpath`/`nodeid`）：

```json
{
  "code": 441,
  "error": "type nodeid not found"
}
```

442（未提供`text`参数）：

```json
{
  "code": 442,
  "error": "type text not found"
}
```

443（提供了`xpath`但值为空）：

```json
{
  "code": 443,
  "error": "type xpath is empty"
}
```

444（Web实例不可用）：

```json
{
  "code": 444,
  "error": "type delegate not initialized"
}
```

445（未找到目标元素）：

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

460（未提供`params`字段）：

```json
{
  "code": 460,
  "error": "send_keys params not found"
}
```

461（未提供`key`字段）：

```json
{
  "code": 461,
  "error": "send_keys keys not found"
}
```

462（`key`为空字符串或无有效按键）：

```json
{
  "code": 462,
  "error": "send_keys no valid keys"
}
```

463（`key`值无法识别）：

```json
{
  "code": 463,
  "error": "send_keys unknown main key"
}
```
