# InputMethodSetting

InputMethodSetting提供输入法配置与查询能力，面向前台应用提供以下功能：

- **输入法变化订阅**：通过[on('imeChange')](arkts-ime-inputmethod-inputmethodsetting-i.md#on-1)订阅输入法及子类型变化事件，当用户切换输入法时收到通知。  
- **输入法列表查询**：通过[getInputMethods](arkts-ime-inputmethod-inputmethodsetting-i.md#getinputmethods-1)查询已激活/未激活输入法列表，通过[getAllInputMethods](arkts-ime-inputmethod-inputmethodsetting-i.md#getallinputmethods-1)查询所有已安装输入法列表，通过[listInputMethodSubtype](arkts-ime-inputmethod-inputmethodsetting-i.md#listinputmethodsubtype-1)查询指定输入法的子类型列表。  
- **面板可见性查询**：通过isPanelShown查询输入法面板是否显示。  
- **输入法选择对话框**：通过showOptionalInputMethods显示输入法选择对话框（已废弃，建议使用InputMethodListDialog）。

需通过[getSetting](arkts-ime-inputmethod-getsetting-f.md#getsetting-1)获取InputMethodSetting实例后使用。

下列API均需使用[getSetting](arkts-ime-inputmethod-getsetting-f.md#getsetting-1)获取到InputMethodSetting实例后，通过实例调用。

**起始版本：** 8

<!--Device-inputMethod-interface InputMethodSetting--><!--Device-inputMethod-interface InputMethodSetting-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## displayOptionalInputMethod

```TypeScript
displayOptionalInputMethod(callback: AsyncCallback<void>): void
```

显示输入法选择对话框。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** inputMethodList/InputMethodListDialog

<!--Device-InputMethodSetting-displayOptionalInputMethod(callback: AsyncCallback<void>): void--><!--Device-InputMethodSetting-displayOptionalInputMethod(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当输入法选择对话框显示成功。err为undefined，否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().displayOptionalInputMethod((err: BusinessError) => {
  if (err) {
    console.error(`Failed to displayOptionalInputMethod, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in displaying optionalInputMethod.');
});

```

## displayOptionalInputMethod

```TypeScript
displayOptionalInputMethod(): Promise<void>
```

显示输入法选择对话框。使用promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** inputMethodList/InputMethodListDialog

<!--Device-InputMethodSetting-displayOptionalInputMethod(): Promise<void>--><!--Device-InputMethodSetting-displayOptionalInputMethod(): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().displayOptionalInputMethod().then(() => {
  console.info('Succeeded in displaying optionalInputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to displayOptionalInputMethod, code: ${err.code}, message: ${err.message}`);
})

```

## getAllInputMethods

```TypeScript
getAllInputMethods(callback: AsyncCallback<Array<InputMethodProperty>>): void
```

获取所有输入法应用列表。使用callback异步回调。

**起始版本：** 11

<!--Device-InputMethodSetting-getAllInputMethods(callback: AsyncCallback<Array<InputMethodProperty>>): void--><!--Device-InputMethodSetting-getAllInputMethods(callback: AsyncCallback<Array<InputMethodProperty>>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<InputMethodProperty>> | 是 | 回调函数，返回所有输入法列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800001](../errorcode-inputmethod-framework.md#12800001-包管理服务异常) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().getAllInputMethods((err: BusinessError, data: Array<inputMethod.InputMethodProperty>) => {
  if (err) {
    console.error(`Failed to getAllInputMethods, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting all inputMethods.');
});

```

## getAllInputMethods

```TypeScript
getAllInputMethods(): Promise<Array<InputMethodProperty>>
```

获取所有输入法应用列表。使用promise异步回调。

**起始版本：** 11

<!--Device-InputMethodSetting-getAllInputMethods(): Promise<Array<InputMethodProperty>>--><!--Device-InputMethodSetting-getAllInputMethods(): Promise<Array<InputMethodProperty>>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<InputMethodProperty>> | Promise对象，返回所有输入法列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800001](../errorcode-inputmethod-framework.md#12800001-包管理服务异常) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().getAllInputMethods().then((data: Array<inputMethod.InputMethodProperty>) => {
  console.info('Succeeded in getting all inputMethods.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getAllInputMethods, code: ${err.code}, message: ${err.message}`);
})

```

## getAllInputMethodsSync

```TypeScript
getAllInputMethodsSync(): Array<InputMethodProperty>
```

获取所有输入法应用列表。同步接口。

**起始版本：** 11

<!--Device-InputMethodSetting-getAllInputMethodsSync(): Array<InputMethodProperty>--><!--Device-InputMethodSetting-getAllInputMethodsSync(): Array<InputMethodProperty>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<InputMethodProperty> | 返回所有输入法列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800001](../errorcode-inputmethod-framework.md#12800001-包管理服务异常) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
let imeProperty: Array<inputMethod.InputMethodProperty> = inputMethod.getSetting().getAllInputMethodsSync();

```

## getInputMethodState

```TypeScript
getInputMethodState(): Promise<EnabledState>
```

查询输入法的启用状态。使用promise异步回调。

**起始版本：** 15

<!--Device-InputMethodSetting-getInputMethodState(): Promise<EnabledState>--><!--Device-InputMethodSetting-getInputMethodState(): Promise<EnabledState>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<EnabledState> | Promise对象，返回EnabledState.DISABLED表示未启用; 返回EnabledState.BASIC_MODE表示基础模式; 返回EnabledState.FULL_EXPERIENCE_MODE表示完整体验模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800004](../errorcode-inputmethod-framework.md#12800004-不是输入法应用) | not an input method application. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().getInputMethodState().then((status: inputMethod.EnabledState) => {
  console.info(`Succeeded in getInputMethodState, status: ${status}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getInputMethodState, code: ${err.code}, message: ${err.message}`);
});

```

## getInputMethods

```TypeScript
getInputMethods(enable: boolean, callback: AsyncCallback<Array<InputMethodProperty>>): void
```

获取已激活/未激活的输入法应用列表。使用callback异步回调。

**起始版本：** 9

<!--Device-InputMethodSetting-getInputMethods(enable: boolean, callback: AsyncCallback<Array<InputMethodProperty>>): void--><!--Device-InputMethodSetting-getInputMethods(enable: boolean, callback: AsyncCallback<Array<InputMethodProperty>>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | true表示返回已激活输入法列表，false表示返回未激活输入法列表。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<InputMethodProperty>> | 是 | 回调函数，返回已激活/未激活输入法列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800001](../errorcode-inputmethod-framework.md#12800001-包管理服务异常) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().getInputMethods(true, (err: BusinessError, data: Array<inputMethod.InputMethodProperty>) => {
  if (err) {
    console.error(`Failed to getInputMethods, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting inputMethods.');
});

```

## getInputMethods

```TypeScript
getInputMethods(enable: boolean): Promise<Array<InputMethodProperty>>
```

获取已激活/未激活的输入法应用列表。使用promise异步回调。

**起始版本：** 9

<!--Device-InputMethodSetting-getInputMethods(enable: boolean): Promise<Array<InputMethodProperty>>--><!--Device-InputMethodSetting-getInputMethods(enable: boolean): Promise<Array<InputMethodProperty>>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | true表示返回已激活输入法列表，false表示返回未激活输入法列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<InputMethodProperty>> | Promise对象，返回已激活/未激活输入法列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800001](../errorcode-inputmethod-framework.md#12800001-包管理服务异常) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().getInputMethods(true).then((data: Array<inputMethod.InputMethodProperty>) => {
  console.info('Succeeded in getting inputMethods.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getInputMethods, code: ${err.code}, message: ${err.message}`);
})


```

## getInputMethodsSync

```TypeScript
getInputMethodsSync(enable: boolean): Array<InputMethodProperty>
```

获取已激活/未激活的输入法应用列表。同步接口。

**起始版本：** 11

<!--Device-InputMethodSetting-getInputMethodsSync(enable: boolean): Array<InputMethodProperty>--><!--Device-InputMethodSetting-getInputMethodsSync(enable: boolean): Array<InputMethodProperty>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | true表示返回已激活输入法列表，false表示返回未激活输入法列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<InputMethodProperty> | 返回已激活/未激活输入法列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800001](../errorcode-inputmethod-framework.md#12800001-包管理服务异常) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
let imeProperty: Array<inputMethod.InputMethodProperty> = inputMethod.getSetting().getInputMethodsSync(true);

```

## listCurrentInputMethodSubtype

```TypeScript
listCurrentInputMethodSubtype(callback: AsyncCallback<Array<InputMethodSubtype>>): void
```

查询当前输入法应用的所有子类型。使用callback异步回调。

**起始版本：** 9

<!--Device-InputMethodSetting-listCurrentInputMethodSubtype(callback: AsyncCallback<Array<InputMethodSubtype>>): void--><!--Device-InputMethodSetting-listCurrentInputMethodSubtype(callback: AsyncCallback<Array<InputMethodSubtype>>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<InputMethodSubtype>> | 是 | 回调函数，返回当前输入法应用的所有子类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800001](../errorcode-inputmethod-framework.md#12800001-包管理服务异常) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

let inputMethodSetting: inputMethod.InputMethodSetting = inputMethod.getSetting();
inputMethodSetting.listCurrentInputMethodSubtype((err: BusinessError, data: Array<InputMethodSubtype>) => {
  if (err) {
    console.error(`Failed to listCurrentInputMethodSubtype, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in listing currentInputMethodSubtype.');
});

```

## listCurrentInputMethodSubtype

```TypeScript
listCurrentInputMethodSubtype(): Promise<Array<InputMethodSubtype>>
```

查询当前输入法应用的所有子类型。使用promise异步回调。

**起始版本：** 9

<!--Device-InputMethodSetting-listCurrentInputMethodSubtype(): Promise<Array<InputMethodSubtype>>--><!--Device-InputMethodSetting-listCurrentInputMethodSubtype(): Promise<Array<InputMethodSubtype>>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<InputMethodSubtype>> | Promise对象，返回当前输入法应用的所有子类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800001](../errorcode-inputmethod-framework.md#12800001-包管理服务异常) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

let inputMethodSetting: inputMethod.InputMethodSetting = inputMethod.getSetting();

inputMethodSetting.listCurrentInputMethodSubtype().then((data: Array<InputMethodSubtype>) => {
  console.info('Succeeded in listing currentInputMethodSubtype.');
}).catch((err: BusinessError) => {
  console.error(`Failed to listCurrentInputMethodSubtype, code: ${err.code}, message: ${err.message}`);
})


```

## listInputMethod

```TypeScript
listInputMethod(callback: AsyncCallback<Array<InputMethodProperty>>): void
```

查询已安装的输入法列表。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getInputMethods](arkts-ime-inputmethod-inputmethodsetting-i.md#getinputmethods-1)

<!--Device-InputMethodSetting-listInputMethod(callback: AsyncCallback<Array<InputMethodProperty>>): void--><!--Device-InputMethodSetting-listInputMethod(callback: AsyncCallback<Array<InputMethodProperty>>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<InputMethodProperty>> | 是 | 回调函数，返回已安装的输入法列表。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().listInputMethod((err: BusinessError, data: Array<inputMethod.InputMethodProperty>) => {
  if (err) {
    console.error(`Failed to listInputMethod, code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in listing inputMethod.');
});

```

## listInputMethod

```TypeScript
listInputMethod(): Promise<Array<InputMethodProperty>>
```

查询已安装的输入法列表。使用promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getInputMethods](arkts-ime-inputmethod-inputmethodsetting-i.md#getinputmethods-1)

<!--Device-InputMethodSetting-listInputMethod(): Promise<Array<InputMethodProperty>>--><!--Device-InputMethodSetting-listInputMethod(): Promise<Array<InputMethodProperty>>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<InputMethodProperty>> | Promise对象，返回已安装输入法列表。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().listInputMethod().then((data: Array<inputMethod.InputMethodProperty>) => {
  console.info('Succeeded in listing inputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to listInputMethod, code: ${err.code}, message: ${err.message}`);
})

```

## listInputMethodSubtype

```TypeScript
listInputMethodSubtype(
      inputMethodProperty: InputMethodProperty,
      callback: AsyncCallback<Array<InputMethodSubtype>>
    ): void
```

获取指定输入法应用的所有子类型。使用callback异步回调。

**起始版本：** 9

<!--Device-InputMethodSetting-listInputMethodSubtype(
      inputMethodProperty: InputMethodProperty,
      callback: AsyncCallback<Array<InputMethodSubtype>>
    ): void--><!--Device-InputMethodSetting-listInputMethodSubtype(
      inputMethodProperty: InputMethodProperty,
      callback: AsyncCallback<Array<InputMethodSubtype>>
    ): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputMethodProperty | [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | 是 | 输入法应用。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<InputMethodSubtype>> | 是 | 回调函数，返回指定输入法应用的所有子类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800001](../errorcode-inputmethod-framework.md#12800001-包管理服务异常) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

let inputMethodProperty: inputMethod.InputMethodProperty = {
  name: 'com.example.keyboard',
  id: 'propertyId',
}
let inputMethodSetting: inputMethod.InputMethodSetting = inputMethod.getSetting();

inputMethodSetting.listInputMethodSubtype(inputMethodProperty,
  (err: BusinessError, data: Array<InputMethodSubtype>) => {
    if (err) {
      console.error(`Failed to listInputMethodSubtype, code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in listing inputMethodSubtype.');
  });

```

## listInputMethodSubtype

```TypeScript
listInputMethodSubtype(inputMethodProperty: InputMethodProperty): Promise<Array<InputMethodSubtype>>
```

获取指定输入法应用的所有子类型。使用promise异步回调。

**起始版本：** 9

<!--Device-InputMethodSetting-listInputMethodSubtype(inputMethodProperty: InputMethodProperty): Promise<Array<InputMethodSubtype>>--><!--Device-InputMethodSetting-listInputMethodSubtype(inputMethodProperty: InputMethodProperty): Promise<Array<InputMethodSubtype>>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputMethodProperty | [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | 是 | 输入法应用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<InputMethodSubtype>> | Promise对象，返回指定输入法应用的所有子类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800001](../errorcode-inputmethod-framework.md#12800001-包管理服务异常) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

let inputMethodProperty: inputMethod.InputMethodProperty = {
  name: 'com.example.keyboard',
  id: 'propertyId',
}
let inputMethodSetting: inputMethod.InputMethodSetting = inputMethod.getSetting();

inputMethodSetting.listInputMethodSubtype(inputMethodProperty).then((data: Array<InputMethodSubtype>) => {
  console.info('Succeeded in listing inputMethodSubtype.');
}).catch((err: BusinessError) => {
  console.error(`Failed to listInputMethodSubtype, code: ${err.code}, message: ${err.message}`);
})

```

## off('imeChange')

```TypeScript
off(
      type: 'imeChange',
      callback?: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void
    ): void
```

取消订阅输入法及子类型变化监听事件。使用callback异步回调。

**起始版本：** 9

<!--Device-InputMethodSetting-off(
      type: 'imeChange',
      callback?: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void
    ): void--><!--Device-InputMethodSetting-off(
      type: 'imeChange',
      callback?: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void
    ): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'imeChange' | 是 | 设置监听类型，固定取值为'imeChange'。 |
| callback | (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void | 否 | 回调函数，返回取消订阅的输入法属性对象及子类型对象。 |

**示例：**

```TypeScript
inputMethod.getSetting().off('imeChange');

```

## on('imeChange')

```TypeScript
on(
      type: 'imeChange',
      callback: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void
    ): void
```

订阅输入法及子类型变化监听事件。使用callback异步回调。

**起始版本：** 9

<!--Device-InputMethodSetting-on(
      type: 'imeChange',
      callback: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void
    ): void--><!--Device-InputMethodSetting-on(
      type: 'imeChange',
      callback: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void
    ): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'imeChange' | 是 | 设置监听类型，固定取值为'imeChange'。 |
| callback | (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void | 是 | 回调函数，返回输入法属性对象及子类型对象。 |

**示例：**

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';

inputMethod.getSetting()
  .on('imeChange', (inputMethodProperty: inputMethod.InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => {
    console.info(`Succeeded in subscribing imeChange: inputMethodProperty.name: ${inputMethodProperty.name} ` +
      `, inputMethodSubtype.id: ${inputMethodSubtype.id}`);
  });

```

## showOptionalInputMethods

```TypeScript
showOptionalInputMethods(callback: AsyncCallback<boolean>): void
```

显示输入法选择对话框。使用callback异步回调。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** inputMethodList/InputMethodListDialog

<!--Device-InputMethodSetting-showOptionalInputMethods(callback: AsyncCallback<boolean>): void--><!--Device-InputMethodSetting-showOptionalInputMethods(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 回调函数。当输入法选择对话框显示成功，err为undefined，data为true；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().showOptionalInputMethods((err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to showOptionalInputMethods, code: ${err.code}, message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in showing optionalInputMethods.');
  } else {
    console.error(`Failed to showOptionalInputMethods.`);
  }
});

```

## showOptionalInputMethods

```TypeScript
showOptionalInputMethods(): Promise<boolean>
```

显示输入法选择对话框。使用promise异步回调。

**起始版本：** 9

**废弃版本：** 18

**替代接口：** inputMethodList/InputMethodListDialog

<!--Device-InputMethodSetting-showOptionalInputMethods(): Promise<boolean>--><!--Device-InputMethodSetting-showOptionalInputMethods(): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象。当输入法选择对话框显示成功，err为undefined，data为true；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().showOptionalInputMethods().then((result: boolean) => {
  if (result) {
    console.info('Succeeded in showing optionalInputMethods.');
  } else {
    console.error(`Failed to showOptionalInputMethods.`);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to showOptionalInputMethods, code: ${err.code}, message: ${err.message}`);
})

```

