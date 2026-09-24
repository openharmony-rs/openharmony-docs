# openAuthDialogForUkeyProvider

## 导入模块

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## openAuthDialogForUkeyProvider

```TypeScript
function openAuthDialogForUkeyProvider(dialogInfo: UkeyAuthDialogInfo, ukeyAuthRequest: UkeyAuthRequest): Promise<void>
```

打开USB Key凭证的Ukey认证对话框。该接口仅Ukey驱动应用调用。实现支付、证书更新等场景下的自定义对话框功能。Ukey认证对话框需要Ukey驱动应用实现。该接口使用promise返回结果。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.CRYPTO_EXTENSION_REGISTER

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dialogInfo | [UkeyAuthDialogInfo](arkts-devicecertificate-certificatemanagerdialog-ukeyauthdialoginfo-i.md) | 是 | 需要打开的Ukey认证对话框信息。 |
| ukeyAuthRequest | [UkeyAuthRequest](arkts-devicecertificate-certificatemanagerdialog-ukeyauthrequest-i.md) | 是 | USB Key凭证认证请求信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported because the certificate management application hap is not preinstalled in the system. |
| [29700001](../errorcode-certManagerDialog.md#29700001-内部错误) | The certificate manager service processing failed. Possible causes: 1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |
| [29700002](../errorcode-certManagerDialog.md#29700002-操作取消) | The user cancels the authentication operation. |
| [29700003](../errorcode-certManagerDialog.md#29700003-证书安装失败错误) | The authentication operation failed, such as: The USB key certificate does not exist. The USB key status is abnormal, Please ask the user to check the status of the Ukey. |
| [29700005](../errorcode-certManagerDialog.md#29700005-操作不符合设备安全策略) | The operation does not comply with the device security policy. Only the PC/2in1 device can open the dialog box of the UkeyAuthExtensionAbility type. |
| [29700006](../errorcode-certManagerDialog.md#29700006-入参校验失败) | Indicates that the input parameters validation failed. For example, the parameter format is incorrect or the value range is invalid. |
| 29700009 | The operation in the Ukey authentication dialog box timed out. |
| 29700010 | The Ukey authentication dialog box cannot be opened concurrently. Please try again later. |
