# InputMethodController

下列API示例中都需使用[getController](arkts-ime-inputmethod-getcontroller-f.md#getcontroller-1)获取到InputMethodController实例，再通过实例调用对应方法。

InputMethodController是输入法客户端控制器，面向前台应用提供与输入法交互的核心能力。通过`inputMethod.getController()`获取实例后，可进行以下操作：

- **绑定管理**：通过[attach](arkts-ime-inputmethod-inputmethodcontroller-i.md#attach-1)建立与输入法的绑定，通过[detach](arkts-ime-inputmethod-inputmethodcontroller-i.md#detach-1)解除绑定。attach和detach必须配对使用。  
- **键盘控制**：通过[showTextInput](arkts-ime-inputmethod-inputmethodcontroller-i.md#showtextinput-1)拉起软键盘进入编辑状态，通过[hideTextInput](arkts-ime-inputmethod-inputmethodcontroller-i.md#hidetextinput-1)隐藏软键盘退出编辑状态。showTextInput和hideTextInput必须配对使用。  
- **编辑框状态同步**：通过[updateCursor](arkts-ime-inputmethod-inputmethodcontroller-i.md#updatecursor-1)、[changeSelection](arkts-ime-inputmethod-inputmethodcontroller-i.md#changeselection-1)、[updateAttribute](arkts-ime-inputmethod-inputmethodcontroller-i.md#updateattribute-1)等接口向输入法同步光标、选区、属性等编辑框状态信息。  
- **事件订阅**：通过on('insertText')、on('deleteLeft')等接口订阅输入法应用发送的文本操作事件。

典型调用序列：`getController()` → `attach()` → `showTextInput()`/`hideTextInput()` → `detach()`

> **注意：**  
>  
> attach和detach必须配对使用，showTextInput和hideTextInput必须配对使用，否则可能导致资源泄漏或状态不一致。

**起始版本：** 6

<!--Device-inputMethod-interface InputMethodController--><!--Device-inputMethod-interface InputMethodController-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

<a id="hidesoftkeyboard"></a>
## hideSoftKeyboard

```TypeScript
hideSoftKeyboard(displayId: number): Promise<void>
```

隐藏指定屏幕上的输入法软键盘。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.CONNECT_IME_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputMethodController-hideSoftKeyboard(displayId: long): Promise<void>--><!--Device-InputMethodController-hideSoftKeyboard(displayId: long): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | number | 是 | 屏幕ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permissions check fails. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayId: number = 30;
inputMethod.getController().hideSoftKeyboard(displayId).then(() => {
  console.info('Succeeded in hiding softKeyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide softKeyboard, code: ${err.code}, message: ${err.message}`);
});

```

<a id="showsoftkeyboard"></a>
## showSoftKeyboard

```TypeScript
showSoftKeyboard(displayId: number): Promise<void>
```

在指定屏幕上显示输入法软键盘。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.CONNECT_IME_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputMethodController-showSoftKeyboard(displayId: long): Promise<void>--><!--Device-InputMethodController-showSoftKeyboard(displayId: long): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | number | 是 | 屏幕ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permissions check fails. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayId: number = 20;
inputMethod.getController().showSoftKeyboard(displayId).then(() => {
  console.info('Succeeded in showing softKeyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show softKeyboard, code: ${err.code}, message: ${err.message}`);
});

```

