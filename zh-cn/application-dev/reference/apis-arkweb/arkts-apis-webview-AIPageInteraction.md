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
> - 返回值非空时为JSON字符串，应用可通过`JSON.parse`解析后使用。
> - 当网页不可用、命令无法执行或无结果返回时，接口返回空字符串。
> - 查询类命令（getFullDom、getLiteDom）请参见[AIPageCommand](./arkts-apis-webview-AIPageCommand.md)。

## 命令总览

| method | 功能 | 入参格式 | 返回格式 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| [click](#click) | 点击目标元素 | [ClickCommand](#clickcommand) | 无 | 使目标元素响应点击事件(click event)，不关注是否产生真实的鼠标事件(mouse event)。 |
| [focus](#focus) | 使目标元素获取焦点 | [FocusCommand](#focuscommand) | 无 | 将焦点移动到目标元素，使其可以接收键盘输入等后续交互。 |
| [cursor_position](#cursor_position) | 获取当前文本插入符位置 | 无 | [CursorPositionResult](#cursorpositionresult) | 获取当前页面中文本插入符（caret）的位置，坐标相对于Web组件。 |
| [type](#type) | 向目标元素输入文本 | [TypeCommand](#typecommand) | 无 | 在目标元素指定位置插入文本，支持先清空后输入。若目标元素未获取焦点，先获取焦点再输入。 |
| [send_keys](#send_keys) | 发送键盘事件 | [SendKeysCommand](#sendkeyscommand) | 无 | 向前端发送键盘事件，支持功能键、数字键、字母键、符号键、编辑键、导航键和修饰键。 |

## 通用目标元素定位

`click`、`focus`、`type`命令需要通过目标元素定位参数指定操作对象，支持以下两种方式：

| 参数 | 类型 | 说明 |
| ---- | ---- | ---- |
| xpath | string | 目标元素的XPath，可通过[getFullDom](./arkts-apis-webview-AIPageCommand.md#getfulldom)或[getLiteDom](./arkts-apis-webview-AIPageCommand.md#getlitedom)获取。 |
| nodeid | string | 目标元素的节点标识，可通过[getFullDom](./arkts-apis-webview-AIPageCommand.md#getfulldom)或[getLiteDom](./arkts-apis-webview-AIPageCommand.md#getlitedom)返回的`id`字段获取。 |

> **说明：**
>
> - `xpath`与`nodeid`互斥，均传入时以`nodeid`为准。

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
>
### 返回说明

命令执行成功时返回空字符串。

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

空字符串。

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

命令执行成功时返回空字符串。

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

空字符串。

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

### 请求示例

```json
{
  "method": "cursor_position"
}
```

### 返回示例

```json
{
  "result": {
    "x": 100,
    "y": 200
  }
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
    "clear": true
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

命令执行成功时返回空字符串。

### 请求示例

```json
{
  "method": "type",
  "params": {
    "xpath": "/html[1]/body[1]/input[1]",
    "text": "Hello World",
    "index": 0,
    "clear": true
  }
}
```

### 返回示例

空字符串。

## send_keys

向前端发送键盘事件。

### SendKeysCommand

```json
{
  "method": "send_keys",
  "params": {
    "key": "PageDown",
    "keyaction": "keydown"
  }
}
```

### 入参说明

| 参数 | 子参数 | 参数项 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| method | - | - | string | 是 | 命令名称，固定为`send_keys`。 |
| params | - | - | Object | 是 | 命令参数。 |
| params | - | key | string | 是 | 需要发送的按键名称，取值请参见[send_keys的params.key字段取值说明](#send_keys的paramskey字段取值说明)。发送字母时大小写敏感。 |
| params | - | keyaction | string | 是 | 按键动作类型，取值为`keydown`或`keyup`。 |

> **说明：**
>
> - 发送字母时大小写敏感，例如`KeyA`和`Keya`表示不同的按键。
> - 可通过连续发送`keydown`和`keyup`模拟完整的按键操作。

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

### 返回说明

命令执行成功时返回空字符串。

### 请求示例

```json
{
  "method": "send_keys",
  "params": {
    "key": "PageDown",
    "keyaction": "keydown"
  }
}
```

### 返回示例

空字符串。
