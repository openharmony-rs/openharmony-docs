# KeyboardDelegate

KeyboardDelegate是键盘事件监听代理对象，用于输入法应用监听物理键盘按键事件和编辑框文本/光标/选区变化事件。输入法应用通过[getKeyboardDelegate](arkts-ime-inputmethodengine-getkeyboarddelegate-f.md#getkeyboarddelegate-1)获取该实例。**核心功能概述：**

- **物理键盘按键事件**：通过on('keyDown'|'keyUp')订阅物理按键的按下/抬起事件，通过on('keyEvent')订阅更完整的按键事件（含组合键信息）。callback返回true表示按键事件被消费，返回false表示不消费。  
- **光标与选区变化事件**：通过on('cursorContextChange')订阅光标位置变化事件，通过on('selectionChange')订阅文本选区变化事件。输入法应用可根据这些事件调整候选词位置或输入策略。  
- **文本变化事件**：通过on('textChange')订阅编辑框文本内容变化事件，输入法应用可据此更新候选词或输入建议。  
- **编辑框属性变化事件**：通过on('editorAttributeChanged')订阅编辑框属性变化事件，输入法应用可根据编辑框属性变化动态调整键盘布局。**使用场景：**  
- 开发物理键盘快捷键处理功能时，订阅on('keyDown'|'keyUp')或on('keyEvent')事件拦截特定按键。  
- 需要根据编辑框实时状态（光标、选区、文本、属性）调整输入法行为时，订阅对应的on事件。

下列API均需使用[getKeyboardDelegate](arkts-ime-inputmethodengine-getkeyboarddelegate-f.md#getkeyboarddelegate-1)获取到KeyboardDelegate实例后，通过实例调用。

**起始版本：** 8

<!--Device-inputMethodEngine-interface KeyboardDelegate--><!--Device-inputMethodEngine-interface KeyboardDelegate-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

<a id="off"></a>
## off('keyDown' | 'keyUp')

```TypeScript
off(type: 'keyDown' | 'keyUp', callback?: (event: KeyEvent) => boolean): void
```

取消订阅硬键盘（即物理键盘）上物理按键的按下或抬起事件。

**起始版本：** 8

<!--Device-KeyboardDelegate-off(type: 'keyDown' | 'keyUp', callback?: (event: KeyEvent) => boolean): void--><!--Device-KeyboardDelegate-off(type: 'keyDown' | 'keyUp', callback?: (event: KeyEvent) => boolean): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyDown' \| 'keyUp' | 是 | 设置监听类型。<br/>- 'keyDown'表示键盘按下。<br/>- 'keyUp'表示键盘抬起。 |
| callback | (event: KeyEvent) =&gt; boolean | 否 | 取消订阅的回调函数，用于取消特定的键盘按键事件订阅。传入callback时取消指定回调的订阅，参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
inputMethodEngine.getKeyboardDelegate().off('keyUp', (keyEvent: inputMethodEngine.KeyEvent) => {
  console.info('delete keyUp notification.');
  return true;
});
inputMethodEngine.getKeyboardDelegate().off('keyDown', (keyEvent: inputMethodEngine.KeyEvent) => {
  console.info('delete keyDown notification.');
  return true;
});

```

<a id="off-1"></a>
## off('keyDown' | 'keyUp')

```TypeScript
off(type: 'keyDown' | 'keyUp', callback?: (event: KeyEvent) => boolean): void
```

取消订阅硬键盘（即物理键盘）上物理按键的按下或抬起事件。

**起始版本：** 8

<!--Device-KeyboardDelegate-off(type: 'keyDown' | 'keyUp', callback?: (event: KeyEvent) => boolean): void--><!--Device-KeyboardDelegate-off(type: 'keyDown' | 'keyUp', callback?: (event: KeyEvent) => boolean): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyDown' \| 'keyUp' | 是 | 设置监听类型。<br/>- 'keyDown'表示键盘按下。<br/>- 'keyUp'表示键盘抬起。 |
| callback | (event: KeyEvent) =&gt; boolean | 否 | 取消订阅的回调函数，用于取消特定的键盘按键事件订阅。传入callback时取消指定回调的订阅，参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
inputMethodEngine.getKeyboardDelegate().off('keyUp', (keyEvent: inputMethodEngine.KeyEvent) => {
  console.info('delete keyUp notification.');
  return true;
});
inputMethodEngine.getKeyboardDelegate().off('keyDown', (keyEvent: inputMethodEngine.KeyEvent) => {
  console.info('delete keyDown notification.');
  return true;
});

```

<a id="off-2"></a>
## off('keyEvent')

```TypeScript
off(type: 'keyEvent', callback?: (event: InputKeyEvent) => boolean): void
```

取消订阅硬键盘（即物理键盘）事件。使用callback异步回调。

**起始版本：** 10

<!--Device-KeyboardDelegate-off(type: 'keyEvent', callback?: (event: InputKeyEvent) => boolean): void--><!--Device-KeyboardDelegate-off(type: 'keyEvent', callback?: (event: InputKeyEvent) => boolean): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyEvent' | 是 | 设置监听类型，固定取值为'keyEvent'。 |
| callback | (event: InputKeyEvent) =&gt; boolean | 否 | 取消订阅的回调函数，用于取消特定的键盘事件订阅。传入callback时取消指定回调的订阅，参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
import type { KeyEvent } from '@kit.InputKit';

inputMethodEngine.getKeyboardDelegate().off('keyEvent', (keyEvent: KeyEvent) => {
  console.info('This is a callback function which will be deregistered.');
  return true;
});
inputMethodEngine.getKeyboardDelegate().off('keyEvent');

```

<a id="off-3"></a>
## off('cursorContextChange')

```TypeScript
off(type: 'cursorContextChange', callback?: (x: number, y: number, height: number) => void): void
```

取消订阅光标变化事件。

**起始版本：** 8

<!--Device-KeyboardDelegate-off(type: 'cursorContextChange', callback?: (x: number, y: number, height: number) => void): void--><!--Device-KeyboardDelegate-off(type: 'cursorContextChange', callback?: (x: number, y: number, height: number) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cursorContextChange' | 是 | 光标变化事件，固定取值为'cursorContextChange'。 |
| callback | (x: number, y: number, height: number) =&gt; void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
inputMethodEngine.getKeyboardDelegate().off('cursorContextChange');

```

<a id="off-4"></a>
## off('selectionChange')

```TypeScript
off(
      type: 'selectionChange',
      callback?: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void
    ): void
```

取消订阅文本选择范围变化事件。

**起始版本：** 8

<!--Device-KeyboardDelegate-off(
      type: 'selectionChange',
      callback?: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void
    ): void--><!--Device-KeyboardDelegate-off(
      type: 'selectionChange',
      callback?: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void
    ): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'selectionChange' | 是 | 文本选择变化事件，固定取值为'selectionChange'。 |
| callback | (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) =&gt; void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
inputMethodEngine.getKeyboardDelegate()
  .off('selectionChange', (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => {
    console.info('delete selectionChange notification.');
  });

```

<a id="off-5"></a>
## off('textChange')

```TypeScript
off(type: 'textChange', callback?: (text: string) => void): void
```

取消订阅文本内容变化事件。使用callback异步回调。

**起始版本：** 8

<!--Device-KeyboardDelegate-off(type: 'textChange', callback?: (text: string) => void): void--><!--Device-KeyboardDelegate-off(type: 'textChange', callback?: (text: string) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'textChange' | 是 | 文本变化事件，固定取值为'textChange'。 |
| callback | (text: string) =&gt; void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
inputMethodEngine.getKeyboardDelegate().off('textChange', (text: string) => {
  console.info('delete textChange notification. text:' + text);
});

```

<a id="off-6"></a>
## off('editorAttributeChanged')

```TypeScript
off(type: 'editorAttributeChanged', callback?: (attr: EditorAttribute) => void): void
```

取消订阅编辑框属性变化事件。使用callback异步回调。

**起始版本：** 10

<!--Device-KeyboardDelegate-off(type: 'editorAttributeChanged', callback?: (attr: EditorAttribute) => void): void--><!--Device-KeyboardDelegate-off(type: 'editorAttributeChanged', callback?: (attr: EditorAttribute) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'editorAttributeChanged' | 是 | 编辑框属性变化事件，固定取值为'editorAttributeChanged'。 |
| callback | (attr: EditorAttribute) =&gt; void | 否 | 所要取消订阅的回调处理函数。参数不填写时，默认取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
inputMethodEngine.getKeyboardDelegate().off('editorAttributeChanged');

```

<a id="on"></a>
## on('keyDown' | 'keyUp')

```TypeScript
on(type: 'keyDown' | 'keyUp', callback: (event: KeyEvent) => boolean): void
```

订阅硬键盘（即物理键盘）上物理按键的按下或抬起事件。使用callback异步回调。

**使用场景：** 实现快捷键功能、拦截特殊按键、处理功能键（如删除、回车等）等。

**使用后效果：** 当物理按键按下/抬起时触发回调，回调函数返回按键信息。若按键事件被事件订阅者消费，则callback应返回true，否则返回false。返回true时按键事件不再向编辑框传递，返回false时按键事件继续向编辑框传递。

**起始版本：** 8

<!--Device-KeyboardDelegate-on(type: 'keyDown' | 'keyUp', callback: (event: KeyEvent) => boolean): void--><!--Device-KeyboardDelegate-on(type: 'keyDown' | 'keyUp', callback: (event: KeyEvent) => boolean): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyDown' \| 'keyUp' | 是 | 设置监听类型。<br/>- 'keyDown'表示键盘按下。<br/>- 'keyUp'表示键盘抬起。 |
| callback | (event: KeyEvent) =&gt; boolean | 是 | 回调函数，返回按键信息。 若按键事件被事件订阅者消费，则callback应返回true，否则返回false。 |

**示例：**

```TypeScript
inputMethodEngine.getKeyboardDelegate().on('keyUp', (keyEvent: inputMethodEngine.KeyEvent) => {
  console.info(`inputMethodEngine keyCode.(keyUp): ${keyEvent.keyCode}`);
  console.info(`inputMethodEngine keyAction.(keyUp): ${keyEvent.keyAction}`);
  return true;
});
inputMethodEngine.getKeyboardDelegate().on('keyDown', (keyEvent: inputMethodEngine.KeyEvent) => {
  console.info(`inputMethodEngine keyCode.(keyDown): ${keyEvent.keyCode}`);
  console.info(`inputMethodEngine keyAction.(keyDown): ${keyEvent.keyAction}`);
  return true;
});

```

<a id="on-1"></a>
## on('keyDown' | 'keyUp')

```TypeScript
on(type: 'keyDown' | 'keyUp', callback: (event: KeyEvent) => boolean): void
```

订阅硬键盘（即物理键盘）上物理按键的按下或抬起事件。使用callback异步回调。

**使用场景：** 实现快捷键功能、拦截特殊按键、处理功能键（如删除、回车等）等。

**使用后效果：** 当物理按键按下/抬起时触发回调，回调函数返回按键信息。若按键事件被事件订阅者消费，则callback应返回true，否则返回false。返回true时按键事件不再向编辑框传递，返回false时按键事件继续向编辑框传递。

**起始版本：** 8

<!--Device-KeyboardDelegate-on(type: 'keyDown' | 'keyUp', callback: (event: KeyEvent) => boolean): void--><!--Device-KeyboardDelegate-on(type: 'keyDown' | 'keyUp', callback: (event: KeyEvent) => boolean): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyDown' \| 'keyUp' | 是 | 设置监听类型。<br/>- 'keyDown'表示键盘按下。<br/>- 'keyUp'表示键盘抬起。 |
| callback | (event: KeyEvent) =&gt; boolean | 是 | 回调函数，返回按键信息。 若按键事件被事件订阅者消费，则callback应返回true，否则返回false。 |

**示例：**

```TypeScript
inputMethodEngine.getKeyboardDelegate().on('keyUp', (keyEvent: inputMethodEngine.KeyEvent) => {
  console.info(`inputMethodEngine keyCode.(keyUp): ${keyEvent.keyCode}`);
  console.info(`inputMethodEngine keyAction.(keyUp): ${keyEvent.keyAction}`);
  return true;
});
inputMethodEngine.getKeyboardDelegate().on('keyDown', (keyEvent: inputMethodEngine.KeyEvent) => {
  console.info(`inputMethodEngine keyCode.(keyDown): ${keyEvent.keyCode}`);
  console.info(`inputMethodEngine keyAction.(keyDown): ${keyEvent.keyAction}`);
  return true;
});

```

<a id="on-2"></a>
## on('keyEvent')

```TypeScript
on(type: 'keyEvent', callback: (event: InputKeyEvent) => boolean): void
```

订阅硬键盘（即物理键盘）事件。使用callback异步回调。与on('keyDown'|'keyUp')相比，on('keyEvent')提供更完整的按键事件信息（包含组合键Ctrl/Shift/Alt状态、unicodeChar等），适用于需要处理组合键或获取更丰富按键信息的场景。

**使用场景：** 需要处理组合键（如Ctrl+C、Shift+Enter等）或获取更完整按键信息（如unicodeChar、ctrlKey等）的场景。

**使用后效果：** 当物理按键事件触发时回调被调用。若按键事件被事件订阅者消费，则callback应返回true，否则返回false。

**起始版本：** 10

<!--Device-KeyboardDelegate-on(type: 'keyEvent', callback: (event: InputKeyEvent) => boolean): void--><!--Device-KeyboardDelegate-on(type: 'keyEvent', callback: (event: InputKeyEvent) => boolean): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyEvent' | 是 | 设置监听类型，固定取值为'keyEvent'。 |
| callback | (event: InputKeyEvent) =&gt; boolean | 是 | 回调函数，入参为按键事件信息，返回值类型为布尔类型。<br/>- 入参按键事件信息的数据类型为[InputKeyEvent](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-keyevent-keyevent-i.md)。<br/>- 若按键事件被事件订阅者消费，则callback应返回true，否则返回false。 |

**示例：**

```TypeScript
import type { KeyEvent } from '@kit.InputKit';

inputMethodEngine.getKeyboardDelegate().on('keyEvent', (keyEvent: KeyEvent) => {
  console.info(`inputMethodEngine keyEvent.action:${ keyEvent.action}`);
  console.info(`inputMethodEngine keyEvent.key.code: ${keyEvent.key.code}`);
  console.info(`inputMethodEngine keyEvent.ctrlKey: ${keyEvent.ctrlKey}`);
  console.info(`inputMethodEngine keyEvent.unicodeChar: ${keyEvent.unicodeChar}`);
  return true;
});

```

<a id="on-3"></a>
## on('cursorContextChange')

```TypeScript
on(type: 'cursorContextChange', callback: (x: number, y: number, height: number) => void): void
```

订阅光标变化事件。使用callback异步回调。

**使用场景：** 实时更新候选词显示位置、根据光标位置调整输入法界面、实现跟随光标的浮动菜单等。

**使用后效果：** 当编辑框光标位置发生变化时触发回调，返回光标的x坐标、y坐标和高度信息，输入法应用可据此调整候选词窗口或面板的定位。

**起始版本：** 8

<!--Device-KeyboardDelegate-on(type: 'cursorContextChange', callback: (x: number, y: number, height: number) => void): void--><!--Device-KeyboardDelegate-on(type: 'cursorContextChange', callback: (x: number, y: number, height: number) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cursorContextChange' | 是 | 光标变化事件，固定取值为'cursorContextChange'。 |
| callback | (x: number, y: number, height: number) =&gt; void | 是 | 回调函数，返回光标信息。<br/>- x为光标上端的x坐标值，单位：px，y为光标上端的y坐标值，单位：px，height为光标的高度值，单位：px。 |

**示例：**

```TypeScript
inputMethodEngine.getKeyboardDelegate().on('cursorContextChange', (x: number, y: number, height: number) => {
  console.info('inputMethodEngine cursorContextChange x:' + x);
  console.info('inputMethodEngine cursorContextChange y:' + y);
  console.info('inputMethodEngine cursorContextChange height:' + height);
});

```

<a id="on-4"></a>
## on('selectionChange')

```TypeScript
on(
      type: 'selectionChange',
      callback: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void
    ): void
```

订阅文本选择范围变化事件。使用callback异步回调。

**使用场景：** 监听用户选中文本以提供剪切、复制、粘贴等快捷操作、根据选择文本显示相关建议、实现文本编辑辅助功能等。

**使用后效果：** 当编辑框中文本选择范围发生变化时触发回调，返回变化前后的选区起始和终止下标。

**起始版本：** 8

<!--Device-KeyboardDelegate-on(
      type: 'selectionChange',
      callback: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void
    ): void--><!--Device-KeyboardDelegate-on(
      type: 'selectionChange',
      callback: (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => void
    ): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'selectionChange' | 是 | 文本选择变化事件，固定取值为'selectionChange'。 |
| callback | (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) =&gt; void | 是 | 回调函数，返回文本选择信息。<br/>- oldBegin为变化前被选中文本的起始下标，oldEnd为变化前被选中文本的终止下标。<br/>- newBegin为变化后被选中文本的起始下标，newEnd为变化后被选中文本的终止下标。 |

**示例：**

```TypeScript
inputMethodEngine.getKeyboardDelegate()
  .on('selectionChange', (oldBegin: number, oldEnd: number, newBegin: number, newEnd: number) => {
    console.info('selectionChange oldBegin:' + oldBegin);
    console.info('selectionChange oldEnd:' + oldEnd);
    console.info('selectionChange newBegin:' + newBegin);
    console.info('selectionChange newEnd:' + newEnd);
  });

```

<a id="on-5"></a>
## on('textChange')

```TypeScript
on(type: 'textChange', callback: (text: string) => void): void
```

订阅文本内容变化事件。使用callback异步回调。

**使用场景：** 输入法应用需要根据编辑框文本内容变化更新候选词、提供智能输入建议、实现联想输入等。

**使用后效果：** 当编辑框文本内容发生变化时触发回调，返回当前编辑框的完整文本内容。

**起始版本：** 8

<!--Device-KeyboardDelegate-on(type: 'textChange', callback: (text: string) => void): void--><!--Device-KeyboardDelegate-on(type: 'textChange', callback: (text: string) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'textChange' | 是 | 文本变化事件，固定取值为'textChange'。 |
| callback | (text: string) =&gt; void | 是 | 回调函数，返回订阅的文本内容。 |

**示例：**

```TypeScript
inputMethodEngine.getKeyboardDelegate().on('textChange', (text: string) => {
  console.info('inputMethodEngine textChange. text:' + text);
});

```

<a id="on-6"></a>
## on('editorAttributeChanged')

```TypeScript
on(type: 'editorAttributeChanged', callback: (attr: EditorAttribute) => void): void
```

订阅编辑框属性变化事件。使用callback异步回调。

**使用场景：** 输入法应用需要根据编辑框属性变化（如输入类型从文本切换到数字、回车键类型从"搜索"切换到"发送"等）动态调整键盘布局。

**使用后效果：** 当编辑框属性发生变化时触发回调，返回变化后的编辑框属性信息（包括inputPattern和enterKeyType），输入法应用可据此重新调整键盘布局。

**起始版本：** 10

<!--Device-KeyboardDelegate-on(type: 'editorAttributeChanged', callback: (attr: EditorAttribute) => void): void--><!--Device-KeyboardDelegate-on(type: 'editorAttributeChanged', callback: (attr: EditorAttribute) => void): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'editorAttributeChanged' | 是 | 编辑框属性变化事件，固定取值为'editorAttributeChanged'。 |
| callback | (attr: EditorAttribute) =&gt; void | 是 | 回调函数，返回变化的编辑框属性。 |

**示例：**

```TypeScript
inputMethodEngine.getKeyboardDelegate()
  .on('editorAttributeChanged', (editorAttribute: inputMethodEngine.EditorAttribute) => {
    console.info(`Succeeded in receiving attribute of editor, inputPattern = ${editorAttribute.inputPattern}, enterKeyType = ${editorAttribute.enterKeyType}`);
  });

```

