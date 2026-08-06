# InputMethodController

下列API示例中都需使用[getController]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_获取到InputMethodController实例，再通过实例调用对应方法。 InputMethodController是输入法客户端控制器，面向前台应用提供与输入法交互的核心能力。通过\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_获取实例后，可进行以下操作： - **绑定管理**：通过 [attach]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_ 建立与输入法的绑定，通过[detach]\_\_\_JSDOC\_LINK\_DESC\_USD\_8\_\_\_解除绑定。attach和 detach必须配对使用。 - **键盘控制**：通过[showTextInput]\_\_\_JSDOC\_LINK\_DESC\_USD\_9\_\_\_拉 起软键盘进入编辑状态，通过[hideTextInput]\_\_\_JSDOC\_LINK\_DESC\_USD\_10\_\_\_隐 藏软键盘退出编辑状态。showTextInput和hideTextInput必须配对使用。 - **编辑框状态同步**：通过 [updateCursor]\_\_\_JSDOC\_LINK\_DESC\_USD\_11\_\_\_ 、 [changeSelection]\_\_\_JSDOC\_LINK\_DESC\_USD\_12\_\_\_ 、 [updateAttribute]\_\_\_JSDOC\_LINK\_DESC\_USD\_13\_\_\_ 等接口向输入法同步光标、选区、属性等编辑框状态信息。 - **事件订阅**：通过on('insertText')、on('deleteLeft')等接口订阅输入法应用发送的文本操作事件。 典型调用序列：\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_ → \_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_ → \_\_\_INLINE\_CODE\_DESC\_USD\_3\_\_\_/\_\_\_INLINE\_CODE\_DESC\_USD\_4\_\_\_ → \_\_\_INLINE\_CODE\_DESC\_USD\_5\_\_\_ > **注意：** > > attach和detach必须配对使用，showTextInput和hideTextInput必须配对使用，否则可能导致资源泄漏或状态不一致。

**起始版本：** 6

**ArkTS模式：** ArkTS-Dyn起始版本为6；ArkTS-Sta起始版本为23。

<!--Device-inputMethod-interface InputMethodController--><!--Device-inputMethod-interface InputMethodController-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

## hideSoftKeyboard

ArkTS-Dyn:
```TypeScript
hideSoftKeyboard(displayId: number): Promise<void>
```

ArkTS-Sta:
```TypeScript
hideSoftKeyboard(displayId: long): Promise<void>
```

隐藏指定屏幕上的输入法软键盘。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.CONNECT_IME_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputMethodController-hideSoftKeyboard(displayId: long): Promise<void>--><!--Device-InputMethodController-hideSoftKeyboard(displayId: long): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 是 | 屏幕ID。 |

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

ArkTS-Dyn示例:

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayId: number = 30;
inputMethod.getController().hideSoftKeyboard(displayId).then(() => {
  console.info('Succeeded in hiding softKeyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to hide softKeyboard, code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例:

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayId: long = 30;
inputMethod.getController().hideSoftKeyboard(displayId).then(() => {
  console.info('Succeeded in hiding softKeyboard.');
}).catch((err: BusinessError): void=> {
  console.error(`Failed to hide softKeyboard, code: ${err.code}, message: ${err.message}`);
});
```

## showSoftKeyboard

ArkTS-Dyn:
```TypeScript
showSoftKeyboard(displayId: number): Promise<void>
```

ArkTS-Sta:
```TypeScript
showSoftKeyboard(displayId: long): Promise<void>
```

在指定屏幕上显示输入法软键盘。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.CONNECT_IME_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputMethodController-showSoftKeyboard(displayId: long): Promise<void>--><!--Device-InputMethodController-showSoftKeyboard(displayId: long): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 是 | 屏幕ID。 |

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

ArkTS-Dyn示例:

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayId: number = 20;
inputMethod.getController().showSoftKeyboard(displayId).then(() => {
  console.info('Succeeded in showing softKeyboard.');
}).catch((err: BusinessError) => {
  console.error(`Failed to show softKeyboard, code: ${err.code}, message: ${err.message}`);
});
```

ArkTS-Sta示例:

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let displayId: long = 20;
inputMethod.getController().showSoftKeyboard(displayId).then(() => {
  console.info('Succeeded in showing softKeyboard.');
}).catch((err: BusinessError): void=> {
  console.error(`Failed to show softKeyboard, code: ${err.code}, message: ${err.message}`);
});
```

