# InputMethodController

下列API示例中都需使用[getController](arkts-ime-getcontroller-f.md#getcontroller-1)获取到InputMethodController实例，再通过实例调用对应方法。

InputMethodController是输入法客户端控制器，面向前台应用提供与输入法交互的核心能力。通过`inputMethod.getController()`获取实例后，可进行以下操作：

- **绑定管理**：通过
[attach](arkts-ime-inputmethodcontroller-i.md#attach-1)
建立与输入法的绑定，通过[detach](arkts-ime-inputmethodcontroller-i.md#detach-1)解除绑定。attach和
detach必须配对使用。
- **键盘控制**：通过[showTextInput](arkts-ime-inputmethodcontroller-i.md#showtextinput-1)拉
起软键盘进入编辑状态，通过[hideTextInput](arkts-ime-inputmethodcontroller-i.md#hidetextinput-1)隐
藏软键盘退出编辑状态。showTextInput和hideTextInput必须配对使用。
- **编辑框状态同步**：通过
[updateCursor](arkts-ime-inputmethodcontroller-i.md#updatecursor-1)
、
[changeSelection](arkts-ime-inputmethodcontroller-i.md#changeselection-1)
、
[updateAttribute](arkts-ime-inputmethodcontroller-i.md#updateattribute-1)
等接口向输入法同步光标、选区、属性等编辑框状态信息。
- **事件订阅**：通过on('insertText')、on('deleteLeft')等接口订阅输入法应用发送的文本操作事件。

典型调用序列：`getController()` → `attach()` → `showTextInput()`/`hideTextInput()` → `detach()`

> **注意：**
>
> attach和detach必须配对使用，showTextInput和hideTextInput必须配对使用，否则可能导致资源泄漏或状态不一致。

**起始版本：** 6

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## attach

```TypeScript
attach(showKeyboard: boolean, textConfig: TextConfig, callback: AsyncCallback<void>): void
```

自绘控件绑定输入法。使用callback异步回调。

**含义/功能**：建立自绘控件与输入法应用之间的绑定关系，是自绘控件使用输入法功能的前提。

**使用场景：**自绘控件（非系统原生编辑框）需要与输入法交互时，必须先调用此接口建立绑定。原生编辑框获焦时系统自动绑定，无需调用此接口。

**使用后效果**：绑定成功后，自绘控件可调用showTextInput/hideTextInput控制键盘显隐、调用updateCursor/changeSelection同步编辑框状态、订阅输入法事件等。

**异步返回方式**：使用callback异步回调。成功时err为undefined；失败时返回BusinessError对象。

**前提条件/前置操作**：自绘控件所在窗口需处于获焦状态，否则绑定会失败。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| showKeyboard | boolean | 是 | 绑定输入法成功后，是否拉起输入法键盘。<br>- true表示拉起。<br>- false表示不拉起。 |
| textConfig | TextConfig | 是 | 编辑框的配置信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当绑定输入法成功后，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let inputAttribute: inputMethod.InputAttribute = {
  textInputType: inputMethod.TextInputType.TEXT,
  enterKeyType: inputMethod.EnterKeyType.GO
}
let textConfig: inputMethod.TextConfig = { inputAttribute: inputAttribute };
inputMethod.getController().attach(true, textConfig, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to attach, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in attaching the inputMethod.');
});

```

## attach

```TypeScript
attach(showKeyboard: boolean, textConfig: TextConfig): Promise<void>
```

自绘控件绑定输入法。使用promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| showKeyboard | boolean | 是 | 绑定输入法成功后，是否拉起输入法键盘。<br>- true表示拉起。<br>- false表示不拉起。 |
| textConfig | TextConfig | 是 | 编辑框的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let inputAttribute: inputMethod.InputAttribute = {
  textInputType: inputMethod.TextInputType.TEXT,
  enterKeyType: inputMethod.EnterKeyType.GO
}
let textConfig: inputMethod.TextConfig = { inputAttribute: inputAttribute };
inputMethod.getController().attach(true, textConfig).then(() => {
  console.info('Succeeded in attaching inputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to attach, code: ${err.code}, message: ${err.message}`);
});

```

## attach

```TypeScript
attach(showKeyboard: boolean, textConfig: TextConfig, requestKeyboardReason: RequestKeyboardReason): Promise<void>
```

自绘控件绑定输入法。使用promise异步回调。

**起始版本：** 15

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| showKeyboard | boolean | 是 | 绑定输入法成功后，是否拉起输入法键盘。<br>- true表示拉起。<br>- false表示不拉起。 |
| textConfig | TextConfig | 是 | 编辑框的配置信息。 |
| requestKeyboardReason | RequestKeyboardReason | 是 | 请求键盘输入的原因。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let inputAttribute: inputMethod.InputAttribute = {
  textInputType: inputMethod.TextInputType.TEXT,
  enterKeyType: inputMethod.EnterKeyType.GO
}
let textConfig: inputMethod.TextConfig = { inputAttribute: inputAttribute };
let requestKeyboardReason: inputMethod.RequestKeyboardReason = inputMethod.RequestKeyboardReason.MOUSE;

inputMethod.getController().attach(true, textConfig, requestKeyboardReason).then(() => {
  console.info('Succeeded in attaching inputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to attach, code: ${err.code}, message: ${err.message}`);
});

```

## attachWithUIContext

```TypeScript
attachWithUIContext(uiContext: UIContext, textConfig: TextConfig, attachOptions?: AttachOptions): Promise<void>
```

自绘控件绑定输入法。使用promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uiContext | UIContext | 是 | UIContext实例对象。 |
| textConfig | TextConfig | 是 | 编辑框的配置信息。 |
| attachOptions | AttachOptions | 否 | 绑定附加选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { UIContext } from '@kit.ArkUI';

let uiContext: UIContext | undefined = UIContext.getCallingScopeUIContext();
let inputAttribute: inputMethod.InputAttribute = {
  textInputType: inputMethod.TextInputType.TEXT,
  enterKeyType: inputMethod.EnterKeyType.GO
}
let textConfig: inputMethod.TextConfig = { inputAttribute: inputAttribute };
let attachOptions: inputMethod.AttachOptions = { showKeyboard: true };
inputMethod.getController().attachWithUIContext(uiContext, textConfig, attachOptions).then(() => {
  console.info('Succeeded in attaching inputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to attach, code: ${err.code}, message: ${err.message}`);
});

```

## changeSelection

```TypeScript
changeSelection(text: string, start: number, end: number, callback: AsyncCallback<void>): void
```

当编辑框内被选中的文本信息内容或文本范围发生变化时，可调用该接口更新文本信息，使输入法应用感知到变化。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 整个输入文本。 |
| start | number | 是 | 所选文本的起始位置。该参数应为大于或等于0的整数。 |
| end | number | 是 | 所选文本的结束位置。该参数应为大于或等于0的整数。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当文本信息更新成功时，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().changeSelection('text', 0, 5, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to changeSelection, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in changing selection.');
});

```

## changeSelection

```TypeScript
changeSelection(text: string, start: number, end: number): Promise<void>
```

当编辑框内被选中的文本信息内容或文本范围发生变化时，可调用该接口更新文本信息，使输入法应用感知到变化。使用promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 整个输入文本。 |
| start | number | 是 | 所选文本的起始位置。该参数应为大于或等于0的整数。 |
| end | number | 是 | 所选文本的结束位置。该参数应为大于或等于0的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().changeSelection('test', 0, 5).then(() => {
  console.info('Succeeded in changing selection.');
}).catch((err: BusinessError) => {
  console.error(`Failed to changeSelection, code: ${err.code}, message: ${err.message}`);
});

```

## detach

```TypeScript
detach(callback: AsyncCallback<void>): void
```

自绘控件解除与输入法的绑定。使用callback异步回调。

**含义/功能**：解除自绘控件与输入法应用之间的绑定关系，释放相关资源。

**使用场景：**自绘控件不再需要与输入法交互时调用（如页面切换、编辑框被销毁等）。

**使用后效果**：解除绑定后，不能再调用showTextInput、hideTextInput、updateCursor等需要绑定状态的接口。输入法软键盘将被隐藏。

**异步返回方式**：使用callback异步回调。成功时err为undefined；失败时返回BusinessError对象。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当解绑定输入法成功时，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().detach((err: BusinessError) => {
  if (err) {
    console.error(`Failed to detach, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in detaching inputMethod.');
});

```

## detach

```TypeScript
detach(): Promise<void>
```

自绘控件解除与输入法的绑定。使用promise异步回调。

**含义/功能**：解除自绘控件与输入法应用之间的绑定关系，释放相关资源。

**使用场景：**自绘控件不再需要与输入法交互时调用。

**使用后效果**：解除绑定后，不能再调用需要绑定状态的接口。输入法软键盘将被隐藏。

**异步返回方式**：使用Promise异步回调。成功时无返回结果；失败时返回BusinessError对象。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().detach().then(() => {
  console.info('Succeeded in detaching inputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to detach, code: ${err.code}, message: ${err.message}`);
});

```

## discardTypingText

```TypeScript
discardTypingText(): Promise<void>
```

编辑框应用发送“清空正在输入的文字”命令到输入法。使用promise异步回调。

**起始版本：** 20

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |
| [12800015](../errorcode-inputmethod-framework.md#12800015-消息接收端无法接收自定义通信数据) | the other side does not accept the request. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().discardTypingText().then(() => {
  console.info('Succeeded discardTypingText.');
}).catch((err: BusinessError) => {
  console.error(`Failed to discardTypingText, code: ${err.code}, message: ${err.message}`);
});

```

## hideSoftKeyboard

```TypeScript
hideSoftKeyboard(callback: AsyncCallback<void>): void
```

隐藏输入法软键盘。使用callback异步回调。

**含义/功能**：强制隐藏当前输入法的软键盘。

**使用场景：**系统应用需要强制隐藏输入法软键盘时使用。

**使用后效果**：输入法软键盘被隐藏。

**异步返回方式**：使用callback异步回调。成功时err为undefined；失败时返回BusinessError对象。

**前提条件/前置操作**：编辑框与输入法绑定时才能调用。

**相似接口差异点及选取原则**：

- **hideSoftKeyboard**：面向系统应用，需权限ohos.permission.CONNECT_IME_ABILITY，仅隐藏键盘不退出编辑状态。
- **hideTextInput**：面向自绘控件，隐藏键盘并退出编辑状态，可再次showTextInput重新进入。
- **选取原则**：自绘控件使用hideTextInput；系统应用且有权限时使用hideSoftKeyboard。

**起始版本：** 9

**需要权限：** ohos.permission.CONNECT_IME_ABILITY

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当软键盘隐藏成功。err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permissions check fails. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().hideSoftKeyboard((err: BusinessError) => {
  if (!err) {
    console.info('Succeeded in hiding softKeyboard.');
  } else {
    console.error(`Failed to hide softKeyboard, code: ${err.code}, message: ${err.message}`);
  }
})

```

## hideSoftKeyboard

```TypeScript
hideSoftKeyboard(): Promise<void>
```

隐藏输入法软键盘。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.CONNECT_IME_ABILITY

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permissions check fails. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().hideSoftKeyboard().then(() => {
  console.info('Succeeded in hiding softKeyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide softKeyboard, code: ${err.code}, message: ${err.message}`);
});

```

## hideTextInput

```TypeScript
hideTextInput(callback: AsyncCallback<void>): void
```

退出文本编辑状态。使用callback异步回调。

**含义/功能**：隐藏软键盘，使编辑框退出文本编辑状态。

**使用场景：**自绘控件不再需要输入时调用，如用户点击了编辑框外的区域、切换到其他页面等。

**使用后效果**：软键盘被隐藏，编辑框退出编辑状态。调用此接口不会解除与输入法的绑定，再次调用showTextInput可重新进入编辑状态。

**异步返回方式**：使用callback异步回调。成功时err为undefined；失败时返回BusinessError对象。

**前提条件/前置操作**：需先调用
[attach](arkts-ime-inputmethodcontroller-i.md#attach-1)
完成绑定，且已调用showTextInput进入编辑状态。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当成功退出编辑状态时，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().hideTextInput((err: BusinessError) => {
  if (err) {
    console.error(`Failed to hideTextInput, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in hiding text input.');
});

```

## hideTextInput

```TypeScript
hideTextInput(): Promise<void>
```

退出文本编辑状态。使用promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().hideTextInput().then(() => {
  console.info('Succeeded in hiding inputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hideTextInput, code: ${err.code}, message: ${err.message}`);
})

```

## off('selectByRange')

```TypeScript
off(type: 'selectByRange', callback?: Callback<Range>): void
```

取消订阅输入法应用按范围选中文本事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'selectByRange' | 是 | 设置监听类型，固定取值为'selectByRange'。 |
| callback | Callback&lt;Range&gt; | 否 | 取消订阅的回调函数，需要与on接口传入的保持一致。<br>参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onSelectByRangeCallback: Callback<inputMethod.Range> = (range: inputMethod.Range): void => {
  console.info(`Succeeded in subscribing selectByRange, start: ${range.start} , end: ${range.end}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('selectByRange', onSelectByRangeCallback);
inputMethodController.off('selectByRange');

```

## off('selectByMovement')

```TypeScript
off(type: 'selectByMovement', callback?: Callback<Movement>): void
```

取消订阅输入法应用按光标移动方向，选中文本事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'selectByMovement' | 是 | 设置监听类型，固定取值为'selectByMovement'。 |
| callback | Callback&lt;Movement&gt; | 否 | 取消订阅的回调函数，需要与on接口传入的保持一致。<br>参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onSelectByMovementCallback: Callback<inputMethod.Movement> = (movement: inputMethod.Movement): void => {
  console.info(`Succeeded in subscribing selectByMovement, movement.direction: ${movement.direction}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('selectByMovement', onSelectByMovementCallback);
inputMethodController.off('selectByMovement');

```

## off('insertText')

```TypeScript
off(type: 'insertText', callback?: (text: string) => void): void
```

取消订阅输入法应用插入文本事件。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'insertText' | 是 | 设置监听类型，固定取值为'insertText'。 |
| callback | (text: string) =&gt; void | 否 | 取消订阅的回调函数，需要与on接口传入的保持一致。<br/>参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onInsertTextCallback: Callback<string> = (text: string): void => {
  console.info(`Succeeded in subscribing insertText: ${text}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('insertText', onInsertTextCallback);
inputMethodController.off('insertText');

```

## off('deleteLeft')

```TypeScript
off(type: 'deleteLeft', callback?: (length: number) => void): void
```

取消订阅输入法应用向左删除文本事件。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deleteLeft' | 是 | 设置监听，固定取值为'deleteLeft'。 |
| callback | (length: number) =&gt; void | 否 | 取消订阅的回调函数，需要与on接口传入的保持一致。<br>参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onDeleteLeftCallback: Callback<number> = (length: number): void => {
  console.info(`Succeeded in subscribing deleteLeft, length: ${length}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('deleteLeft', onDeleteLeftCallback);
inputMethodController.off('deleteLeft');

```

## off('deleteRight')

```TypeScript
off(type: 'deleteRight', callback?: (length: number) => void): void
```

取消订阅输入法应用向右删除文本事件。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deleteRight' | 是 | 设置监听类型，固定取值为`deleteRight`。 |
| callback | (length: number) =&gt; void | 否 | 取消订阅的回调函数，需要与on接口传入的保持一致。<br>参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onDeleteRightCallback: Callback<number> = (length: number): void => {
  console.info(`Succeeded in subscribing deleteRight, length: ${length}`);
};
let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('deleteRight', onDeleteRightCallback);
inputMethodController.off('deleteRight');

```

## off('sendKeyboardStatus')

```TypeScript
off(type: 'sendKeyboardStatus', callback?: (keyboardStatus: KeyboardStatus) => void): void
```

取消订阅输入法应用发送输入法软键盘状态事件。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sendKeyboardStatus' | 是 | 设置监听类型，固定取值为'sendKeyboardStatus'。 |
| callback | (keyboardStatus: KeyboardStatus) =&gt; void | 否 | 取消订阅的回调函数。参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onSendKeyboardStatus: Callback<inputMethod.KeyboardStatus> = (keyboardStatus: inputMethod.KeyboardStatus): void => {
  console.info(`Succeeded in subscribing sendKeyboardStatus, keyboardStatus: ${keyboardStatus}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('sendKeyboardStatus', onSendKeyboardStatus);
inputMethodController.off('sendKeyboardStatus');

```

## off('sendFunctionKey')

```TypeScript
off(type: 'sendFunctionKey', callback?: (functionKey: FunctionKey) => void): void
```

取消订阅输入法应用发送功能键事件。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sendFunctionKey' | 是 | 设置监听类型，固定取值为'sendFunctionKey'。 |
| callback | (functionKey: FunctionKey) =&gt; void | 否 | 取消订阅的回调函数，需要与on接口传入的保持一致。<br>参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onSendFunctionKey: Callback<inputMethod.FunctionKey> = (functionKey: inputMethod.FunctionKey): void => {
  console.info(`Succeeded in subscribing sendFunctionKey, functionKey: ${functionKey.enterKeyType}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('sendFunctionKey', onSendFunctionKey);
inputMethodController.off('sendFunctionKey');

```

## off('moveCursor')

```TypeScript
off(type: 'moveCursor', callback?: (direction: Direction) => void): void
```

取消订阅输入法应用移动光标事件。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'moveCursor' | 是 | 设置监听类型，固定取值为'moveCursor'。 |
| callback | (direction: Direction) =&gt; void | 否 | 取消订阅的回调函数，需要与on接口传入的保持一致。<br>参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onMoveCursorCallback: Callback<inputMethod.Direction> = (direction: inputMethod.Direction): void => {
  console.info(`Succeeded in subscribing moveCursor, direction: ${direction}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('moveCursor', onMoveCursorCallback);
inputMethodController.off('moveCursor');

```

## off('handleExtendAction')

```TypeScript
off(type: 'handleExtendAction', callback?: (action: ExtendAction) => void): void
```

取消订阅输入法应用发送扩展编辑操作事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'handleExtendAction' | 是 | 设置监听类型，固定取值为'handleExtendAction'。 |
| callback | (action: ExtendAction) =&gt; void | 否 | 取消订阅的回调函数，需要与on接口传入的保持一致。<br>参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let onHandleExtendActionCallback: Callback<inputMethod.ExtendAction> = (action: inputMethod.ExtendAction): void => {
  console.info(`Succeeded in subscribing handleExtendAction, action: ${action}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('handleExtendAction', onHandleExtendActionCallback);
inputMethodController.off('handleExtendAction');

```

## off('getLeftTextOfCursor')

```TypeScript
off(type: 'getLeftTextOfCursor', callback?: (length: number) => string): void
```

取消订阅输入法应用获取光标左侧指定长度文本事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'getLeftTextOfCursor' | 是 | 设置监听类型，固定取值为'getLeftTextOfCursor'。 |
| callback | (length: number) =&gt; string | 否 | 取消订阅的回调函数，需要与on接口传入的保持一致。<br>参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
let getLeftTextOfCursorCallback: (length: number) => string = (length: number): string => {
  console.info(`Succeeded in unsubscribing getLeftTextOfCursor, length: ${length}`);
  let text: string = "";
  return text;
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('getLeftTextOfCursor', getLeftTextOfCursorCallback);
inputMethodController.off('getLeftTextOfCursor');

```

## off('getRightTextOfCursor')

```TypeScript
off(type: 'getRightTextOfCursor', callback?: (length: number) => string): void
```

取消订阅输入法应用获取光标右侧指定长度文本事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'getRightTextOfCursor' | 是 | 设置监听类型，固定取值为'getRightTextOfCursor'。 |
| callback | (length: number) =&gt; string | 否 | 取消订阅的回调函数，需要与on接口传入的保持一致。<br>参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
let getRightTextOfCursorCallback: (length: number) => string = (length: number): string => {
  console.info(`Succeeded in unsubscribing getRightTextOfCursor, length: ${length}`);
  let text: string = "";
  return text;
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('getRightTextOfCursor', getRightTextOfCursorCallback);
inputMethodController.off('getRightTextOfCursor');

```

## off('getTextIndexAtCursor')

```TypeScript
off(type: 'getTextIndexAtCursor', callback?: () => number): void
```

取消订阅输入法应用获取光标处文本索引事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'getTextIndexAtCursor' | 是 | 设置监听类型，固定取值为'getTextIndexAtCursor'。 |
| callback | () =&gt; number | 否 | 取消订阅的回调函数，需要与on接口传入的保持一致。<br>参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
let getTextIndexAtCursorCallback: () => number = (): number => {
  console.info(`Succeeded in unsubscribing getTextIndexAtCursor.`);
  let index: number = 0;
  return index;
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.off('getTextIndexAtCursor', getTextIndexAtCursorCallback);
inputMethodController.off('getTextIndexAtCursor');

```

## off('setPreviewText')

```TypeScript
off(type: 'setPreviewText', callback?: SetPreviewTextCallback): void
```

取消订阅输入法应用操作文本预览内容的事件。使用callback异步回调。

**起始版本：** 17

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'setPreviewText' | 是 | 设置监听类型，固定取值为'setPreviewText'。 |
| callback | SetPreviewTextCallback | 否 | 取消订阅的回调函数，需要与on接口传入的保持一致。<br>参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
let setPreviewTextCallback1: inputMethod.SetPreviewTextCallback = (text: string, range: inputMethod.Range): void => {
  console.info(`SetPreviewTextCallback1: Received text - ${text}, Received range - start: ${range.start}, end: ${range.end}`);
};

let setPreviewTextCallback2: inputMethod.SetPreviewTextCallback = (text: string, range: inputMethod.Range): void => {
  console.info(`setPreviewTextCallback2: Received text - ${text}, Received range - start: ${range.start}, end: ${range.end}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.on('setPreviewText', setPreviewTextCallback1);
console.info(`SetPreviewTextCallback1 subscribed to setPreviewText`);
inputMethodController.on('setPreviewText', setPreviewTextCallback2);
console.info(`SetPreviewTextCallback2 subscribed to setPreviewText`);
// 仅取消setPreviewText的callback1的回调。
inputMethodController.off('setPreviewText', setPreviewTextCallback1);
console.info(`SetPreviewTextCallback1 unsubscribed from setPreviewText`);
// 取消setPreviewText的所有回调。
inputMethodController.off('setPreviewText');
console.info(`All callbacks unsubscribed from setPreviewText`);

```

## off('finishTextPreview')

```TypeScript
off(type: 'finishTextPreview', callback?: Callback<void>): void
```

取消订阅结束文本预览事件。使用callback异步回调。

**起始版本：** 17

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'finishTextPreview' | 是 | 设置监听类型，固定取值为'finishTextPreview'。 |
| callback | Callback&lt;void&gt; | 否 | 取消订阅的回调函数，需要与on接口传入的保持一致。<br>参数不填写时，取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let finishTextPreviewCallback1: Callback<void> = (): void => {
  console.info(`FinishTextPreviewCallback1: finishTextPreview event triggered`);
};
let finishTextPreviewCallback2: Callback<void> = (): void => {
  console.info(`FinishTextPreviewCallback2: finishTextPreview event triggered`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.on('finishTextPreview', finishTextPreviewCallback1);
console.info(`FinishTextPreviewCallback1 subscribed to finishTextPreview`);
inputMethodController.on('finishTextPreview', finishTextPreviewCallback2);
console.info(`FinishTextPreviewCallback2 subscribed to finishTextPreview`);
// 仅取消finishTextPreview的callback1的回调。
inputMethodController.off('finishTextPreview', finishTextPreviewCallback1);
console.info(`FinishTextPreviewCallback1 unsubscribed from finishTextPreview`);
// 取消finishTextPreview的所有回调。
inputMethodController.off('finishTextPreview');
console.info(`All callbacks unsubscribed from finishTextPreview`);

```

## on('selectByRange')

```TypeScript
on(type: 'selectByRange', callback: Callback<Range>): void
```

订阅输入法应用按范围选中文本事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'selectByRange' | 是 | 设置监听类型，固定取值为'selectByRange'。 |
| callback | Callback&lt;Range&gt; | 是 | 回调函数，返回需要选中的文本范围。<br/>根据传入的文本范围，开发者在回调函数中编辑框中相应文本。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```TypeScript
inputMethod.getController().on('selectByRange', (range: inputMethod.Range) => {
  console.info(`Succeeded in subscribing selectByRange: start: ${range.start} , end: ${range.end}`);
});

```

## on('selectByMovement')

```TypeScript
on(type: 'selectByMovement', callback: Callback<Movement>): void
```

订阅输入法应用按光标移动方向，选中文本事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'selectByMovement' | 是 | 设置监听类型，固定取值为'selectByMovement'。 |
| callback | Callback&lt;Movement&gt; | 是 | 回调函数，返回光标移动的方向。<br/>根据传入的光标移动方向，选中编辑框中相应文本。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```TypeScript
inputMethod.getController().on('selectByMovement', (movement: inputMethod.Movement) => {
  console.info('Succeeded in subscribing selectByMovement: direction: ' + movement.direction);
});

```

## on('insertText')

```TypeScript
on(type: 'insertText', callback: (text: string) => void): void
```

订阅输入法应用插入文本事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'insertText' | 是 | 设置监听类型，固定取值为'insertText'。 |
| callback | (text: string) =&gt; void | 是 | 回调函数，返回需要插入的文本内容。<br/>根据传入的文本，在回调函数中操作编辑框中的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
function callback1(text: string): void {
  console.info(`Succeeded in getting callback1, data: ${text}`);
}

function callback2(text: string): void {
  console.info(`Succeeded in getting callback2, data: ${text}`);
}

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
// 注册回调
inputMethodController.on('insertText', callback1);
inputMethodController.on('insertText', callback2);
// 仅取消insertText的callback1的回调
inputMethodController.off('insertText', callback1);
// 取消insertText的所有回调
inputMethodController.off('insertText');

```

## on('deleteLeft')

```TypeScript
on(type: 'deleteLeft', callback: (length: number) => void): void
```

订阅输入法应用向左删除文本事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deleteLeft' | 是 | 设置监听类型，固定取值为'deleteLeft'。 |
| callback | (length: number) =&gt; void | 是 | 回调函数，返回需要向左删除的文本长度。<br/>根据传入的删除长度，在回调函数中操作编辑框中的文本。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
inputMethod.getController().on('deleteLeft', (length: number) => {
  console.info(`Succeeded in subscribing deleteLeft, length: ${length}`);
});

```

## on('deleteRight')

```TypeScript
on(type: 'deleteRight', callback: (length: number) => void): void
```

订阅输入法应用向右删除文本事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deleteRight' | 是 | 设置监听类型，固定取值为'deleteRight'。 |
| callback | (length: number) =&gt; void | 是 | 回调函数，返回需要向右删除的文本长度。<br/>根据传入的删除长度，在回调函数中操作编辑框中的文本。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
inputMethod.getController().on('deleteRight', (length: number) => {
  console.info(`Succeeded in subscribing deleteRight, length: ${length}`);
});

```

## on('sendKeyboardStatus')

```TypeScript
on(type: 'sendKeyboardStatus', callback: (keyboardStatus: KeyboardStatus) => void): void
```

订阅输入法应用发送输入法软键盘状态事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sendKeyboardStatus' | 是 | 设置监听类型，固定取值为'sendKeyboardStatus'。 |
| callback | (keyboardStatus: KeyboardStatus) =&gt; void | 是 | 回调函数，返回软键盘状态。<br/>根据传入的软键盘状态，在回调函数中做相应操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
inputMethod.getController().on('sendKeyboardStatus', (keyboardStatus: inputMethod.KeyboardStatus) => {
  console.info(`Succeeded in subscribing sendKeyboardStatus, keyboardStatus: ${keyboardStatus}`);
});

```

## on('sendFunctionKey')

```TypeScript
on(type: 'sendFunctionKey', callback: (functionKey: FunctionKey) => void): void
```

订阅输入法应用发送功能键事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sendFunctionKey' | 是 | 设置监听类型，固定取值为'sendFunctionKey'。 |
| callback | (functionKey: FunctionKey) =&gt; void | 是 | 回调函数，返回输入法应用发送的功能键信息。<br/>根据返回的功能键信息，做相应操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
inputMethod.getController().on('sendFunctionKey', (functionKey: inputMethod.FunctionKey) => {
  console.info(`Succeeded in subscribing sendFunctionKey, functionKey.enterKeyType: ${functionKey.enterKeyType}`);
});

```

## on('moveCursor')

```TypeScript
on(type: 'moveCursor', callback: (direction: Direction) => void): void
```

订阅输入法应用移动光标事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'moveCursor' | 是 | 设置监听类型，固定取值为'moveCursor'。 |
| callback | (direction: Direction) =&gt; void | 是 | 回调函数，返回光标信息。<br/>根据返回的光标移动方向，改变光标位置，如光标向上或向下。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
inputMethod.getController().on('moveCursor', (direction: inputMethod.Direction) => {
  console.info(`Succeeded in subscribing moveCursor, direction: ${direction}`);
});

```

## on('handleExtendAction')

```TypeScript
on(type: 'handleExtendAction', callback: (action: ExtendAction) => void): void
```

订阅输入法应用发送扩展编辑操作事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'handleExtendAction' | 是 | 设置监听类型，固定取值为'handleExtendAction'。 |
| callback | (action: ExtendAction) =&gt; void | 是 | 回调函数，返回扩展编辑操作类型。<br/>根据传入的扩展编辑操作类型，做相应的操作，如剪切、复制等。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
inputMethod.getController().on('handleExtendAction', (action: inputMethod.ExtendAction) => {
  console.info(`Succeeded in subscribing handleExtendAction, action: ${action}`);
});

```

## on('getLeftTextOfCursor')

```TypeScript
on(type: 'getLeftTextOfCursor', callback: (length: number) => string): void
```

订阅输入法应用获取光标左侧指定长度文本事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'getLeftTextOfCursor' | 是 | 设置监听类型，固定取值为'getLeftTextOfCursor'。 |
| callback | (length: number) =&gt; string | 是 | 回调函数，获取编辑框最新状态下光标左侧指定长度的文本内容并返回。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
inputMethod.getController().on('getLeftTextOfCursor', (length: number) => {
  console.info(`Succeeded in subscribing getLeftTextOfCursor, length: ${length}`);
  let text: string = "";
  return text;
});

```

## on('getRightTextOfCursor')

```TypeScript
on(type: 'getRightTextOfCursor', callback: (length: number) => string): void
```

订阅输入法应用获取光标右侧指定长度文本事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'getRightTextOfCursor' | 是 | 设置监听类型，固定取值为'getRightTextOfCursor'。 |
| callback | (length: number) =&gt; string | 是 | 回调函数，获取编辑框最新状态下光标右侧指定长度的文本内容并返回。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
inputMethod.getController().on('getRightTextOfCursor', (length: number) => {
  console.info(`Succeeded in subscribing getRightTextOfCursor, length: ${length}`);
  let text: string = "";
  return text;
});

```

## on('getTextIndexAtCursor')

```TypeScript
on(type: 'getTextIndexAtCursor', callback: () => number): void
```

订阅输入法应用获取光标处文本索引事件。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'getTextIndexAtCursor' | 是 | 设置监听类型，固定取值为'getTextIndexAtCursor'。 |
| callback | () =&gt; number | 是 | 回调函数，获取编辑框最新状态下光标处文本索引并返回。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
inputMethod.getController().on('getTextIndexAtCursor', () => {
  console.info(`Succeeded in subscribing getTextIndexAtCursor.`);
  let index: number = 0;
  return index;
});

```

## on('setPreviewText')

```TypeScript
on(type: 'setPreviewText', callback: SetPreviewTextCallback): void
```

订阅输入法应用操作文本预览内容的事件。使用callback异步回调。

**起始版本：** 17

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'setPreviewText' | 是 | 设置监听类型，固定取值为'setPreviewText'。 |
| callback | SetPreviewTextCallback | 是 | 回调函数。用于接收文本预览的内容并返回。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

**示例：**

```TypeScript
let setPreviewTextCallback1: inputMethod.SetPreviewTextCallback = (text: string, range: inputMethod.Range): void => {
  console.info(`SetPreviewTextCallback1: Received text - ${text}, Received range - start: ${range.start}, end: ${range.end}`);
};

let setPreviewTextCallback2: inputMethod.SetPreviewTextCallback = (text: string, range: inputMethod.Range): void => {
  console.info(`setPreviewTextCallback2: Received text - ${text}, Received range - start: ${range.start}, end: ${range.end}`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.on('setPreviewText', setPreviewTextCallback1);
console.info(`SetPreviewTextCallback1 subscribed to setPreviewText`);
inputMethodController.on('setPreviewText', setPreviewTextCallback2);
console.info(`SetPreviewTextCallback2 subscribed to setPreviewText`);
// 仅取消setPreviewText的callback1的回调。
inputMethodController.off('setPreviewText', setPreviewTextCallback1);
console.info(`SetPreviewTextCallback1 unsubscribed from setPreviewText`);
// 取消setPreviewText的所有回调。
inputMethodController.off('setPreviewText');
console.info(`All callbacks unsubscribed from setPreviewText`);

```

## on('finishTextPreview')

```TypeScript
on(type: 'finishTextPreview', callback: Callback<void>): void
```

订阅结束文本预览事件。使用callback异步回调。

**起始版本：** 17

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'finishTextPreview' | 是 | 设置监听类型，固定取值为'finishTextPreview'。 |
| callback | Callback&lt;void&gt; | 是 | 回调函数。用于处理预览文本结束的逻辑，类型为void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |

**示例：**

```TypeScript
import { Callback } from '@kit.BasicServicesKit';

let finishTextPreviewCallback1: Callback<void> = (): void => {
  console.info(`FinishTextPreviewCallback1: finishTextPreview event triggered`);
};
let finishTextPreviewCallback2: Callback<void> = (): void => {
  console.info(`FinishTextPreviewCallback2: finishTextPreview event triggered`);
};

let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.on('finishTextPreview', finishTextPreviewCallback1);
console.info(`FinishTextPreviewCallback1 subscribed to finishTextPreview`);
inputMethodController.on('finishTextPreview', finishTextPreviewCallback2);
console.info(`FinishTextPreviewCallback2 subscribed to finishTextPreview`);
// 仅取消finishTextPreview的callback1的回调。
inputMethodController.off('finishTextPreview', finishTextPreviewCallback1);
console.info(`FinishTextPreviewCallback1 unsubscribed from finishTextPreview`);
// 取消finishTextPreview的所有回调。
inputMethodController.off('finishTextPreview');
console.info(`All callbacks unsubscribed from finishTextPreview`);

```

## recvMessage

```TypeScript
recvMessage(msgHandler?: MessageHandler): void
```

注册或取消注册MessageHandler。

**起始版本：** 15

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| msgHandler | MessageHandler | 否 | 该对象通过[onMessage](arkts-ime-messagehandler-i.md#onmessage-1)接收来自输入法应用所发送的自定义通信数据，并通过[onTerminated](arkts-ime-messagehandler-i.md#onterminated-1)接收终止此对象订阅的消息。<br>若不填写此参数，则取消全局已注册的[MessageHandler](arkts-ime-messagehandler-i.md)对象，同时触发其[onTerminated](arkts-ime-messagehandler-i.md#onterminated-1)回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let messageHandler: inputMethod.MessageHandler = {
  onTerminated(): void {
    console.info('OnTerminated.');
  },
  onMessage(msgId: string, msgParam?: ArrayBuffer): void {
    console.info('recv message.');
  }
};
let inputMethodController: inputMethod.InputMethodController = inputMethod.getController();
inputMethodController.recvMessage(messageHandler);
// 取消已注册的MessageHandler
inputMethodController.recvMessage();

```

## sendMessage

```TypeScript
sendMessage(msgId: string, msgParam?: ArrayBuffer): Promise<void>
```

发送自定义通信至输入法应用。使用Promise异步回调。
>
> msgId最大限制256B，msgParam最大限制128KB。

**起始版本：** 15

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| msgId | string | 是 | 需要发送至输入法应用的自定义数据的标识符。 |
| msgParam | ArrayBuffer | 否 | 需要发送至输入法应用的自定义数据的消息体。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1. Incorrect parameter types. 2. Incorrect parameter length. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |
| [12800014](../errorcode-inputmethod-framework.md#12800014-输入法应用非完全访问模式) | the input method is in basic mode. |
| [12800015](../errorcode-inputmethod-framework.md#12800015-消息接收端无法接收自定义通信数据) | the other side does not accept the request. |
| [12800016](../errorcode-inputmethod-framework.md#12800016-输入法客户端未处于编辑状态) | input method client is not editable. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let msgId: string = "testMsgId";
let msgParam: ArrayBuffer = new ArrayBuffer(128);
inputMethod.getController().sendMessage(msgId, msgParam).then(() => {
  console.info('Succeeded send message.');
}).catch((err: BusinessError) => {
  console.error(`Failed to send message, code: ${err.code}, message: ${err.message}`);
});

```

## setCallingWindow

```TypeScript
setCallingWindow(windowId: number, callback: AsyncCallback<void>): void
```

设置要避让软键盘的窗口。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | number | 是 | 绑定输入法应用的应用程序所在的窗口Id。该参数应为整数。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当设置成功时，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let windowId: number = 2000;
inputMethod.getController().setCallingWindow(windowId, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to setCallingWindow, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in setting callingWindow.');
});

```

## setCallingWindow

```TypeScript
setCallingWindow(windowId: number): Promise<void>
```

设置要避让软键盘的窗口。使用promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | number | 是 | 绑定输入法应用的应用程序所在的窗口Id。该参数应为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let windowId: number = 2000;
inputMethod.getController().setCallingWindow(windowId).then(() => {
  console.info('Succeeded in setting callingWindow.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setCallingWindow, code: ${err.code}, message: ${err.message}`);
});

```

## showSoftKeyboard

```TypeScript
showSoftKeyboard(callback: AsyncCallback<void>): void
```

显示输入法软键盘。使用callback异步回调。

**含义/功能**：强制显示当前输入法的软键盘。

**使用场景：**系统应用需要强制显示输入法软键盘时使用（如设置应用测试输入法）。

**使用后效果**：输入法软键盘弹出显示。

**异步返回方式**：使用callback异步回调。成功时err为undefined；失败时返回BusinessError对象。

**前提条件/前置操作**：编辑框与输入法绑定时才能调用。

**相似接口差异点及选取原则**：

- **showSoftKeyboard**：面向系统应用，需权限ohos.permission.CONNECT_IME_ABILITY，仅显示键盘不改变编辑状态。
- **showTextInput**：面向自绘控件，需先attach绑定，拉起键盘并进入编辑状态。
- **选取原则**：自绘控件使用showTextInput；系统应用且有权限时使用showSoftKeyboard。

**起始版本：** 9

**需要权限：** ohos.permission.CONNECT_IME_ABILITY

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当软键盘显示成功。err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permissions check fails. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().showSoftKeyboard((err: BusinessError) => {
  if (!err) {
    console.info('Succeeded in showing softKeyboard.');
  } else {
    console.error(`Failed to show softKeyboard, ${err.code}, message: ${err.message}`);
  }
});

```

## showSoftKeyboard

```TypeScript
showSoftKeyboard(): Promise<void>
```

显示输入法软键盘。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.CONNECT_IME_ABILITY

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permissions check fails. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().showSoftKeyboard().then(() => {
  console.info('Succeeded in showing softKeyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show softKeyboard, code: ${err.code}, message: ${err.message}`);
});

```

## showTextInput

```TypeScript
showTextInput(callback: AsyncCallback<void>): void
```

进入文本编辑状态。使用callback异步回调。

**含义/功能**：拉起软键盘，使编辑框进入文本编辑状态。

**使用场景：**自绘控件绑定输入法后，需要显示软键盘开始文本输入时调用。

**使用后效果**：软键盘弹出，编辑框进入可输入的文本编辑状态。

**异步返回方式**：使用callback异步回调。成功时err为undefined；失败时返回BusinessError对象。

**前提条件/前置操作**：需先调用
[attach](arkts-ime-inputmethodcontroller-i.md#attach-1)
完成绑定，否则会报12800009错误。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。若成功进入编辑状态，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().showTextInput((err: BusinessError) => {
  if (err) {
    console.error(`Failed to showTextInput, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in showing the inputMethod.');
});

```

## showTextInput

```TypeScript
showTextInput(): Promise<void>
```

进入文本编辑状态。使用promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().showTextInput().then(() => {
  console.info('Succeeded in showing text input.');
}).catch((err: BusinessError) => {
  console.error(`Failed to showTextInput, code: ${err.code}, message: ${err.message}`);
});

```

## showTextInput

```TypeScript
showTextInput(requestKeyboardReason: RequestKeyboardReason): Promise<void>
```

进入文本编辑状态。使用promise异步回调。

**起始版本：** 15

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| requestKeyboardReason | RequestKeyboardReason | 是 | 请求键盘输入的原因。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let requestKeyboardReason: inputMethod.RequestKeyboardReason = inputMethod.RequestKeyboardReason.MOUSE;

inputMethod.getController().showTextInput(requestKeyboardReason).then(() => {
  console.info('Succeeded in showing text input.');
}).catch((err: BusinessError) => {
  console.error(`Failed to showTextInput, code: ${err.code}, message: ${err.message}`);
});

```

## stopInput

```TypeScript
stopInput(callback: AsyncCallback<boolean>): void
```

结束输入会话。使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [stopInputSession](arkts-ime-inputmethodcontroller-i.md#stopinputsession-1)

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。当会话结束成功，err为undefined，data为true；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().stopInput((err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to stopInput, code: ${err.code}, message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in stopping input.');
  } else {
    console.error('Failed to stopInput.');
  }
});

```

## stopInput

```TypeScript
stopInput(): Promise<boolean>
```

结束输入会话。使用promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [stopInputSession](arkts-ime-inputmethodcontroller-i.md#stopinputsession-1)

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示会话结束成功；返回false表示会话结束失败。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().stopInput().then((result: boolean) => {
  if (result) {
    console.info('Succeeded in stopping input.');
  } else {
    console.error('Failed to stopInput.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to stopInput, code: ${err.code}, message: ${err.message}`);
});

```

## stopInputSession

```TypeScript
stopInputSession(callback: AsyncCallback<boolean>): void
```

结束输入会话。使用callback异步回调。

**含义/功能**：结束当前的输入会话，隐藏软键盘。

**使用场景：**应用需要主动结束输入会话时调用（如用户完成了输入操作）。

**使用后效果**：软键盘被隐藏，输入会话结束。与hideTextInput不同，stopInputSession直接结束会话而不需要先进入编辑状态。

**异步返回方式**：使用callback异步回调。成功时err为undefined，data为true；失败时返回BusinessError对象。

**前提条件/前置操作**：编辑框与输入法绑定时才能调用，即点击编辑控件后。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。当结束输入会话成功时，err为undefined，data为true；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().stopInputSession((err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to stopInputSession, code: ${err.code}, message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in stopping inputSession.');
  } else {
    console.error('Failed to stopInputSession.');
  }
});

```

## stopInputSession

```TypeScript
stopInputSession(): Promise<boolean>
```

结束输入会话。使用promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示结束输入会话成功，返回false表示结束输入会话失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getController().stopInputSession().then((result: boolean) => {
  if (result) {
    console.info('Succeeded in stopping inputSession.');
  } else {
    console.error('Failed to stopInputSession.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to stopInputSession, code: ${err.code}, message: ${err.message}`);
});

```

## updateAttribute

```TypeScript
updateAttribute(attribute: InputAttribute, callback: AsyncCallback<void>): void
```

更新编辑框属性信息。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| attribute | InputAttribute | 是 | 编辑框属性对象。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当编辑框属性信息更新成功时，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let inputAttribute: inputMethod.InputAttribute = { textInputType: 0, enterKeyType: 1 };
inputMethod.getController().updateAttribute(inputAttribute, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to updateAttribute, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in updating attribute.');
});

```

## updateAttribute

```TypeScript
updateAttribute(attribute: InputAttribute): Promise<void>
```

更新编辑框属性信息。使用promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| attribute | InputAttribute | 是 | 编辑框属性对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let inputAttribute: inputMethod.InputAttribute = { textInputType: 0, enterKeyType: 1 };
inputMethod.getController().updateAttribute(inputAttribute).then(() => {
  console.info('Succeeded in updating attribute.');
}).catch((err: BusinessError) => {
  console.error(`Failed to updateAttribute, code: ${err.code}, message: ${err.message}`);
});

```

## updateCursor

```TypeScript
updateCursor(cursorInfo: CursorInfo, callback: AsyncCallback<void>): void
```

当编辑框内的光标信息发生变化时，调用该接口使输入法感知到光标变化。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cursorInfo | CursorInfo | 是 | 光标信息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当光标信息更新成功时，err为undefined；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let cursorInfo: inputMethod.CursorInfo = {
  left: 0,
  top: 0,
  width: 600,
  height: 800
};
inputMethod.getController().updateCursor(cursorInfo, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to updateCursor, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in updating cursorInfo.');
});


```

## updateCursor

```TypeScript
updateCursor(cursorInfo: CursorInfo): Promise<void>
```

当编辑框内的光标信息发生变化时，调用该接口使输入法感知到光标变化。使用promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cursorInfo | CursorInfo | 是 | 光标信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |
| [12800009](../errorcode-inputmethod-framework.md#12800009-输入法客户端未绑定) | input method client detached. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let cursorInfo: inputMethod.CursorInfo = {
  left: 0,
  top: 0,
  width: 600,
  height: 800
};
inputMethod.getController().updateCursor(cursorInfo).then(() => {
  console.info('Succeeded in updating cursorInfo.');
}).catch((err: BusinessError) => {
  console.error(`Failed to updateCursor, code: ${err.code}, message: ${err.message}`);
});

```

