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

<!--Device-certificateManagerDialog-function openAuthDialogForUkeyProvider(dialogInfo: UkeyAuthDialogInfo, ukeyAuthRequest: UkeyAuthRequest): Promise<void>--><!--Device-certificateManagerDialog-function openAuthDialogForUkeyProvider(dialogInfo: UkeyAuthDialogInfo, ukeyAuthRequest: UkeyAuthRequest): Promise<void>-End-->

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
| [29700001](../errorcode-certManagerDialog.md#29700001-内部错误) | The certificate manager service processing failed. Possible causes:         1. IPC communication failed; 2. Memory operation error; 3. File operation error. Please try again. |
| [29700002](../errorcode-certManagerDialog.md#29700002-操作取消) | The user cancels the authentication operation. |
| [29700003](../errorcode-certManagerDialog.md#29700003-证书安装失败错误) | The authentication operation failed, such as: The USB key certificate does not exist. The USB key status is abnormal, Please ask the user to check the status of the Ukey. |
| [29700005](../errorcode-certManagerDialog.md#29700005-操作不符合设备安全策略) | The operation does not comply with the device security policy. Only the PC/2in1 device can open the dialog box of the UkeyAuthExtensionAbility type. |
| [29700006](../errorcode-certManagerDialog.md#29700006-入参校验失败) | Indicates that the input parameters validation failed. For example, the parameter format is incorrect or the value range is invalid. |
| [29700009](../errorcode-certManagerDialog.md#29700009-证书管理对话框操作超时) | The operation in the Ukey authentication dialog box timed out. |
| [29700010](../errorcode-certManagerDialog.md#29700010-不支持并发调用) | The Ukey authentication dialog box cannot be opened concurrently. Please try again later. |

**示例**

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

/* abilityType为Ukey认证对话框的Ability类型，此处赋值UKEY_AUTH_EXTENSION_ABILITY */
let abilityType: certificateManagerDialog.AbilityType =
  certificateManagerDialog.AbilityType.UKEY_AUTH_EXTENSION_ABILITY;
/* abilityName为UKey驱动应用实现的UkeyAuthExtensionAbility名称，此处仅为示例 */
let abilityName: string = 'com.example.ukeydriver.UkeyAuthExtensionAbility';
let dialogInfo: certificateManagerDialog.UkeyAuthDialogInfo = {
  abilityType: abilityType,
  abilityName: abilityName
};
/* keyUri为USB Key证书凭据的唯一标识符，调用方自行获取，此处仅为示例 */
let keyUri: string = 'test';
/* 传入Ukey鉴权对话框的自定义数据，此处仅为示例 */
let customData: Uint8Array = new Uint8Array([0x01, 0x02, 0x03]);
/* Ukey认证对话框的操作超时时间，单位为秒，取值范围为[180, 600]内的整数 */
let timeoutDuration: number = 300;
let ukeyAuthRequest: certificateManagerDialog.UkeyAuthRequest = {
  keyUri: keyUri,
  customData: customData,
  timeoutDuration: timeoutDuration
};
try {
  certificateManagerDialog.openAuthDialogForUkeyProvider(dialogInfo, ukeyAuthRequest).then(() => {
    console.info(`Succeeded in opening ukey auth dialog`);
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to open ukey auth dialog. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to open ukey auth dialog. Code: ${error.code}, message: ${error.message}`);
}
```
