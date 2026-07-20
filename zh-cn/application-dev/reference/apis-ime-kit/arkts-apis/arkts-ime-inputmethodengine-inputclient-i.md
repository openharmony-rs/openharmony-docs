# InputClient

InputClient是输入法客户端对象，代表当前绑定到输入法应用的编辑框客户端。InputClient实例通过InputMethodAbility的[on('inputStart')](inputMethodEngine.InputMethodAbility.on(type: 'inputStart', callback: (kbController: KeyboardController, inputClient: InputClient) => void))事件回调获取，每个绑定事件对应一个InputClient实例，输入法应用通过该实例与编辑框进行文本交互。**核心功能概述：**

- **文本获取**：通过[getForward](arkts-ime-inputmethodengine-inputclient-i.md#getforward-1)/[getForwardSync](arkts-ime-inputmethodengine-inputclient-i.md#getforwardsync-1)获取光标前的文本，通过[getBackward](arkts-ime-inputmethodengine-inputclient-i.md#getbackward-1)/[getBackwardSync](arkts-ime-inputmethodengine-inputclient-i.md#getbackwardsync-1)获取光标后的文本，用于分析已输入内容并提供智能补全。  
- **文本编辑**：通过[insertText](arkts-ime-inputmethodengine-inputclient-i.md#inserttext-1)/[insertTextSync](arkts-ime-inputmethodengine-inputclient-i.md#inserttextsync-1)插入文本，通过[deleteForward](arkts-ime-inputmethodengine-inputclient-i.md#deleteforward-1)/[deleteForwardSync](arkts-ime-inputmethodengine-inputclient-i.md#deleteforwardsync-1)删除光标前的文本，通过[deleteBackward](arkts-ime-inputmethodengine-inputclient-i.md#deletebackward-1)/[deleteBackwardSync](arkts-ime-inputmethodengine-inputclient-i.md#deletebackwardsync-1)删除光标后的文本。  
- **功能键与光标**：通过[sendKeyFunction](arkts-ime-inputmethodengine-inputclient-i.md#sendkeyfunction-1)发送功能键（如回车键），通过[moveCursor](arkts-ime-inputmethodengine-inputclient-i.md#movecursor-1)/[moveCursorSync](arkts-ime-inputmethodengine-inputclient-i.md#movecursorsync-1)移动光标。  
- **选区操作**：通过[selectByRange](arkts-ime-inputmethodengine-inputclient-i.md#selectbyrange-1)/[selectByRangeSync](arkts-ime-inputmethodengine-inputclient-i.md#selectbyrangesync-1)按范围选中文本，通过[selectByMovement](arkts-ime-inputmethodengine-inputclient-i.md#selectbymovement-1)/[selectByMovementSync](arkts-ime-inputmethodengine-inputclient-i.md#selectbymovementsync-1)按方向选中文本。  
- **编辑框属性**：通过[getEditorAttribute](arkts-ime-inputmethodengine-inputclient-i.md#geteditorattribute-1)/[getEditorAttributeSync](arkts-ime-inputmethodengine-inputclient-i.md#geteditorattributesync-1)获取编辑框属性信息（输入类型、回车键类型等），据此调整键盘布局。  
- **文本预览**：通过[setPreviewText](arkts-ime-inputmethodengine-inputclient-i.md#setpreviewtext-1)/[setPreviewTextSync](arkts-ime-inputmethodengine-inputclient-i.md#setpreviewtextsync-1)设置预览文本，通过[finishTextPreview](arkts-ime-inputmethodengine-inputclient-i.md#finishtextpreview-1)/[finishTextPreviewSync](arkts-ime-inputmethodengine-inputclient-i.md#finishtextpreviewsync-1)结束文本预览。  
- **私有通信**：通过[sendPrivateCommand](arkts-ime-inputmethodengine-inputclient-i.md#sendprivatecommand-1)向应用发送私有命令，通过[sendMessage](arkts-ime-inputmethodengine-inputclient-i.md#sendmessage-1)/[recvMessage](arkts-ime-inputmethodengine-inputclient-i.md#recvmessage-1)进行消息通信。

下列API均需使用[on('inputStart')](inputMethodEngine.InputMethodAbility.on(type: 'inputStart', callback: (kbController: KeyboardController, inputClient: InputClient) => void))获取到InputClient实例后，通过实例调用。

**起始版本：** 9

<!--Device-inputMethodEngine-interface InputClient--><!--Device-inputMethodEngine-interface InputClient-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

<a id="deletebackward"></a>
## deleteBackward

```TypeScript
deleteBackward(length: number, callback: AsyncCallback<boolean>): void
```

删除光标后固定长度的文本。使用callback异步回调。

**使用场景：** 实现删除键功能、删除光标后的字符、快速修正输入、实现自定义删除逻辑等。

**使用后效果：** 成功时返回true，编辑框中光标后指定长度的文本被删除。

**起始版本：** 9

<!--Device-InputClient-deleteBackward(length: int, callback: AsyncCallback<boolean>): void--><!--Device-InputClient-deleteBackward(length: int, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。当光标后固定长度的文本删除成功，err为undefined，data为true；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800002](../errorcode-inputmethod-framework.md#12800002-输入法应用异常) | input method engine error. Possible causes:1.input method panel not created. 2.the input method application does not subscribe to related events. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
inputClient.deleteBackward(length, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to deleteBackward. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in deleting backward.');
  } else {
    console.error(`Failed to deleteBackward.`);
  }
});

```

<a id="deletebackward-1"></a>
## deleteBackward

```TypeScript
deleteBackward(length: number): Promise<boolean>
```

删除光标后固定长度的文本。使用promise异步回调。

**起始版本：** 9

<!--Device-InputClient-deleteBackward(length: int): Promise<boolean>--><!--Device-InputClient-deleteBackward(length: int): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。resolve返回true表示删除光标后固定长度的文本成功；resolve返回false表示删除光标后固定长度的文本失败；reject时抛出错误对象，表示执行过程中发生错误。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800002](../errorcode-inputmethod-framework.md#12800002-输入法应用异常) | input method engine error. Possible causes:1.input method panel not created. 2.the input method application does not subscribe to related events. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
inputClient.deleteBackward(length).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in deleting backward.');
  } else {
    console.error('Failed to deleteBackward.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to deleteBackward. Code is ${err.code}, message is ${err.message}`);
});

```

<a id="deletebackwardsync"></a>
## deleteBackwardSync

```TypeScript
deleteBackwardSync(length: number): void
```

删除光标后固定长度的文本。

**起始版本：** 10

<!--Device-InputClient-deleteBackwardSync(length: int): void--><!--Device-InputClient-deleteBackwardSync(length: int): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800002](../errorcode-inputmethod-framework.md#12800002-输入法应用异常) | input method engine error. Possible causes:1.input method panel not created. 2.the input method application does not subscribe to related events. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
let length: number = 1;
inputClient.deleteBackwardSync(length);

```

<a id="deleteforward"></a>
## deleteForward

```TypeScript
deleteForward(length: number, callback: AsyncCallback<boolean>): void
```

删除光标前固定长度的文本。使用callback异步回调。

**使用场景：** 实现退格键功能、逐字删除输入、删除错误的输入、实现自定义删除逻辑等。

**使用后效果：** 成功时返回true，编辑框中光标前指定长度的文本被删除。

**起始版本：** 9

<!--Device-InputClient-deleteForward(length: int, callback: AsyncCallback<boolean>): void--><!--Device-InputClient-deleteForward(length: int, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。当光标前固定长度的文本删除成功，err为undefined，data为true；当光标前固定长度的文本删除失败，err为undefined，data为false；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800002](../errorcode-inputmethod-framework.md#12800002-输入法应用异常) | input method engine error. Possible causes:1.input method panel not created. 2.the input method application does not subscribe to related events. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
inputClient.deleteForward(length, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to deleteForward. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in deleting forward.');
  } else {
    console.error(`Failed to deleteForward.`);
  }
});

```

<a id="deleteforward-1"></a>
## deleteForward

```TypeScript
deleteForward(length: number): Promise<boolean>
```

删除光标前固定长度的文本。使用promise异步回调。

**起始版本：** 9

<!--Device-InputClient-deleteForward(length: int): Promise<boolean>--><!--Device-InputClient-deleteForward(length: int): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。resolve返回true表示删除光标前固定长度的文本成功；resolve返回false表示删除光标前固定长度的文本失败；reject时抛出错误对象，表示执行过程中发生错误。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800002](../errorcode-inputmethod-framework.md#12800002-输入法应用异常) | input method engine error. Possible causes:1.input method panel not created. 2.the input method application does not subscribe to related events. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
inputClient.deleteForward(length).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in deleting forward.');
  } else {
    console.error('Failed to delete Forward.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to deleteForward. Code is ${err.code}, message is ${err.message}`);
});

```

<a id="deleteforwardsync"></a>
## deleteForwardSync

```TypeScript
deleteForwardSync(length: number): void
```

删除光标前固定长度的文本。

**起始版本：** 10

<!--Device-InputClient-deleteForwardSync(length: int): void--><!--Device-InputClient-deleteForwardSync(length: int): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800002](../errorcode-inputmethod-framework.md#12800002-输入法应用异常) | input method engine error. Possible causes:1.input method panel not created. 2.the input method application does not subscribe to related events. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
let length: number = 1;
inputClient.deleteForwardSync(length);

```

<a id="finishtextpreview"></a>
## finishTextPreview

```TypeScript
finishTextPreview(): Promise<void>
```

结束预上屏。使用promise异步回调。

**起始版本：** 12

<!--Device-InputClient-finishTextPreview(): Promise<void>--><!--Device-InputClient-finishTextPreview(): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800011](../errorcode-inputmethod-framework.md#12800011-当前输入框不支持预上屏) | text preview not supported. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.finishTextPreview().then(() => {
  console.info('Succeeded in finishing text preview.');
}).catch((err: BusinessError) => {
  console.error(`Failed to finishTextPreview. Code is ${err.code}, message is ${err.message}`);
});

```

<a id="finishtextpreviewsync"></a>
## finishTextPreviewSync

```TypeScript
finishTextPreviewSync(): void
```

结束预上屏。

**起始版本：** 12

<!--Device-InputClient-finishTextPreviewSync(): void--><!--Device-InputClient-finishTextPreviewSync(): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800011](../errorcode-inputmethod-framework.md#12800011-当前输入框不支持预上屏) | text preview not supported. |

**示例：**

```TypeScript
inputClient.finishTextPreviewSync();

```

<a id="getattachoptions"></a>
## getAttachOptions

```TypeScript
getAttachOptions(): AttachOptions
```

获取绑定输入法时的附加选项。

**起始版本：** 19

<!--Device-InputClient-getAttachOptions(): AttachOptions--><!--Device-InputClient-getAttachOptions(): AttachOptions-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AttachOptions](arkts-ime-inputmethod-attachoptions-i.md) | 返回绑定输入法时的附加选项内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 19+ |

**示例：**

```TypeScript
let attachOptions: inputMethodEngine.AttachOptions = inputClient.getAttachOptions();
console.info(`Succeeded in getting AttachOptions, AttachOptions is ${attachOptions}`);

```

<a id="getbackward"></a>
## getBackward

```TypeScript
getBackward(length: number, callback: AsyncCallback<string>): void
```

获取光标后固定长度的文本。使用callback异步回调。

**起始版本：** 9

<!--Device-InputClient-getBackward(length: int, callback: AsyncCallback<string>): void--><!--Device-InputClient-getBackward(length: int, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。当光标后固定长度的文本获取成功，err为undefined，data为获取到的文本；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800006](../errorcode-inputmethod-framework.md#12800006-输入法控制器异常) | input method controller error. Possible cause:create InputMethodController object failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
inputClient.getBackward(length, (err: BusinessError, text: string) => {
  if (err) {
    console.error(`Failed to getBackward. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in getting backward, text: ' + text);
});

```

<a id="getbackward-1"></a>
## getBackward

```TypeScript
getBackward(length: number): Promise<string>
```

获取光标后固定长度的文本。使用promise异步回调。

**起始版本：** 9

<!--Device-InputClient-getBackward(length: int): Promise<string>--><!--Device-InputClient-getBackward(length: int): Promise<string>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回光标后固定长度的文本。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800006](../errorcode-inputmethod-framework.md#12800006-输入法控制器异常) | input method controller error. Possible cause:create InputMethodController object failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
inputClient.getBackward(length).then((text: string) => {
  console.info('Succeeded in getting backward, text: ' + text);
}).catch((err: BusinessError) => {
  console.error(`Failed to getBackward. Code is ${err.code}, message is ${err.message}`);
});

```

<a id="getbackwardsync"></a>
## getBackwardSync

```TypeScript
getBackwardSync(length: number): string
```

获取光标后固定长度的文本。

**起始版本：** 10

<!--Device-InputClient-getBackwardSync(length: int): string--><!--Device-InputClient-getBackwardSync(length: int): string-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回光标后固定长度的文本。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800006](../errorcode-inputmethod-framework.md#12800006-输入法控制器异常) | input method controller error. Possible cause:create InputMethodController object failed. |

**示例：**

```TypeScript
let length: number = 1;
let text: string = inputClient.getBackwardSync(length);
console.info(`Succeeded in getting backward, text: ${text}`);

```

<a id="getcallingwindowinfo"></a>
## getCallingWindowInfo

```TypeScript
getCallingWindowInfo(): Promise<WindowInfo>
```

获取当前拉起输入法的输入框所在应用窗口信息。使用promise异步回调。

**起始版本：** 12

<!--Device-InputClient-getCallingWindowInfo(): Promise<WindowInfo>--><!--Device-InputClient-getCallingWindowInfo(): Promise<WindowInfo>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;WindowInfo&gt; | Promise对象，返回拉起输入法的输入框所在应用窗口信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800012](../errorcode-inputmethod-framework.md#12800012-软键盘类型面板未创建) | the input method panel does not exist. |
| [12800013](../errorcode-inputmethod-framework.md#12800013-窗口管理服务错误) | window manager service error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.getCallingWindowInfo().then((windowInfo: inputMethodEngine.WindowInfo) => {
  console.info(`windowInfo.rect: ${windowInfo.rect.left}, ${windowInfo.rect.top}, ${windowInfo.rect.width}, ${windowInfo.rect.height}`);
  console.info(`windowInfo.status: ${windowInfo.status}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getCallingWindowInfo. Code is ${err.code}, message is ${err.message}`);
});

```

<a id="geteditorattribute"></a>
## getEditorAttribute

```TypeScript
getEditorAttribute(callback: AsyncCallback<EditorAttribute>): void
```

获取编辑框属性值。使用callback异步回调。

**使用场景：** 根据编辑框类型调整输入法界面、根据编辑框配置提供不同的输入建议、实现特定输入逻辑、适配不同类型的输入框等。

**使用后效果：** 返回编辑框属性信息（包括inputPattern输入类型和enterKeyType回车键类型），输入法应用据此调整键盘布局。

**起始版本：** 9

<!--Device-InputClient-getEditorAttribute(callback: AsyncCallback<EditorAttribute>): void--><!--Device-InputClient-getEditorAttribute(callback: AsyncCallback<EditorAttribute>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;EditorAttribute&gt; | 是 | 回调函数。当编辑框属性值获取成功，err为undefined，data为编辑框属性值；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

<a id="geteditorattribute-1"></a>
## getEditorAttribute

```TypeScript
getEditorAttribute(): Promise<EditorAttribute>
```

获取编辑框属性值。使用promise异步回调。

**起始版本：** 9

<!--Device-InputClient-getEditorAttribute(): Promise<EditorAttribute>--><!--Device-InputClient-getEditorAttribute(): Promise<EditorAttribute>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;EditorAttribute&gt; | Promise对象，返回编辑框属性值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.getEditorAttribute().then((editorAttribute: inputMethodEngine.EditorAttribute) => {
  console.info(`editorAttribute.inputPattern:  ${editorAttribute.inputPattern}`);
  console.info(`editorAttribute.enterKeyType:  ${editorAttribute.enterKeyType}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getEditorAttribute. Code is ${err.code}, message is ${err.message}`);
});

```

<a id="geteditorattributesync"></a>
## getEditorAttributeSync

```TypeScript
getEditorAttributeSync(): EditorAttribute
```

获取编辑框属性值。

**起始版本：** 10

<!--Device-InputClient-getEditorAttributeSync(): EditorAttribute--><!--Device-InputClient-getEditorAttributeSync(): EditorAttribute-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EditorAttribute](arkts-ime-inputmethodengine-editorattribute-i.md) | 编辑框属性对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
let editorAttribute: inputMethodEngine.EditorAttribute = inputClient.getEditorAttributeSync();
console.info(`editorAttribute.inputPattern:  ${editorAttribute.inputPattern}`);
console.info(`editorAttribute.enterKeyType:  ${editorAttribute.enterKeyType}`);

```

<a id="getforward"></a>
## getForward

```TypeScript
getForward(length: number, callback: AsyncCallback<string>): void
```

获取光标前固定长度的文本。使用callback异步回调。**使用场景：** 分析已输入文本内容以提供智能补全建议、检查文本格式、实现文本预测功能、实现文本语义分析等。**使用后效果：** 成功时返回光标前指定长度的文本字符串，输入法应用可据此更新候选词或输入建议。

**起始版本：** 9

<!--Device-InputClient-getForward(length: int, callback: AsyncCallback<string>): void--><!--Device-InputClient-getForward(length: int, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。当光标前固定长度的文本获取成功，err为undefined，data为获取到的文本；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800006](../errorcode-inputmethod-framework.md#12800006-输入法控制器异常) | input method controller error. Possible cause:create InputMethodController object failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
inputClient.getForward(length, (err: BusinessError, text: string) => {
  if (err) {
    console.error(`Failed to getForward. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in getting forward, text: ' + text);
});

```

<a id="getforward-1"></a>
## getForward

```TypeScript
getForward(length: number): Promise<string>
```

获取光标前固定长度的文本。使用promise异步回调。

**起始版本：** 9

<!--Device-InputClient-getForward(length: int): Promise<string>--><!--Device-InputClient-getForward(length: int): Promise<string>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回光标前固定长度的文本。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800006](../errorcode-inputmethod-framework.md#12800006-输入法控制器异常) | input method controller error. Possible cause:create InputMethodController object failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
inputClient.getForward(length).then((text: string) => {
  console.info('Succeeded in getting forward, text: ' + text);
}).catch((err: BusinessError) => {
  console.error(`Failed to getForward. Code is ${err.code}, message is ${err.message}`);
});

```

<a id="getforwardsync"></a>
## getForwardSync

```TypeScript
getForwardSync(length: number): string
```

获取光标前固定长度的文本。

**起始版本：** 10

<!--Device-InputClient-getForwardSync(length: int): string--><!--Device-InputClient-getForwardSync(length: int): string-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回光标前固定长度的文本。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800006](../errorcode-inputmethod-framework.md#12800006-输入法控制器异常) | input method controller error. Possible cause:create InputMethodController object failed. |

**示例：**

```TypeScript
let length: number = 1;
let text: string = inputClient.getForwardSync(length);
console.info(`Succeeded in getting forward, text: ${text}`);

```

<a id="gettextindexatcursor"></a>
## getTextIndexAtCursor

```TypeScript
getTextIndexAtCursor(callback: AsyncCallback<number>): void
```

获取光标所在处的文本索引。使用callback异步回调。

**起始版本：** 10

<!--Device-InputClient-getTextIndexAtCursor(callback: AsyncCallback<int>): void--><!--Device-InputClient-getTextIndexAtCursor(callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当文本索引获取成功，err为undefined，index为光标所在处的文本索引；否则err为错误对象，index为undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800006](../errorcode-inputmethod-framework.md#12800006-输入法控制器异常) | input method controller error. Possible cause:create InputMethodController object failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.getTextIndexAtCursor((err: BusinessError, index: number) => {
  if (err) {
    console.error(`Failed to getTextIndexAtCursor. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in getTextIndexAtCursor: ' + index);
});

```

<a id="gettextindexatcursor-1"></a>
## getTextIndexAtCursor

```TypeScript
getTextIndexAtCursor(): Promise<number>
```

获取光标所在处的文本索引。使用promise异步回调。

**起始版本：** 10

<!--Device-InputClient-getTextIndexAtCursor(): Promise<int>--><!--Device-InputClient-getTextIndexAtCursor(): Promise<int>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回光标所在处的文本索引。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800006](../errorcode-inputmethod-framework.md#12800006-输入法控制器异常) | input method controller error. Possible cause:create InputMethodController object failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.getTextIndexAtCursor().then((index: number) => {
  console.info('Succeeded in getTextIndexAtCursor: ' + index);
}).catch((err: BusinessError) => {
  console.error(`Failed to getTextIndexAtCursor. Code is ${err.code}, message is ${err.message}`);
});

```

<a id="gettextindexatcursorsync"></a>
## getTextIndexAtCursorSync

```TypeScript
getTextIndexAtCursorSync(): number
```

获取光标所在处的文本索引。

**起始版本：** 10

<!--Device-InputClient-getTextIndexAtCursorSync(): int--><!--Device-InputClient-getTextIndexAtCursorSync(): int-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回光标所在处的文本索引。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800006](../errorcode-inputmethod-framework.md#12800006-输入法控制器异常) | input method controller error. Possible cause:create InputMethodController object failed. |

**示例：**

```TypeScript
let index: number = inputClient.getTextIndexAtCursorSync();
console.info(`Succeeded in getTextIndexAtCursorSync, index: ${index}`);

```

<a id="inserttext"></a>
## insertText

```TypeScript
insertText(text: string, callback: AsyncCallback<boolean>): void
```

插入文本。使用callback异步回调。

**使用场景：** 插入候选词、插入特殊符号、实现文本自动补全、快速插入常用短语等。

**使用后效果：** 成功时返回true，文本已插入到编辑框光标位置。

**起始版本：** 9

<!--Device-InputClient-insertText(text: string, callback: AsyncCallback<boolean>): void--><!--Device-InputClient-insertText(text: string, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 文本内容。建议长度不超过1KB。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。当文本插入成功，err为undefined，data为true；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800002](../errorcode-inputmethod-framework.md#12800002-输入法应用异常) | input method engine error. Possible causes:1.input method panel not created. 2.the input method application does not subscribe to related events. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';


inputClient.insertText('test', (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to insertText. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in inserting text.');
  } else {
    console.error('Failed to insertText.');
  }
});

```

<a id="inserttext-1"></a>
## insertText

```TypeScript
insertText(text: string): Promise<boolean>
```

插入文本。使用promise异步回调。

**起始版本：** 9

<!--Device-InputClient-insertText(text: string): Promise<boolean>--><!--Device-InputClient-insertText(text: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 文本。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。resolve返回true表示插入文本成功；resolve返回false表示插入文本失败；reject时抛出错误对象，表示执行过程中发生错误。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800002](../errorcode-inputmethod-framework.md#12800002-输入法应用异常) | input method engine error. Possible causes:1.input method panel not created. 2.the input method application does not subscribe to related events. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.insertText('test').then((result: boolean) => {
  if (result) {
    console.info('Succeeded in inserting text.');
  } else {
    console.error('Failed to insertText.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to insertText. Code is ${err.code}, message is ${err.message}`);
});

```

<a id="inserttextsync"></a>
## insertTextSync

```TypeScript
insertTextSync(text: string): void
```

插入文本。

**起始版本：** 10

<!--Device-InputClient-insertTextSync(text: string): void--><!--Device-InputClient-insertTextSync(text: string): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 文本内容。建议长度不超过1KB。建议长度不超过1KB。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800002](../errorcode-inputmethod-framework.md#12800002-输入法应用异常) | input method engine error. Possible causes:1.input method panel not created. 2.the input method application does not subscribe to related events. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
inputClient.insertTextSync('test');

```

<a id="movecursor"></a>
## moveCursor

```TypeScript
moveCursor(direction: number, callback: AsyncCallback<void>): void
```

移动光标。使用callback异步回调。

**使用场景：** 实现光标移动到特定位置、实现上下左右移动光标功能、实现快速定位、实现自定义光标控制等。

**使用后效果：** 成功时编辑框中的光标按指定方向移动一步。direction取值参见

**起始版本：** 9

<!--Device-InputClient-moveCursor(direction: int, callback: AsyncCallback<void>): void--><!--Device-InputClient-moveCursor(direction: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| direction | number | 是 | 光标移动方向。<br/>- 当值为1时，表示向上。<br/>- 当值为2时，表示向下。<br/>- 当值为3时，表示向左。<br/>- 当值为4时，表示向右。不能小于0。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当光标移动成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.moveCursor(inputMethodEngine.Direction.CURSOR_UP, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to moveCursor. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in moving cursor.');
});

```

<a id="movecursor-1"></a>
## moveCursor

```TypeScript
moveCursor(direction: number): Promise<void>
```

移动光标。使用promise异步回调。

**起始版本：** 9

<!--Device-InputClient-moveCursor(direction: int): Promise<void>--><!--Device-InputClient-moveCursor(direction: int): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| direction | number | 是 | 光标移动方向。<br/>- 当值为1时，表示向上。<br/>- 当值为2时，表示向下。<br/>- 当值为3时，表示向左。<br/>- 当值为4时，表示向右。不能小于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.moveCursor(inputMethodEngine.Direction.CURSOR_UP).then(() => {
  console.info('Succeeded in moving cursor.');
}).catch((err: BusinessError) => {
  console.error(`Failed to moveCursor. Code is ${err.code}, message is ${err.message}`);
});

```

<a id="movecursorsync"></a>
## moveCursorSync

```TypeScript
moveCursorSync(direction: number): void
```

移动光标。

**起始版本：** 10

<!--Device-InputClient-moveCursorSync(direction: int): void--><!--Device-InputClient-moveCursorSync(direction: int): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| direction | number | 是 | 光标移动方向。<br/>- 当值为1时，表示向上。<br/>- 当值为2时，表示向下。<br/>- 当值为3时，表示向左。<br/>- 当值为4时，表示向右。不能小于0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
inputClient.moveCursorSync(inputMethodEngine.Direction.CURSOR_UP);

```

<a id="off"></a>
## off('attachOptionsDidChange')

```TypeScript
off(type: 'attachOptionsDidChange', callback?: Callback<AttachOptions>): void
```

取消订阅绑定输入法时的附加选项变更事件。使用callback异步回调。

**起始版本：** 19

<!--Device-InputClient-off(type: 'attachOptionsDidChange', callback?: Callback<AttachOptions>): void--><!--Device-InputClient-off(type: 'attachOptionsDidChange', callback?: Callback<AttachOptions>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'attachOptionsDidChange' | 是 | 绑定输入法时的附加选项变更事件，固定取值为'attachOptionsDidChange'。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;AttachOptions&gt; | 否 | 取消订阅的回调函数。参数不填写时，默认取消订阅type对应的所有回调事件。 |

**示例：**

```TypeScript
let attachOptionsDidChangeCallback: (attachOptions: inputMethodEngine.AttachOptions) => void =
  (_attachOptions: inputMethodEngine.AttachOptions) => {
    console.info(`AttachOptionsDidChangeCallback1: attachOptionsDidChange event triggered`);
  };

inputClient.on('attachOptionsDidChange', attachOptionsDidChangeCallback);
console.info(`attachOptionsDidChangeCallback subscribed to attachOptionsDidChange`);
inputClient.off('attachOptionsDidChange', attachOptionsDidChangeCallback);
console.info(`attachOptionsDidChange unsubscribed from attachOptionsDidChange`);

```

<a id="on"></a>
## on('attachOptionsDidChange')

```TypeScript
on(type: 'attachOptionsDidChange', callback: Callback<AttachOptions>): void
```

订阅绑定输入法时的附加选项变更事件。使用callback异步回调。

**起始版本：** 19

<!--Device-InputClient-on(type: 'attachOptionsDidChange', callback: Callback<AttachOptions>): void--><!--Device-InputClient-on(type: 'attachOptionsDidChange', callback: Callback<AttachOptions>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'attachOptionsDidChange' | 是 | 绑定输入法时的附加选项变更事件，固定取值为'attachOptionsDidChange'。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;AttachOptions&gt; | 是 | 回调函数，返回绑定输入法时的附加选项。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.<br>**适用版本：** 19+ |

**示例：**

```TypeScript
// 创建附加选项变更回调函数
let attachOptionsDidChangeCallback: (attachOptions: inputMethodEngine.AttachOptions) => void =
  (_attachOptions: inputMethodEngine.AttachOptions) => {
    console.info(`AttachOptionsDidChangeCallback1: attachOptionsDidChange event triggered`);
  };

// 订阅绑定输入法时的附加选项变更事件
inputClient.on('attachOptionsDidChange', attachOptionsDidChangeCallback);
console.info(`attachOptionsDidChangeCallback subscribed to attachOptionsDidChange`);
// 取消订阅绑定输入法时的附加选项变更事件
inputClient.off('attachOptionsDidChange', attachOptionsDidChangeCallback);
console.info(`attachOptionsDidChange unsubscribed from attachOptionsDidChange`);

```

<a id="recvmessage"></a>
## recvMessage

```TypeScript
recvMessage(msgHandler?: MessageHandler): void
```

注册或取消注册Messagehandler。

**起始版本：** 15

<!--Device-InputClient-recvMessage(msgHandler?: MessageHandler): void--><!--Device-InputClient-recvMessage(msgHandler?: MessageHandler): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| msgHandler | [MessageHandler](arkts-ime-inputmethod-messagehandler-i.md) | 否 | 该对象将通过[onMessage](arkts-ime-inputmethodengine-messagehandler-i.md#onmessage-1)接收来自已绑定当前输入法应用的编辑框应用所发送的自定义通信数据，并通过[onTerminated](arkts-ime-inputmethodengine-messagehandler-i.md#onterminated-1)接收终止此对象订阅的消息。<br>若不填写此参数，则取消全局已注册的[MessageHandler](arkts-ime-inputmethodengine-messagehandler-i.md)对象，同时触发其[onTerminated](arkts-ime-inputmethodengine-messagehandler-i.md#onterminated-1)回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Incorrect parameter types. |

**示例：**

```TypeScript
inputMethodEngine.getInputMethodAbility()
  .on('inputStart',
    (kbController: inputMethodEngine.KeyboardController, client: inputMethodEngine.InputClient) => {
      // 创建消息处理器，用于接收编辑框应用发送的自定义通信数据
      let messageHandler: inputMethodEngine.MessageHandler = {
        onTerminated(): void {
          console.info('OnTerminated.');
        },
        onMessage(msgId: string, msgParam?: ArrayBuffer): void {
          console.info('recv message.');
        }
      }
      // 注册消息处理器
      client.recvMessage(messageHandler);
    });

```

<a id="selectbymovement"></a>
## selectByMovement

```TypeScript
selectByMovement(movement: Movement, callback: AsyncCallback<void>): void
```

根据光标移动方向选中文本。使用callback异步回调。

**起始版本：** 10

<!--Device-InputClient-selectByMovement(movement: Movement, callback: AsyncCallback<void>): void--><!--Device-InputClient-selectByMovement(movement: Movement, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| movement | [Movement](arkts-ime-inputmethod-movement-i.md) | 是 | 选中时光标移动的方向。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当成功发送选中事件后，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 设置选中时光标向上移动
let movement: inputMethodEngine.Movement = { direction: 1 };
inputClient.selectByMovement(movement, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to selectByMovement. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in selecting by movement.');
});

```

<a id="selectbymovement-1"></a>
## selectByMovement

```TypeScript
selectByMovement(movement: Movement): Promise<void>
```

根据光标移动方向选中文本。使用promise异步回调。

**起始版本：** 10

<!--Device-InputClient-selectByMovement(movement: Movement): Promise<void>--><!--Device-InputClient-selectByMovement(movement: Movement): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| movement | [Movement](arkts-ime-inputmethod-movement-i.md) | 是 | 选中时光标移动的方向。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 设置选中时光标向上移动
let movement: inputMethodEngine.Movement = { direction: 1 };
inputClient.selectByMovement(movement).then(() => {
  console.info('Succeeded in selecting by movement.');
}).catch((err: BusinessError) => {
  console.error(`Failed to selectByMovement. Code is ${err.code}, message is ${err.message}`);
});

```

<a id="selectbymovementsync"></a>
## selectByMovementSync

```TypeScript
selectByMovementSync(movement: Movement): void
```

根据光标移动方向选中文本。

**起始版本：** 10

<!--Device-InputClient-selectByMovementSync(movement: Movement): void--><!--Device-InputClient-selectByMovementSync(movement: Movement): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| movement | [Movement](arkts-ime-inputmethod-movement-i.md) | 是 | 选中时光标移动的方向。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
// 设置选中时光标向上移动
let movement: inputMethodEngine.Movement = { direction: 1 };
inputClient.selectByMovementSync(movement);

```

<a id="selectbyrange"></a>
## selectByRange

```TypeScript
selectByRange(range: Range, callback: AsyncCallback<void>): void
```

根据索引范围选中文本。使用callback异步回调。

**起始版本：** 10

<!--Device-InputClient-selectByRange(range: Range, callback: AsyncCallback<void>): void--><!--Device-InputClient-selectByRange(range: Range, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [Range](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-scan-range-i.md) | 是 | 选中文本的范围。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当成功发送选中事件后，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 设置预上屏文本的替换范围为第一个字符
// 设置选中文本的起始和结束位置
let range: inputMethodEngine.Range = { start: 0, end: 1 };
inputClient.selectByRange(range, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to selectByRange. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in selecting by range.');
});

```

<a id="selectbyrange-1"></a>
## selectByRange

```TypeScript
selectByRange(range: Range): Promise<void>
```

根据索引范围选中文本。使用promise异步回调。

**起始版本：** 10

<!--Device-InputClient-selectByRange(range: Range): Promise<void>--><!--Device-InputClient-selectByRange(range: Range): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [Range](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-scan-range-i.md) | 是 | 选中文本的范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 设置预上屏文本的替换范围为第一个字符
// 设置选中文本的起始和结束位置
let range: inputMethodEngine.Range = { start: 0, end: 1 };
inputClient.selectByRange(range).then(() => {
  console.info('Succeeded in selecting by range.');
}).catch((err: BusinessError) => {
  console.error(`Failed to selectByRange. Code is ${err.code}, message is ${err.message}`);
});

```

<a id="selectbyrangesync"></a>
## selectByRangeSync

```TypeScript
selectByRangeSync(range: Range): void
```

根据索引范围选中文本。

**起始版本：** 10

<!--Device-InputClient-selectByRangeSync(range: Range): void--><!--Device-InputClient-selectByRangeSync(range: Range): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| range | [Range](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-scan-range-i.md) | 是 | 选中文本的范围。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
// 设置预上屏文本的替换范围为第一个字符
// 设置选中文本的起始和结束位置
let range: inputMethodEngine.Range = { start: 0, end: 1 };
inputClient.selectByRangeSync(range);

```

<a id="sendextendaction"></a>
## sendExtendAction

```TypeScript
sendExtendAction(action: ExtendAction, callback: AsyncCallback<void>): void
```

发送扩展编辑操作。使用callback异步回调。

**起始版本：** 10

<!--Device-InputClient-sendExtendAction(action: ExtendAction, callback: AsyncCallback<void>): void--><!--Device-InputClient-sendExtendAction(action: ExtendAction, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| action | [ExtendAction](arkts-ime-inputmethodengine-extendaction-e.md) | 是 | 要发送的扩展操作。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。发送成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800006](../errorcode-inputmethod-framework.md#12800006-输入法控制器异常) | input method controller error. Possible cause:create InputMethodController object failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.sendExtendAction(inputMethodEngine.ExtendAction.COPY, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to sendExtendAction. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in sending extend action.');
});

```

<a id="sendextendaction-1"></a>
## sendExtendAction

```TypeScript
sendExtendAction(action: ExtendAction): Promise<void>
```

发送扩展编辑操作。使用promise异步回调。

**起始版本：** 10

<!--Device-InputClient-sendExtendAction(action: ExtendAction): Promise<void>--><!--Device-InputClient-sendExtendAction(action: ExtendAction): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| action | [ExtendAction](arkts-ime-inputmethodengine-extendaction-e.md) | 是 | 要发送的扩展操作。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800006](../errorcode-inputmethod-framework.md#12800006-输入法控制器异常) | input method controller error. Possible cause:create InputMethodController object failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputClient.sendExtendAction(inputMethodEngine.ExtendAction.COPY).then(() => {
  console.info('Succeeded in sending extend action.');
}).catch((err: BusinessError) => {
  console.error(`Failed to sendExtendAction. Code is ${err.code}, message is ${err.message}`);
});

```

<a id="sendkeyfunction"></a>
## sendKeyFunction

```TypeScript
sendKeyFunction(action: number, callback: AsyncCallback<boolean>): void
```

发送功能键。使用callback异步回调。

**起始版本：** 9

<!--Device-InputClient-sendKeyFunction(action: int, callback: AsyncCallback<boolean>): void--><!--Device-InputClient-sendKeyFunction(action: int, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| action | number | 是 | 功能键键值。<br/>- 当值为0时，表示无效按键。<br/>- 当值为1时，表示确认键（即回车键）。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。当功能键发送成功，err为undefined，data为true；当功能键发送失败，err为undefined，data为false；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let action: number = 1;

inputClient.sendKeyFunction(action, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to sendKeyFunction. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in sending key function.');
  } else {
    console.error('Failed to sendKeyFunction.');
  }
});

```

<a id="sendkeyfunction-1"></a>
## sendKeyFunction

```TypeScript
sendKeyFunction(action: number): Promise<boolean>
```

发送功能键。使用promise异步回调。

**起始版本：** 9

<!--Device-InputClient-sendKeyFunction(action: int): Promise<boolean>--><!--Device-InputClient-sendKeyFunction(action: int): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| action | number | 是 | 功能键键值。<br/>当值为0时，表示无效按键；<br/>当值为1时，表示确认键（即回车键）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。resolve返回true表示功能键发送成功；resolve返回false表示功能键发送失败；reject时抛出错误对象，表示执行过程中发生错误。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let action: number = 1;
inputClient.sendKeyFunction(action).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in sending key function.');
  } else {
    console.error('Failed to sendKeyFunction.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to sendKeyFunction. Code is ${err.code}, message is ${err.message}`);
});

```

<a id="sendmessage"></a>
## sendMessage

```TypeScript
sendMessage(msgId: string, msgParam?: ArrayBuffer): Promise<void>
```

发送自定义通信至已绑定当前输入法应用的编辑框应用。使用Promise异步回调。

**起始版本：** 15

<!--Device-InputClient-sendMessage(msgId: string, msgParam?: ArrayBuffer): Promise<void>--><!--Device-InputClient-sendMessage(msgId: string, msgParam?: ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| msgId | string | 是 | 需要发送至已绑定当前输入法应用的编辑框应用的自定义数据的标识符。最大长度256字节。最大长度256字节。 |
| msgParam | ArrayBuffer | 否 | 需要发送至已绑定当前输入法应用的编辑框应用的自定义数据的消息体。 |

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
inputClient.sendMessage(msgId, msgParam).then(() => {
  console.info('Succeeded send message.');
}).catch((err: BusinessError) => {
  console.error(`Failed to send message. Code is ${err.code}, message is ${err.message}`);
});

```

<a id="sendprivatecommand"></a>
## sendPrivateCommand

```TypeScript
sendPrivateCommand(commandData: Record<string, CommandDataType>): Promise<void>
```

发送私有数据至需要与输入法应用通信的系统其他部分。使用promise异步回调。

**起始版本：** 12

<!--Device-InputClient-sendPrivateCommand(commandData: Record<string, CommandDataType>): Promise<void>--><!--Device-InputClient-sendPrivateCommand(commandData: Record<string, CommandDataType>): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| commandData | Record&lt;string, CommandDataType&gt; | 是 | 私有数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800010](../errorcode-inputmethod-framework.md#12800010-不是系统配置的默认输入法) | not the preconfigured default input method. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethodEngine.getInputMethodAbility().on('inputStart', (kbController, textInputClient) => {
  let record: Record<string, inputMethodEngine.CommandDataType> = {
    "valueString1": "abcdefg",
    "valueString2": true,
    "valueString3": 500,
  }
  textInputClient.sendPrivateCommand(record).then(() => {
  }).catch((err: BusinessError) => {
    if (err) {
      console.error(`sendPrivateCommand catch error: ${err.code}, message: ${err.message}`);
    }
  });
})

```

<a id="setpreviewtext"></a>
## setPreviewText

```TypeScript
setPreviewText(text: string, range: Range): Promise<void>
```

设置预上屏文本。使用promise异步回调。

**起始版本：** 12

<!--Device-InputClient-setPreviewText(text: string, range: Range): Promise<void>--><!--Device-InputClient-setPreviewText(text: string, range: Range): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 预上屏的文本。建议长度不超过1KB。 |
| range | [Range](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-scan-range-i.md) | 是 | 替换的文本范围。<br/>- 当值为{ start: -1, end: -1 }时，默认将参数text替换当前预上屏区域全部文本。<br/>- 当start等于end，默认将参数text插入start对应的光标位置。<br/>- 当start不等于end，将参数text替换range对应区域的文本。<br/>- 当start与end为其他含有负数值的组合，按照参数错误返回。<br/>- 当输入框已有预上屏文本，参数range不得超过预上屏文本范围，否则按照参数错误返回。<br/>- 当输入框无预上屏文本，参数range不得超过输入框文本范围，否则按照参数错误返回。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800011](../errorcode-inputmethod-framework.md#12800011-当前输入框不支持预上屏) | text preview not supported. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 设置预上屏文本的替换范围为第一个字符
// 设置选中文本的起始和结束位置
let range: inputMethodEngine.Range = { start: 0, end: 1 };
inputClient.setPreviewText('test', range).then(() => {
  console.info('Succeeded in setting preview text.');
}).catch((err: BusinessError) => {
  console.error(`Failed to setPreviewText. Code is ${err.code}, message is ${err.message}`);
});

```

<a id="setpreviewtextsync"></a>
## setPreviewTextSync

```TypeScript
setPreviewTextSync(text: string, range: Range): void
```

设置预上屏文本。

**起始版本：** 12

<!--Device-InputClient-setPreviewTextSync(text: string, range: Range): void--><!--Device-InputClient-setPreviewTextSync(text: string, range: Range): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 预上屏的文本。建议长度不超过1KB。 |
| range | [Range](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-scan-range-i.md) | 是 | 替换的文本范围。<br/>- 当值为{ start: -1, end: -1 }时，默认将参数text替换当前预上屏区域全部文本。<br/>- 当start等于end，默认将参数text插入start对应的光标位置。<br/>- 当start不等于end，将参数text替换range对应区域的文本。<br/>- 当start与end为其他含有负数值的组合，按照参数错误返回。<br/>- 当输入框已有预上屏文本，参数range不得超过预上屏文本范围，否则按照参数错误返回。<br/>- 当输入框无预上屏文本，参数range不得超过输入框文本范围，否则按照参数错误返回。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |
| [12800011](../errorcode-inputmethod-framework.md#12800011-当前输入框不支持预上屏) | text preview not supported. |

**示例：**

```TypeScript
// 设置预上屏文本的替换范围为第一个字符
// 设置选中文本的起始和结束位置
let range: inputMethodEngine.Range = { start: 0, end: 1 };
inputClient.setPreviewTextSync('test', range);

```

