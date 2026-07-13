# supportsCACertDialog

## supportsCACertDialog

```TypeScript
function supportsCACertDialog(): boolean
```

判断设备是否支持[openCertificateDetailDialog](arkts-devicecertificate-opencertificatedetaildialog-f.md#opencertificatedetaildialog-1)，[openInstallCertificateDialog](arkts-devicecertificate-openinstallcertificatedialog-f.md#openinstallcertificatedialog-1)和[openUninstallCertificateDialog](arkts-devicecertificate-openuninstallcertificatedialog-f.md#openuninstallcertificatedialog-1)接口打开管理CA证书的对话框。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 设备是否支持打开CA证书管理对话框。true：支持，false：不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [29700001](../errorcode-certManagerDialog.md#29700001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |

**示例：**

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  /* 判断设备是否支持打开CA证书管理对话框。 */
  let isSupport: boolean = certificateManagerDialog.supportsCACertDialog();
  console.info(`Succeeded in checking whether the device supports CA dialog.`)
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether the device supports CA dialog. Code: ${error.code}, message: ${error.message}`);
}

```

