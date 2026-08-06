# showAlertBeforeBackPage

## showAlertBeforeBackPage

```TypeScript
function showAlertBeforeBackPage(options: EnableAlertOptions): void
```

开启页面返回询问对话框。调用此方法后，执行\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_返回页面时将弹出确认对话框，用户确认后才执行页面返回操作。 适用于需要防止用户误操作返回导致数据丢失的场景，例如用户正在填写表单、编辑文档或进行支付操作时，弹出确认对话框以避免意外退出。 > **说明：** > > - 从API version 9开始支持，从API version 18开始废弃，建议使用 > [showAlertBeforeBackPage]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_替代。showAlertBeforeBackPage需先 > 通过[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_获取 > [Router]\_\_\_JSDOC\_LINK\_DESC\_USD\_5\_\_\_实例，然后通过该实例进行调用。 > > - 从API version 10开始，可以通过使用[UIContext]\_\_\_JSDOC\_LINK\_DESC\_USD\_6\_\_\_中的 > \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_方法获取当前UI上下文关联的 > [Router]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_对象。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 18

**替代接口：** [@ohos.arkui.UIContext:Router#showAlertBeforeBackPage](arkts-arkui-arkui-uicontext-router-c.md#showalertbeforebackpage)

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-router-function showAlertBeforeBackPage(options: EnableAlertOptions): void--><!--Device-router-function showAlertBeforeBackPage(options: EnableAlertOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 文本弹窗信息描述。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 1. Mandatory parameters are left unspecified.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 2. Incorrect parameters types.\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  this.getUIContext().getRouter().showAlertBeforeBackPage({
    message: 'Message Info'
  });
} catch (err) {
  console.error(`showAlertBeforeBackPage failed. Code: ${(err as BusinessError).code}, message: ${(err as BusinessError).message}`);
}
```

