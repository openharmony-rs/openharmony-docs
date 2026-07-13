# InputMethodEngine

下列API均需使用[getInputMethodEngine](arkts-ime-getinputmethodengine-f.md#getinputmethodengine-1)获取到InputMethodEngine实例后，通过实例调用。

**起始版本：** 8

**废弃版本：** 23

**替代接口：** [InputMethodAbility](arkts-ime-inputmethodability-i.md)

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## off('inputStart')

```TypeScript
off(
      type: 'inputStart',
      callback?: (kbController: KeyboardController, textInputClient: TextInputClient) => void
    ): void
```

取消订阅输入法绑定成功事件。

**起始版本：** 8

**废弃版本：** 23

**替代接口：** off(type:

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'inputStart' | 是 | 设置监听类型，固定取值为'inputStart'。 |
| callback | (kbController: KeyboardController, textInputClient: TextInputClient) =&gt; void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
inputMethodEngine.getInputMethodEngine()
  .off('inputStart',
    (_kbController: inputMethodEngine.KeyboardController, _textClient: inputMethodEngine.TextInputClient) => {
      console.info('delete inputStart notification.');
    });

```

## off('keyboardShow' | 'keyboardHide')

```TypeScript
off(type: 'keyboardShow' | 'keyboardHide', callback?: () => void): void
```

取消订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 23

**替代接口：** off(type:

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyboardShow' \| 'keyboardHide' | 是 | 要取消监听的输入法软键盘事件类型。<br/>-'keyboardShow'表示显示输入法软键盘。<br/>-'keyboardHide'表示隐藏输入法软键盘。 |
| callback | () =&gt; void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
inputMethodEngine.getInputMethodEngine().off('keyboardShow');
inputMethodEngine.getInputMethodEngine().off('keyboardHide');

```

## off('keyboardShow' | 'keyboardHide')

```TypeScript
off(type: 'keyboardShow' | 'keyboardHide', callback?: () => void): void
```

取消订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 23

**替代接口：** off(type:

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyboardShow' \| 'keyboardHide' | 是 | 要取消监听的输入法软键盘事件类型。<br/>-'keyboardShow'表示显示输入法软键盘。<br/>-'keyboardHide'表示隐藏输入法软键盘。 |
| callback | () =&gt; void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
inputMethodEngine.getInputMethodEngine().off('keyboardShow');
inputMethodEngine.getInputMethodEngine().off('keyboardHide');

```

## on('inputStart')

```TypeScript
on(
      type: 'inputStart',
      callback: (kbController: KeyboardController, textInputClient: TextInputClient) => void
    ): void
```

订阅输入法绑定成功事件。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 23

**替代接口：** on(type:

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'inputStart' | 是 | 设置监听类型，固定取值为'inputStart'。 |
| callback | (kbController: KeyboardController, textInputClient: TextInputClient) =&gt; void | 是 | 回调函数，返回订阅输入法的KeyboardController和TextInputClient实例。 |

**示例：**

```TypeScript
inputMethodEngine.getInputMethodEngine()
  .on('inputStart',
    (keyboardController: inputMethodEngine.KeyboardController, textInputClient: inputMethodEngine.TextInputClient) => {
      // 使用kbController和textClient进行相关操作
    });

```

## on('keyboardShow' | 'keyboardHide')

```TypeScript
on(type: 'keyboardShow' | 'keyboardHide', callback: () => void): void
```

订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 23

**替代接口：** on(type:

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyboardShow' \| 'keyboardHide' | 是 | 设置监听类型。<br/>-'keyboardShow'表示显示输入法软键盘。<br/>-'keyboardHide'表示隐藏输入法软键盘。 |
| callback | () =&gt; void | 是 | 回调函数。 |

**示例：**

```TypeScript
inputMethodEngine.getInputMethodEngine().on('keyboardShow', () => {
  console.info('inputMethodEngine keyboardShow.');
});
inputMethodEngine.getInputMethodEngine().on('keyboardHide', () => {
  console.info('inputMethodEngine keyboardHide.');
});

```

## on('keyboardShow' | 'keyboardHide')

```TypeScript
on(type: 'keyboardShow' | 'keyboardHide', callback: () => void): void
```

订阅输入法软键盘显示或隐藏事件。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 23

**替代接口：** on(type:

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'keyboardShow' \| 'keyboardHide' | 是 | 设置监听类型。<br/>-'keyboardShow'表示显示输入法软键盘。<br/>-'keyboardHide'表示隐藏输入法软键盘。 |
| callback | () =&gt; void | 是 | 回调函数。 |

**示例：**

```TypeScript
inputMethodEngine.getInputMethodEngine().on('keyboardShow', () => {
  console.info('inputMethodEngine keyboardShow.');
});
inputMethodEngine.getInputMethodEngine().on('keyboardHide', () => {
  console.info('inputMethodEngine keyboardHide.');
});

```

