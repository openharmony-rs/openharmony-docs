# switchCurrentInputMethodAndSubtype

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
import { inputMethodEngine } from '@kit.IMEKit';
import { InputMethodListDialog, PatternOptions, Pattern } from '@kit.IMEKit';
import { PanelInfo, PanelType, PanelFlag } from '@kit.IMEKit';
import { InputMethodExtraConfig } from '@kit.IMEKit';
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## switchCurrentInputMethodAndSubtype

```TypeScript
function switchCurrentInputMethodAndSubtype(
    inputMethodProperty: InputMethodProperty,
    inputMethodSubtype: InputMethodSubtype,
    callback: AsyncCallback<boolean>
  ): void
```

切换至指定输入法的指定子类型，适用于跨输入法切换子类型。使用callback异步回调。

**起始版本：** 23

**需要权限：** 
- API版本9 - 10：ohos.permission.CONNECT_IME_ABILITY

<!--Device-inputMethod-function switchCurrentInputMethodAndSubtype(    inputMethodProperty: InputMethodProperty,    inputMethodSubtype: InputMethodSubtype,    callback: AsyncCallback<boolean>  ): void--><!--Device-inputMethod-function switchCurrentInputMethodAndSubtype(    inputMethodProperty: InputMethodProperty,    inputMethodSubtype: InputMethodSubtype,    callback: AsyncCallback<boolean>  ): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputMethodProperty | [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | 是 | 目标输入法。 |
| inputMethodSubtype | [InputMethodSubtype](arkts-ime-inputmethodsubtype-i.md) | 是 | 目标输入法子类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。当输入法和子类型切换成功，err为undefined，data为获取到的切换子类型结果true；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800005](../errorcode-inputmethod-framework.md#12800005-配置持久化失败) | configuration persistence error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permissions check fails.<br>**适用版本：** 9 - 10 |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**示例**

ArkTS-Dyn示例:

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

let currentIme: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod();
let imSubType: InputMethodSubtype = inputMethod.getCurrentInputMethodSubtype();
inputMethod.switchCurrentInputMethodAndSubtype(currentIme, imSubType, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to switchCurrentInputMethodAndSubtype, code: ${err.code}, message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in switching currentInputMethodAndSubtype.');
  } else {
    console.error('Failed to switchCurrentInputMethodAndSubtype.');
  }
});
```

ArkTS-Sta示例:

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let currentIme = inputMethod.getCurrentInputMethod();
let imSubType = inputMethod.getCurrentInputMethodSubtype();

inputMethod.switchCurrentInputMethodAndSubtype(currentIme, imSubType, (err: BusinessError | null, result: boolean | undefined) => {
  if (err) {
    console.error(`Failed to switchCurrentInputMethodAndSubtype, code: ${err.code}, message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in switching currentInputMethodAndSubtype.');
  } else {
    console.error('Failed to switchCurrentInputMethodAndSubtype.');
  }
});.
```


## switchCurrentInputMethodAndSubtype

```TypeScript
function switchCurrentInputMethodAndSubtype(
    inputMethodProperty: InputMethodProperty,
    inputMethodSubtype: InputMethodSubtype
  ): Promise<boolean>
```

切换至指定输入法的指定子类型，适用于跨输入法切换子类型。使用promise异步回调。

**起始版本：** 23

**需要权限：** 
- API版本9 - 10：ohos.permission.CONNECT_IME_ABILITY

<!--Device-inputMethod-function switchCurrentInputMethodAndSubtype(    inputMethodProperty: InputMethodProperty,    inputMethodSubtype: InputMethodSubtype  ): Promise<boolean>--><!--Device-inputMethod-function switchCurrentInputMethodAndSubtype(    inputMethodProperty: InputMethodProperty,    inputMethodSubtype: InputMethodSubtype  ): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputMethodProperty | [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | 是 | 目标输入法。 |
| inputMethodSubtype | [InputMethodSubtype](arkts-ime-inputmethodsubtype-i.md) | 是 | 目标输入法子类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示切换至指定输入法的指定子类型成功，返回false表示切换至指定输入法的指定子类型失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800005](../errorcode-inputmethod-framework.md#12800005-配置持久化失败) | configuration persistence error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | permissions check fails.<br>**适用版本：** 9 - 10 |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**示例**

ArkTS-Dyn示例:

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

let currentIme: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod();
let imSubType: InputMethodSubtype = inputMethod.getCurrentInputMethodSubtype();
inputMethod.switchCurrentInputMethodAndSubtype(currentIme, imSubType).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in switching currentInputMethodAndSubtype.');
  } else {
    console.error('Failed to switchCurrentInputMethodAndSubtype.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to switchCurrentInputMethodAndSubtype, code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例:

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let currentIme = inputMethod.getCurrentInputMethod();
let imSubType = inputMethod.getCurrentInputMethodSubtype();

inputMethod.switchCurrentInputMethodAndSubtype(currentIme, imSubType).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in switching currentInputMethodAndSubtype.');
  } else {
    console.error('Failed to switchCurrentInputMethodAndSubtype.');
  }
}).catch((err: BusinessError): void=> {
  console.error(`Failed to switchCurrentInputMethodAndSubtype, code: ${err.code}, message: ${err.message}`);
})
```

