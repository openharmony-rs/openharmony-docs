# @ohos.inputMethodEngine (输入法服务)

本模块面向输入法应用（包括系统输入法应用、三方输入法应用），为输入法应用提供能力，包括：创建软键盘窗口、插入/删除字符、选中文本、监听物理键盘按键事件等。

 > **说明：**
 >
 > - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
 > - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { inputMethodEngine } from '@kit.IMEKit';
```

## 常量

功能键常量值、编辑框常量值及光标常量值。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

| 名称 | 类型 | 值 | 说明 |
| -------- | -------- | -------- | -------- |
| ENTER_KEY_TYPE_UNSPECIFIED | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 0 | 无功能键。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| ENTER_KEY_TYPE_GO | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 2 | “前往”功能键。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| ENTER_KEY_TYPE_SEARCH | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 3 | “搜索”功能键。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| ENTER_KEY_TYPE_SEND | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 4 | “发送”功能键。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| ENTER_KEY_TYPE_NEXT | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 5 | “下一个”功能键。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| ENTER_KEY_TYPE_DONE | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 6 | “回车”功能键。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| ENTER_KEY_TYPE_PREVIOUS | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 7 | “前一个”功能键。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| ENTER_KEY_TYPE_NEWLINE<sup>12+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 8 | “换行”功能键。<br/>**ArkTS-Dyn起始版本：** 12<br/>**ArkTS-Sta起始版本：** 23 |
| PATTERN_NULL | ArkTS-Dyn: number<br/>ArkTS-Sta: int | -1 | 无特殊性编辑框。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| PATTERN_TEXT | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 0 | 文本编辑框。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| PATTERN_NUMBER | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 2 | 数字编辑框。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| PATTERN_PHONE | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 3 | 电话号码编辑框。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| PATTERN_DATETIME | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 4 | 日期编辑框。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| PATTERN_EMAIL | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 5 | 邮件编辑框。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| PATTERN_URI | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 6 | 超链接编辑框。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| PATTERN_PASSWORD | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 7 | 密码编辑框。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |+
| PATTERN_PASSWORD_NUMBER<sup>11+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 8 | 数字密码编辑框。<br/>**ArkTS-Dyn起始版本：** 11<br/>**ArkTS-Sta起始版本：** 23 |
| PATTERN_PASSWORD_SCREEN_LOCK<sup>11+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 9 | 锁屏密码编辑框。<br/>**ArkTS-Dyn起始版本：** 11<br/>**ArkTS-Sta起始版本：** 23 |
| PATTERN_USER_NAME<sup>20+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 10 | 用户名编辑框。<br/>**ArkTS-Dyn起始版本：** 20<br/>**ArkTS-Sta起始版本：** 23 |
| PATTERN_NEW_PASSWORD<sup>20+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 11 | 新密码编辑框。<br/>**ArkTS-Dyn起始版本：** 20<br/>**ArkTS-Sta起始版本：** 23 |
| PATTERN_NUMBER_DECIMAL<sup>20+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 12 | 带小数点的数字编辑框。<br/>**ArkTS-Dyn起始版本：** 20<br/>**ArkTS-Sta起始版本：** 23 |
| PATTERN_ONE_TIME_CODE<sup>20+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 13 | 验证码编辑框。<br/>**ArkTS-Dyn起始版本：** 20<br/>**ArkTS-Sta起始版本：** 23 |
| OPTION_ASCII | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 20 | 允许输入ASCII值。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| OPTION_NONE | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 0 | 不指定编辑框输入属性。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| OPTION_AUTO_CAP_CHARACTERS | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 2 | 允许输入字符。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| OPTION_AUTO_CAP_SENTENCES | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 8 | 允许输入句子。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| OPTION_AUTO_WORDS | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 4 | 允许输入单词。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| OPTION_MULTI_LINE | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 1 | 允许输入多行。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| OPTION_NO_FULLSCREEN | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 10 | 半屏样式。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| FLAG_SELECTING | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 2 | 编辑框处于选择状态。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| FLAG_SINGLE_LINE | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 1 | 编辑框为单行。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| DISPLAY_MODE_PART | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 0 | 编辑框显示为半屏。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| DISPLAY_MODE_FULL | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 1 | 编辑框显示为全屏。<br/>**ArkTS-Dyn起始版本：** 8<br/>**ArkTS-Sta起始版本：** 23 |
| CURSOR_UP<sup>9+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 1 | 光标上移。<br/>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23 |
| CURSOR_DOWN<sup>9+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 2 | 光标下移。<br/>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23 |
| CURSOR_LEFT<sup>9+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 3 | 光标左移。<br/>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23 |
| CURSOR_RIGHT<sup>9+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 4 | 光标右移。<br/>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23 |
| WINDOW_TYPE_INPUT_METHOD_FLOAT<sup>9+</sup> | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 2105 | 输入法应用窗口风格标识。<br/>**ArkTS-Dyn起始版本：** 9<br/>**ArkTS-Sta起始版本：** 23 |

## inputMethodEngine.getinputMethodAbility<sup>9+</sup>

ArkTS-Dyn: getinputMethodAbility(): inputMethodAbility

ArkTS-Sta: getinputMethodAbility(): inputMethodAbility | null

获取输入法应用客户端实例[inputMethodAbility](#inputmethodability)，仅支持输入法应用调用。<br/>输入法应用获取该实例后，可订阅软键盘显示/隐藏请求事件、创建/销毁输入法面板等。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                      | 说明               |
| ----------------------------------------- | ------------------ |
| ArkTS-Dyn: [inputMethodAbility](#inputmethodability) <br>ArkTS-Sta: [inputMethodAbility](#inputmethodability) \| null | 输入法应用客户端。 |

**示例：**

```ts
let inputMethodAbility = inputMethodEngine.getinputMethodAbility();
```

## inputMethodEngine.getKeyboardDelegate<sup>9+</sup>

ArkTS-Dyn: getKeyboardDelegate(): KeyboardDelegate

ArkTS-Sta: getKeyboardDelegate(): KeyboardDelegate | null

获取客户端编辑事件监听代理实例[KeyboardDelegate](#keyboarddelegate)。<br/>输入法应用获取该实例后，可订阅物理键盘按键事件、选中文本变化事件等。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                  | 说明                     |
| ------------------------------------- | ------------------------ |
| ArkTS-Dyn: [KeyboardDelegate](#keyboarddelegate) <br>ArkTS-Sta: [KeyboardDelegate](#keyboarddelegate) \| null | 客户端编辑事件监听代理。 |

**示例：**

```ts
let KeyboardDelegate = inputMethodEngine.getKeyboardDelegate();
```

## inputMethodEngine.getInputMethodEngine<sup>(deprecated)</sup>

getInputMethodEngine(): InputMethodEngine

获取输入法应用客户端实例[InputMethodEngine](#inputmethodengine)。<br/>输入法应用获取该实例后，可订阅软键盘显示/隐藏请求事件等。

> **说明：**
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[getinputMethodAbility()](#inputmethodenginegetinputmethodability9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**返回值：**

| 类型                                      | 说明               |
| ----------------------------------------- | ------------------ |
| [InputMethodEngine](#inputmethodengine) | 输入法应用客户端。 |

**示例：**

```ts
let InputMethodEngine = inputMethodEngine.getInputMethodEngine();
```

## inputMethodEngine.createKeyboardDelegate<sup>(deprecated)</sup>

createKeyboardDelegate(): KeyboardDelegate

获取客户端编辑事件监听代理实例[KeyboardDelegate](#keyboarddelegate)。输入法应用获取该实例后，可订阅物理键盘按键事件、选中文本变化事件等。

> **说明：**
>
>从API version 8开始支持，API version 9开始废弃，建议使用[getKeyboardDelegate()](#inputmethodenginegetkeyboarddelegate9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**返回值：**

| 类型                                  | 说明                     |
| ------------------------------------- | ------------------------ |
| [KeyboardDelegate](#keyboarddelegate) | 客户端编辑事件监听代理。 |

**示例：**

```ts
let keyboardDelegate = inputMethodEngine.createKeyboardDelegate();
```

## CommandDataType<sup>12+</sup>

ArkTS-Dyn: type CommandDataType = number | string | boolean

ArkTS-Sta: type CommandDataType = int | string | boolean

表示私有数据类型，接口参数具体类型根据其功能而定。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 类型    | 说明                 |
| ------- | -------------------- |
| string  | 表示值类型为字符串。  |
| ArkTS-Dyn: number<br/>ArkTS-Sta: int  | 表示值类型为数字。   |
| boolean | 表示值类型为布尔值。 |

## SizeChangeCallback<sup>15+</sup>

type SizeChangeCallback = (size: window.Size, keyboardArea?: KeyboardArea) => void

当输入法面板大小变化时触发的回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

| 参数名       | 类型                                                 | 必填 | 说明                             |
| ------------ | ---------------------------------------------------- | ---- | -------------------------------- |
| size         | [window.Size](../apis-arkui/arkts-apis-window-i.md#size7) | 是   | 当前面板大小。                   |
| keyboardArea | [KeyboardArea](#keyboardarea15)                      | 否   | 当前面板中可作为键盘区域的大小。 |

### IMAInputStartCallback<sup>23+</sup>

type IMAInputStartCallback = (kbController: KeyboardController, inputClient: InputClient) => void

输入法绑定成功事件的回调函数类型，用于定义inputStart事件触发时执行的回调函数格式。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名       | 类型                                                 | 必填 | 说明                             |
| ------------ | ---------------------------------------------------- | ---- | -------------------------------- |
| kbController     | [KeyboardController](#keyboardcontroller) | 是   | 回调函数，返回输入法操作相关实例。                 |
| inputClient  | [InputClient](#inputclient9) | 是   | 输入法操作相关实例。 |

### KeyEventCallback<sup>23+</sup>

type KeyEventCallback = (event: KeyEvent) => boolean

按键按下（keyDown）或按键抬起（keyUp）事件的回调函数类型，用于定义这两类按键事件触发时执行的回调函数格式。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| event | [KeyEvent](../apis-input-kit/js-apis-keyevent.md#keyevent) | 是 | 按键事件对象，包含按键码、按键类型、事件时间等按键相关信息。 |

**返回值：**

| 类型                                  | 说明                     |
| ------------------------------------- | ------------------------ |
| boolean | 是否消费该按键事件：返回true表示消费，系统不再向下传递该事件；返回false表示不消费，系统继续处理该事件。 |

### InputKeyEventCallback<sup>23+</sup>

type InputKeyEventCallback = (event: InputKeyEvent) => boolean

按键事件（keyEvent）的回调函数类型，用于定义keyEvent事件触发时执行的回调函数格式。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| event | [InputKeyEvent](../apis-input-kit/js-apis-input-keyevent.md#InputKeyEvent) | 是 | 输入按键事件对象，包含按键编码、事件类型、触发时间等按键事件相关信息。 |

**返回值：**

| 类型                                  | 说明                     |
| ------------------------------------- | ------------------------ |
| boolean | 是否消费该按键事件：返回true表示消费此事件，系统不再向下传递该事件；返回false表示不消费此事件，系统将继续处理该事件。 |

### CursorContextChangeCallback<sup>23+</sup>

type CursorContextChangeCallback = (x: double, y: double, height: double) => void

光标上下文变化（cursorContextChange）事件的回调函数类型，用于定义该事件触发时执行的回调函数格式。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| x | double | 是 | x为光标上端的的x坐标值，单位为px。 |
| y | double | 是 | y为光标上端的y坐标值，单位为px。 |
| height | double | 是 | eight为光标的高度值，单位为px。 |

## SelectionChangeCallback<sup>23+</sup>

type SelectionChangeCallback = (oldBegin: int, oldEnd: int, newBegin: int, newEnd: int) => void

文本选择范围变化（selectionChange）事件的回调函数类型，用于定义该事件触发时执行的回调函数格式。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| oldBegin | int | 是 |oldBegin为变化前被选中文本的起始下标。 |
| oldEnd | int | 是 | oldEnd为变化前被选中文本的终止下标。 |
| newBegin | int | 是 | newBegin为变化后被选中文本的起始下标。 |
| newEnd | int | 是 | newEnd为变化后被选中文本的终止下标。 |

## OnMessageCallback<sup>23+</sup>

type OnMessageCallback = (msgId: string, msgParam?: ArrayBuffer) => void

当输入法框架需要显示预览文本时触发的回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

| 参数名       | 类型          | 必填 | 说明                          |
| ------- | ----------------- | ---- | ----------------------------- |
| msgId    | string        | 是   | 接收到的自定义通信数据的标识符。  |
| msgParam   | ArrayBuffer | 否   | 接收到的自定义通信数据的消息体。 |

## InputMethodEngine

下列API均需使用[getInputMethodEngine](#inputmethodenginegetinputmethodenginedeprecated)获取到InputMethodEngine实例后，通过实例调用。

### on('inputStart')

on(type: 'inputStart', callback: (kbController: KeyboardController, textInputClient: TextInputClient) => void): void

订阅输入法绑定成功事件。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                        | 是   | 设置监听类型，固定取值为'inputStart'。 |
| callback | (kbController: [KeyboardController](#keyboardcontroller), textInputClient: [TextInputClient](#textinputclientdeprecated)) => void | 是 | 回调函数，返回订阅输入法的KeyboardController和TextInputClient实例。 |

**示例：**

```ts
inputMethodEngine.getInputMethodEngine()
  .on('inputStart', (kbController: inputMethodEngine.KeyboardController, textClient: inputMethodEngine.TextInputClient) => {
  let keyboardController = kbController;
  let textInputClient = textClient;
});
```

### off('inputStart')

off(type: 'inputStart', callback?: (kbController: KeyboardController, textInputClient: TextInputClient) => void): void

取消订阅输入法绑定成功事件。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名   | 类型                 | 必填 | 说明                     |
| -------- | -------------------- | ---- | ------------------------ |
| type | string                                                       | 是   | 设置监听类型，固定取值为'inputStart'。 |
| callback | (kbController: [KeyboardController](#keyboardcontroller), textInputClient: [TextInputClient](#textinputclientdeprecated)) => void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。|

**示例：**

```ts
inputMethodEngine.getInputMethodEngine()
  .off('inputStart', (kbController: inputMethodEngine.KeyboardController, textClient: inputMethodEngine.TextInputClient) => {
  console.info('delete inputStart notification.');
});
```

### on('keyboardShow'|'keyboardHide')

on(type: 'keyboardShow'|'keyboardHide', callback: () => void): void

订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | 是   | 设置监听类型。<br/>-'keyboardShow'表示显示输入法软键盘。<br/>-'keyboardHide'表示隐藏输入法软键盘。 |
| callback | () => void   | 是   | 回调函数。                                                   |

**示例：**

```ts
inputMethodEngine.getInputMethodEngine().on('keyboardShow', () => {
  console.info('inputMethodEngine keyboardShow.');
});
inputMethodEngine.getInputMethodEngine().on('keyboardHide', () => {
  console.info('inputMethodEngine keyboardHide.');
});
```

### off('keyboardShow'|'keyboardHide')

off(type: 'keyboardShow'|'keyboardHide', callback?: () => void): void

取消订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | 是   | 要取消监听的输入法软键盘类型。<br/>-'keyboardShow'表示显示输入法软键盘。<br/>-'keyboardHide'表示隐藏输入法软键盘。|
| callback | () => void   | 否   | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
inputMethodEngine.getInputMethodEngine().off('keyboardShow');
inputMethodEngine.getInputMethodEngine().off('keyboardHide');
```

## inputMethodAbility

下列API均需使用[getinputMethodAbility](#inputmethodenginegetinputmethodability9)获取到inputMethodAbility实例后，通过实例调用。

### on('inputStart')<sup>9+</sup>

on(type: 'inputStart', callback: (kbController: KeyboardController, inputClient: InputClient) => void): void

订阅输入法绑定成功事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onInputStart](#oninputstart23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                        | 是   | 设置监听类型，固定取值为'inputStart'。 |
| callback | (kbController: [KeyboardController](#keyboardcontroller), inputClient: [InputClient](#inputclient9)) => void | 是 | 回调函数，返回输入法操作相关实例。 |

**示例：**

```ts
  inputMethodEngine.getinputMethodAbility()
    .on('inputStart', (kbController: inputMethodEngine.KeyboardController, client: inputMethodEngine.InputClient) => {
    let keyboardController = kbController;
    let inputClient = client;
  });

```

### off('inputStart')<sup>9+</sup>

off(type: 'inputStart', callback?: (kbController: KeyboardController, inputClient: InputClient) => void): void

取消订阅输入法绑定成功事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offInputStart](#offinputstart23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名   | 类型                 | 必填 | 说明                     |
| -------- | -------------------- | ---- | ------------------------ |
| type | string                                                       | 是   | 设置监听类型，固定取值为'inputStart'。 |
| callback | (kbController: [KeyboardController](#keyboardcontroller), inputClient: [InputClient](#inputclient9)) => void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。|

**示例：**

```ts
inputMethodEngine.getinputMethodAbility().off('inputStart');
```

### on('inputStop')<sup>9+</sup>

on(type: 'inputStop', callback: () => void): void

订阅停止输入法应用事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onInputStop](#onInputStop23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | 是   | 设置监听类型，固定取值为'inputStop'。 |
| callback | () => void   | 是   | 回调函数。                        |

**示例：**

```ts
inputMethodEngine.getinputMethodAbility().on('inputStop', () => {
  console.info('inputMethodAbility inputStop');
});
```

### off('inputStop')<sup>9+</sup>

off(type: 'inputStop', callback: () => void): void

取消订阅停止输入法应用事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offInputStop](#offinputstop23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | 是   | 设置监听类型，固定取值为'inputStop'。 |
| callback | () => void   | 是   | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。        |

**示例：**

```ts
inputMethodEngine.getinputMethodAbility().off('inputStop', () => {
  console.info('inputMethodAbility delete inputStop notification.');
});
```

### on('setCallingWindow')<sup>9+</sup>

on(type: 'setCallingWindow', callback: (wid: number) => void): void

订阅设置调用窗口事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onSetCallingWindow](#onsetcallingwindow23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | 是   | 设置监听类型，固定取值为'setCallingWindow'。 |
| callback | (wid: number) => void | 是   | 回调函数，返回调用方窗口的Id。                     |

**示例：**

```ts
inputMethodEngine.getinputMethodAbility().on('setCallingWindow', (wid: number) => {
  console.info('inputMethodAbility setCallingWindow');
});
```

### off('setCallingWindow')<sup>9+</sup>

off(type: 'setCallingWindow', callback: (wid:number) => void): void

取消订阅设置调用窗口事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offSetCallingWindow](#offsetcallingwindow23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | 是   | 设置监听类型，固定取值为'setCallingWindow'。|
| callback | (wid:number) => void | 是   | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
inputMethodEngine.getinputMethodAbility().off('setCallingWindow', (wid: number) => {
  console.info('inputMethodAbility delete setCallingWindow notification.');
});
```

### on('keyboardShow'|'keyboardHide')<sup>9+</sup>

on(type: 'keyboardShow'|'keyboardHide', callback: () => void): void

订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onKeyboardShow](#onkeyboardshow23),[onKeyboardHide](#onkeyboardhide23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | 是   | 设置监听类型。<br/>- 'keyboardShow'表示显示输入法软键盘。<br/>- 'keyboardHide'表示隐藏输入法软键盘。 |
| callback | () => void   | 是   | 回调函数。                                                   |

**示例：**

```ts
inputMethodEngine.getinputMethodAbility().on('keyboardShow', () => {
  console.info('inputMethodAbility keyboardShow.');
});
inputMethodEngine.getinputMethodAbility().on('keyboardHide', () => {
  console.info('inputMethodAbility keyboardHide.');
});
```

### off('keyboardShow'|'keyboardHide')<sup>9+</sup>

off(type: 'keyboardShow'|'keyboardHide', callback?: () => void): void

取消订阅输入法事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offKeyboardShow](#offkeyboardshow23),[offKeyboardHide](#offkeyboardhide23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | 是   | 设置监听类型。<br/>- 'keyboardShow'表示显示键盘。<br/>- 'keyboardHide'表示隐藏键盘。 |
| callback | () => void   | 否   | 系统通知切换输入子类型时触发的指定回调函数。 |

**示例：**

```ts
inputMethodEngine.getinputMethodAbility().off('keyboardShow', () => {
  console.info('inputMethodAbility delete keyboardShow notification.');
});
inputMethodEngine.getinputMethodAbility().off('keyboardHide', () => {
  console.info('inputMethodAbility delete keyboardHide notification.');
});
```

### on('setSubtype')<sup>9+</sup>

on(type: 'setSubtype', callback: (inputMethodSubtype: InputMethodSubtype) => void): void

订阅设置输入法子类型事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onSetSubtype](#onsetsubtype23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名    | 类型 | 必填  | 说明 |
| -------- | --- | ---- | --- |
| type     | string | 是   | 设置监听类型，固定取值为'setSubtype'。 |
| callback | (inputMethodSubtype: [InputMethodSubtype](js-apis-inputmethod-subtype.md)) => void | 是   | 回调函数，返回设置的输入法子类型。                         |

**示例：**

```ts
import { InputMethodSubtype } from '@kit.IMEKit';

inputMethodEngine.getinputMethodAbility().on('setSubtype', (inputMethodSubtype: InputMethodSubtype) => {
  console.info('inputMethodAbility setSubtype.');
});
```

### off('setSubtype')<sup>9+</sup>

off(type: 'setSubtype', callback?: (inputMethodSubtype: InputMethodSubtype) => void): void

取消订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offSetSubtype](#offsetsubtype23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名   | 类型  | 必填 | 说明   |
| ------- | ----- | ---- | ---- |
| type     | string | 是   | 设置监听类型，固定取值为'setSubtype'。 |
| callback | (inputMethodSubtype: [InputMethodSubtype](js-apis-inputmethod-subtype.md)) => void | 否   | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。  |

**示例：**

```ts
inputMethodEngine.getinputMethodAbility().off('setSubtype', () => {
  console.info('inputMethodAbility delete setSubtype notification.');
});
```

### on('securityModeChange')<sup>11+</sup>

on(type: 'securityModeChange', callback: Callback< SecurityMode>): void

订阅输入法安全模式改变类型事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onSecurityModeChange](#onsecuritymodechange23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                           |
| -------- | ------------------------------------------- | ---- | ---------------------------------------------- |
| type     | string                                      | 是   | 设置监听类型，固定取值为'securityModeChange'。 |
| callback | Callback\<[SecurityMode](#securitymode11)> | 是   | 回调函数，返回当前输入法应用的安全模式。       |

**示例：**

```ts
inputMethodEngine.getinputMethodAbility().on('securityModeChange', (securityMode: inputMethodEngine.SecurityMode) => {
  console.info(`inputMethodAbility securityModeChange, security is ${securityMode}`);
});
```

### off('securityModeChange')<sup>11+</sup>

off(type: 'securityModeChange', callback?: Callback< SecurityMode>): void

取消订阅输入法安全模式改变类型事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offSecurityModeChange](#offsecuritymodechange23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                                         |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                      | 是   | 设置监听类型，固定取值为'securityModeChange'。               |
| callback | Callback\<[SecurityMode](#securitymode11)> | 否   | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
let securityChangeCallback = (securityMode: inputMethodEngine.SecurityMode) => {
  console.info(`inputMethodAbility securityModeChange, security is ${securityMode}`);
};
let inputMethodAbility = inputMethodEngine.getinputMethodAbility();
inputMethodAbility.on('securityModeChange', securityChangeCallback);
inputMethodAbility.off('securityModeChange', securityChangeCallback);
```

### on('privateCommand')<sup>12+</sup>

on(type: 'privateCommand', callback: Callback<Record<string, CommandDataType>>): void;

订阅输入法私有数据事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onPrivateCommand](#onprivatecommand23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名   | 类型                                          | 必填 | 说明                                       |
| -------- | --------------------------------------------- | ---- | ------------------------------------------ |
| type     | string                                        | 是   | 设置监听类型，固定取值为'privateCommand'。 |
| callback | Callback<Record<string, [CommandDataType](#commanddatatype12)>> | 是   | 回调函数，返回向输入法应用发送的私有数据。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                                       |
| -------- | ---------------------------------------------- |
| 12800010 | not the preconfigured default input method. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine } from '@kit.IMEKit';

let privateCommandCallback = (record: Record<string, inputMethodEngine.CommandDataType>) => {
  record.forEach((key, value) => {
    console.info(`private command key: ${key}, value: ${value}`);
  });
}
console.info(`regist private command `);
inputMethodEngine.getinputMethodAbility().on('privateCommand', privateCommandCallback);
```

### off('privateCommand')<sup>12+</sup>

off(type: 'privateCommand', callback?: Callback<Record<string, CommandDataType>>): void

取消订阅输入法私有数据事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offPrivateCommand](#offprivatecommand23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                                         |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                      | 是   | 设置监听类型，固定取值为'privateCommand'。                   |
| callback | Callback<Record<string, [CommandDataType](#commanddatatype12)>> | 否   | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                                       |
| -------- | ---------------------------------------------- |
| 12800010 | not the preconfigured default input method. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine } from '@kit.IMEKit';

let privateCommandCallback = (record: Record<string, inputMethodEngine.CommandDataType>) => {
  record.forEach((key, value) => {
    console.info(`private command key: ${key}, value: ${value}`);
  });
}
console.info(`regist private command `);
inputMethodEngine.getinputMethodAbility().off('privateCommand', privateCommandCallback);
```

### on('callingDisplayDidChange')<sup>18+</sup>

on(type: 'callingDisplayDidChange', callback: Callback\<number>): void

订阅编辑框对应窗口所在屏幕ID变化。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onCallingDisplayDidChange](#oncallingdisplaydidchange23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名   | 类型                                          | 必填 | 说明                                       |
| -------- | --------------------------------------------- | ---- | ------------------------------------------ |
| type     | string                                        | 是   | 设置监听类型，固定取值为'callingDisplayDidChange'。 |
| callback |  Callback\<number> | 是   | 回调函数，返回编辑框设置对应窗口屏幕ID。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                       |
| -------- | ---------------------------------------------- |
| 801 | capability not supported. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine } from '@kit.IMEKit';

let callingDisplayDidChangeCallback = (num: number) => {
  console.info(`display id: ${num}`);
}
console.info(`regist calling display changed`);
inputMethodEngine.getinputMethodAbility().on('callingDisplayDidChange', callingDisplayDidChangeCallback);
```

### off('callingDisplayDidChange')<sup>18+</sup>

off(type: 'callingDisplayDidChange', callback?: Callback\<number>): void

取消编辑框对应窗口所在屏幕ID变化。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offCallingDisplayDidChange](#offcallingdisplaydidchange23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 18

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                                         |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                      | 是   | 设置监听类型，固定取值为'callingDisplayDidChange'。                   |
| callback | Callback\<number>  | 否   | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine } from '@kit.IMEKit';

console.info(`unregist calling display changed `);
inputMethodEngine.getinputMethodAbility().off('callingDisplayDidChange', (num: number) => {
  console.info('inputMethodAbility delete calling display  notification.');
});

```

### on('discardTypingText')<sup>20+</sup>

on(type: 'discardTypingText', callback: Callback\<void>): void

订阅编辑框应用发送“清空候选词”事件到输入法。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onDiscardTypingText](#ondiscardtypingtext23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名   | 类型                                          | 必填 | 说明                                       |
| -------- | --------------------------------------------- | ---- | ------------------------------------------ |
| type     | string                                        | 是   | 设置监听类型，固定取值为'discardTypingText'。<br/> - 'discardTypingText'：表示订阅编辑框应用发送“清空候选词”事件到输入法。 |
| callback |  Callback\<void> | 是   | 回调函数。当命令发送成功，err为undefined，否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import inputMethodEngine from '@ohos.inputMethodEngine';

console.info(`discard the typing text`);
inputMethodEngine.getinputMethodAbility().on('discardTypingText', () => {
  console.info('inputMethodAbility discard the typing text.');
});
```

### off('discardTypingText')<sup>20+</sup>

off(type: 'discardTypingText', callback?: Callback\<void>): void

取消订阅编辑框应用发送“清空候选词”事件到输入法。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offDiscardTypingText](#offdiscardtypingtext23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                                         |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                      | 是   | 设置监听类型，固定取值为'discardTypingText'。<br/> - 'discardTypingText'：表示取消订阅编辑框应用发送“清空候选词”事件到输入法。 |
| callback | Callback\<void>  | 否   | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import inputMethodEngine from '@ohos.inputMethodEngine';

console.info(`discard the typing text`);
inputMethodEngine.getinputMethodAbility().off('discardTypingText', () => {
  console.info('inputMethodAbility discard the typing text.');
});
```

### getSecurityMode<sup>11+</sup>

getSecurityMode(): SecurityMode

获取输入法应用的当前安全模式。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                            | 说明       |
| ------------------------------- | ---------- |
| [SecurityMode](#securitymode11) | 安全模式。 |

**错误码：**

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 12800004 | not an input method application. |

**示例：**

```ts
let security: inputMethodEngine.SecurityMode= inputMethodEngine.getinputMethodAbility().getSecurityMode();
console.info(`getSecurityMode, securityMode is: ${security}`);
```

### createPanel<sup>10+</sup>

createPanel(ctx: BaseContext, info: PanelInfo, callback: AsyncCallback\<Panel>): void

创建输入法面板，仅支持输入法应用调用。使用callback异步回调。<br>单个输入法应用仅允许创建一个[软键盘类型](#paneltype10)和[状态栏类型](#paneltype10)的面板。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型        | 必填 | 说明                     |
| ------- | ----------- | ---- | ------------------------ |
| ctx     | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | 是   | 当前输入法应用上下文信息。 |
| info    | [PanelInfo](#panelinfo10)   | 是   | 输入法应用信息。 |
| callback | AsyncCallback\<[Panel](#panel10)> | 是   | 回调函数。当输入法面板创建成功，返回当前创建的输入法面板对象。  |

**错误码：**

| 错误码ID   | 错误信息                       |
| ---------- | ----------------------------- |
| 401        | parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 12800004   | not an input method application. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let panelInfo: inputMethodEngine.PanelInfo = {
  type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
  flag: inputMethodEngine.PanelFlag.FLG_FIXED
}
inputMethodEngine.getinputMethodAbility()
  .createPanel(this.context, panelInfo, (err: BusinessError, panel: inputMethodEngine.Panel) => {
  if (err) {
    console.error(`Failed to createPanel: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info('Succeed in creating panel.');
})

```

### createPanel<sup>10+</sup>

createPanel(ctx: BaseContext, info: PanelInfo): Promise\<Panel>

创建输入法面板，仅支持输入法应用调用。使用promise异步回调。<br>单个输入法应用仅允许创建一个[软键盘类型](#paneltype10)和[状态栏类型](#paneltype10)的面板。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名   | 类型        | 必填 | 说明                     |
| ------- | ----------- | ---- | ------------------------ |
| ctx     | [BaseContext](../apis-ability-kit/js-apis-inner-application-baseContext.md) | 是   | 当前输入法应用上下文信息。 |
| info    | [PanelInfo](#panelinfo10)   | 是   | 输入法面板信息。 |

**返回值：**
| 类型   | 说明                                                                 |
| ------- | ------------------------------------------------------------------ |
| Promise\<[Panel](#panel10)> | 回调函数。当输入法面板创建成功，返回当前创建的输入法面板对象。  |

**错误码：**

| 错误码ID   | 错误信息                       |
| ---------- | ----------------------------- |
| 401        | parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 12800004   | not an input method application. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let panelInfo: inputMethodEngine.PanelInfo = {
  type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
  flag: inputMethodEngine.PanelFlag.FLG_FIXED
}
inputMethodEngine.getinputMethodAbility().createPanel(this.context, panelInfo)
  .then((panel: inputMethodEngine.Panel) => {
    console.info('Succeed in creating panel.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create panel: code: ${err.code} ,message: ${err.message}`);
  })
```

### destroyPanel<sup>10+</sup>

destroyPanel(panel: Panel, callback: AsyncCallback\<void>): void

销毁输入法面板。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型        | 必填 | 说明                     |
| ------- | ----------- | ---- | ------------------------ |
| panel     | [Panel](#panel10) | 是   | 要销毁的面板对象。 |
| callback | AsyncCallback\<void> | 是   | 回调函数。当输入法面板销毁成功，err为undefined，否则为错误对象。  |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let panelInfo: inputMethodEngine.PanelInfo = {
  type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
  flag: inputMethodEngine.PanelFlag.FLG_FIXED
}
let inputPanel: inputMethodEngine.Panel | undefined = undefined;

inputMethodEngine.getinputMethodAbility()
.createPanel(this.context, panelInfo, (err: BusinessError, panel: inputMethodEngine.Panel) => {
  if (err) {
    console.error(`Failed to create panel: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  inputPanel = panel;
  console.info('Succeed in creating panel.');
})

if (inputPanel) {
  inputMethodEngine.getinputMethodAbility().destroyPanel(inputPanel, (err: BusinessError) => {
    if (err !== undefined) {
      console.error(`Failed to destroy panel: code: ${err.code} ,message: ${err.message}`);
      return;
    }
    console.info('Succeed in destroying panel.');
  })
}
```

### destroyPanel<sup>10+</sup>

destroyPanel(panel: Panel): Promise\<void>

销毁输入法面板。使用promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型        | 必填 | 说明                     |
| ---------| ----------- | ---- | ------------------------ |
| panel    | [Panel](#panel10)       | 是   | 要销毁的面板对象。      |

**返回值：**
| 类型    | 说明                                                                 |
| ------- | -------------------------------------------------------------------- |
| Promise\<void> | 无返回结果的Promise对象。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let panelInfo: inputMethodEngine.PanelInfo = {
  type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
  flag: inputMethodEngine.PanelFlag.FLG_FIXED
}
let inputPanel: inputMethodEngine.Panel | undefined = undefined;

inputMethodEngine.getinputMethodAbility()
  .createPanel(this.context, panelInfo, (err: BusinessError, panel: inputMethodEngine.Panel) => {
  if (err) {
    console.error(`Failed to create panel: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  inputPanel = panel;
  console.info('Succeed in creating panel.');
})

if (inputPanel) {
  inputMethodEngine.getinputMethodAbility().destroyPanel(inputPanel).then(() => {
    console.info('Succeed in destroying panel.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to destroy panel: code: ${err.code} ,message: ${err.message}`);
  });
}
```

### onInputStart<sup>23+</sup>

onInputStart(callback: IMAInputStartCallback): void

订阅输入法绑定成功事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('inputStart')](#oninputstart9)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| callback | [IMAInputStartCallback](#IMAInputStartCallback23) | 是 | 回调函数，返回订阅输入法的KeyboardController和TextInputClient实例。 |

**示例：**

```ts
let inputMethodAbility = inputMethodEngine.getinputMethodAbility();

inputMethodAbility!
.onInputStart((kbController: inputMethodEngine.KeyboardController, client: inputMethodEngine.InputClient) => {
  let keyboardController = kbController;
  let inputClient = client;
});

```

### offInputStart<sup>23+</sup>

offInputStart(callback?: IMAInputStartCallback): void

取消订阅输入法绑定成功事件。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('inputStart')](#offinputstart9)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| callback | [IMAInputStartCallback](#IMAInputStartCallback23) | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
let inputMethodAbility = inputMethodEngine.getinputMethodAbility();

inputMethodAbility!
  .offInputStart((kbController: inputMethodEngine.KeyboardController, textClient: inputMethodEngine.InputClient) => {
  console.info('delete inputStart notification.');
});
```

### onInputStop<sup>23+</sup>

onInputStop(callback: Callback&lt;void&gt;): void

订阅停止输入法应用事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('inputStop')](#oninputstop9)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;void&gt; | 是 | 系统要求输入法终止输入流程时触发的回调函数，无入参，用于执行输入停止后的清理逻辑（如隐藏键盘、释放资源等）。 |

**示例：**

```ts
let inputMethodAbility = inputMethodEngine.getinputMethodAbility();
inputMethodAbility!.onInputStop(() => {
  console.info('inputMethodAbility inputStop');
});
```

### offInputStop<sup>23+</sup>

offInputStop(callback: Callback&lt;void&gt;): void

取消订阅输入法输入停止（[inputStop](#onInputStop23)）事件，停止监听系统要求输入法终止输入流程的触发动作。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('inputStop')](#offinputstop9)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;void&gt; | 是 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
let inputMethodAbility = inputMethodEngine.getinputMethodAbility();
inputMethodAbility!.offInputStop(() => {
  console.info('inputMethodAbility delete inputStop notification.');
});
```

### onSetCallingWindow<sup>23+</sup>

onSetCallingWindow(callback: Callback&lt;int&gt;): void

订阅设置调用窗口事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('setCallingWindow')](#onsetcallingwindow9)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;int&gt;	 | 是 | 回调函数，返回调用方窗口的Id。 |

**示例：**

```ts
let inputMethodAbility = inputMethodEngine.getinputMethodAbility();
inputMethodAbility!.onSetCallingWindow((wid: int) => {
  console.info('inputMethodAbility setCallingWindow');
});
```

### offSetCallingWindow<sup>23+</sup>

offSetCallingWindow(callback: Callback&lt;int&gt;): void

取消订阅编辑框设置调用窗口 ID（[setCallingWindow](#onSetCallingWindow23)）事件，停止监听编辑框设置调用窗口标识的触发动作。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('setCallingWindow')](#offsetcallingwindow9)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;int&gt;	 | 是 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
let inputMethodAbility = inputMethodEngine.getinputMethodAbility();
inputMethodAbility!.offSetCallingWindow((wid: int) => {
  console.info('inputMethodAbility delete setCallingWindow notification.');
});
```

### onKeyboardShow<sup>23+</sup>

onKeyboardShow(callback:Callback&lt;void&gt;): void

订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('keyboardShow'|'keyboardHide')](#onkeyboardshowkeyboardhide9)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;void&gt;	 | 是 | 回调函数。 |


**示例：**

```ts
let inputMethodAbility = inputMethodEngine.getinputMethodAbility();
inputMethodAbility!.onKeyboardShow(() => {
  console.info('inputMethodEngine keyboardShow.');
});
inputMethodAbility!.onKeyboardHide(() => {
  console.info('inputMethodEngine keyboardHide.');
});
```

### offKeyboardShow<sup>23+</sup>

offKeyboardShow(callback?: Callback&lt;void&gt;): void

取消订阅输入法事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('keyboardShow'|'keyboardHide')](#offkeyboardshowkeyboardhide9)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;void&gt;	 | 否 | 	回调函数。 |


**示例：**

```ts
let inputMethodAbility = inputMethodEngine.getinputMethodAbility();

inputMethodAbility!.offKeyboardShow(() => {
  console.info('inputMethodAbility delete keyboardShow notification.');
});
inputMethodAbility!.offKeyboardHide(() => {
  console.info('inputMethodAbility delete keyboardHide notification.');
});
```

### onKeyboardHide<sup>23+</sup>

onKeyboardHide(callback: Callback&lt;void&gt;): void

订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('keyboardShow'|'keyboardHide')](#onkeyboardshowkeyboardhide9)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;void&gt;	 | 是 | 回调函数。 |

**示例：**

```ts
let inputMethodAbility = inputMethodEngine.getinputMethodAbility();
inputMethodAbility!.onKeyboardShow(() => {
  console.info('inputMethodEngine keyboardShow.');
});
inputMethodAbility!.onKeyboardHide(() => {
  console.info('inputMethodEngine keyboardHide.');
});
```

### offKeyboardHide<sup>23+</sup>

offKeyboardHide(callback?: Callback&lt;void&gt;): void

取消订阅输入法键盘隐藏（[keyboardHide](#onKeyboardHide23)）事件，停止监听输入法键盘隐藏的触发动作。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('keyboardShow'|'keyboardHide')](#offkeyboardshowkeyboardhide9)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;void&gt;	 | 否 | 系统通知切换输入子类型时触发的特定回调函数。 |

**示例：**

```ts
let inputMethodAbility = inputMethodEngine.getinputMethodAbility();
inputMethodAbility!.offKeyboardShow(() => {
  console.info('inputMethodAbility delete keyboardShow notification.');
});
inputMethodAbility!.offKeyboardHide(() => {
  console.info('inputMethodAbility delete keyboardHide notification.');
});
```

### onSetSubtype<sup>23+</sup>

onSetSubtype(callback: Callback&lt;InputMethodSubtype&gt;): void

订阅设置输入法子类型事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('setSubtype')](#onsetsubtype9)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| callback | [InputMethodSubtype](js-apis-inputmethod-subtype.md) | 是 | 回调函数，返回设置的输入法子类型。 |

**示例：**

```ts
import { InputMethodSubtype } from '@kit.IMEKit';
let inputMethodAbility = inputMethodEngine.getinputMethodAbility();

inputMethodAbility!.onSetSubtype((inputMethodSubtype: InputMethodSubtype) => {
  console.info('inputMethodAbility setSubtype.');
});
```

### offSetSubtype<sup>23+</sup>

offSetSubtype(callback?: Callback&lt;InputMethodSubtype&gt;): void

取消订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('setSubtype')](#offsetsubtype9)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| callback | [InputMethodSubtype](js-apis-inputmethod-subtype.md) | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
import { InputMethodSubtype } from '@kit.IMEKit';
let inputMethodAbility = inputMethodEngine.getinputMethodAbility();

inputMethodAbility!.onSetSubtype((inputMethodSubtype: InputMethodSubtype) => {
  console.info('inputMethodAbility setSubtype.');
});
```

### onSecurityModeChange<sup>23+</sup>

onSecurityModeChange(callback: Callback&lt;SecurityMode&gt;): void

订阅输入法安全模式改变类型事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('securityModeChange')](#onsecuritymodechange11)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| callback | [SecurityMode](#securitymode11) | 是 | 回调函数，返回当前输入法应用的安全模式。 |

**示例：**

```ts
let inputMethodAbility = inputMethodEngine.getinputMethodAbility();

inputMethodAbility!.onSecurityModeChange((securityMode: inputMethodEngine.SecurityMode) => {
  console.info(`inputMethodAbility securityModeChange, security is ${securityMode}`);
});
```

### offSecurityModeChange<sup>23+</sup>

offSecurityModeChange(callback?: Callback&lt;SecurityMode&gt;): void

取消订阅输入法安全模式改变类型事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('securityModeChange')](#offsecuritymodechange11)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                         |
| -------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| callback | [SecurityMode](#securitymode11) | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
let InputMethodEngine = inputMethodEngine.getinputMethodAbility();
let securityChangeCallback = (securityMode: inputMethodEngine.SecurityMode) => {
  console.info(`inputMethodAbility securityModeChange, security is ${securityMode}`);
};
InputMethodEngine.onSecurityModeChange(securityChangeCallback);
InputMethodEngine.offSecurityModeChange(securityChangeCallback);
```

### onPrivateCommand<sup>23+</sup>

onPrivateCommand(callback: Callback&lt;Record&lt;string, CommandDataType&gt;&gt;): void

订阅输入法私有数据事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('privateCommand')](#onprivatecommand12)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | Callback&lt;Record&lt;string, [CommandDataType](#commanddatatype12)&gt;&gt;	 | 是 |  回调函数，返回向输入法应用发送的私有数据。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                                       |
| -------- | ---------------------------------------------- |
| 12800010 | not the preconfigured default input method. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine } from '@kit.IMEKit';

let inputMethodAbility = inputMethodEngine.getinputMethodAbility();

let privateCommandCallback = (record: Record<string, inputMethodEngine.CommandDataType>) => {
  record.forEach((key, value) => {
    console.info(`private command key: ${key}, value: ${value}`);
  });
}

console.info(`regist private command `);
inputMethodAbility!.onPrivateCommand(privateCommandCallback);
```

### offPrivateCommand<sup>23+</sup>

offPrivateCommand(callback?: Callback&lt;Record&lt;string, CommandDataType&gt;&gt;): void

取消订阅输入法私有数据事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('privateCommand')](#offprivatecommand12)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | Callback&lt;Record&lt;string, [CommandDataType](#commanddatatype12)&gt;&gt;	 | 否  |  取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                                       |
| -------- | ---------------------------------------------- |
| 12800010 | not the preconfigured default input method. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine } from '@kit.IMEKit';

let inputMethodAbility = inputMethodEngine.getinputMethodAbility();
let privateCommandCallback = (record: Record<string, inputMethodEngine.CommandDataType>) => {
  record.forEach((key, value) => {
    console.info(`private command key: ${key}, value: ${value}`);
  });
}
console.info(`regist private command `);
inputMethodAbility!.offPrivateCommand(privateCommandCallback);
```

### onCallingDisplayDidChange<sup>23+</sup>

onCallingDisplayDidChange(callback: Callback&lt;int&gt;): void

订阅编辑框对应窗口所在屏幕ID变化。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('callingDisplayDidChange')](#oncallingdisplaydidchange18)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | Callback&lt;int&gt; | 是 |  回调函数，返回编辑框设置对应窗口屏幕ID。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                       |
| -------- | ---------------------------------------------- |
| 801 | capability not supported. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine } from '@kit.IMEKit';

let inputMethodAbility = inputMethodEngine.getinputMethodAbility();
let callingDisplayDidChangeCallback = (num: int) => {
  console.info(`display id: ${num}`);
}

console.info(`regist calling display changed`);
inputMethodAbility!.onCallingDisplayDidChange(callingDisplayDidChangeCallback);
```

### offCallingDisplayDidChange<sup>23+</sup>

offCallingDisplayDidChange(callback?: Callback&lt;int&gt;): void

取消编辑框对应窗口所在屏幕ID变化。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('callingDisplayDidChange')](#offcallingdisplaydidchange18)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | Callback&lt;int&gt;| 否  | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine } from '@kit.IMEKit';

let inputMethodAbility = inputMethodEngine.getinputMethodAbility();

console.info(`unregist calling display changed `);
inputMethodAbility!.offCallingDisplayDidChange((num: int) => {
  console.info('inputMethodAbility delete calling display  notification.');
});
```

### onDiscardTypingText<sup>23+</sup>

onDiscardTypingText(callback: Callback&lt;void&gt;): void

订阅编辑框应用发送“清空候选词”事件到输入法。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('discardTypingText')](#ondiscardtypingtext20)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | 	Callback&lt;void&gt; | 是  | 回调函数。当命令发送成功，err为undefined，否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import inputMethodEngine from '@ohos.inputMethodEngine';

let inputMethodAbility = inputMethodEngine.getinputMethodAbility();
console.info(`discard the typing text`);
inputMethodAbility!.onDiscardTypingText(() => {
  console.info('inputMethodAbility discard the typing text.');
});
```

### offDiscardTypingText<sup>23+</sup>

offDiscardTypingText(callback?: Callback&lt;void&gt;): void

取消订阅编辑框应用发送“清空候选词”事件到输入法。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('discardTypingText')](#offdiscardtypingtext20)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | 	Callback&lt;void&gt; | 否  | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import inputMethodEngine from '@ohos.inputMethodEngine';

let inputMethodAbility = inputMethodEngine.getinputMethodAbility();
console.info(`discard the typing text`);
inputMethodAbility!.offDiscardTypingText(() => {
  console.info('inputMethodAbility discard the typing text.');
});
```

## KeyboardDelegate

下列API均需使用[getKeyboardDelegate](#inputmethodenginegetkeyboarddelegate9)获取到KeyboardDelegate实例后，通过实例调用。

### on('keyDown'|'keyUp')

on(type: 'keyDown'|'keyUp', callback: (event: KeyEvent) => boolean): void

订阅硬键盘（即物理键盘）上物理按键的按下或抬起事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onKeyDown](#onkeydown23)，[onKeyUp](#onkeyup23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名   | 类型                            | 必填 | 说明                                                  |
| -------- | ------------------------------- | ---- |-----------------------------------------------------|
| type   | string         | 是   | 设置监听类型。<br/>- 'keyDown'表示键盘按下。<br/>- 'keyUp'表示键盘抬起。 |
| callback | (event: [KeyEvent](#keyevent)) => boolean | 是 | 回调函数，返回按键信息。 若按键事件被事件订阅者消费，则callback应返回true，否则返回false。   |

**示例：**

```ts

inputMethodEngine.getKeyboardDelegate().on('keyUp', (keyEvent: inputMethodEngine.KeyEvent) => {
  console.info(`inputMethodEngine keyCode.(keyDown): ${keyEvent.keyCode}`);
  console.info(`inputMethodEngine keyAction.(keyDown): ${keyEvent.keyAction}`);
  return true;
});
inputMethodEngine.getKeyboardDelegate().on('keyDown', (keyEvent: inputMethodEngine.KeyEvent) => {
  console.info(`inputMethodEngine keyCode.(keyDown): ${keyEvent.keyCode}`);
  console.info(`inputMethodEngine keyAction.(keyDown): ${keyEvent.keyAction}`);
  return true;
});

```

### off('keyDown'|'keyUp')

off(type: 'keyDown'|'keyUp', callback?: (event: KeyEvent) => boolean): void

取消订阅硬键盘（即物理键盘）上物理按键的按下或抬起事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offKeyDown](#offkeydown23)，[offKeyUp](#offkeyup23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名    | 类型     | 必填  | 说明  |
| -------- | ------- | ---- | ----- |
| type     | string  | 是   | 设置监听类型。<br/>- 'keyDown'表示键盘按下。<br/>- 'keyUp'表示键盘抬起。 |
| callback | (event: [KeyEvent](#keyevent)) => boolean | 否   | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。   |

**示例：**

```ts
inputMethodEngine.getKeyboardDelegate().off('keyUp', (keyEvent: inputMethodEngine.KeyEvent) => {
  console.info('delete keyUp notification.');
  return true;
});
inputMethodEngine.getKeyboardDelegate().off('keyDown', (keyEvent: inputMethodEngine.KeyEvent) => {
  console.info('delete keyDown notification.');
  return true;
});
```

### on('keyEvent')<sup>10+</sup>

on(type: 'keyEvent', callback: (event: InputKeyEvent) => boolean): void

订阅硬键盘（即物理键盘）事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onKeyEvent](#onkeyevent23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型     | 必填 | 说明                                                         |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | 是   | 设置监听类型，固定取值为'keyEvent'。 |
| callback | (event: [InputKeyEvent](../apis-input-kit/js-apis-keyevent.md#keyevent)) => boolean | 是   | 回调函数，入参为按键事件信息，返回值类型为布尔类型。<br/>-&nbsp;入参按键事件信息的数据类型为[InputKeyEvent](../apis-input-kit/js-apis-keyevent.md#keyevent)。<br/>-&nbsp;若按键事件被事件订阅者消费，则callback应返回true，否则返回false。|

**示例：**

```ts
import type { KeyEvent } from '@kit.InputKit';

inputMethodEngine.getKeyboardDelegate().on('keyEvent', (keyEvent: KeyEvent) => {
  console.info(`inputMethodEngine keyEvent.action: ${keyEvent.action}`);
  console.info(`inputMethodEngine keyEvent.key.code: ${keyEvent.key.code}`);
  console.info(`inputMethodEngine keyEvent.ctrlKey: ${keyEvent.ctrlKey}`);
  console.info(`inputMethodEngine keyEvent.unicodeChar: ${keyEvent.unicodeChar}`);
  return true;
});
```

### off('keyEvent')<sup>10+</sup>

off(type: 'keyEvent', callback?: (event: InputKeyEvent) => boolean): void

取消订阅硬键盘（即物理键盘）事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offKeyEvent](#offkeyevent23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型     | 必填 | 说明                                                         |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| type     | string   | 是   | 设置监听类型，固定取值为'keyEvent'。 |
| callback | function | 否   | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。|

**示例：**

```ts
import type { KeyEvent } from '@kit.InputKit';

inputMethodEngine.getKeyboardDelegate().off('keyEvent', (keyEvent: KeyEvent) => {
  console.info('This is a callback function which will be deregistered.');
  return true;
});
inputMethodEngine.getKeyboardDelegate().off('keyEvent');
```

### on('cursorContextChange')

on(type: 'cursorContextChange', callback: (x: number, y:number, height:number) => void): void

订阅光标变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onCursorContextChange](#oncursorcontextchange23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名    | 类型  | 必填  | 说明  |
| -------- | ---- | ---- | ----- |
| type     | string | 是   | 光标变化事件，固定取值为'cursorContextChange'。 |
| callback | (x: number, y: number, height: number) => void | 是   | 回调函数，返回光标信息。<br/>-x为光标上端的的x坐标值，单位为px。y为光标上端的y坐标值，单位为px。height为光标的高度值，单位为px。 |

**示例：**

```ts
inputMethodEngine.getKeyboardDelegate().on('cursorContextChange', (x: number, y: number, height: number) => {
  console.info(`inputMethodEngine cursorContextChange x: ${x}`);
  console.info(`inputMethodEngine cursorContextChange y: ${y}`);
  console.info(`inputMethodEngine cursorContextChange height: ${height}`);
});
```

### off('cursorContextChange')

off(type: 'cursorContextChange', callback?: (x: number, y: number, height: number) => void): void

取消订阅光标变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offCursorContextChange](#offcursorcontextchange23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

  **参数：**

| 参数名    | 类型  | 必填  | 说明   |
| -------- | ---- | ---- | ------ |
| type     | string  | 是   | 光标变化事件，固定取值为'cursorContextChange'。 |
| callback | (x: number, y:number, height:number) => void | 否   | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |


  **示例：**

```ts
inputMethodEngine.getKeyboardDelegate().off('cursorContextChange', (x: number, y: number, height: number) => {
  console.info('delete cursorContextChange notification.');
});
```
### on('selectionChange')

on(type: 'selectionChange', callback: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void): void

订阅文本选择范围变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onSelectionChange](#onselectionchange23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名    | 类型   | 必填 | 说明   |
| -------- | ----- | ---- | ---- |
| type     | string  | 是   | 文本选择变化事件，固定取值为'selectionChange'。 |
| callback | (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void | 是   | 回调函数，返回文本选择信息。<br/>- oldBegin为变化前被选中文本的起始下标，oldEnd为变化前被选中文本的终止下标。<br/>- newBegin为变化后被选中文本的起始下标，newEnd为变化后被选中文本的终止下标。|

**示例：**

```ts

inputMethodEngine.getKeyboardDelegate()
  .on('selectionChange', (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => {
  console.info(`inputMethodEngine beforeEach selectionChange oldBegin: ${oldBegin}`);
  console.info(`inputMethodEngine beforeEach selectionChange oldEnd: ${oldEnd}`);
  console.info(`inputMethodEngine beforeEach selectionChange newBegin:' ${newBegin}`);
  console.info(`inputMethodEngine beforeEach selectionChange newEnd: ${newEnd}`);
});
```

### off('selectionChange')

off(type: 'selectionChange', callback?: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void): void

取消订阅文本选择范围变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offSelectionChange](#offselectionchange23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名   | 类型  | 必填 | 说明     |
| -------- | ------- | ---- | ------- |
| type     | string  | 是   | 文本选择变化事件，固定取值为'selectionChange'。 |
| callback | (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void | 否   | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。|

**示例：**

```ts

inputMethodEngine.getKeyboardDelegate()
.off('selectionChange', (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number)  => {
  console.info('delete selectionChange notification.');
});

```


### on('textChange')

on(type: 'textChange', callback: (text: string) => void): void

订阅文本内容变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onTextChange](#ontextchange23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | 是   | 文本变化事件，固定取值为'textChange'。 |
| callback | (text: string) => void | 是   | 回调函数，返回订阅的文本内容。|

**示例：**

```ts
inputMethodEngine.getKeyboardDelegate().on('textChange', (text: string) => {
  console.info(`inputMethodEngine textChange. text:' ${text}`);
});
```

### off('textChange')

off(type: 'textChange', callback?: (text: string) => void): void

取消订阅文本内容变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offTextChange](#offtextchange23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | 是   | 文本变化事件，固定取值为'textChange'。 |
| callback | (text: string) => void | 否   | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。|

**示例：**

```ts
inputMethodEngine.getKeyboardDelegate().off('textChange', (text: string) => {
  console.info(`delete textChange notification. text:' ${text}`);
});
```

### on('editorAttributeChanged')<sup>10+</sup>

on(type: 'editorAttributeChanged', callback: (attr: EditorAttribute) => void): void

订阅编辑框属性变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onEditorAttributeChanged](#oneditorattributechanged23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | 是   | 文本变化事件，固定取值为'editorAttributeChanged'。 |
| callback | (attr: [EditorAttribute](#editorattribute)) => void | 是   | 回调函数，返回变化的编辑框属性。|

**示例：**

```ts

inputMethodEngine.getKeyboardDelegate().on('editorAttributeChanged', (attr: inputMethodEngine.EditorAttribute) => {
  console.info(`Succeeded in receiving attribute of editor, inputPattern =    ${attr.inputPattern}, enterKeyType = ${attr.enterKeyType}`);
});

```

### off('editorAttributeChanged')<sup>10+</sup>

off(type: 'editorAttributeChanged', callback?: (attr: EditorAttribute) => void): void

取消订阅编辑框属性变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offEditorAttributeChanged](#offeditorattributechanged23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| type     | string | 是   | 文本变化事件，固定取值为'editorAttributeChanged'。 |
| callback | (attr: [EditorAttribute](#editorattribute)) => void | 否   | 所要取消订阅的回调处理函数。参数不填写时，默认取消订阅type对应的所有回调事件。 |

**示例：**

```ts
inputMethodEngine.getKeyboardDelegate().off('editorAttributeChanged');
```

### onKeyDown<sup>23+</sup>

onKeyDown(callback: KeyEventCallback): void

订阅硬键盘（即物理键盘）上物理按键的按下或抬起事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('keyDown'|'keyUp')](#onkeydownkeyup)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [KeyEventCallback](#KeyEventCallback23) | 是 | 回调函数，返回按键信息。 若按键事件被事件订阅者消费，则callback应返回true，否则返回false。 |

**示例：**

```ts
let KeyboardDelegate = inputMethodEngine.getKeyboardDelegate()
let inputMethodEngineDelegate = inputMethodEngine.getKeyboardDelegate();
if (inputMethodEngineDelegate) {
  
  inputMethodEngineDelegate!.onKeyUp((keyEvent: inputMethodEngine.KeyEvent) => {
    console.info(`inputMethodEngine keyCode.(keyDown): ${keyEvent.keyCode}`);
    console.info(`inputMethodEngine keyAction.(keyDown): ${keyEvent.keyAction}`);
    return true;
  });
  inputMethodEngineDelegate!.onKeyDown((keyEvent: inputMethodEngine.KeyEvent) => {
    console.info(`inputMethodEngine keyCode.(keyDown): ${keyEvent.keyCode}`);
    console.info(`inputMethodEngine keyAction.(keyDown): ${keyEvent.keyAction}`);
    return true;
  });
}
  
```

### offKeyDown<sup>23+</sup>

offKeyDown(callback?: KeyEventCallback): void

取消订阅硬键盘（即物理键盘）上物理按键的按下或抬起事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('keyDown'|'keyUp')](#offkeydownkeyup)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [KeyEventCallback](#KeyEventCallback23) | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
let inputMethodEngineDelegate = inputMethodEngine.getKeyboardDelegate();
if (inputMethodEngineDelegate) {
  inputMethodEngineDelegate!.offKeyUp((keyEvent: inputMethodEngine.KeyEvent) => {
    console.info('delete keyUp notification.');
    return true;
  });
  inputMethodEngineDelegate!.offKeyDown((keyEvent: inputMethodEngine.KeyEvent) => {
    console.info('delete keyDown notification.');
    return true;
  });
}
```

### onKeyUp<sup>23+</sup>

onKeyUp(callback: KeyEventCallback): void

订阅硬键盘（即物理键盘）上物理按键的按下或抬起事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('keyDown'|'keyUp')](#onkeydownkeyup)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [KeyEventCallback](#keyeventcallback23) | 是 | 回调函数，返回按键信息。 若按键事件被事件订阅者消费，则callback应返回true，否则返回false。 |

**示例：**

```ts
let inputMethodEngineDelegate = inputMethodEngine.getKeyboardDelegate();
if (inputMethodEngineDelegate) {
  inputMethodEngineDelegate!.onKeyUp((keyEvent: inputMethodEngine.KeyEvent) => {
    console.info(`inputMethodEngine keyCode.(keyDown): ${keyEvent.keyCode}`);
    console.info(`inputMethodEngine keyAction.(keyDown): ${keyEvent.keyAction}`);
    return true;
  });
  inputMethodEngineDelegate!.onKeyDown((keyEvent: inputMethodEngine.KeyEvent) => {
    console.info(`inputMethodEngine keyCode.(keyDown): ${keyEvent.keyCode}`);
    console.info(`inputMethodEngine keyAction.(keyDown): ${keyEvent.keyAction}`);
    return true;
  });
} 
```

### offKeyUp<sup>23+</sup>

offKeyUp(callback?: KeyEventCallback): void

取消订阅硬键盘（即物理键盘）上物理按键的按下或抬起事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('keyDown'|'keyUp')](#offkeydownkeyup)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [KeyEventCallback](#KeyEventCallback23) | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
let inputMethodEngineDelegate = inputMethodEngine.getKeyboardDelegate();
if (inputMethodEngineDelegate) {
  inputMethodEngineDelegate!.offKeyUp((keyEvent: inputMethodEngine.KeyEvent) => {
    console.info('delete keyUp notification.');
    return true;
  });
  inputMethodEngineDelegate!.offKeyDown((keyEvent: inputMethodEngine.KeyEvent) => {
    console.info('delete keyDown notification.');
    return true;
  });
}
```

### onKeyEvent<sup>23+</sup>

onKeyEvent(callback: InputKeyEventCallback): void

订阅硬键盘（即物理键盘）事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('keyEvent')](#onkeyevent10)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23
[KeyboardController](#keyboardcontroller)
**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [InputKeyEventCallback](#InputKeyEventCallback23) | 是 | 回调函数，入参为按键事件信息，返回值类型为布尔类型。<br/>-&nbsp;入参按键事件信息的数据类型为[InputKeyEvent](../apis-input-kit/js-apis-keyevent.md#keyevent)。<br/>-&nbsp;若按键事件被事件订阅者消费，则callback应返回true，否则返回false。 |

**示例：**

```ts
import type { KeyEvent } from '@kit.InputKit';

let inputMethodEngineDelegate = inputMethodEngine.getKeyboardDelegate();
if (inputMethodEngineDelegate) {
  inputMethodEngineDelegate!.onKeyEvent((keyEvent: KeyEvent) => {
    console.info(`inputMethodEngine keyEvent.action: ${keyEvent.action}`);
    console.info(`inputMethodEngine keyEvent.key.code: ${keyEvent.key.code}`);
    console.info(`inputMethodEngine keyEvent.ctrlKey: ${keyEvent.ctrlKey}`);
    console.info(`inputMethodEngine keyEvent.unicodeChar: ${keyEvent.unicodeChar}`);
    return true;
  });
}
```

### offKeyEvent<sup>23+</sup>

offKeyEvent(callback?: InputKeyEventCallback): void

取消订阅硬键盘（即物理键盘）事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('keyEvent')](#offkeyevent10)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [InputKeyEventCallback](#InputKeyEventCallback23) | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
import type { KeyEvent } from '@kit.InputKit';

let inputMethodEngineDelegate = inputMethodEngine.getKeyboardDelegate();
if (inputMethodEngineDelegate) {
  inputMethodEngineDelegate!.offKeyEvent((keyEvent: KeyEvent) => {
    console.info('This is a callback function which will be deregistered.');
    return true;
  });
  inputMethodEngineDelegate!.offKeyEvent();
}
```

### onCursorContextChange<sup>23+</sup>

onCursorContextChange(callback: CursorContextChangeCallback): void

订阅光标变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('CursorcontextChange')](#cursorcontextchange)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [CursorContextChangeCallback](#CursorContextChangeCallback23) | 是 | 回调函数，返回光标信息。<br/>-x为光标上端的的x坐标值，单位为px。y为光标上端的y坐标值，单位为px。height为光标的高度值，单位为px。|

**示例：**

```ts
let inputMethodEngineDelegate = inputMethodEngine.getKeyboardDelegate();
if (inputMethodEngineDelegate) {
  inputMethodEngineDelegate!.onCursorContextChange((x: double, y: double, height: double) => {
    console.info(`inputMethodEngine cursorContextChange x:${x}, y:${y}, height:${height}`);
  });
}
```

### offCursorContextChange<sup>23+</sup>

offCursorContextChange(callback?: CursorContextChangeCallback): void

取消订阅光标上下文变更[cursorcontextchange](#onCursorContextChange23)事件，停止监听编辑框中光标位置及上下文文本的变更动作。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('cursorcontextChange')](#offcursorcontextchange)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [CursorContextChangeCallback](#CursorContextChangeCallback23) | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
let inputMethodEngineDelegate = inputMethodEngine.getKeyboardDelegate();
if (inputMethodEngineDelegate) {
  inputMethodEngineDelegate!.offCursorContextChange((x: double, y: double, height: double) => {
    console.info('delete cursorContextChange notification.');
  });
}
```

### onSelectionChange<sup>23+</sup>

onSelectionChange(callback: SelectionChangeCallback): void

订阅文本选择范围变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('selectionChange')](#onselectionchange)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [SelectionChangeCallback](#SelectionChangeCallback23) | 是 | 回调函数，返回文本选择信息。<br/>- oldBegin为变化前被选中文本的起始下标，oldEnd为变化前被选中文本的终止下标。<br/>- newBegin为变化后被选中文本的起始下标，newEnd为变化后被选中文本的终止下标。 |

**示例：**

```ts
let inputMethodEngineDelegate = inputMethodEngine.getKeyboardDelegate();
if (inputMethodEngineDelegate) {
  inputMethodEngineDelegate!
    .onSelectionChange((oldBegin: int, oldEnd: int, newBegin: int, newEnd: int) => {
      console.info(`inputMethodEngine beforeEach selectionChange oldBegin: ${oldBegin}`);
      console.info(`inputMethodEngine beforeEach selectionChange oldEnd: ${oldEnd}`);
      console.info(`inputMethodEngine beforeEach selectionChange newBegin: ${newBegin}`);
      console.info(`inputMethodEngine beforeEach selectionChange newEnd: ${newEnd}`);
    });
  
}
```

### offSelectionChange<sup>23+</sup>

offSelectionChange(callback?: SelectionChangeCallback): void

取消订阅文本选择范围变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('selectionChange')](#offselectionchange)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | [SelectionChangeCallback](#SelectionChangeCallback23) | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
let inputMethodEngineDelegate = inputMethodEngine.getKeyboardDelegate();
if (inputMethodEngineDelegate) {
  inputMethodEngineDelegate!.offSelectionChange((oldBegin: int, oldEnd: int, newBegin: int, newEnd: int) => {
    console.info('delete selectionChange notification.');
  });
}
```

### onTextChange<sup>23+</sup>

onTextChange(callback: Callback&lt;string&gt;): void

订阅文本内容变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('textChange')](#ontextchange)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;string&gt; | 是 | 回调函数，返回订阅的文本内容。 |

**示例：**

```ts
let inputMethodEngineDelegate = inputMethodEngine.getKeyboardDelegate();
if (inputMethodEngineDelegate) {
  inputMethodEngineDelegate!.onTextChange((text: string) => {
    console.info(`inputMethodEngine textChange. text: ' ${text}`);
  });
}
```

### offTextChange<sup>23+</sup>

offTextChange(callback?: Callback&lt;string&gt;): void

取消订阅文本内容变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('textChange')](#offtextchange)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;string&gt; | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
let inputMethodEngineDelegate = inputMethodEngine.getKeyboardDelegate();
if (inputMethodEngineDelegate) {
  inputMethodEngineDelegate!.offTextChange((text: string) => {
    console.info(`delete textChange notification. text: ${text}`);
  });
}
```

### onEditorAttributeChanged<sup>23+</sup>

onEditorAttributeChanged(callback: Callback&lt;EditorAttribute&gt;): void

订阅编辑框属性变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('editorAttributeChanged')](#oneditorattributechanged10)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[EditorAttribute](#editorattribute)&gt; | 是 | 回调函数，返回变化的编辑框属性。 |

**示例：**

```ts
let inputMethodEngineDelegate = inputMethodEngine.getKeyboardDelegate();
if (inputMethodEngineDelegate) {
  inputMethodEngineDelegate!.onEditorAttributeChanged((attr: inputMethodEngine.EditorAttribute) => {
    console.info(`Succeeded in receiving attribute of editor, inputPattern = ${attr.inputPattern}, enterKeyType = ${attr.enterKeyType}`);
  });
}
```

### offEditorAttributeChanged<sup>23+</sup>

offEditorAttributeChanged(callback?: Callback&lt;EditorAttribute&gt;): void

取消订阅编辑框属性变化事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('editorAttributeChanged')](#offeditorattributechanged10)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型   | 必填 | 说明                                                         |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[EditorAttribute](#editorattribute)&gt; | 否 | 所要取消订阅的回调处理函数。参数不填写时，默认取消订阅type对应的所有回调事件。 |

**示例：**

```ts
let inputMethodEngineDelegate = inputMethodEngine.getKeyboardDelegate();
if (inputMethodEngineDelegate) {
  inputMethodEngineDelegate!.offEditorAttributeChanged();
}
```

## Panel<sup>10+</sup>

下列API均需使用[createPanel](#createpanel10)获取到Panel实例后，通过实例调用。

### setUiContent<sup>10+</sup>

setUiContent(path: string, callback: AsyncCallback\<void>): void

为当前的输入法面板加载具体页面内容，使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| path | string | 是   | 具体页面的路径。 |
| callback | AsyncCallback\<void> | 是   | 回调函数。当面板页面内容加载成功，err为undefined，否则err为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

panel.setUiContent('pages/page2/page2', (err: BusinessError) => {
  if (err) {
    console.error(`Failed to setUiContent: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info('Succeeded in setting the content.');
});

```

### setUiContent<sup>10+</sup>

setUiContent(path: string): Promise\<void>

为当前的输入法面板加载具体页面内容，使用Promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| path | string | 是   |  具体页面的路径。 |

**返回值：**

| 类型   | 说明                             |
| ------- | ------------------------------ |
| Promise\<void> | 无返回结果的Promise对象。  |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

panel.setUiContent('pages/page2/page2').then(() => {
  console.info('Succeeded in setting the content.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setUiContent: code: ${err.code} ,message: ${err.message}`);
});

```

### setUiContent<sup>10+</sup>

setUiContent(path: string, storage: LocalStorage, callback: AsyncCallback\<void>): void

为当前的输入法面板加载与LocalStorage相关联的具体页面内容，使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| path | string | 是   | LocalStorage相关联的具体页面的路径。 |
| storage | [LocalStorage](../apis-arkui/arkui-ts/ts-state-management.md#localstorage9) | 是   | 存储单元，为应用程序范围内的可变和不可变状态属性提供存储。|
| callback | AsyncCallback\<void> | 是   | 回调函数。当面板页面内容加载成功，err为undefined，否则err为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let storage = new LocalStorage();
storage.setOrCreate('storageSimpleProp',121);

panel.setUiContent('pages/page2/page2', storage, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to setUiContent: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info('Succeeded in setting the content.');
});
```

### setUiContent<sup>10+</sup>

setUiContent(path: string, storage: LocalStorage): Promise\<void>

为当前面板加载与LocalStorage相关联的具体页面内容，使用Promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| path | string | 是   | 设置加载页面的路径。 |
| storage | [LocalStorage](../apis-arkui/arkui-ts/ts-state-management.md#localstorage9) | 是   | 存储单元，为应用程序范围内的可变状态属性和非可变状态属性提供存储。|

**返回值：**

| 类型   | 说明                             |
| ------- | ------------------------------ |
| Promise\<void> | 无返回结果的Promise对象。  |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let storage = new LocalStorage();
storage.setOrCreate('storageSimpleProp',121);
panel.setUiContent('pages/page2/page2', storage).then(() => {
  console.info('Succeeded in setting the content.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setUiContent: code: ${err.code} ,message: ${err.message}`);
});
```

### resize<sup>10+</sup>

ArkTS-Dyn: resize(width: number, height: number, callback: AsyncCallback\<void>): void

ArkTS-Sta: resize(width: long, height: long, callback: AsyncCallback\<void>): void

改变当前输入法面板的大小，使用callback异步回调。

> **说明**
>
> 面板宽度不超出屏幕宽度，面板高度不高于屏幕高度的0.7倍。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| width | ArkTS-Dyn: number <br>ArkTS-Sta: long | 是   | 目标面板的宽度，单位为px。|
| height | ArkTS-Dyn: number <br>ArkTS-Sta: long | 是   | 目标面板的高度，单位为px。|
| callback | AsyncCallback\<void> | 是   | 回调函数。当面板大小改变成功，err为undefined，否则err为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |

**示例：**

ArkTS-Dyn示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let width:number = 500;
let height:number = 1000;
panel.resize(width, height, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to resize panel: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info('Succeeded in changing the panel size.');
});
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let width:long = 500;
let height:long = 1000;
panel.resize(width, height, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to resize panel: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info('Succeeded in changing the panel size.');
});
```

### resize<sup>10+</sup>

ArkTS-Dyn: resize(width: number, height: number): Promise\<void>

ArkTS-Sta: resize(width: long, height: long): Promise\<void>

改变当前输入法面板的大小，使用Promise异步回调。

> **说明**
>
> 面板宽度不超出屏幕宽度，面板高度不高于屏幕高度的0.7倍。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| width | ArkTS-Dyn: number <br>ArkTS-Sta: long | 是   | 目标面板的宽度，单位为px。|
| height | ArkTS-Dyn: number <br>ArkTS-Sta: long | 是   | 目标面板的高度，单位为px。|

**返回值：**

| 类型   | 说明                             |
| ------- | ------------------------------ |
| Promise\<void> | 无返回结果的Promise对象。  |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |

**示例：**

ArkTS-Dyn示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let width: number = 500
let height: number = 1000
panel.resize(width, height).then(() => {
  console.info('Succeeded in changing the panel size.');
}).catch((err: BusinessError) => {
  console.error(`Failed to resize panel: code: ${err.code} ,message: ${err.message}`);
});
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let width: long = 500
let height: long = 1000

panel.resize(width, height).then(() => {
  console.info('Succeeded in changing the panel size.');
}).catch((err: BusinessError) => {
  console.error(`Failed to resize panel: code: ${err.code} ,message: ${err.message}`);
});
```

### moveTo<sup>10+</sup>

ArkTS-Dyn: moveTo(x: number, y: number, callback: AsyncCallback\<void>): void

ArkTS-Sta: moveTo(x: int, y: int, callback: AsyncCallback\<void>): void

移动面板位置，使用callback异步回调。[面板状态](#panelflag10)为固定态时，不产生实际移动效果。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| x | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是   | x轴方向移动的值，值大于0表示右移，单位为px。|
| y | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是   | y轴方向移动的值，值大于0表示下移，单位为px。|
| callback | AsyncCallback\<void> | 是   | 回调函数。当面板位置移动成功，err为undefined，否则err为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

panel.moveTo(300, 300, (err: BusinessError) =>{
  if (err) {
    console.error(`Failed to move panel: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info('Succeeded in moving the panel.');
});
```

### moveTo<sup>10+</sup>

ArkTS-Dyn: moveTo(x: number, y: number): Promise\<void>

ArkTS-Sta: moveTo(x: int, y: int): Promise\<void>

移动面板位置，使用promise异步回调。[面板状态](#panelflag10)为固定态时，不产生实际移动效果。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| x | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是   |x轴方向移动的值，值大于0表示右移，单位为px。|
| y | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是   |y轴方向移动的值，值大于0表示下移，单位为px。|

**返回值：**

| 类型   | 说明                             |
| ------- | ------------------------------ |
| Promise\<void> | 无返回结果的Promise对象。  |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

panel.moveTo(300, 300).then(() => {
  console.info('Succeeded in moving the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to move panel: code: ${err.code} ,message: ${err.message}`);
});
```

### startMoving<sup>15+</sup>

startMoving(): void

发送移动命令给窗口，不产生实际移动效果（仅在鼠标点击作用才可以移动）。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 801 | capability not supported. |
| 12800002 | input method engine error. Possible causes: 1.input method panel not created. 2.the input method application does not subscribe to related events. |
| 12800013 | window manager service error. |
| 12800017 | invalid panel type or panel flag. |

**示例：**

```ts
panel.startMoving();
console.info('Succeeded in moving the panel.');
```

### getDisplayId<sup>15+</sup>


ArkTS-Dyn: getDisplayId(): Promise\<number>

ArkTS-Sta: getDisplayId(): Promise\<long>

获取当前窗口的所在id,使用Promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型   | 说明                             |
| ------- | ------------------------------ |
| ArkTS-Dyn: Promise\<number> <br>ArkTS-Sta: Promise\<long>| Promise对象。返回窗口的displayId。  |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 12800002 | input method engine error. Possible causes: 1.input method panel not created. 2.the input method application does not subscribe to related events. |
| 12800013 | window manager service error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
panel.getDisplayId().then((result: number) => {
  console.info('get displayId:' + result);
}).catch((err: BusinessError) => {
  console.error(`Failed to get displayId: code: ${err.code} ,message: ${err.message}`);
});
```

### show<sup>10+</sup>

show(callback: AsyncCallback\<void>): void

显示当前输入法面板，使用callback异步回调。输入法应用与编辑框绑定成功后可正常调用。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | AsyncCallback\<void> | 是   | 回调函数。当面板显示成功，err为undefined，否则err为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

panel.show((err: BusinessError) => {
  if (err) {
    console.error(`Failed to show panel: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info('Succeeded in showing the panel.');
});
```

### show<sup>10+</sup>

show(): Promise\<void>

显示当前输入法面板，使用promise异步回调。输入法应用与编辑框绑定成功后可正常调用。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型   | 说明                             |
| ------- | ------------------------------ |
| Promise\<void> | 无返回结果的Promise对象。  |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

panel.show().then(() => {
  console.info('Succeeded in showing the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show panel: code: ${err.code} ,message: ${err.message}`);
});
```

### hide<sup>10+</sup>

hide(callback: AsyncCallback\<void>): void

隐藏当前输入法面板，使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | AsyncCallback\<void> | 是   | 回调函数。当面板隐藏成功，err为undefined，否则err为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

panel.hide((err: BusinessError) => {
  if (err) {
    console.error(`Failed to hide panel: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info('Succeeded in hiding the panel.');
});
```

### hide<sup>10+</sup>

hide(): Promise\<void>

隐藏当前输入法面板，使用promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型   | 说明                             |
| ------- | ------------------------------ |
| Promise\<void> | 无返回结果的Promise对象。  |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

panel.hide().then(() => {
  console.info('Succeeded in hiding the panel.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide panel: code: ${err.code} ,message: ${err.message}`);
});
```

### adjustPanelRect<sup>12+</sup>

adjustPanelRect(flag: PanelFlag, rect: PanelRect): void

预设置输入法应用横竖屏大小。接口调用完毕表示adjust请求已提交到输入法框架，不表示执行完毕。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| flag | [PanelFlag](#panelflag10) | 是 | 目标面板状态类型。类型为FLG_FIXED或FLG_FLOATING。 |
| rect | [PanelRect](#panelrect12) | 是   | 目标面板横屏状态及竖屏状态的横坐标，纵坐标，宽度以及高度。固定态：高度不能超过屏幕高度的70%，宽度不能超过屏幕宽度；悬浮态：高度不能超过屏幕高度，宽度不能超过屏幕宽度。|

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800013 | window manager service error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';


let panelFlag: inputMethodEngine.PanelFlag = inputMethodEngine.PanelFlag.FLG_FIXED;
let panelRect:inputMethodEngine.PanelRect = {
  landscapeRect:{left:100, top:100, width:400, height:400},
  portraitRect:{left:200, top:200, width:300, height:300}
};
panel.adjustPanelRect(panelFlag, panelRect);

```

### adjustPanelRect<sup>15+</sup>

adjustPanelRect(flag: PanelFlag, rect: EnhancedPanelRect): void

预设置输入法应用横竖屏大小、位置、自定义避让区域以及热区。

> **说明：**
>
> 仅用于SOFT_KEYBOARD类型，状态为FLG_FIXED或FLG_FLOATING的面板。此接口兼容[adjustPanelRect](#adjustpanelrect12)的调用方法，若入参rect仅填写属性landscapeRect和portraitRect，则默认调用[adjustPanelRect](#adjustpanelrect12)。
>
> 此接口为同步接口，接口返回仅代表系统侧收到设置的请求，不代表已完成设置。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                      | 必填 | 说明                                                       |
| ------ | ----------------------------------------- | ---- | ---------------------------------------------------------- |
| flag   | [PanelFlag](#panelflag10)                 | 是   | 目标面板状态类型。类型为FLG_FIXED或FLG_FLOATING。          |
| rect   | [EnhancedPanelRect](#enhancedpanelrect15) | 是   | 目标面板横屏状态及竖屏状态的位置、大小、避让区域以及热区。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 12800013 | window manager service error.                                |
| 12800017 | invalid panel type or panel flag.                            |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let panelFlag: inputMethodEngine.PanelFlag = inputMethodEngine.PanelFlag.FLG_FIXED;
let panelRect: inputMethodEngine.EnhancedPanelRect = {
  landscapeAvoidY: 650,
  landscapeInputRegion: [{left:300, top:650, width:2000, height:500}],
  portraitAvoidY: 1800,
  portraitInputRegion: [{left:0, top:1800, width:1200, height:800}],
  fullScreenMode: true
};
panel.adjustPanelRect(panelFlag, panelRect);
```

### updatelnputRegion<sup>15+</sup>

updateRegion(inputRegion: Array&lt;window.Rect&gt;): void

更新当前状态下输入法面板内的热区。

> **说明：**
>
> 仅用于SOFT_KEYBOARD类型，状态为FLG_FIXED或FLG_FLOATING的面板。
>
> 此接口为同步接口，接口返回仅代表系统侧收到更新热区的请求，不代表已完成热区更新。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型                                                         | 必填 | 说明                                                         |
| ----------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| inputRegion | Array&lt;[window.Rect](../apis-arkui/arkts-apis-window-i.md#rect7)&gt; | 是   | 面板内接收输入事件的区域。<br/>- 数组大小限制为[1, 4]。<br/>- 传入的热区位置是相对于输入法面板窗口左顶点的位置。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 12800013 | window manager service error.                                |
| 12800017 | invalid panel type or panel flag.                            |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let inputRegion: Array<window.Rect> = [{left:300, top:650, width:2000, height:500}];
panel.updateRegion(inputRegion);
```

### on('show')<sup>10+</sup>

on(type: 'show', callback: () => void): void

监听当前面板显示状态，使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onShow](#onshow23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| type | string | 是 | 监听当前面板的状态类型，固定取值为'show'。 |
| callback | () => void | 是   | 回调函数。 |

**示例：**

```ts
panel.on('show', () => {
  console.info('Panel is showing.');
});
```

### on('hide')<sup>10+</sup>

on(type: 'hide', callback: () => void): void

监听当前面板隐藏状态，使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onHide](#onhide23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| type | string | 是 | 监听当前面板的状态类型，固定取值为'hide'。 |
| callback | () => void | 是   | 回调函数。 |

**示例：**

```ts
panel.on('hide', () => {
  console.info('Panel is hiding.');
});
```

### on('sizeChange')<sup>12+</sup>

on(type: 'sizeChange', callback: SizeChangeCallback): void

监听当前面板大小变化，使用callback异步回调。

> **说明：**
>
> 仅用于SOFT_KEYBOARD类型，状态为FLG_FIXED或FLG_FLOATING的面板。输入法通过adjustPanelRect等接口对面板大小进行调节时，系统会根据一定规则校验计算出最终的数值（例如超出屏幕等场景），输入法应用可通过该回调获取的真实面板大小，完成最终的面板布局刷新。
>
>-  从API version 12-14开始支持，此接口回调函数中仅包含[window.Size](../apis-arkui/arkts-apis-window-i.md#size7)类型的必选参数。
>-  从API version 15起，调用[adjustPanelRect](#adjustpanelrect15)接口后，此接口回调函数增加[KeyboardArea](#keyboardarea15)类型的可选参数。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onSizeChange](#onsizechange23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                                   |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------ |
| type     | string                                      | 是   | 监听当前面板的大小是否产生变化，固定值为'sizeChange'。 |
| callback | [SizeChangeCallback](#sizechangecallback15) | 是   | 回调函数。返回当前软键盘面板的大小，包含宽度和高度值。 |

**示例：**

```ts
import { window } from '@kit.ArkUI';

panel.on('sizeChange', (windowSize: window.Size) => {
  console.info(`panel size changed, width: ${windowSize.width}, height: ${windowSize.height}`);
});

panel.on('sizeChange', (windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  console.info(`panel size changed, windowSize: ${windowSize}, keyboardArea: ${keyboardArea}`);
});
```

### off('show')<sup>10+</sup>

off(type: 'show', callback?: () => void): void

取消监听当前输入法面板的隐藏状态，使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offShow](#offshow23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| type | string | 是 | 取消监听当前面板的状态类型，固定取值为'show'。 |
| callback | () => void | 否   | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |

**示例：**

```ts
panel.off('show');
```

### off('hide')<sup>10+</sup>

off(type: 'hide', callback?: () => void): void

取消监听当前面板隐藏状态，使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offHide](#offhide23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| type | string | 是 | 要取消监听的当前面板状态类型，固定取值为'hide'。 |
| callback | () => void | 否   | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |

**示例：**

```ts
panel.off('hide');
```

### off('sizeChange')<sup>12+</sup>

off(type: 'sizeChange', callback?: SizeChangeCallback): void

取消监听当前面板大小变化，使用callback异步回调。

> **说明：**
>
> 仅用于SOFT_KEYBOARD类型，状态为FLG_FIXED或FLG_FLOATING的面板。输入法通过adjustPanelRect等接口对面板大小进行调节时，系统会根据一定规则校验计算出最终的数值（例如超出屏幕等场景），输入法应用可通过该回调获取的真实面板大小，完成最终的面板布局刷新。
>
>-  从API version 12-14开始支持，此接口回调函数中仅包含[window.Size](../apis-arkui/arkts-apis-window-i.md#size7)类型的必选参数。
>-  从API version 15起，调用[adjustPanelRect](#adjustpanelrect15)接口后，此接口回调函数增加[KeyboardArea](#keyboardarea15)类型的可选参数。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offSizeChange](#offsizechange23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 12

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                                     |
| -------- | ------------------------------------------- | ---- | -------------------------------------------------------- |
| type     | string                                      | 是   | 监听当前面板的大小是否产生变化，固定取值为'sizeChange'。 |
| callback | [SizeChangeCallback](#sizechangecallback15) | 否   | 回调函数。返回当前软键盘面板的大小，包含宽度和高度值。   |

**示例：**

```ts
import { window } from '@kit.ArkUI';

panel.off('sizeChange', (windowSize: window.Size) => {
  console.info(`panel size changed, width: ${windowSize.width}, height: ${windowSize.height}`);
});
```

### changeFlag<sup>10+</sup>

changeFlag(flag: PanelFlag): void

将输入法应用的面板状态改变为固定态或者悬浮态，仅对[SOFT_KEYBOARD](#paneltype10)生效。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| flag | [PanelFlag](#panelflag10) | 是 | 目标面板状态类型。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |

**示例：**

```ts
let panelFlag: inputMethodEngine.PanelFlag = inputMethodEngine.PanelFlag.FLG_FIXED;
panel.changeFlag(panelFlag);
```

### setPrivacyMode<sup>11+</sup>

setPrivacyMode(isPrivacyMode: boolean): void

将输入法应用的面板设置为隐私模式，隐私模式不可被录屏、截屏。

**需要权限：** ohos.permission.PRIVACY_WINDOW

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名        | 类型    | 必填 | 说明               |
| ------------- | ------- | ---- | ------------------ |
| isPrivacyMode | boolean | 是   | 是否设置隐私模式。<br/>- 值为true，表示将设置为隐私模式。<br/>- 值为false，表示将设置为非隐私模式。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 201      | permissions check fails.  |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```ts
let isPrivacyMode = true;
panel.setPrivacyMode(isPrivacyMode);
```

### setImmersiveMode<sup>15+</sup>

setImmersiveMode(mode: ImmersiveMode): void

设置输入法应用的沉浸模式。只能设置不使用沉浸模式(NONE_IMMERSIVE)、浅色沉浸模式(LIGHT_IMMERSIVE)或深色沉浸模式(DARK_IMMERSIVE)。不能设置为沉浸模式(IMMERSIVE)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| mode | [ImmersiveMode](#immersivemode15) | 是   | 沉浸模式。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 401      | parameter error. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed.           |
| 12800002 | input method engine error. Possible causes: 1.input method panel not created. 2.the input method application does not subscribe to related events. |
| 12800013  | window manager service error.                          |

**示例：**

```ts
panel.setImmersiveMode(inputMethodEngine.ImmersiveMode.LIGHT_IMMERSIVE);
```

### getImmersiveMode<sup>15+</sup>

getImmersiveMode(): ImmersiveMode

获取输入法应用沉浸模式。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型                            | 说明       |
| ------------------------------- | ---------- |
| [ImmersiveMode](#immersivemode15) | 沉浸模式。 |

**示例：**

```ts
let mode = panel.getImmersiveMode();
```

### setImmersiveEffect<sup>20+</sup>

setImmersiveEffect(effect: ImmersiveEffect): void

设置输入法应用的沉浸效果。
- 只有在[启用沉浸式模式](#setimmersivemode15)时，才能使用渐变模式和流光模式。
- 只有在启用渐变模式时，才能使用流光模式。
- 未启用渐变模式时，渐变高度必须为0px。
- 只有系统应用才能设置流光模式。
- 必须先调用以下任一接口，才能调用当前接口：
  - [adjustPanelRect](#adjustpanelrect12)(支持API version 12)
  - [adjustPanelRect](#adjustpanelrect15)(支持API version 15)
  - [resize](#resize10)(支持API version 10)

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| effect | [ImmersiveEffect](#immersiveeffect20) | 是   | 沉浸效果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 801  |capability not supported.                          |
| 12800002   |input method engine error. Possible causes:1.input method panel not created. 2.the input method application does not subscribe to related events. |
| 12800013   |window manager service error.                          |
| 12800020   |invalid immersive effect. 1.The gradient mode and the fluid light mode can only be used when the immersive mode is enabled. 2.The fluid light mode can only be used when the gradient mode is enabled. 3.When the gradient mode is not enabled, the gradient height can only be 0. |
| 12800021   |this operation is allowed only after adjustPanelRect or resize is called. |

**示例：**

```ts
let effect: inputMethodEngine.ImmersiveEffect = {
  gradientHeight: 100,
  gradientMode: inputMethodEngine.GradientMode.LINEAR_GRADIENT
}
panel.setImmersiveMode(effect);
```

### setKeepScreenOn<sup>20+</sup>

setKeepScreenOn(isKeepScreenOn: boolean): Promise\<void>

设置屏幕常亮。使用Promise异步回调。

> **说明：**
>
> - 当键盘拉起时设置常亮生效，键盘关闭则自动失效。
> - 规范使用该接口：必要场景（例如：语音输入）下，设置该属性为true；退出必要场景后，重置该属性为false；其他场景下，不使用该接口。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| isKeepScreenOn | boolean | 是   | 是否设置屏幕常亮。true表示打开屏幕常亮，false表示关闭屏幕常亮。 |

**返回值：**

| 类型   | 说明                             |
| ------- | ------------------------------ |
| Promise\<void> | 无返回结果的Promise对象。  |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 12800013 | window manager service error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let isKeepScreenOn = true;
this.panel.setKeepScreenOn(isKeepScreenOn).then(() => {
  console.info(`setKeepScreenOn success.`);
}).catch((error: BusinessError) => {
  console.error(`setKeepScreenOn failed, code: ${err.code}, message: ${err.message}`);
})
```

### setShadow<sup>20+</sup>

setShadow(radius: double, color: string, offsetX: double, offsetY: double): void

设置输入法面板的阴影效果，包括阴影半径、颜色、水平偏移和垂直偏移。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| radius | double | 是   | 阴影模糊半径。数值越大，阴影越模糊；取值需≥0，若传入负数会触发参数校验错误。 |
| color | string | 是   | 阴影颜色。仅支持十六进制颜色格式，不支持命名颜色或RGB/RGBA函数格式。 |
| radius | double | 是   | 阴影水平偏移量。正数表示阴影向右偏移，负数表示向左偏移，0 表示无水平偏移。 |
| radius | double | 是   | 阴影垂直偏移量。正数表示阴影向下偏移，负数表示向上偏移，0 表示无垂直偏移。 |


**返回值：**

| 类型   | 说明                             |
| ------- | ------------------------------ |
| void | 无返回值。  |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 12800002 | Input method engine service error. |
| 12800013 | window manager service error. |
| 12800014 | Invalid parameter. |

**示例：**

```ts
const shadowRadius = 8.0;
const shadowColor = '#80000000';
const offsetX = 2.0;
const offsetY = 2.0;
this.panel?.setShadow(shadowRadius, shadowColor, offsetX, offsetY);
```

### getSystemPanelCurrentInsets<sup>21+</sup>

getSystemPanelCurrentInsets(displayId: number): Promise\<SystemPanelInsets>

获取指定屏幕当前状态（例如：折叠或展开）下，当前输入法键盘状态（例如：悬浮或固定）下输入法软键盘相对系统面板的偏移区域。使用Promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 21

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| displayId | number | 是   | 输入法键盘所在屏幕的displayId，可通过[getDisplayId](#getdisplayid15)获取 |

**返回值：**

| 类型   | 说明                             |
| ------- | ------------------------------ |
| Promise\<[SystemPanelInsets](#systempanelinsets21)> | Promise对象。输入法键盘与系统面板的偏移区域。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                                                |
| -------- | ------------------------------------------------------- |
| 12800013 | window manager service error. |
| 12800017 | invalid panel type or panel flag. Possible causes: 1. Current panel's type is not SOFT_KEYBOARD.  2. Panel's flag is not FLG_FIXED or FLG_FLOATING. |
| 12800022 | invalid displayId. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMethodEngine } from '@kit.IMEKit';

let inputMethodAbility: inputMethodEngine.inputMethodAbility = inputMethodEngine.getinputMethodAbility();
let panelConfig: inputMethodEngine.PanelInfo = {
  type: inputMethodEngine.PanelType.SOFT_KEYBOARD,
  flag: inputMethodEngine.PanelFlag.FLG_FIXED
}
// 以下逻辑需要在输入法InputMethodExtensionAbility中执行，this.context是InputMethodExtensionAbility的上下文
inputMethodAbility.createPanel(this.context, panelConfig).then( (panel: inputMethodEngine.Panel) =>{
  panel.getDisplayId().then((displayId: number) => {
    panel.getSystemPanelCurrentInsets(displayId).then((insets: inputMethodEngine.SystemPanelInsets) => {
      console.info(`getSystemPanelCurrentInsets success, insets is { left: ${insets.left}, right: ${insets.right}, bottom: ${insets.bottom} }`);
    }).catch((error: BusinessError) => {
      console.error(`getSystemPanelCurrentInsets failed, code: ${error.code}, message: ${error.message}`);
    })
  });
})
```

### setSystemPanelButtonColor<sup>22+</sup>

setSystemPanelButtonColor(fillColor: string | undefined, backgroundColor: string | undefined): Promise\<void>

设置当前面板功能键颜色和功能键的背景颜色。使用Promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| fillColor | string\|undefined | 是   | 功能键的颜色，取值范围为[#01000000, #FFFFFFFF] 或 [#000000, #FFFFFF]，不支持具有完全透明Alpha通道（#00xxxxxx）的值。 |
| backgroundColor | string\|undefined | 是   | 功能键的背景颜色，取值范围为[#01000000, #FFFFFFFF] 或 [#000000, #FFFFFF]，不支持具有完全透明Alpha通道（#00xxxxxx）的值。 |

**返回值：**

| 类型   | 说明                             |
| ------- | ------------------------------ |
| Promise\<void> | Promise对象。无返回结果。  |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
let fillColor = "#FFFF00";
let backgroundColor = "#0000FF";
this.panel.setSystemPanelButtonColor(fillColor, backgroundColor).then(() => {
  console.info(`setSystemPanelButtonColor success.`);
}).catch((error: BusinessError) => {
  console.error(`setSystemPanelButtonColor failed, code: ${error.code}, message: ${error.message}`);
})
```

### onShow<sup>23+</sup>

onShow(callback: Callback&lt;void&gt;): void

监听当前面板显示状态，使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('show')](#onshow10)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | Callback&lt;void&gt;	 | 是 | 回调函数。 |

**示例：**

```ts
panel.onShow(() => {
  console.info('Panel is showing.');
});
```

### offShow<sup>23+</sup>

offShow(callback?: Callback&lt;void&gt;): void

取消监听当前输入法面板的隐藏状态，使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('show')](#offshow10)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | Callback&lt;void&gt;	 | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
panel.offShow();
```

### onHide<sup>23+</sup>

onHide(callback: Callback&lt;void&gt;): void

监听当前面板隐藏状态，使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('hide')](#onhide10)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | Callback&lt;void&gt;	 | 是 | 回调函数。 |

**示例：**

```ts
panel!.onShow(() => {
  console.info('Panel is showing.');
});
```

### offHide<sup>23+</sup>

offHide(callback?: Callback&lt;void&gt;): void

取消监听当前面板隐藏状态，使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('hide')](#offhide10)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | Callback&lt;void&gt;	 | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```ts
panel.offHide();
```

### onSizeChange<sup>23+</sup>

onSizeChange(callback: SizeChangeCallback): void

监听当前面板大小变化，使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('sizeChange')](#onsizechange12)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | [SizeChangeCallback](#SizeChangeCallback15) | 是 | 回调函数。返回当前软键盘面板的大小，包含宽度和高度值。 |

**示例：**

```ts
import { window } from '@kit.ArkUI';

panel.onSizeChange((windowSize: window.Size) => {
  console.info(`panel size changed, width: ${windowSize.width}, height: ${windowSize.height}`);
});
panel.onSizeChange((windowSize: window.Size, keyboardArea: inputMethodEngine.KeyboardArea) => {
  console.info(`panel size changed, windowSize: ${windowSize)}, keyboardArea: ${keyboardArea}`);
});
```

### offSizeChange<sup>23+</sup>

offSizeChange(callback?: SizeChangeCallback): void

取消监听当前面板大小变化，使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[off('sizeChange')](#offsizechange12)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | [SizeChangeCallback](#SizeChangeCallback15) | 否 | 回调函数。返回当前软键盘面板的大小，包含宽度和高度值。 |

**示例：**

```ts
import { window } from '@kit.ArkUI';

panel.offSizeChange((windowSize: window.Size) => {
  console.info(`panel size changed, width: ${windowSize.width}, height: ${windowSize.height}`);
});
```

## KeyboardController

下列API均需使用[on('inputStart')](#oninputstart9)获取到KeyboardController实例后，通过实例调用。

### hide<sup>9+</sup>

hide(callback: AsyncCallback&lt;void&gt;): void

隐藏输入法。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | AsyncCallback&lt;void> | 是   | 回调函数。当输入法隐藏成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                 |
| -------- | -------------------------- |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.hide((err: BusinessError) => {
  if (err) {
    console.error(`Failed to hide. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info('Succeeded in hiding keyboard.');
});
```

### hide<sup>9+</sup>

hide(): Promise&lt;void&gt;

隐藏输入法。使用promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型             | 说明                      |
| ---------------- | ------------------------- |
| Promise&lt;void> | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                 |
| -------- | -------------------------- |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.hide().then(() => {
  console.info('Succeeded in hiding keyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide. Code:${err.code}, message:${err.message}`);
});
```

### hideKeyboard<sup>(deprecated)</sup>

hideKeyboard(callback: AsyncCallback&lt;void&gt;): void

隐藏输入法。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[hide](#hide9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名   | 类型                   | 必填 | 说明     |
| -------- | ---------------------- | ---- | -------- |
| callback | AsyncCallback&lt;void> | 是   | 回调函数。当输入法隐藏成功，err为undefined，否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.hideKeyboard((err: BusinessError) => {
  if (err) {
    console.error(`Failed to hideKeyboard: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info('Succeeded in hiding keyboard.');
});
```

### hideKeyboard<sup>(deprecated)</sup>

hideKeyboard(): Promise&lt;void&gt;

隐藏输入法。使用promise异步回调。

> **说明：**
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[hide](#hide9-1)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**返回值：**

| 类型             | 说明                      |
| ---------------- | ------------------------- |
| Promise&lt;void> | 无返回结果的Promise对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.hideKeyboard().then(() => {
  console.info('Succeeded in hiding keyboard.');
}).catch((err: BusinessError) => {
  console.info(`Failed to hideKeyboard: code: ${err.code} ,message: ${err.message}`);
});
```

### exitCurrentInputType<sup>11+</sup>

exitCurrentInputType(callback: AsyncCallback&lt;void&gt;): void

退出当前输入类型，仅支持系统配置的默认输入法应用调用。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                                         |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback&lt;void> | 是   | 回调函数。当退出当前输入类型成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                                       |
| -------- | ---------------------------------------------- |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800010 | not the preconfigured default input method. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.exitCurrentInputType((err: BusinessError) => {
  if (err) {
    console.error(`Failed to exit current input type. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info('Succeeded in exiting current input type.');
});
```

### exitCurrentInputType<sup>11+</sup>

exitCurrentInputType(): Promise&lt;void&gt;

退出当前输入类型，仅支持系统配置的默认输入法应用调用。使用promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型             | 说明                      |
| ---------------- | ------------------------- |
| Promise&lt;void> | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                                       |
| -------- | ---------------------------------------------- |
| 12800008 | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| 12800010 | not the preconfigured default input method. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.exitCurrentInputType().then(() => {
  console.info('Succeeded in exiting current input type.');
}).catch((err: BusinessError) => {
  console.error(`Failed to exit current input type. Code:${err.code}, message:${err.message}`);
});
```

## SecurityMode<sup>11+</sup>

输入法的安全模式，如BASIC或FULL。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

| 名称  | 值   | 说明                                         |
| ----- | ---- | -------------------------------------------- |
| BASIC | 0    | 基础访问模式，基础打字模式，会限制网络访问。 |
| FULL  | 1    | 完全访问模式，不做限制，可以访问网络。       |

## ExtendAction<sup>10+</sup>

编辑框中文本的扩展编辑操作类型，如剪切、复制等。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

| 名称 | 值 |说明 |
| -------- | -------- |-------- |
| SELECT_ALL  | 0 |全选。 |
| CUT  | 3 |剪切。 |
| COPY  | 4 |复制。 |
| PASTE  | 5 |粘贴。 |

## Direction<sup>10+</sup>

光标的移动方向。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

| 名称 | 值 |说明 |
| -------- | -------- |-------- |
| CURSOR_UP  | 1 |向上。 |
| CURSOR_DOWN  | 2 |向下。 |
| CURSOR_LEFT  | 3 |向左。 |
| CURSOR_RIGHT  | 4 |向右。 |

## Range<sup>10+</sup>

选中的文本范围。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| start  | number | 否 | 否 | 选中文本的首字符在编辑框的索引值。|
| end  | number | 否 | 否 | 选中文本的末字符在编辑框的索引值。|

## Movement<sup>10+</sup>

选中文本时，光标移动的方向

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| direction  | [Direction](#direction10) | 否 | 否 | 选中文本时，光标的移动方向。|

## MessageHandler<sup>15+</sup>

自定义通信对象。

> **说明：**
>
> 开发者可通过注册此对象来接收已绑定当前输入法应用的编辑框应用所发送的自定义通信数据，接收到自定义通信数据时会触发此对象中[onMessage](#onmessage15)回调函数。
>
> 此对象全局唯一，多次注册仅保留最后一次注册的对象及有效性，并触发上一个已注册对象的[onTerminated](#onterminated15)回调函数。
>
> 若取消注册全局已注册的对象时，会触发被取消对象中[onTerminated](#onterminated15)回调函数。

### 属性

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| onMessage | [OnMessageCallback](#onmessagecallback23)| 否 | 否 | 必填。接收输入法应用发送的自定义数据回调函数。|
| onTerminated | Callback&lt;void&gt;| 否 | 否 | 必填。监听对象终止回调函数。|

### onMessage<sup>15+</sup>

onMessage(msgId: string, msgParam?: ArrayBuffer): void

接收已绑定当前输入法应用的编辑框应用发送的自定义数据回调函数。

> **说明：**
>
> 当已注册的[MessageHandler](#messagehandler15)接收到来自已绑定当前输入法应用的编辑框应用所发送的自定义通信数据时，会触发该回调函数。
>
> msgId为必选参数，msgParam为可选参数。存在收到仅有msgId自定义数据的可能，需与数据发送方确认自定义数据。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 15

**参数：**

| 参数名   | 类型        | 必填 | 说明                             |
| -------- | ----------- | ---- | -------------------------------- |
| msgId    | string      | 是   | 接收到的自定义通信数据的标识符。 |
| msgParam | ArrayBuffer | 否   | 接收到的自定义通信数据的消息体。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethodEngine.getinputMethodAbility()
  .on('inputStart', (kbController: inputMethodEngine.KeyboardController, client: inputMethodEngine.InputClient) => {
  let keyboardController = kbController;
  let inputClient = client;
  let messageHandler: inputMethodEngine.MessageHandler = {
    onTerminated(): void {
      console.info('OnTerminated.');
    },
    onMessage(msgId: string, msgParam?:ArrayBuffer): void {
      console.info('recv message.');
    }
  }
  inputClient.recvMessage(messageHandler);
});
```

### onTerminated<sup>15+</sup>

onTerminated(): void

监听对象终止回调函数。

> **说明：**
>
> 当应用注册新的[MessageHandler](#messagehandler15)对象时，会触发上一个已注册[MessageHandler](#messagehandler15)对象的[onTerminated](#onterminated15)回调函数。
>
> 当应用取消注册时，会触发当前已注册[MessageHandler](#messagehandler15)对象的[onTerminated](#onterminated15)回调函数。

 **ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 15

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethodEngine.getinputMethodAbility()
  .on('inputStart', (kbController: inputMethodEngine.KeyboardController, client: inputMethodEngine.InputClient) => {
  let keyboardController = kbController;
  let inputClient = client;
  let messageHandler: inputMethodEngine.MessageHandler = {
    onTerminated(): void {
      console.info('OnTerminated.');
    },
    onMessage(msgId: string, msgParam?:ArrayBuffer): void {
      console.info('recv message.');
    }
  }
  inputClient.recvMessage(messageHandler);
});
```

## InputClient<sup>9+</sup>

下列API均需使用[on('inputStart')](#oninputstart9)获取到InputClient实例后，通过实例调用。

### sendKeyFunction<sup>9+</sup>

ArkTS-Dyn: sendKeyFunction(action: number, callback: AsyncCallback&lt;boolean&gt;): void

ArkTS-Sta: sendKeyFunction(action: int, callback: AsyncCallback&lt;boolean&gt;): void

发送功能键。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| action | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是 | 功能键键值。<br/>- 当值为0时，表示无效按键。<br/>- 当值为1时，表示确认键（即回车键）。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。当功能键发送成功，err为undefined，data为true；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                 |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

 **示例：**

ArkTS-Dyn示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let action:number = 1;
inputClient.sendKeyFunction(action, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to sendKeyFunction: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in sending key function.');
  } else {
    console.error('Failed to sendKeyFunction.');
  }
});
```

ArkTS-Sta示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let action:long = 1;
inputClient.sendKeyFunction(action, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to sendKeyFunction: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in sending key function.');
  } else {
    console.error('Failed to sendKeyFunction.');
  }
});
```

### sendKeyFunction<sup>9+</sup>

ArkTS-Dyn: sendKeyFunction(action: number): Promise&lt;boolean&gt;

ArkTS-Sta: sendKeyFunction(action: int): Promise&lt;boolean&gt;

发送功能键。使用promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| action | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是 | 功能键键值。<br/>当值为0时，表示无效按键；<br/>当值为1时，表示确认键（即回车键）。 |

**返回值：**

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; |  Promise对象。返回true表示功能键发送成功；返回false表示功能键发送失败。|

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                 |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

ArkTS-Dyn示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let action:number = 1;

inputClient.sendKeyFunction(action).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in sending key function.');
  } else {
    console.error('Failed to sendKeyFunction.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to sendKeyFunction: code: ${err.code} ,message: ${err.message}`);
});
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let action: int = 1;

inputClient.sendKeyFunction(action).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in sending key function.');
  } else {
    console.error('Failed to sendKeyFunction.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to sendKeyFunction: code: ${err.code} ,message: ${err.message}`);
});
```

### getForward<sup>9+</sup>

ArkTS-Dyn: getForward(length: number, callback: AsyncCallback&lt;string&gt;): void

ArkTS-Sta: getForward(length: int, callback: AsyncCallback&lt;string&gt;): void

获取光标前固定长度的文本。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| length | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是 | 文本长度。不能小于0。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。当光标前固定长度的文本获取成功，err为undefined，data为获取到的文本；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                     |
| -------- | ------------------------------ |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800006 | input method controller error. Possible cause: create InputmethodController object failed. |

**示例：**

ArkTS-Dyn示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
inputClient.getForward(length, (err: BusinessError, text: string) => {
  if (err) {
    console.error(`Failed to getForward: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting forward, text: ${text}`);
});
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length: int = 1;
inputClient.getForward(length, (err: BusinessError, text: string) => {
  if (err) {
    console.error(`Failed to getForward: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting forward, text: ${text}`);
});
```

### getForward<sup>9+</sup>

ArkTS-Dyn: getForward(length: number): Promise&lt;string&gt;

ArkTS-Sta: getForward(length: int): Promise&lt;string&gt;

获取光标前固定长度的文本。使用promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| length | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是 | 文本长度。不能小于0 |

**返回值：**

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise&lt;string&gt;           |  Promise对象，返回光标前固定长度的文本。                     |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                     |
| -------- | ------------------------------ |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800006 | input method controller error. Possible cause: create InputmethodController object failed. |

**示例：**

ArkTS-Dyn示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
inputClient.getForward(length).then((text: string) => {
  console.info(`Succeeded in getting forward, text: ${text}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getForward: code: ${err.code} ,message: ${err.message}`);
});
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length: int = 1;
inputClient.getForward(length).then((text: string) => {
  console.info(`Succeeded in getting forward, text: ${text}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getForward: code: ${err.code} ,message: ${err.message}`);
});
```

### getForwardSync<sup>10+</sup>

ArkTS-Dyn: getForwardSync(length: number): string

ArkTS-Sta: getForwardSync(length: int): string

获取光标前固定长度的文本。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| length | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是   | 文本长度。不能小于0。 |

**返回值：**

| 类型   | 说明                       |
| ------ | -------------------------- |
| string | 返回光标前固定长度的文本。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800006 | input method controller error. Possible cause: create InputmethodController object failed. |

**示例：**

ArkTS-Dyn示例:

```ts
let length: number = 1;

let text: string = inputClient.getForwardSync(length);
console.info(`Succeeded in getting forward, text: ${text}`);
```

ArkTS-Sta示例:

```ts
let length: int = 1;

let text: string = inputClient.getForwardSync(length);
console.info(`Succeeded in getting forward, text: ${text}`);
```

### getBackward<sup>9+</sup>

ArkTS-Dyn: getBackward(length: number, callback: AsyncCallback&lt;string&gt;): void

ArkTS-Sta: getBackward(length: int, callback: AsyncCallback&lt;string&gt;): void

获取光标后固定长度的文本。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| length | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是 | 文本长度。不能小于0。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。当光标后固定长度的文本获取成功，err为undefined，data为获取到的文本；否则为错误对象。|

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                     |
| -------- | ------------------------------ |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800006 | input method controller error. Possible cause: create InputmethodController object failed. |

**示例：**

ArkTS-Dyn示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
inputClient.getBackward(length, (err: BusinessError, text: string) => {
  if (err) {
    console.error(`Failed to getBackward: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting backward, text: ${text}`);
});
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length: int = 1;

inputClient.getBackward(length, (err: BusinessError, text: string) => {
  if (err) {
    console.error(`Failed to getBackward: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting backward, text: ${text}`);
});
```

### getBackward<sup>9+</sup>

ArkTS-Dyn: getBackward(length: number): Promise&lt;string&gt;

ArkTS-Sta: getBackward(length: int): Promise&lt;string&gt;

获取光标后固定长度的文本。使用promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| length | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是 | 文本长度。不能小于0。 |

**返回值：**

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise&lt;string&gt;           |  Promise对象，返回光标后固定长度的文本。                     |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                     |
| -------- | ------------------------------ |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800006 | input method controller error. Possible cause: create InputmethodController object failed. |

**示例：**

ArkTS-Dyn示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;

inputClient.getBackward(length).then((text: string) => {
  console.info(`Succeeded in getting backward, text: ${text}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getBackward: code: ${err.code} ,message: ${err.message}`);
});
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length: int = 1;

inputClient.getBackward(length).then((text: string) => {
  console.info(`Succeeded in getting backward, text: ${text}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getBackward: code: ${err.code} ,message: ${err.message}`);
});
```

### getBackwardSync<sup>10+</sup>

ArkTS-Dyn: getBackwardSync(length: number): string

ArkTS-Sta: getBackwardSync(length: int): string

获取光标后固定长度的文本。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| length | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是   | 文本长度。不能小于0。 |

**返回值：**

| 类型   | 说明                       |
| ------ | -------------------------- |
| string | 返回光标后固定长度的文本。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800006 | input method controller error. Possible cause: create InputmethodController object failed. |

**示例：**

ArkTS-Dyn示例:
```ts
let length: number = 1;

let text: string = inputClient.getBackwardSync(length);
console.info(`Succeeded in getting backward, text: ${text}`);
```

ArkTS-Sta示例：
```ts
let length: int = 1;

let text: string = inputClient.getBackwardSync(length);
console.info(`Succeeded in getting backward, text: ${text}`);
```

### deleteForward<sup>9+</sup>

ArkTS-Dyn: deleteForward(length: number, callback: AsyncCallback&lt;boolean&gt;): void

ArkTS-Sta: deleteForward(length: int, callback: AsyncCallback&lt;boolean&gt;): void

删除光标前固定长度的文本。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| length | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是 | 文本长度。不能小于0。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。当光标前固定长度的文本删除成功，err为undefined，data为true；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                 |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800002 | input method engine error. Possible causes: 1.input method panel not created. 2.the input method application does not subscribe to related events. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

ArkTS-Dyn示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;

inputClient.deleteForward(length, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to deleteForward: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in deleting forward.');
  } else {
    console.error(`Failed to deleteForward.`);
  }
});
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length: int = 1;
inputClient.deleteForward(length, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to deleteForward: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in deleting forward.');
  } else {
    console.error(`Failed to deleteForward.`);
  }
});
```

### deleteForward<sup>9+</sup>

ArkTS-Dyn: deleteForward(length: number): Promise&lt;boolean&gt;

ArkTS-Sta: deleteForward(length: int): Promise&lt;boolean&gt;

删除光标前固定长度的文本。使用promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| length | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是   | 文本长度。不能小于0。 |

**返回值：**  

| 类型                   | 说明           |
| ---------------------- | -------------- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示删除光标前固定长度的文本成功；返回false表示删除光标前固定长度的文本失败。|

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                 |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800002 | input method engine error. Possible causes: 1.input method panel not created. 2.the input method application does not subscribe to related events. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

ArkTS-Dyn示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
inputClient.deleteForward(length).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in deleting forward.');
  } else {
    console.error('Failed to delete Forward.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to deleteForward: code: ${err.code} ,message: ${err.message}`);
});
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length: int = 1;
inputClient.deleteForward(length).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in deleting forward.');
  } else {
    console.error('Failed to delete Forward.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to deleteForward: code: ${err.code} ,message: ${err.message}`);
});
```

### deleteForwardSync<sup>10+</sup>

ArkTS-Dyn: deleteForwardSync(length: number): void

ArkTS-Sta: deleteForwardSync(length: int): void

删除光标前固定长度的文本。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| length | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是   | 文本长度。不能小于0。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                   |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800002 | input method engine error. Possible causes: 1.input method panel not created. 2.the input method application does not subscribe to related events. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

ArkTS-Dyn示例:

```ts
let length: number = 1;

inputClient.deleteForwardSync(length);
console.info('Succeeded in deleting forward.');
```

ArkTS-Sta示例：

```ts
let length: int = 1;

inputClient.deleteForwardSync(length);
console.info('Succeeded in deleting forward.');
```

### deleteBackward<sup>9+</sup>

ArkTS-Dyn: deleteBackward(length: number, callback: AsyncCallback&lt;boolean&gt;): void

ArkTS-Sta: deleteBackward(length: int, callback: AsyncCallback&lt;boolean&gt;): void

删除光标后固定长度的文本。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                         | 必填 | 说明           |
| -------- | ---------------------------- | ---- | -------------- |
| length   | ArkTS-Dyn: number <br>ArkTS-Sta: int                       | 是   | 文本长度。不能小于0。     |
| callback | AsyncCallback&lt;boolean&gt; | 是   | 回调函数。当光标后固定长度的文本删除成功，err为undefined，data为true；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                 |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800002 | input method engine error. Possible causes: 1.input method panel not created. 2.the input method application does not subscribe to related events. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

ArkTS-Dyn示例:
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
inputClient.deleteBackward(length, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to deleteBackward: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in deleting backward.');
  } else {
    console.error(`Failed to deleteBackward.`);
  }
});
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@ohos.base';

let length: int = 1;
inputClient.deleteBackward(length, (err: BusinessError | null, result: boolean | undefined) => {
  if (err) {
    console.error(`Failed to deleteBackward: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in deleting backward.');
  } else {
    console.error(`Failed to deleteBackward.`);
  }
});
```

### deleteBackward<sup>9+</sup>

ArkTS-Dyn: deleteBackward(length: number): Promise&lt;boolean&gt;

ArkTS-Sta: deleteBackward(length: int): Promise&lt;boolean&gt;

删除光标后固定长度的文本。使用promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| length | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是 | 文本长度。不能小于0。    |

**返回值：** 

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; |  Promise对象。返回true表示删除光标后固定长度的文本成功；返回false表示删除光标后固定长度的文本失败。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                 |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800002 | input method engine error. Possible causes: 1.input method panel not created. 2.the input method application does not subscribe to related events. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length = 1;
inputClient.deleteBackward(length).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in deleting backward.');
  } else {
    console.error('Failed to deleteBackward.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to deleteBackward: code: ${err.code} ,message: ${err.message}`);
});
```

### deleteBackwardSync<sup>10+</sup>

ArkTS-Dyn: deleteBackwardSync(length: number): void

ArkTS-Sta: deleteBackwardSync(length: int): void

删除光标后固定长度的文本。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| length | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是   | 文本长度。不能小于0。  |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                   |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800002 | input method engine error. Possible causes: 1.input method panel not created. 2.the input method application does not subscribe to related events. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
let length = 1;

inputClient.deleteBackwardSync(length);
console.info('Succeeded in deleting backward.');
```

### insertText<sup>9+</sup>

insertText(text:string, callback: AsyncCallback&lt;boolean&gt;): void

插入文本。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| text | string | 是 | 文本内容。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。当文本插入成功，err为undefined，data为true；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                 |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800002 | input method engine error. Possible causes: 1.input method panel not created. 2.the input method application does not subscribe to related events. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.insertText('test', (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to insertText: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in inserting text.');
  } else {
    console.error('Failed to insertText.');
  }
});
```

### insertText<sup>9+</sup>

insertText(text:string): Promise&lt;boolean&gt;

插入文本。使用promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| text | string | 是 | 文本。 |

**返回值：**  

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt;  |  Promise对象。返回true表示插入文本成功；返回false表示插入文本失败。  |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                 |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800002 | input method engine error. Possible causes: 1.input method panel not created. 2.the input method application does not subscribe to related events. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.insertText('test').then((result: boolean) => {
  if (result) {
    console.info('Succeeded in inserting text.');
  } else {
    console.error('Failed to insertText.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to insertText: code: ${err.code} ,message: ${err.message}`);
});
```

### insertTextSync<sup>10+</sup>

insertTextSync(text: string): void

插入文本。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| text   | string | 是   | 文本内容。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                   |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800002 | input method engine error. Possible causes: 1.input method panel not created. 2.the input method application does not subscribe to related events. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
inputClient.insertTextSync('test');
console.info('Succeeded in inserting text.');
```

### getEditorAttribute<sup>9+</sup>

ArkTS-Dyn: getEditorAttribute(callback: AsyncCallback&lt;EditorAttribute&gt;): void

ArkTS-Sta: getEditorAttribute(callback: AsyncCallback&lt;EditorAttribute | null&gt;): void

获取编辑框属性值。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名                         | 类型                          | 必填                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| callback | ArkTS-Dyn: AsyncCallback&lt;[EditorAttribute](#editorattribute)&gt; <br>ArkTS-Sta: AsyncCallback&lt;[EditorAttribute](#editorattribute) \| null&gt; | 是 |  回调函数。当编辑框属性值获取成功，err为undefined，data为编辑框属性值；否则为错误对象。|

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                 |
| -------- | -------------------------- |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.getEditorAttribute((err: BusinessError, editorAttribute: inputMethodEngine.EditorAttribute) => {
  if (err) {
    console.error(`Failed to getEditorAttribute: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info(`editorAttribute.inputPattern:  ${editorAttribute.inputPattern}`);
  console.info(`editorAttribute.enterKeyType:  ${editorAttribute.enterKeyType}`);
});
```

### getEditorAttribute<sup>9+</sup>

ArkTS-Dyn: getEditorAttribute(): Promise&lt;EditorAttribute&gt;

ArkTS-Sta: getEditorAttribute(): Promise&lt;EditorAttribute | null&gt;

获取编辑框属性值。使用promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| ArkTS-Dyn: Promise&lt;[EditorAttribute](#editorattribute)&gt; <br>ArkTS-Sta: Promise&lt;[EditorAttribute](#editorattribute) \| null&gt; |  Promise对象，返回编辑框属性值。           |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                 |
| -------- | -------------------------- |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.getEditorAttribute().then((editorAttribute: inputMethodEngine.EditorAttribute) => {
  console.info(`editorAttribute.inputPattern:  ${editorAttribute.inputPattern}`);
  console.info(`editorAttribute.enterKeyType:  ${editorAttribute.enterKeyType}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getEditorAttribute: code: ${err.code} ,message: ${err.message}`);
});
```

### getEditorAttributeSync<sup>10+</sup>

ArkTS-Dyn: getEditorAttributeSync(): EditorAttribute

ArkTS-Sta: getEditorAttributeSync(): EditorAttribute | null

获取编辑框属性值。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                | 说明           |
| ----------------------------------- | -------------- |
| ArkTS-Dyn: [EditorAttribute](#editorattribute) <br>ArkTS-Sta: [EditorAttribute](#editorattribute) \| null | 编辑框属性对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                   |
| -------- | -------------------------- |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
let editorAttribute: inputMethodEngine.EditorAttribute = inputClient.getEditorAttributeSync();
console.info(`editorAttribute.inputPattern:  ${editorAttribute.inputPattern}`);
console.info(`editorAttribute.enterKeyType:  ${editorAttribute.enterKeyType}`);
```

### moveCursor<sup>9+</sup>

ArkTS-Dyn: moveCursor(direction: number, callback: AsyncCallback&lt;void&gt;): void

ArkTS-Sta: moveCursor(direction: int, callback: AsyncCallback&lt;void&gt;): void

移动光标。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型                      | 必填 | 说明           |
| --------- | ------------------------- | ---- | -------------- |
| direction | ArkTS-Dyn: number <br>ArkTS-Sta: int                    | 是   | 光标移动方向。<br/>- 当值为1时，表示向上。<br/>- 当值为2时，表示向下。<br/>- 当值为3时，表示向左。<br/>- 当值为4时，表示向右。不能小于0。 |
| callback  | AsyncCallback&lt;void&gt; | 是   | 回调函数。当光标移动成功，err为undefined，否则为错误对象。    |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                 |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.moveCursor(inputMethodEngine.Direction.CURSOR_UP, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to moveCursor: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info('Succeeded in moving cursor.');
});
```

### moveCursor<sup>9+</sup>

ArkTS-Dyn: moveCursor(direction: number): Promise&lt;void&gt;

ArkTS-Sta: moveCursor(direction: int): Promise&lt;void&gt;

移动光标。使用promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型   | 必填 | 说明                                                         |
| --------- | ------ | ---- | ------------------------------------------------------------ |
| direction | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是   | 光标移动方向。<br/>- 当值为1时，表示向上。<br/>- 当值为2时，表示向下。<br/>- 当值为3时，表示向左。<br/>- 当值为4时，表示向右。不能小于0。 |

**返回值：**  

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                 |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.moveCursor(inputMethodEngine.Direction.CURSOR_UP).then(() => {
  console.info('Succeeded in moving cursor.');
}).catch((err: BusinessError) => {
  console.error(`Failed to moveCursor: code: ${err.code} ,message: ${err.message}`);
});
```

### moveCursorSync<sup>10+</sup>

ArkTS-Dyn: moveCursorSync(direction: number): void

ArkTS-Sta: moveCursorSync(direction: int): void

移动光标。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名    | 类型   | 必填 | 说明                                                         |
| --------- | ------ | ---- | ------------------------------------------------------------ |
| direction | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是   | 光标移动方向。<br/>- 当值为1时，表示向上。<br/>- 当值为2时，表示向下。<br/>- 当值为3时，表示向左。<br/>- 当值为4时，表示向右。不能小于0。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                   |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
inputClient.moveCursorSync(inputMethodEngine.Direction.CURSOR_UP);
console.info('Succeeded in moving cursor.');
```

### selectByRange<sup>10+</sup>

selectByRange(range: Range, callback: AsyncCallback&lt;void&gt;): void

根据索引范围选中文本。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                      | 必填 | 说明                                                         |
| -------- | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| range    | [Range](#range10) | 是   | 选中文本的范围。                                             |
| callback | AsyncCallback&lt;void&gt;                                 | 是   | 回调函数。当成功发送选中事件后，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                   |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let range: inputMethodEngine.Range = { start: 0, end: 1 };
inputClient.selectByRange(range, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to selectByRange: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info('Succeeded in selecting by range.');
});
```

### selectByRange<sup>10+</sup>

selectByRange(range: Range): Promise&lt;void&gt;

根据索引范围选中文本。使用promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                                      | 必填 | 说明             |
| ------ | --------------------------------------------------------- | ---- | ---------------- |
| range  | [Range](#range10) | 是   | 选中文本的范围。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                   |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let range: inputMethodEngine.Range = { start: 0, end: 1 };
inputClient.selectByRange(range).then(() => {
  console.info('Succeeded in selecting by range.');
}).catch((err: BusinessError) => {
  console.error(`Failed to selectByRange: code: ${err.code} ,message: ${err.message}`);
});
```

### selectByRangeSync<sup>10+</sup>

selectByRangeSync(range: Range): void

根据索引范围选中文本。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型              | 必填 | 说明             |
| ------ | ----------------- | ---- | ---------------- |
| range  | [Range](#range10) | 是   | 选中文本的范围。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                   |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
let range: inputMethodEngine.Range = { start: 0, end: 1 };
inputClient.selectByRangeSync(range);
console.info('Succeeded in selecting by range.');
```

### selectByMovement<sup>10+</sup>

selectByMovement(movement: Movement, callback: AsyncCallback&lt;void&gt;): void

根据光标移动方向选中文本。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型  | 必填 | 说明   |
| -------- | ------ | ---- | ------ |
| movement | [Movement](#movement10)   | 是   | 选中时光标移动的方向。  |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。当成功发送选中事件后，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                   |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let movement: inputMethodEngine.Movement = { direction: 1 };
inputClient.selectByMovement(movement, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to selectByMovement: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info('Succeeded in selecting by movement.');
});
```

### selectByMovement<sup>10+</sup>

selectByMovement(movement: Movement): Promise&lt;void&gt;

根据索引范围选中文本。使用promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                   |
| -------- | ------------------------------------------------------------ | ---- | ---------------------- |
| movement | [Movement](#movement10) | 是   | 选中时光标移动的方向。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                   |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let movement: inputMethodEngine.Movement = { direction: 1 };
inputClient.selectByMovement(movement).then(() => {
  console.info('Succeeded in selecting by movement.');
}).catch((err: BusinessError) => {
  console.error(`Failed to selectByMovement: code: ${err.code} ,message: ${err.message}`);
});
```

### selectByMovementSync<sup>10+</sup>

selectByMovementSync(movement: Movement): void

根据光标移动方向选中文本。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名   | 类型                    | 必填 | 说明                   |
| -------- | ----------------------- | ---- | ---------------------- |
| movement | [Movement](#movement10) | 是   | 选中时光标移动的方向。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                   |
| -------- | -------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |

**示例：**

```ts
let movement: inputMethodEngine.Movement = { direction: 1 };  
inputClient.selectByMovementSync(movement);
console.info('Succeeded in selecting by movement.');
```

### getTextIndexAtCursor<sup>10+</sup>

ArkTS-Dyn: getTextIndexAtCursor(callback: AsyncCallback&lt;number&gt;): void

ArkTS-Sta: getTextIndexAtCursor(callback: AsyncCallback&lt;int&gt;): void

获取光标所在处的文本索引。使用callback异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                        | 必填 | 说明                                                         |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| callback | ArkTS-Dyn: AsyncCallback&lt;number&gt; <br>ArkTS-Sta: AsyncCallback&lt; int&gt; | 是   | 回调函数。当文本索引获取成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800006 | input method controller error. Possible cause: create InputmethodController object failed. |

**示例：**

ArkTs-Dyn示例:

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.getTextIndexAtCursor((err: BusinessError, index: number) => {
  if (err) {
    console.error(`Failed to getTextIndexAtCursor: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getTextIndexAtCursor: ${index}`);
});
```

ArkTs-Sta示例:

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.getTextIndexAtCursor((err: BusinessError, index: int) => {
  if (err) {
    console.error(`Failed to getTextIndexAtCursor: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getTextIndexAtCursor: ${index}`);
});
```

### getTextIndexAtCursor<sup>10+</sup>

ArkTS-Dyn: getTextIndexAtCursor(): Promise&lt;number&gt;

ArkTS-Sta: getTextIndexAtCursor(): Promise&lt;int&gt;

获取光标所在处的文本索引。使用promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                  | 说明                                    |
| --------------------- | --------------------------------------- |
| ArkTS-Dyn: Promise&lt;number&gt; <br>ArkTS-Sta: Promise&lt;int&gt; | Promise对象，返回光标所在处的文本索引。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800006 | input method controller error. Possible cause: create InputmethodController object failed. |

**示例：**

ArkTs-Dyn示例:

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.getTextIndexAtCursor().then((index: number) => {
  console.info(`Succeeded in getTextIndexAtCursor: ${index}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getTextIndexAtCursor: code: ${err.code} ,message: ${err.message}`);
});
```

ArkTs-Sta示例:

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.getTextIndexAtCursor().then((index: int) => {
  console.info(`Succeeded in getTextIndexAtCursor: ${index}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getTextIndexAtCursor: code: ${err.code} ,message: ${err.message}`);
});
```

### getTextIndexAtCursorSync<sup>10+</sup>

ArkTS-Dyn: getTextIndexAtCursorSync(): number

ArkTS-Sta: getTextIndexAtCursorSync(): int

获取光标所在处的文本索引。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型   | 说明                       |
| ------ | -------------------------- |
| ArkTS-Dyn: number <br>ArkTS-Sta: int | 返回光标所在处的文本索引。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800006 | input method controller error. Possible cause: create InputmethodController object failed. |

**示例：**

ArkTs-Dyn示例:

```ts
let index: number = inputClient.getTextIndexAtCursorSync();
console.info(`Succeeded in getTextIndexAtCursorSync, index: ${index}`);
```

ArkTs-Sta示例:

```ts
let index: int = inputClient.getTextIndexAtCursorSync();
console.info(`Succeeded in getTextIndexAtCursorSync, index: ${index}`);
```

### sendExtendAction<sup>10+</sup>

sendExtendAction(action: ExtendAction, callback: AsyncCallback&lt;void&gt;): void

发送扩展编辑操作。使用callback异步回调。

> **说明**
>
> 输入法应用调用该接口向编辑框发送扩展编辑操作，编辑框监听相应事件[on('handleExtendAction')](./js-apis-inputmethod.md#onhandleextendaction10)，从而进一步做出处理。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                        | 必填 | 说明                                                         |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| action | [ExtendAction](#extendaction10) | 是   | 要发送的扩展操作。 |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。发送成功，err为undefined，否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800006 | input method controller error. Possible cause: create InputmethodController object failed. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.sendExtendAction(inputMethodEngine.ExtendAction.COPY, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to sendExtendAction: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info('Succeeded in sending extend action.');
});
```

### sendExtendAction<sup>10+</sup>

sendExtendAction(action: ExtendAction): Promise&lt;void&gt;

发送扩展编辑操作。使用promise异步回调。

>**说明**
>
> 输入法应用调用该接口向编辑框发送扩展编辑操作，编辑框监听相应事件[on('handleExtendAction')](./js-apis-inputmethod.md#onhandleextendaction10)，从而进一步做出处理。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| action | [ExtendAction](#extendaction10) | 是 | 要发送的扩展操作。 |

**返回值：**

| 类型                  | 说明                                    |
| --------------------- | --------------------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800006 | input method controller error. Possible cause: create InputmethodController object failed. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.sendExtendAction(inputMethodEngine.ExtendAction.COPY).then(() => {
  console.info('Succeeded in sending extend action.');
}).catch((err: BusinessError) => {
  console.error(`Failed to sendExtendAction: code: ${err.code} ,message: ${err.message}`);
});
```

### sendPrivateCommand<sup>12+</sup>

sendPrivateCommand(commandData: Record&lt;string, CommandDataType&gt;): Promise&lt;void&gt;

发送私有数据至需要与输入法应用通信的系统其他部分。

>**说明：**
>
> - 私有数据通道是系统预置输入法应用与系统特定组件（如文本框、桌面应用等）的通信机制，常用于设备级厂商在特定设备上实现自定义的输入法功能。
> - 私有数据规格限制：总大小32KB，数量限制5条。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型                            | 必填 | 说明       |
| ----------- | ------------------------------- | ---- | ---------- |
| commandData | Record<string, [CommandDataType](#commanddatatype12)> | 是   | 私有数据。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                       |
| -------- | ---------------------------------------------- |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800010 | not the preconfigured default input method. |

**示例：**

ArkTs-Dyn示例:

```ts
import { inputMethodEngine } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

inputMethodEngine.getinputMethodAbility().on('inputStart', (kbController, textInputClient) => {
  let record: Record<string, inputMethodEngine.CommandDataType> = {
    "valueString1": "abcdefg",
    "valueString2": true,
    "valueString3": 500,
  }
  textInputClient.sendPrivateCommand(record).then(() => {
  }).catch((err: BusinessError) => {
    if (err !== undefined) {
      console.error(`sendPrivateCommand catch error: ${err.code} ${err.message}`);
    }
  });
})
```

ArkTs-Sta示例:

```ts
import { inputMethodEngine } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

inputMethodEngine.getinputMethodAbility().onInputStart((kbController, textInputClient) => {
  let record: Record<string, inputMethodEngine.CommandDataType> = {
    "valueString1": "abcdefg",
    "valueString2": true,
    "valueString3": 500,
  }
  textInputClient.sendPrivateCommand(record).then(() => {
  }).catch((err: BusinessError) => {
    if (err !== undefined) {;
      console.error(`sendPrivateCommand catch error: ${err.code} ${err.message}`);
    }
  });
  console.error(`sendPrivateCommand catch error: ${err.code} ${err.message}`);
})
```

### getCallingWindowInfo<sup>12+</sup>

ArkTS-Dyn: getCallingWindowInfo(): Promise&lt;WindowInfo&gt;

ArkTS-Sta: getCallingWindowInfo(): Promise&lt;WindowInfo | null&gt;;

获取当前拉起输入法的输入框所在应用窗口信息。使用promise异步回调。

>**说明：**
>
>本接口仅适用于适配使用[Panel](#panel10)作为软键盘窗口的输入法应用。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**
 
| 类型                                       | 说明                                                  |
| ------------------------------------------ | ----------------------------------------------------- |
| ArkTS-Dyn: Promise&lt;[WindowInfo](#windowinfo12)&gt; <br>ArkTS-Sta: Promise&lt;[WindowInfo](#windowinfo12) \| null&gt; | Promise对象，返回拉起输入法的输入框所在应用窗口信息。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                          |
| -------- | --------------------------------- |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800012 | the input method panel does not exist. |
| 12800013 | window manager service error.     |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.getCallingWindowInfo().then((windowInfo: inputMethodEngine.WindowInfo) => {
  console.info(`windowInfo.rect: ${windowInfo.rect}`);
  console.info(`windowInfo.status: ${windowInfo.status}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getCallingWindowInfo: code: ${err.code} ,message: ${err.message}`);
});
```

### setPreviewText<sup>12+</sup>

setPreviewText(text: string, range: Range): Promise&lt;void&gt;

设置预上屏文本。使用promise异步回调。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型              | 必填 | 说明                                                         |
| ------ | ----------------- | ---- | ------------------------------------------------------------ |
| text   | string            | 是   | 将被预上屏的文本。                                           |
| range  | [Range](#range10) | 是   | 目标替换的文本范围。<br/>- 当值为{ start: -1, end: -1 }时，默认将参数text替换当前预上屏区域全部文本。<br/>- 当start等于end，默认将参数text插入start对应的光标位置。<br/>- 当start不等于end，将参数text替换range对应区域的文本。<br/>- 当start与end为其他含有负数值的组合，按照参数错误返回。<br/>- 当输入框已有预上屏文本，参数range不得超过预上屏文本范围，否则按照参数错误返回。<br/>- 当输入框无预上屏文本，参数range不得超过输入框文本范围，否则按照参数错误返回。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800011 | text preview not supported.                               |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let range: inputMethodEngine.Range = { start: 0, end: 1 };
inputClient.setPreviewText('test', range).then(() => {
  console.info('Succeeded in setting preview text.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setPreviewText: code: ${err.code} ,message: ${err.message}`);
});
```

### setPreviewTextSync<sup>12+</sup>

setPreviewTextSync(text: string, range: Range): void

设置预上屏文本。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型              | 必填 | 说明                                                         |
| ------ | ----------------- | ---- | ------------------------------------------------------------ |
| text   | string            | 是   | 将被预上屏的文本。                                           |
| range  | [Range](#range10) | 是   | 目标替换的文本范围。<br/>- 当值为{ start: -1, end: -1 }时，默认将参数text替换当前预上屏区域全部文本。<br/>- 当start等于end，默认将参数text插入start对应的光标位置。<br/>- 当start不等于end，将参数text替换range对应区域的文本。<br/>- 当start与end为其他含有负数值的组合，按照参数错误返回。<br/>- 当输入框已有预上屏文本，参数range不得超过预上屏文本范围，否则按照参数错误返回。<br/>- 当输入框无预上屏文本，参数range不得超过输入框文本范围，否则按照参数错误返回。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed.           |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800011 | text preview not supported.                               |

**示例：**

```ts
let range: inputMethodEngine.Range = { start: 0, end: 1 };
inputClient.setPreviewTextSync('test', range);
console.info('Succeeded in setting preview text with synchronized method.');
```

### finishTextPreview<sup>12+</sup>

finishTextPreview(): Promise&lt;void&gt;

结束预上屏。使用promise异步回调。

>**说明：**
>
>若当前输入框已有预上屏状态文本，调用此接口后，预上屏内容将被系统正式上屏。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800011 | text preview not supported. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.finishTextPreview().then(() => {
  console.info('Succeeded in finishing text preview.');
}).catch((err: BusinessError) => {
  console.error(`Failed to finishTextPreview: code: ${err.code} ,message: ${err.message}`);
});
```

### finishTextPreviewSync<sup>12+</sup>

finishTextPreviewSync(): void

结束预上屏。

>**说明：**
>
>若当前输入框已有预上屏状态文本，调用此接口后，预上屏内容将被系统正式上屏。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)。

| 错误码ID | 错误信息                       |
| -------- | ------------------------------ |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800011 | text preview not supported. |

**示例：**

```ts
inputClient.finishTextPreviewSync();
console.info('Succeeded in finishing text preview with synchronized method.');
```

### sendMessage<sup>15+</sup>

sendMessage(msgId: string, msgParam?: ArrayBuffer): Promise<void&gt;

发送自定义通信至已绑定当前输入法应用的编辑框应用。使用Promise异步回调。

> **说明：**
>
> 该接口需要编辑框与输入法绑定并进入编辑状态，且输入法应用处于完整体验模式时才能调用。
>
> msgId最大限制256B，msgParam最大限制128KB。

**系统能力：**  SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型        | 必填 | 说明                                                         |
| -------- | ----------- | ---- | ------------------------------------------------------------ |
| msgId    | string      | 是   | 需要发送至已绑定当前输入法应用的编辑框应用的自定义数据的标识符。 |
| msgParam | ArrayBuffer | 否   | 需要发送至已绑定当前输入法应用的编辑框应用的自定义数据的消息体。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                    |
| -------- | ------------------------------------------- |
| 401      | parameter error. Possible causes: 1. Incorrect parameter types. 2. Incorrect parameter length.  |
| 12800003 | input method client error. Possible causes: 1.the edit box is not focused. 2.no edit box is bound to current input method application. |
| 12800009 | input method client detached.               |
| 12800014 | the input method is in basic mode.          |
| 12800015 | the other side does not accept the request. |
| 12800016 | input method client is not editable.        |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let msgId: string = "testMsgId";
let msgParam: ArrayBuffer = new ArrayBuffer(128);
inputClient.sendMessage(msgId, msgParam).then(() => {
  console.info('Succeeded send message.');
}).catch((err: BusinessError) => {
  console.error(`Failed to send message: code: ${err.code} ,message: ${err.message}`);
});
```

### recvMessage<sup>15+</sup>

recvMessage(msgHandler?: MessageHandler): void;

注册或取消注册Messagehandler。

> **说明：**
>
> [MessageHandler](#messagehandler15)对象全局唯一，多次注册仅保留最后一次注册的对象及有效性，并触发上一个已注册对象的[onTerminated](#onterminated15)回调函数。
>
> 未填写参数，则取消全局已注册的[MessageHandler](#messagehandler15)，并会触发被取消注册对象中[onTerminated](#onterminated15)回调函数。

**系统能力：**  SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                                | 必填 | 说明                                                         |
| ---------- | ----------------------------------- | ---- | ------------------------------------------------------------ |
| msgHandler | [MessageHandler](#messagehandler15) | 否   | 该对象将通过[onMessage](#onmessage15)接收来自已绑定当前输入法应用的编辑框应用所发送的自定义通信数据，并通过[onTerminated](#onterminated15)接收终止此对象订阅的消息。<br>若不填写此参数，则取消全局已注册的[MessageHandler](#messagehandler15)对象，同时触发其[onTerminated](#onterminated15)回调函数。 |

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| void | 无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[输入法框架错误码](errorcode-inputmethod-framework.md)，[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息         |
| -------- | ---------------- |
| 401      | parameter error. Possible causes: 1. Incorrect parameter types. |

**示例：**

ArkTs-Dyn示例:

```ts
import { BusinessError } from '@kit.BasicServicesKit';


inputMethodEngine.getinputMethodAbility()
  .on('inputStart', (kbController: inputMethodEngine.KeyboardController, client: inputMethodEngine.InputClient) => {
  let keyboardController = kbController;
  let inputClient = client;
  let messageHandler: inputMethodEngine.MessageHandler = {
    onTerminated(): void {
      console.info('OnTerminated.');
    },
    onMessage(msgId: string, msgParam?:ArrayBuffer): void {
      console.info('recv message.');
    }
  }
  inputClient.recvMessage(messageHandler);
  
});

```

ArkTs-Sta示例:

```ts
import { BusinessError } from '@kit.BasicServicesKit';

inputMethodEngine.getinputMethodAbility()
.onInputStart((kbController: inputMethodEngine.KeyboardController, client: inputMethodEngine.InputClient) => {
  let keyboardController = kbController;
  let inputClient = client;
  
  let messageHandler: inputMethodEngine.MessageHandler = {
    onTerminated: (): void => {
    console.info('OnTerminated.');
    },
    onMessage: (msgId: string, msgParam?: ArrayBuffer): void => {
    console.info('recv message.');
    }
  }
  inputClient.recvMessage(messageHandler);
});
```

### getAttachOptions<sup>19+</sup>

ArkTS-Dyn: getAttachOptions(): AttachOptions

ArkTS-Sta: getAttachOptions(): AttachOptions | null

获取绑定输入法时的附加选项。

**系统能力：**  SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型 | 说明         |
| ---- | ------------ |
| ArkTS-Dyn: [AttachOptions](#attachoptions19) <br>ArkTS-Sta: [AttachOptions](#attachoptions19) \| null | 返回绑定输入法时的附加选项内容。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息         |
| -------- | ---------------- |
| 801      | Capability not supported. |

**示例：**

```ts
let attachOptions = inputClient.getAttachOptions();
console.info(`Succeeded in getting AttachOptions, AttachOptions is ${attachOptions}`);
```

### on('attachOptionsDidChange')<sup>19+</sup>

on(type: 'attachOptionsDidChange', callback: Callback\<AttachOptions>): void

订阅绑定输入法时的附加选项变更事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[onAttachOptionsDidChange](#onattachoptionsdidchange23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                           |
| -------- | ------------------------------------------- | ---- | ---------------------------------------------- |
| type     | string                                      | 是   | 绑定输入法时的附加选项变更事件，固定取值为'attachOptionsDidChange'。 |
| callback | Callback\<[AttachOptions](#attachoptions19)> | 是   | 回调函数，返回绑定输入法时的附加选项。       |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息         |
| -------- | ---------------- |
| 801      | Capability not supported. |

**示例：**

```ts
let attachOptionsDidChangeCallback = (attachOptions: inputMethodEngine.AttachOptions) => {
  console.info(`AttachOptionsDidChangeCallback1: attachOptionsDidChange event triggered`);
};

inputClient.on('attachOptionsDidChange', attachOptionsDidChangeCallback);
console.info(`attachOptionsDidChangeCallback subscribed to attachOptionsDidChange`);
inputClient.off('attachOptionsDidChange', attachOptionsDidChangeCallback);
console.info(`attachOptionsDidChange unsubscribed from attachOptionsDidChange`);

```

### off('attachOptionsDidChange')<sup>19+</sup>

off(type: 'attachOptionsDidChange', callback?: Callback\<AttachOptions>): void

取消订阅绑定输入法时的附加选项变更事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**相关接口：** 该接口对应的ArkTS-Sta接口是[offAttachOptionsDidChange](#offattachoptionsdidchange23)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                                         |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                      | 是   | 绑定输入法时的附加选项变更事件，固定取值为'attachOptionsDidChange'。               |
| callback | Callback\<[AttachOptions](#attachoptions19)> | 否   | 取消订阅的回调函数。参数不填写时，默认取消订阅type对应的所有回调事件。 |

**示例：**

```ts
let attachOptionsDidChangeCallback = (attachOptions: inputMethodEngine.AttachOptions) => {
  console.info(`AttachOptionsDidChangeCallback1: attachOptionsDidChange event triggered`);
};
inputClient.on('attachOptionsDidChange', attachOptionsDidChangeCallback);
console.info(`attachOptionsDidChangeCallback subscribed to attachOptionsDidChange`);
inputClient.off('attachOptionsDidChange', attachOptionsDidChangeCallback);
console.info(`attachOptionsDidChange unsubscribed from attachOptionsDidChange`);
```

### onAttachOptionsDidChange<sup>23+</sup>

onAttachOptionsDidChange(callback: Callback&lt;AttachOptions&gt;): void

订阅绑定输入法时的附加选项变更事件。使用callback异步回调。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Dyn接口是[on('attachOptionsDidChange')](#onattachoptionsdidchange19)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                                         |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[AttachOptions](#attachoptions19)&gt; | 是   |  回调函数，返回绑定输入法时的附加选项。 |

**示例：**

```ts
let attachOptionsDidChangeCallback = (attachOptions: inputMethodEngine.AttachOptions) => {
  console.info(`AttachOptionsDidChangeCallback1: attachOptionsDidChange event triggered`);
};

inputMethodEngine.getinputMethodAbility()
  .onInputStart((kbController: inputMethodEngine.KeyboardController, client: inputMethodEngine.InputClient) => {
  let keyboardController = kbController;
  let inputClient = client;
  inputClient.onAttachOptionsDidChange(attachOptionsDidChangeCallback);
  console.info(`attachOptionsDidChangeCallback subscribed to attachOptionsDidChange`);
  inputClient.offAttachOptionsDidChange(attachOptionsDidChangeCallback);
  console.info(`attachOptionsDidChange unsubscribed from attachOptionsDidChange`);
});
```

### offAttachOptionsDidChange<sup>23+</sup>

offAttachOptionsDidChange(callback?: Callback&lt;AttachOptions&gt;): void

取消订阅附加选项变更（attachOptionsDidChange）事件，停止监听输入法附加配置项的变更动作。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**相关接口：** 该接口对应的ArkTS-Sta接口是[off('attachOptionsDidChange')](#offattachoptionsdidchange19)。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                        | 必填 | 说明                                                         |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;[AttachOptions](#attachoptions19)&gt; | 是   | 可选参数，需取消的目标回调函数：传入指定回调函数实例时，仅取消该回调的订阅；不传入时，取消所有attachOptionsDidChange事件的订阅。 |

**示例：**

```ts
let attachOptionsDidChangeCallback = (attachOptions: inputMethodEngine.AttachOptions) => {
  console.info(`AttachOptionsDidChangeCallback1: attachOptionsDidChange event triggered`);
};

inputMethodEngine.getinputMethodAbility()
  .onInputStart((kbController: inputMethodEngine.KeyboardController, client: inputMethodEngine.InputClient) => {
  let keyboardController = kbController;
  let inputClient = client;
  inputClient.onAttachOptionsDidChange(attachOptionsDidChangeCallback);
  console.info(`attachOptionsDidChangeCallback subscribed to attachOptionsDidChange`);
  inputClient.offAttachOptionsDidChange(attachOptionsDidChangeCallback);
  console.info(`attachOptionsDidChange unsubscribed from attachOptionsDidChange`);
});
```

### CapitalizeMode<sup>20+</sup>

枚举，定义了文本首字母大写的不同模式。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

| 名称 | 值 | 说明 |
| -------- | -- | -------- |
| NONE | 0 | 不进行任何首字母大写处理。|
| SENTENCES | 1 | 每个句子的首字母大写。|
| WORDS | 2 | 每个单词的首字母大写。|
| CHARACTERS | 3 | 每个字母都大写。|

### EditorAttribute

编辑框属性值。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

| 名称         | 类型 | 只读 | 可选 | 说明               |
| ------------ | -------- | ---- | ---- | ------------------ |
| enterKeyType | ArkTS-Dyn: number <br>ArkTS-Sta: int     | 是   | 否   | 编辑框的功能属性，详见[常量中的功能键定义](#常量)。 |
| inputPattern | ArkTS-Dyn: number <br>ArkTS-Sta: int     | 是   | 否   | 编辑框的文本属性，详见[常量中的编译框定义](#常量)。 |
| isTextPreviewSupported<sup>12+</sup> | boolean | 否 | 否 | 编辑框是否支持预上屏。<br/>- 值为true，表示支持。<br/>- 值为false，表示不支持。 |
| bundleName<sup>14+</sup> | string | 是 | 是 | 编辑框所属应用包名；该值可能为""，使用该属性时需要考虑为""的场景。 |
| immersiveMode<sup>15+</sup> | [ImmersiveMode](#immersivemode15) | 是   | 是   | 输入法沉浸模式。 |
| windowId<sup>18+</sup> | ArkTS-Dyn: number <br>ArkTS-Sta: int   | 是 | 是 | 编辑框设置所属窗口ID。 |
| displayId<sup>18+</sup> | ArkTS-Dyn: number <br>ArkTS-Sta: long   | 是   | 是   | 编辑框设置窗口对应的屏幕ID。如果没有设置windowId，取当前焦点窗口屏幕ID。|
| placeholder<sup>20+</sup> | string | 是 | 是 | 编辑框设置的占位符信息。|
| abilityName<sup>20+</sup> | string | 是 | 是 | 编辑框设置的ability名称。|
| capitalizeMode<sup>20+</sup> | [CapitalizeMode](#capitalizemode20) | 是 | 是 | 编辑框设置大小写模式。如果没有设置或设置非法值，默认不进行任何首字母大写处理。|
| gradientMode<sup>20+</sup> | [GradientMode](#gradientmode20) | 是 | 是 | 渐变模式。如果没有设置或设置非法值，默认不使用渐变模式。|
| extraConfig<sup>22+</sup> | [InputMethodExtraConfig](./js-apis-inputmethod-extraconfig.md#inputmethodextraconfig) | 是 | 是 | 输入法扩展信息。<br/>**ArkTS-Dyn起始版本：** 22<br/>**ArkTS-Sta起始版本：** 23 ||

## KeyEvent

按键属性值。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

| 名称      | 类型 | 只读 | 可选 | 说明         |
| --------- | -------- | ---- | ---- | ------------ |
| keyCode   | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是   | 否   | 按键的键值。键码值说明参考[KeyCode](../apis-input-kit/js-apis-keycode.md#keycode)。 |
| keyAction | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是   | 否   | 按键事件类型。<br/>- 当值为2时，表示按下事件；<br/>- 当值为3时，表示抬起事件。 |

## PanelFlag<sup>10+</sup>

输入法面板状态类型枚举。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

| 名称         | 值 | 说明               |
| ------------ | -- | ------------------ |
| FLG_FIXED  | 0 | 固定态面板类型。 |
| FLG_FLOATING | 1 | 悬浮态面板类型。 |
| FLAG_CANDIDATE<sup>15+</sup> | 2 | 候选词态面板类型。 |

## PanelType<sup>10+</sup>

输入法面板类型枚举。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

| 名称         | 值 | 说明               |
| ------------ | -- | ------------------ |
| SOFT_KEYBOARD | 0 | 软键盘类型。 |
| STATUS_BAR   | 1 | 状态栏类型。 |

## PanelInfo<sup>10+</sup>

输入法面板属性。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

| 名称      | 类型 | 只读 | 可选 | 说明         |
| --------- | -------- | ---- | ---- | ------------ |
| type   	| [PanelType](#paneltype10)   | 否   | 否   | 面板的类型。 |
| flag	    | [PanelFlag](#panelflag10)   | 否   | 是   | 面板的状态类型。 |

## PanelRect<sup>12+</sup>

输入法面板位置大小信息。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

| 名称         | 类型 | 只读 | 可选 | 说明               |
| ------------ | -------- | ---- | ---- | ------------------ |
| landscapeRect | [window.Rect](../apis-arkui/arkts-apis-window-i.md#rect7)   | 否   | 否   | 横屏状态时输入法面板窗口的位置大小。 |
| portraitRect | [window.Rect](../apis-arkui/arkts-apis-window-i.md#rect7)   | 否   | 否   | 竖屏状态时输入法面板窗口的位置大小。 |

## EnhancedPanelRect<sup>15+</sup>

增强的输入法面板位置、大小信息，包含自定义避让区域、自定义热区。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

| 名称                 | 类型                                                         | 只读 | 可选 | 说明                                                         |
| -------------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| landscapeRect        | [window.Rect](../apis-arkui/arkts-apis-window-i.md#rect7)         | 否   | 是   | 横屏状态时输入法面板窗口的位置大小。<br/>- 当fullScreenMode不填写或值为false时，此属性为必选。 |
| portraitRect         | [window.Rect](../apis-arkui/arkts-apis-window-i.md#rect7)         | 否   | 是   | 竖屏状态时，输入法面板窗口的位置大小。<br/>- 当fullScreenMode不填写或值为false时，此属性为必选。 |
| landscapeAvoidY      | ArkTS-Dyn: number <br>ArkTS-Sta: int                                                       | 否   | 是   | 横屏状态时，面板中的避让线距离面板顶部的距离。默认值为0。<br/>- 应用内其他系统组件会对避让线以下的输入法面板区域进行避让。<br/>- 面板为固定态时，避让线到屏幕底部的高度不能超过屏幕高度的70%。 |
| landscapeInputRegion | Array&lt;[window.Rect](../apis-arkui/arkts-apis-window-i.md#rect7)&gt; | 否   | 是   | 横屏状态时，面板接收输入事件的区域。<br/>- 数组大小限制为[1, 4]。默认值为横屏时的面板大小。<br/>- 传入的热区位置是相对于输入法面板窗口左顶点的位置。 |
| portraitAvoidY       | ArkTS-Dyn: number <br>ArkTS-Sta: int                                                       | 否   | 是   | 竖屏状态时，面板中的避让线距离面板顶部的距离。默认值为0。<br/>- 应用内其他系统组件会对避让线以下的输入法面板区域进行避让。<br/>- 面板为固定态时，避让线到屏幕底部的高度不能超过屏幕高度的70%。 |
| portraitInputRegion  | Array&lt;[window.Rect](../apis-arkui/arkts-apis-window-i.md#rect7)&gt; | 否   | 是   | 竖屏状态时，面板接收输入事件的区域。<br/>- 数组大小限制为[1, 4]。默认值为竖屏时的面板大小。<br/>- 传入的热区位置是相对于输入法面板窗口左顶点的位置。 |
| fullScreenMode       | boolean                                                      | 否   | 是   | 是否开启全屏模式。默认值为false。<br/>- 值为true，landscapeRect和portraitRect可不填写。<br/>- 值为false，landscapeRect和portraitRect为必选属性。 |

## KeyboardArea<sup>15+</sup>

面板中的键盘区域。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

| 名称   | 类型   | 只读 | 可选 | 说明                                                         |
| ------ | ------ | ---- | ---- | ------------------------------------------------------------ |
| top    | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是   | 否   | 键盘区域的上边界到面板区域上边界的距离，单位为px，该参数为整数。 |
| bottom | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是   | 否   | 键盘区域的下边界到面板区域下边界的距离，单位为px，该参数为整数。 |
| left   | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是   | 否   | 键盘区域的左边界到面板区域左边界的距离，单位为px，该参数为整数。 |
| right  | ArkTS-Dyn: number <br>ArkTS-Sta: int | 是   | 否   | 键盘区域的右边界到面板区域右边界的距离，单位为px，该参数为整数。 |

## AttachOptions<sup>19+</sup>

绑定输入法时的附加选项。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 23

| 名称   | 类型   | 只读 | 可选 | 说明                                                         |
| ------ | ------ | ---- | ---- | ---------------------------------------------------------- |
| requestKeyboardReason    | [RequestKeyboardReason](#requestkeyboardreason19) | 否   | 是   | 该属性由编辑框应用设置，如果没有设置或设置非法值，则默认没有特定的原因触发键盘请求。 |
| isSimpleKeyboardEnabled<sup>20+</sup>    | boolean | 否   | 是   | 是否使能简单键盘，该属性由编辑框应用设置，true表示使能简单键盘，false表示不使能简单键盘。<br/> 如果没有设置或设置非法值，则默认不使能简单键盘。 <br/>**ArkTS-Dyn起始版本：** 20<br/>**ArkTS-Sta起始版本：** 23 |

## WindowInfo<sup>12+</sup>

窗口信息。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

| 名称   | 类型                                                         | 只读 | 可选 | 说明           |
| ------ | ------------------------------------------------------------ | ---- | ---- | -------------- |
| rect   | [window.Rect](../apis-arkui/arkts-apis-window-i.md#rect7)         | 否   | 否   | 窗口矩形区域。 |
| status | [window.WindowStatusType](../apis-arkui/arkts-apis-window-e.md#windowstatustype11) | 否   | 否   | 窗口模式类型。 |

## ImmersiveMode<sup>15+</sup>

枚举，输入法沉浸模式。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

| 名称         | 值 | 说明               |
| ------------ | -- | ------------------ |
| NONE_IMMERSIVE | 0 | 不使用沉浸模式。 |
| IMMERSIVE      | 1 | 沉浸模式，由输入法应用确定沉浸模式类型。 |
| LIGHT_IMMERSIVE  | 2 | 浅色沉浸模式。 |
| DARK_IMMERSIVE   | 3 | 深色沉浸模式。 |

## RequestKeyboardReason<sup>19+</sup>

枚举，请求键盘输入原因。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 19

**ArkTS-Sta起始版本：** 23

| 名称         | 值 | 说明               |
| ------------ | -- | ------------------ |
| NONE  | 0 | 表示没有特定的原因触发键盘请求。 |
| MOUSE | 1 | 表示键盘请求是由鼠标操作触发的。 |
| TOUCH | 2 | 表示键盘请求是由触摸操作触发的。 |
| OTHER | 20 | 表示键盘请求是由其他原因触发的。 |

## GradientMode<sup>20+</sup>

枚举，输入法渐变模式。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

| 名称         | 值 | 说明               |
| ------------ | -- | ------------------ |
| NONE | 0 | 不使用渐变模式。 |
| LINEAR_GRADIENT | 1 | 线性渐变。 |

## FluidLightMode<sup>20+</sup>

枚举，输入法流体光效模式。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

| 名称         | 值 | 说明               |
| ------------ | -- | ------------------ |
| NONE | 0 | 不使用流体光效模式。 |
| BACKGROUND_FLUID_LIGHT | 1 | 背景流体光效模式。 |

## ImmersiveEffect<sup>20+</sup>

沉浸效果。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

| 名称   | 类型                                  | 只读 | 可选 | 说明           |
| ------ | ------------------------------------ | ---- | ---- | -------------- |
| gradientHeight | ArkTS-Dyn: number <br>ArkTS-Sta: int | 否   | 否   | 渐变高度，不能超过屏幕高度的15%。|
| gradientMode | [GradientMode](#gradientmode20) | 否   | 否   | 渐变模式。 |
| fluidLightMode | [FluidLightMode](#fluidlightmode20) | 否   | 是   | 流体光效模式。<br/>**ArkTS-Dyn起始版本：** 20<br/>**ArkTS-Sta起始版本：** 23 | |

## SystemPanelInsets<sup>21+</sup>

输入法软键盘相对系统面板的偏移区域。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

| 名称   | 类型   | 只读 | 可选 | 说明                                                         |
| ------ | ------ | ---- | ---- | ------------------------------------------------------------ |
| bottom | number | 是   | 否   | 键盘区域的下边界到系统面板区域下边界的距离，单位为px，该参数为整数。 |
| left   | number | 是   | 否   | 键盘区域的左边界到系统面板区域左边界的距离，单位为px，该参数为整数。 |
| right  | number | 是   | 否   | 键盘区域的右边界到系统面板区域右边界的距离，单位为px，该参数为整数。 |

## TextInputClient<sup>(deprecated)</sup>

> **说明：** 
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[InputClient](#inputclient9)替代。

下列API示例中都需使用[on('inputStart')](#oninputstart)回调获取到TextInputClient实例，再通过此实例调用对应方法。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

### getForward<sup>(deprecated)</sup>

getForward(length:number, callback: AsyncCallback&lt;string&gt;): void

获取光标前固定长度的文本。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[getForward](#getforward9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| length | number | 是 | 文本长度。不能小于0。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。当光标前固定长度的文本获取成功，err为undefined，data为获取到的文本；否则为错误对象。|

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length = 1;
textInputClient.getForward(length, (err: BusinessError, text: string) => {
  if (err) {
    console.error(`Failed to getForward: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting forward, text: ' ${text}`);
});
```

### getForward<sup>(deprecated)</sup>

getForward(length:number): Promise&lt;string&gt;

获取光标前固定长度的文本。使用promise异步回调。

> **说明：**
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[getForward](#getforward9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| length | number | 是 | 文本长度。不能小于0。|

**返回值：**

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise&lt;string&gt; |  Promise对象，返回光标前固定长度的文本。                |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length = 1;
textInputClient.getForward(length).then((text: string) => {
  console.info(`Succeeded in getting forward, text: ${text}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getForward: code: ${err.code} ,message: ${err.message}`);
});
```

### getBackward<sup>(deprecated)</sup>

getBackward(length:number, callback: AsyncCallback&lt;string&gt;): void

获取光标后固定长度的文本。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[getBackward](#getbackward9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| length | number | 是 | 文本长度。不能小于0。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。当光标后固定长度的文本获取成功，err为undefined，data为获取到的文本；否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length = 1;
textInputClient.getBackward(length, (err: BusinessError, text: string) => {
  if (err) {
    console.error(`Failed to getBackward: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting borward, text: ${text}`);
});
```

### getBackward<sup>(deprecated)</sup>

getBackward(length:number): Promise&lt;string&gt;

获取光标后固定长度的文本。使用promise异步回调。

> **说明：**
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[getBackward](#getbackward9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| length | number | 是 | 文本长度。不能小于0。 |

**返回值：**

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise&lt;string&gt; |  Promise对象，返回光标后固定长度的文本。                |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length = 1;
textInputClient.getBackward(length).then((text: string) => {
  console.info(`Succeeded in getting backward: ${text}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getBackward: code: ${err.code} ,message: ${err.message}`);
});
```

### deleteForward<sup>(deprecated)</sup>

deleteForward(length:number, callback: AsyncCallback&lt;boolean&gt;): void

删除光标前固定长度的文本。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[deleteForward](#deleteforward9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| length | number | 是 | 文本长度。不能小于0。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。当光标前固定长度的文本删除成功，err为undefined，data为true；否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length = 1;
textInputClient.deleteForward(length, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to deleteForward: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in deleting forward.');
  } else {
    console.error('Failed to deleteForward.');
  }
});
```

### deleteForward<sup>(deprecated)</sup>

deleteForward(length:number): Promise&lt;boolean&gt;

删除光标前固定长度的文本。使用promise异步回调。

> **说明：**
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[deleteForward](#deleteforward9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型   | 必填 | 说明       |
| ------ | ------ | ---- | ---------- |
| length | number | 是   | 文本长度。不能小于0。 |

**返回值：**  

| 类型                   | 说明           |
| ---------------------- | -------------- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示删除光标前固定长度的文本成功；返回false表示删除光标前固定长度的文本失败。|

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length = 1;
textInputClient.deleteForward(length).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in deleting forward.');
  } else {
    console.error('Failed to delete forward.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to deleteForward: code: ${err.code} ,message: ${err.message}`);
});
```

### deleteBackward<sup>(deprecated)</sup>

deleteBackward(length:number, callback: AsyncCallback&lt;boolean&gt;): void

删除光标后固定长度的文本。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[deleteBackward](#deletebackward9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名   | 类型                         | 必填 | 说明           |
| -------- | ---------------------------- | ---- | -------------- |
| length   | number                       | 是   | 文本长度。不能小于0。      |
| callback | AsyncCallback&lt;boolean&gt; | 是   | 回调函数。当光标后固定长度的文本删除成功，err为undefined，data为true；否则为错误对象。|

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length = 1;
textInputClient.deleteBackward(length, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to deleteBackward: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in deleting backward.');
  } else {
    console.error('Failed to deleteBackward.');
  }
});
```

### deleteBackward<sup>(deprecated)</sup>

deleteBackward(length:number): Promise&lt;boolean&gt;

删除光标后固定长度的文本。使用promise异步回调。

> **说明：**
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[deleteBackward](#deletebackward9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| length | number | 是 | 文本长度。不能小于0。  |

**返回值：** 

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; |  Promise对象。返回true表示删除光标后固定长度的文本成功；返回false表示删除光标后固定长度的文本失败。|

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let length = 1;
textInputClient.deleteBackward(length).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in deleting backward.');
  } else {
    console.error('Failed to deleteBackward.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to deleteBackward: code: ${err.code} ,message: ${err.message}`);
});
```
### sendKeyFunction<sup>(deprecated)</sup>

sendKeyFunction(action: number, callback: AsyncCallback&lt;boolean&gt;): void

发送功能键。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[sendKeyFunction](#sendkeyfunction9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| action | number | 是 | 功能键键值。<br/>- 当值为0时，表示无效按键；<br/>- 当值为1时，表示确认键（即回车键）。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。当功能键发送成功，err为undefined，data为true；否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let action = 1;
textInputClient.sendKeyFunction(action, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to sendKeyFunction: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in sending key function.');
  } else {
    console.error('Failed to sendKeyFunction.');
  }
});
```

### sendKeyFunction<sup>(deprecated)</sup>

sendKeyFunction(action: number): Promise&lt;boolean&gt;

发送功能键。使用promise异步回调。

> **说明：**
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[sendKeyFunction](#sendkeyfunction9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| action | number | 是 | 功能键键值。<br/>当值为0时，表示无效按键；<br/>当值为1时，表示确认键（即回车键）。 |

**返回值：**

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; |  Promise对象。返回true表示发送功能键成功；返回false表示发送功能键失败。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let action = 1;
textInputClient.sendKeyFunction(action).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in sending key function.');
  } else {
    console.error('Failed to sendKeyFunction.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to sendKeyFunction: code: ${err.code} ,message: ${err.message}`);
});
```

### insertText<sup>(deprecated)</sup>

insertText(text:string, callback: AsyncCallback&lt;boolean&gt;): void

插入文本。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[insertText](#inserttext9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| text | string | 是 | 文本。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。当文本插入成功，err为undefined，data为true；否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

textInputClient.insertText('test', (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to insertText: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in inserting text.');
  } else {
    console.error('Failed to insertText.');
  }
});
```

### insertText<sup>(deprecated)</sup>

insertText(text:string): Promise&lt;boolean&gt;

插入文本。使用promise异步回调。

> **说明：**
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[insertText](#inserttext9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| text | string | 是 | 文本。 |

**返回值：**  

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; |  Promise对象。返回true表示插入文本成功；返回false表示插入文本失败。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

textInputClient.insertText('test').then((result: boolean) => {
  if (result) {
    console.info('Succeeded in inserting text.');
  } else {
    console.error('Failed to insertText.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to insertText: code: ${err.code} ,message: ${err.message}`);
});
```

### getEditorAttribute<sup>(deprecated)</sup>

getEditorAttribute(callback: AsyncCallback&lt;EditorAttribute&gt;): void

获取编辑框属性值。使用callback异步回调。

> **说明：**
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[getEditorAttribute](#geteditorattribute9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**参数：**

| 参数名    | 类型   | 必填  | 说明   |
| -------- | ----- | ----- | ----- |
| callback | AsyncCallback&lt;[EditorAttribute](#editorattribute)&gt; | 是 |  回调函数。当编辑框的属性值获取成功，err为undefined，data为编辑框属性值；否则为错误对象。|

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

textInputClient.getEditorAttribute((err: BusinessError, editorAttribute: inputMethodEngine.EditorAttribute) => {
  if (err) {
    console.error(`Failed to getEditorAttribute: code: ${err.code} ,message: ${err.message}`);
    return;
  }
  console.info(`editorAttribute.inputPattern: ${editorAttribute.inputPattern}`);
  console.info(`editorAttribute.enterKeyType: ${editorAttribute.enterKeyType}`);
});
```

### getEditorAttribute<sup>(deprecated)</sup>

getEditorAttribute(): Promise&lt;EditorAttribute&gt;

获取编辑框属性值。使用promise异步回调。

> **说明：**
>
> 从API version 8开始支持，API version 9开始废弃，建议使用[getEditorAttribute](#geteditorattribute9)替代。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**ArkTS-Dyn起始版本：** 8

**返回值：**

| 类型                            | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| Promise&lt;[EditorAttribute](#editorattribute)&gt; |  Promise对象，返回编辑框属性值。           |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

textInputClient.getEditorAttribute().then((editorAttribute: inputMethodEngine.EditorAttribute) => {
  console.info(`editorAttribute.inputPattern:  ${editorAttribute.inputPattern}`);
  console.info(`editorAttribute.enterKeyType:  ${editorAttribute.enterKeyType}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getEditorAttribute: code: ${err.code} ,message: ${err.message}`);
});
```
