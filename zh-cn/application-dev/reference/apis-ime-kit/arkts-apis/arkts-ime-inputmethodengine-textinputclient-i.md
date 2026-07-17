# TextInputClient

下列API示例中都需使用[on('inputStart')](arkts-ime-inputmethodengine-inputmethodengine-i.md#on-1)回调获取到TextInputClient实例，再通过此实例调用对应方法。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [InputClient](arkts-ime-inputmethodengine-inputclient-i.md)

<!--Device-inputMethodEngine-interface TextInputClient--><!--Device-inputMethodEngine-interface TextInputClient-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## deleteBackward

```TypeScript
deleteBackward(length: number, callback: AsyncCallback<boolean>): void
```

删除光标后固定长度的文本。使用callback异步回调。

**使用场景：** 实现删除键功能、删除光标后的字符、快速修正输入、实现自定义删除逻辑等。

**使用后效果：** 成功时返回true，编辑框中光标后指定长度的文本被删除。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deleteBackward(length:

<!--Device-TextInputClient-deleteBackward(length: number, callback: AsyncCallback<boolean>): void--><!--Device-TextInputClient-deleteBackward(length: number, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 回调函数。当光标后固定长度的文本删除成功，err为undefined，data为true；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
textInputClient.deleteBackward(length, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to deleteBackward. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in deleting backward.');
  } else {
    console.error('Failed to deleteBackward.');
  }
});

```

## deleteBackward

```TypeScript
deleteBackward(length: number): Promise<boolean>
```

删除光标后固定长度的文本。使用promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deleteBackward(length:

<!--Device-TextInputClient-deleteBackward(length: number): Promise<boolean>--><!--Device-TextInputClient-deleteBackward(length: number): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象。返回true表示删除光标后固定长度的文本成功；返回false表示删除光标后固定长度的文本失败。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
textInputClient.deleteBackward(length).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in deleting backward.');
  } else {
    console.error('Failed to deleteBackward.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to deleteBackward. Code is ${err.code}, message is ${err.message}`);
});

```

## deleteForward

```TypeScript
deleteForward(length: number, callback: AsyncCallback<boolean>): void
```

删除光标前固定长度的文本。使用callback异步回调。

**使用场景：** 实现退格键功能、逐字删除输入、删除错误的输入、实现自定义删除逻辑等。

**使用后效果：** 成功时返回true，编辑框中光标前指定长度的文本被删除。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deleteForward(length:

<!--Device-TextInputClient-deleteForward(length: number, callback: AsyncCallback<boolean>): void--><!--Device-TextInputClient-deleteForward(length: number, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 回调函数。当光标前固定长度的文本删除成功，err为undefined，data为true；当光标前固定长度的文本删除失败，err为undefined，data为false；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
textInputClient.deleteForward(length, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to deleteForward. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in deleting forward.');
  } else {
    console.error('Failed to deleteForward.');
  }
});

```

## deleteForward

```TypeScript
deleteForward(length: number): Promise<boolean>
```

删除光标前固定长度的文本。使用promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deleteForward(length:

<!--Device-TextInputClient-deleteForward(length: number): Promise<boolean>--><!--Device-TextInputClient-deleteForward(length: number): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象。resolve返回true表示删除光标前固定长度的文本成功；resolve返回false表示删除光标前固定长度的文本失败；reject时抛出错误对象，表示执行过程中发生错误。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
textInputClient.deleteForward(length).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in deleting forward.');
  } else {
    console.error('Failed to delete forward.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to deleteForward. Code is ${err.code}, message is ${err.message}`);
});

```

## getBackward

```TypeScript
getBackward(length: number, callback: AsyncCallback<string>): void
```

获取光标后固定长度的文本。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getBackward(length:

<!--Device-TextInputClient-getBackward(length: number, callback: AsyncCallback<string>): void--><!--Device-TextInputClient-getBackward(length: number, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<string> | 是 | 回调函数。当光标后固定长度的文本获取成功，err为undefined，data为获取到的文本；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
textInputClient.getBackward(length, (err: BusinessError, text: string) => {
  if (err) {
    console.error(`Failed to getBackward. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in getting backward, text: ' + text);
});

```

## getBackward

```TypeScript
getBackward(length: number): Promise<string>
```

获取光标后固定长度的文本。使用promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getBackward(length:

<!--Device-TextInputClient-getBackward(length: number): Promise<string>--><!--Device-TextInputClient-getBackward(length: number): Promise<string>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<string> | Promise对象，返回光标后固定长度的文本。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
textInputClient.getBackward(length).then((text: string) => {
  console.info(`'Succeeded in getting backward: ${text}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getBackward. Code is ${err.code}, message is ${err.message}`);
});

```

## getEditorAttribute

```TypeScript
getEditorAttribute(callback: AsyncCallback<EditorAttribute>): void
```

获取编辑框属性值。使用callback异步回调。

**使用场景：** 根据编辑框类型调整输入法界面、根据编辑框配置提供不同的输入建议、实现特定输入逻辑、适配不同类型的输入框等。

**使用后效果：** 返回编辑框属性信息（包括inputPattern输入类型和enterKeyType回车键类型），输入法应用据此调整键盘布局。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEditorAttribute(callback:

<!--Device-TextInputClient-getEditorAttribute(callback: AsyncCallback<EditorAttribute>): void--><!--Device-TextInputClient-getEditorAttribute(callback: AsyncCallback<EditorAttribute>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<EditorAttribute> | 是 | 回调函数。当编辑框的属性值获取成功，err为undefined，data为编辑框属性值；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';


textInputClient.getEditorAttribute((err: BusinessError,
  editorAttribute: inputMethodEngine.EditorAttribute) => {
  if (err) {
    console.error(`Failed to getEditorAttribute. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`editorAttribute.inputPattern: ${editorAttribute.inputPattern}`);
  console.info(`editorAttribute.enterKeyType: ${editorAttribute.enterKeyType}`);
});

```

## getEditorAttribute

```TypeScript
getEditorAttribute(): Promise<EditorAttribute>
```

获取编辑框属性值。使用promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEditorAttribute(callback:

<!--Device-TextInputClient-getEditorAttribute(): Promise<EditorAttribute>--><!--Device-TextInputClient-getEditorAttribute(): Promise<EditorAttribute>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<EditorAttribute> | Promise对象，返回编辑框属性值。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

textInputClient.getEditorAttribute().then((editorAttribute: inputMethodEngine.EditorAttribute) => {
  console.info(`editorAttribute.inputPattern: ${editorAttribute.inputPattern}`);
  console.info(`editorAttribute.enterKeyType: ${editorAttribute.enterKeyType}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getEditorAttribute. Code is ${err.code}, message is ${err.message}`);
});

```

## getForward

```TypeScript
getForward(length: number, callback: AsyncCallback<string>): void
```

获取光标前固定长度的文本。使用callback异步回调。

**使用场景：** 分析已输入文本内容以提供智能补全建议、检查文本格式、实现文本预测功能、实现文本语义分析等。

**使用后效果：** 成功时返回光标前指定长度的文本字符串，输入法应用可据此更新候选词或输入建议。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getForward(length:

<!--Device-TextInputClient-getForward(length: number, callback: AsyncCallback<string>): void--><!--Device-TextInputClient-getForward(length: number, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<string> | 是 | 回调函数。当光标前固定长度的文本获取成功，err为undefined，data为获取到的文本；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
textInputClient.getForward(length, (err: BusinessError, text: string) => {
  if (err) {
    console.error(`Failed to getForward. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in getting forward, text: ' + text);
});

```

## getForward

```TypeScript
getForward(length: number): Promise<string>
```

获取光标前固定长度的文本。使用promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getForward(length:

<!--Device-TextInputClient-getForward(length: number): Promise<string>--><!--Device-TextInputClient-getForward(length: number): Promise<string>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | number | 是 | 文本长度。不能小于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<string> | Promise对象，返回光标前固定长度的文本。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let length: number = 1;
textInputClient.getForward(length).then((text: string) => {
  console.info('Succeeded in getting forward, text: ' + text);
}).catch((err: BusinessError) => {
  console.error(`Failed to getForward. Code is ${err.code}, message is ${err.message}`);
});

```

## insertText

```TypeScript
insertText(text: string, callback: AsyncCallback<boolean>): void
```

插入文本。使用callback异步回调。

**使用场景：** 插入候选词、插入特殊符号、实现文本自动补全、快速插入常用短语等。

**使用后效果：** 成功时返回true，文本已插入到编辑框光标位置。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** insertText(text:

<!--Device-TextInputClient-insertText(text: string, callback: AsyncCallback<boolean>): void--><!--Device-TextInputClient-insertText(text: string, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 文本。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 回调函数。当文本插入成功，err为undefined，data为true；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

textInputClient.insertText('test', (err: BusinessError, result: boolean) => {
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

## insertText

```TypeScript
insertText(text: string): Promise<boolean>
```

插入文本。使用promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** insertText(text:

<!--Device-TextInputClient-insertText(text: string): Promise<boolean>--><!--Device-TextInputClient-insertText(text: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 文本。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象。返回true表示插入文本成功；返回false表示插入文本失败。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

textInputClient.insertText('test').then((result: boolean) => {
  if (result) {
    console.info('Succeeded in inserting text.');
  } else {
    console.error('Failed to insertText.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to insertText. Code is ${err.code}, message is ${err.message}`);
});

```

## sendKeyFunction

```TypeScript
sendKeyFunction(action: number, callback: AsyncCallback<boolean>): void
```

发送功能键。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** sendKeyFunction(action:

<!--Device-TextInputClient-sendKeyFunction(action: number, callback: AsyncCallback<boolean>): void--><!--Device-TextInputClient-sendKeyFunction(action: number, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| action | number | 是 | 功能键键值。<br/>- 当值为0时，表示无效按键；<br/>- 当值为1时，表示确认键（即回车键）。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 回调函数。当功能键发送成功，err为undefined，data为true；当功能键发送失败，err为undefined，data为false；否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let action: number = 1;
textInputClient.sendKeyFunction(action, (err: BusinessError, result: boolean) => {
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

## sendKeyFunction

```TypeScript
sendKeyFunction(action: number): Promise<boolean>
```

发送功能键。使用promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** sendKeyFunction(action:

<!--Device-TextInputClient-sendKeyFunction(action: number): Promise<boolean>--><!--Device-TextInputClient-sendKeyFunction(action: number): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| action | number | 是 | 功能键键值。<br/>当值为0时，表示无效按键；<br/>当值为1时，表示确认键（即回车键）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象。返回true表示发送功能键成功；返回false表示发送功能键失败。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let action: number = 1;
textInputClient.sendKeyFunction(action).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in sending key function.');
  } else {
    console.error('Failed to sendKeyFunction.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to sendKeyFunction:. Code is ${err.code}, message is ${err.message}`);
});

```

