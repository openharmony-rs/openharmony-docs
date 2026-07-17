# KeyboardController

下列API均需使用[on('inputStart')](arkts-ime-inputmethodengine-inputmethodability-i.md#on-1)获取到KeyboardController实例后，通过实例调用。

**起始版本：** 8

<!--Device-inputMethodEngine-interface KeyboardController--><!--Device-inputMethodEngine-interface KeyboardController-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## 导入模块

```TypeScript
import { inputMethodEngine } from '@kit.IMEKit';
```

## exitCurrentInputType

```TypeScript
exitCurrentInputType(callback: AsyncCallback<void>): void
```

退出当前输入类型，仅支持系统配置的默认输入法应用调用。使用callback异步回调。

**起始版本：** 11

<!--Device-KeyboardController-exitCurrentInputType(callback: AsyncCallback<void>): void--><!--Device-KeyboardController-exitCurrentInputType(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当退出当前输入类型成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |
| [12800010](../errorcode-inputmethod-framework.md#12800010-不是系统配置的默认输入法) | not the preconfigured default input method. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.exitCurrentInputType((err: BusinessError) => {
  if (err) {
    console.error(`Failed to exit current input type. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info('Succeeded in exiting current input type.');
});

```

## exitCurrentInputType

```TypeScript
exitCurrentInputType(): Promise<void>
```

退出当前输入类型，仅支持系统配置的默认输入法应用调用。使用promise异步回调。

**起始版本：** 11

<!--Device-KeyboardController-exitCurrentInputType(): Promise<void>--><!--Device-KeyboardController-exitCurrentInputType(): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |
| [12800010](../errorcode-inputmethod-framework.md#12800010-不是系统配置的默认输入法) | not the preconfigured default input method. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.exitCurrentInputType().then(() => {
  console.info('Succeeded in exiting current input type.');
}).catch((err: BusinessError) => {
  console.error(`Failed to exit current input type. Code:${err.code}, message:${err.message}`);
});

```

## hide

```TypeScript
hide(callback: AsyncCallback<void>): void
```

隐藏输入法。使用callback异步回调。

**起始版本：** 9

<!--Device-KeyboardController-hide(callback: AsyncCallback<void>): void--><!--Device-KeyboardController-hide(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当输入法隐藏成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.hide((err: BusinessError) => {
  if (err) {
    console.error(`Failed to hide. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info('Succeeded in hiding keyboard.');
});

```

## hide

```TypeScript
hide(): Promise<void>
```

隐藏输入法。使用promise异步回调。

**起始版本：** 9

<!--Device-KeyboardController-hide(): Promise<void>--><!--Device-KeyboardController-hide(): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800003](../errorcode-inputmethod-framework.md#12800003-客户端应用异常) | input method client error. Possible causes:1.the edit box is not focused. 2.no edit box is bound to current input method application.3.ipc failed due to the large amount of data transferred or other reasons. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.hide().then(() => {
  console.info('Succeeded in hiding keyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide. Code:${err.code}, message:${err.message}`);
});

```

## hideKeyboard

```TypeScript
hideKeyboard(callback: AsyncCallback<void>): void
```

隐藏输入法。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** hide(callback:

<!--Device-KeyboardController-hideKeyboard(callback: AsyncCallback<void>): void--><!--Device-KeyboardController-hideKeyboard(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当输入法隐藏成功，err为undefined，否则为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.hideKeyboard((err: BusinessError) => {
  if (err) {
    console.error(`Failed to hideKeyboard. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in hiding keyboard.');
});

```

## hideKeyboard

```TypeScript
hideKeyboard(): Promise<void>
```

隐藏输入法。使用promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [hide()](arkts-ime-inputmethodengine-keyboardcontroller-i.md#hide-2)

<!--Device-KeyboardController-hideKeyboard(): Promise<void>--><!--Device-KeyboardController-hideKeyboard(): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

keyboardController.hideKeyboard().then(() => {
  console.info('Succeeded in hiding keyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hideKeyboard. Code is ${err.code}, message is ${err.message}`);
});

```

