# InputMethodSetting

In the following API examples, you must first use [getSetting](arkts-ime-inputmethod-getsetting-f.md) to obtain an **InputMethodSetting** instance, and then call the APIs using the obtained instance.

**Since:** 8

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## displayOptionalInputMethod

```TypeScript
displayOptionalInputMethod(callback: AsyncCallback<void>): void
```

Displays a dialog box for selecting an input method. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [inputMethodList/InputMethodListDialog](arkts-ime-inputmethodlist-inputmethodlistdialog-s.md)

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Examples**

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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().displayOptionalInputMethod().then(() => {
  console.info('Succeeded in displaying optionalInputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to displayOptionalInputMethod, code: ${err.code}, message: ${err.message}`);
})
```

## displayOptionalInputMethod

```TypeScript
displayOptionalInputMethod(): Promise<void>
```

Displays a dialog box for selecting an input method. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [inputMethodList/InputMethodListDialog](arkts-ime-inputmethodlist-inputmethodlistdialog-s.md)

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [displayOptionalInputMethod](#displayoptionalinputmethod)

## getAllInputMethods

```TypeScript
getAllInputMethods(callback: AsyncCallback<Array<InputMethodProperty>>): void
```

Obtains a list of all input methods. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md)&gt;&gt; | Yes | Callback used to return a list of all input methods. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800001](../errorcode-inputmethod-framework.md#12800001-bundle-manager-service-exception) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().getAllInputMethods().then((data: Array<inputMethod.InputMethodProperty>) => {
  console.info('Succeeded in getting all inputMethods.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getAllInputMethods, code: ${err.code}, message: ${err.message}`);
})
```

## getAllInputMethods

```TypeScript
getAllInputMethods(): Promise<Array<InputMethodProperty>>
```

Obtains a list of all input methods. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md)&gt;&gt; | Promise used to return a list of all input methods. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800001](../errorcode-inputmethod-framework.md#12800001-bundle-manager-service-exception) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

See [getAllInputMethods](#getallinputmethods)

## getAllInputMethodsSync

```TypeScript
getAllInputMethodsSync(): Array<InputMethodProperty>
```

Obtains a list of all input methods. This API returns the result synchronously.

**Since:** 11

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md)&gt; | List of all input methods. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800001](../errorcode-inputmethod-framework.md#12800001-bundle-manager-service-exception) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
let imeProperty: Array<inputMethod.InputMethodProperty> = inputMethod.getSetting().getAllInputMethodsSync();
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let imeProperty: Array<inputMethod.InputMethodProperty> = inputMethod.getSetting().getAllInputMethodsSync(100);
  console.info('Succeeded in getting all input methods, count: ' + imeProperty.length);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getAllInputMethodsSync. Code: ${error.code}, message: ${error.message}`);
}
```

## getInputMethods

```TypeScript
getInputMethods(enable: boolean, callback: AsyncCallback<Array<InputMethodProperty>>): void
```

Obtains a list of activated or deactivated input methods. This API uses an asynchronous callback to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> An activated input method refers to an input method that is enabled. The default input method is enabled by default. Other input methods can be enabled or disabled as needed. <br>
> <br>
> The list of activated input methods includes the default input method and enabled input methods. The list of deactivated input methods includes all installed input methods except the enabled ones.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to return a list of activated input methods. The value **true** means to return a list of activated input methods, and **false** means to return a list of deactivated input methods. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md)&gt;&gt; | Yes | Callback used to return a list of activated or deactivated input methods. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800001](../errorcode-inputmethod-framework.md#12800001-bundle-manager-service-exception) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().getInputMethods(true).then((data: Array<inputMethod.InputMethodProperty>) => {
  console.info('Succeeded in getting inputMethods.');
}).catch((err: BusinessError) => {
  console.error(`Failed to getInputMethods, code: ${err.code}, message: ${err.message}`);
})
```

## getInputMethods

```TypeScript
getInputMethods(enable: boolean): Promise<Array<InputMethodProperty>>
```

Obtains a list of activated or deactivated input methods. This API uses a promise to return the result. <br> <br>  
> **NOTE:** <br>
> <br>
> An activated input method refers to an input method that is enabled. The default input method is enabled by default. Other input methods can be enabled or disabled as needed. <br>
> <br>
> The list of activated input methods includes the default input method and enabled input methods. The list of deactivated input methods includes all installed input methods except the enabled ones.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to return a list of activated input methods. The value **true** means to return a list of activated input methods, and **false** means to return a list of deactivated input methods. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md)&gt;&gt; | Promise used to return a list of activated or deactivated input methods. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800001](../errorcode-inputmethod-framework.md#12800001-bundle-manager-service-exception) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

See [getInputMethods](#getinputmethods)

## getInputMethodsSync

```TypeScript
getInputMethodsSync(enable: boolean): Array<InputMethodProperty>
```

Obtains a list of activated or deactivated input methods. This API returns the result synchronously. <br> <br>  
> **NOTE:** <br>
> <br>
> An activated input method refers to an input method that is enabled. The default input method is enabled by default. Other input methods can be enabled or disabled as needed. <br>
> <br>
> The list of activated input methods includes the default input method and enabled input methods. The list of deactivated input methods includes all installed input methods except the enabled ones.

**Since:** 11

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to return a list of activated input methods. The value **true** means to return a list of activated input methods, and **false** means to return a list of deactivated input methods. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md)&gt; | List of activated or deactivated input methods. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [12800001](../errorcode-inputmethod-framework.md#12800001-bundle-manager-service-exception) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
let imeProperty: Array<inputMethod.InputMethodProperty> = inputMethod.getSetting().getInputMethodsSync(true);
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let imeProperty: Array<inputMethod.InputMethodProperty> = inputMethod.getSetting().getInputMethodsSync(true, 100);
  console.info('Succeeded in getting enabled input methods, count: ' + imeProperty.length);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getInputMethodsSync. Code: ${error.code}, message: ${error.message}`);
}
```

## getInputMethodState

```TypeScript
getInputMethodState(): Promise<EnabledState>
```

Obtains the input method state. This API uses a promise to return the result.

**Since:** 15

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[EnabledState](arkts-ime-inputmethod-enabledstate-e.md)&gt; | Promise used to return the result. **EnabledState.DISABLED** indicates that the input method is disabled, **EnabledState.BASIC_MODE** indicates that the input method is in basic mode, and **EnabledState.FULL_EXPERIENCE_MODE** indicates that the input method is in full experience mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800004](../errorcode-inputmethod-framework.md#12800004-not-an-input-method) | not an input method application. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().getInputMethodState().then((status: inputMethod.EnabledState) => {
  console.info(`Succeeded in getInputMethodState, status: ${status}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to getInputMethodState, code: ${err.code}, message: ${err.message}`);
});
```

## listCurrentInputMethodSubtype

```TypeScript
listCurrentInputMethodSubtype(callback: AsyncCallback<Array<InputMethodSubtype>>): void
```

Obtains all subtypes of this input method. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[InputMethodSubtype](arkts-ime-inputmethodsubtype-i.md)&gt;&gt; | Yes | Callback used to return all subtypes of the current input method. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800001](../errorcode-inputmethod-framework.md#12800001-bundle-manager-service-exception) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

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

## listCurrentInputMethodSubtype

```TypeScript
listCurrentInputMethodSubtype(): Promise<Array<InputMethodSubtype>>
```

Obtains all subtypes of this input method. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[InputMethodSubtype](arkts-ime-inputmethodsubtype-i.md)&gt;&gt; | Promise used to return all subtypes of the current input method. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800001](../errorcode-inputmethod-framework.md#12800001-bundle-manager-service-exception) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

See [listCurrentInputMethodSubtype](#listcurrentinputmethodsubtype)

## listInputMethod

```TypeScript
listInputMethod(callback: AsyncCallback<Array<InputMethodProperty>>): void
```

Obtains a list of installed input methods. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getInputMethods](#getinputmethods)

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md)&gt;&gt; | Yes | Callback used to return the list of installed input methods. |

**Examples**

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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.getSetting().listInputMethod().then((data: Array<inputMethod.InputMethodProperty>) => {
  console.info('Succeeded in listing inputMethod.');
}).catch((err: BusinessError) => {
  console.error(`Failed to listInputMethod, code: ${err.code}, message: ${err.message}`);
})
```

## listInputMethod

```TypeScript
listInputMethod(): Promise<Array<InputMethodProperty>>
```

Obtains a list of installed input methods. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getInputMethods](#getinputmethods)

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md)&gt;&gt; | Promise used to return the list of installed input methods. |

**Examples**

See [listInputMethod](#listinputmethod)

## listInputMethodSubtype

```TypeScript
listInputMethodSubtype(
      inputMethodProperty: InputMethodProperty,
      callback: AsyncCallback<Array<InputMethodSubtype>>
    ): void
```

Obtains all subtypes of a specified input method. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputMethodProperty | [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | Yes | Input method. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[InputMethodSubtype](arkts-ime-inputmethodsubtype-i.md)&gt;&gt; | Yes | Callback used to return all subtypes of the specified input method. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800001](../errorcode-inputmethod-framework.md#12800001-bundle-manager-service-exception) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

let inputMethodProperty: inputMethod.InputMethodProperty = {
  name: 'com.example.keyboard',
  id: 'propertyId',
  packageName: 'com.example.keyboard',
  methodId: 'propertyId'
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

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

let inputMethodProperty: inputMethod.InputMethodProperty = {
  name: 'com.example.keyboard',
  id: 'propertyId',
  packageName: 'com.example.keyboard',
  methodId: 'propertyId'
}
let inputMethodSetting: inputMethod.InputMethodSetting = inputMethod.getSetting();

inputMethodSetting.listInputMethodSubtype(inputMethodProperty).then((data: Array<InputMethodSubtype>) => {
  console.info('Succeeded in listing inputMethodSubtype.');
}).catch((err: BusinessError) => {
  console.error(`Failed to listInputMethodSubtype, code: ${err.code}, message: ${err.message}`);
})
```

## listInputMethodSubtype

```TypeScript
listInputMethodSubtype(inputMethodProperty: InputMethodProperty): Promise<Array<InputMethodSubtype>>
```

Obtains all subtypes of a specified input method. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputMethodProperty | [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | Yes | Input method. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[InputMethodSubtype](arkts-ime-inputmethodsubtype-i.md)&gt;&gt; | Promise used to return all subtypes of the specified input method. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800001](../errorcode-inputmethod-framework.md#12800001-bundle-manager-service-exception) | bundle manager error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

See [listInputMethodSubtype](#listinputmethodsubtype)

## off('imeChange')

```TypeScript
off(
      type: 'imeChange',
      callback?: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void
    ): void
```

Disables listening for the input method and subtype change event. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'imeChange' | Yes | Listening type. The value is fixed at **'imeChange'**. |
| callback | (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) =&gt; void | No | Callback used to return the input method attributes and subtype. |

## on('imeChange')

```TypeScript
on(
      type: 'imeChange',
      callback: (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) => void
    ): void
```

Enables listening for the input method and subtype change event. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'imeChange' | Yes | Listening type. The value is fixed at **'imeChange'**. |
| callback | (inputMethodProperty: InputMethodProperty, inputMethodSubtype: InputMethodSubtype) =&gt; void | Yes | Callback used to return the input method attributes and subtype. |

## showOptionalInputMethods

```TypeScript
showOptionalInputMethods(callback: AsyncCallback<boolean>): void
```

Displays a dialog box for selecting an input method. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [inputMethodList/InputMethodListDialog](arkts-ime-inputmethodlist-inputmethodlistdialog-s.md)

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is **true**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

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

## showOptionalInputMethods

```TypeScript
showOptionalInputMethods(): Promise<boolean>
```

Displays a dialog box for selecting an input method. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** [inputMethodList/InputMethodListDialog](arkts-ime-inputmethodlist-inputmethodlistdialog-s.md)

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. If the operation is successful, **err** is **undefined** and **data** is **true**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12800008](../errorcode-inputmethod-framework.md#12800008-input-method-manager-service-error) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |

**Examples**

See [showOptionalInputMethods](#showoptionalinputmethods)
