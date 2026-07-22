# openCertificateDetailDialog

## 导入模块

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## openCertificateDetailDialog

```TypeScript
function openCertificateDetailDialog(context: common.Context,cert: Uint8Array, property: CertificateDialogProperty): Promise<void>
```

打开证书管理对话框显示证书的详情。调用成功后，将显示证书的基本信息、有效期、颁发者、使用者等详细信息。使用Promise异步回调。

**起始版本：** 18

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-certificateManagerDialog-function openCertificateDetailDialog(context: common.Context,cert: Uint8Array, property: CertificateDialogProperty): Promise<void>--><!--Device-certificateManagerDialog-function openCertificateDetailDialog(context: common.Context,cert: Uint8Array, property: CertificateDialogProperty): Promise<void>-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | common.Context | 是 | 表示应用的上下文信息。 |
| cert | Uint8Array | 是 | 表示证书数据。 |
| property | [CertificateDialogProperty](arkts-devicecertificate-certificatemanagerdialog-certificatedialogproperty-i.md) | 是 | 表示打开证书管理对话框的属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [29700001](../errorcode-certManagerDialog.md#29700001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [29700003](../errorcode-certManagerDialog.md#29700003-证书安装失败错误) | Show the certificate detail dialog failed, such as the certificate is in an invalid format. |
| [29700004](../errorcode-certManagerDialog.md#29700004-设备类型不支持) | The API is not supported on this device. |

**示例：**

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';

/* context为应用的上下文信息，调用方自行获取，此处仅为示例 */
let context: common.Context = new UIContext().getHostContext() as common.Context;
/* 安装的CA证书数据需要业务赋值，本例数据非CA证书数据 */
let caCert: Uint8Array = new Uint8Array([
  0x30, 0x82, 0x0b, 0xc1, 0x02, 0x01,
]);
let property: certificateManagerDialog.CertificateDialogProperty = {
  showInstallButton: false /* 不显示安装按钮 */
};
try {
  certificateManagerDialog.openCertificateDetailDialog(context, caCert, property).then(() => {
    console.info('Succeeded opening certificate detail dialog.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to open certificate detail dialog. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to open certificate detail dialog. Code: ${error.code}, message: ${error.message}`);
}

```

