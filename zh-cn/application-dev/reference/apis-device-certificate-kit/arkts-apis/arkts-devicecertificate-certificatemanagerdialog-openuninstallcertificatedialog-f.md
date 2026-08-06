# openUninstallCertificateDialog

## openUninstallCertificateDialog

```TypeScript
function openUninstallCertificateDialog(context: common.Context, certType: CertificateType, certUri: string): Promise<void>
```

打开证书管理卸载证书向导，显示相应的页面。使用Promise异步回调。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-certificateManagerDialog-function openUninstallCertificateDialog(context: common.Context, certType: CertificateType, certUri: string): Promise<void>--><!--Device-certificateManagerDialog-function openUninstallCertificateDialog(context: common.Context, certType: CertificateType, certUri: string): Promise<void>-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | common.Context | 是 | 表示应用的上下文信息。 |
| certType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 表示待卸载证书类型，目前仅支持CA\_\_\_ESCAPED\_UNDERSCORE\_\_\_CERT。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_目前仅支持CA\_\_\_ESCAPED\_UNDERSCORE\_\_\_CERT类型。 |
| certUri | string | 是 | 表示待卸载证书的唯一标识符，可通过安装CA证书接口或查询CA证书列表接口获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [29700001](../errorcode-certManagerDialog.md#29700001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Memory operation error; 3. File operation error. Please try again. |
| [29700002](../errorcode-certManagerDialog.md#29700002-操作取消) | The user cancels the uninstallation operation. |
| [29700003](../errorcode-certManagerDialog.md#29700003-证书安装失败错误) | The user uninstall certificate failed in the certificate manager dialog, such as the certificate uri is not exist. |
| [29700004](../errorcode-certManagerDialog.md#29700004-设备类型不支持) | For security purposes, the current device does not support this API.You can use the [supportsCACertDialog]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ to determine whether the device can open the dialog box for deleting a CA certificate with certType set to CA. |
| [29700005](../errorcode-certManagerDialog.md#29700005-操作不符合设备安全策略) | The operation does not comply with the device security policy, such as the device does not allow users to manage the CA certificate of the global user. |

**示例：**

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';

/* context为应用的上下文信息，调用方自行获取，此处仅为示例 */
let context: common.Context = new UIContext().getHostContext() as common.Context;
/* certificateType为证书类型，此处赋值CA_CERT，即删除CA证书 */
let certificateType: certificateManagerDialog.CertificateType = certificateManagerDialog.CertificateType.CA_CERT;
/* certUri为业务安装证书返回的唯一标识符，此处仅为示例 */
let certUri: string = "test";
try {
  certificateManagerDialog.openUninstallCertificateDialog(context, certificateType, certUri).then(() => {
    console.info('Succeeded in opening uninstall certificate');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to open uninstall certificate dialog. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to open uninstall certificate dialog. Code: ${error.code}, message: ${error.message}`);
}
```

