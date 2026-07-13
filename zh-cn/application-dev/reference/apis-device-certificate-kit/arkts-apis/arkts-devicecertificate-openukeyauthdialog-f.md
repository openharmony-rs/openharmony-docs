# openUkeyAuthDialog

## openUkeyAuthDialog

```TypeScript
function openUkeyAuthDialog(context: common.Context, ukeyAuthRequest: UkeyAuthRequest): Promise<void>
```

打开证书管理对话框的USB Key证书凭据PIN码认证页面。在弹出的页面中，用户可以输入PIN码授权USB Key证书凭据。调用成功后，USB
Key证书凭据将被解锁，应用可使用该凭据进行签名、加密等操作。使用Promise异步回调。

**起始版本：** 22

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | common.Context | 是 | 表示应用的上下文信息。 |
| ukeyAuthRequest | UkeyAuthRequest | 是 | 表示USB Key凭据认证请求信息 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have thepermission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [29700006](../errorcode-certManagerDialog.md#29700006-入参校验失败) | Indicates that the input parameters validation failed.For example, the parameter format is incorrect or the value range is invalid. |
| [29700001](../errorcode-certManagerDialog.md#29700001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |
| [29700002](../errorcode-certManagerDialog.md#29700002-操作取消) | The user cancels the authentication operation. |
| [29700003](../errorcode-certManagerDialog.md#29700003-证书安装失败错误) | The authentication operation failed, such as the USB key certificatedoes not exist, the USB key status is abnormal. |

**示例：**

```TypeScript
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';

/* context为应用的上下文信息，调用方自行获取，此处仅为示例 */
let context: common.Context = new UIContext().getHostContext() as common.Context;
/* keyUri为证书凭据的唯一标识符，调用方自行获取，此处仅为示例 */
let keyUri: string = "test"
let ukeyAuthRequest: certificateManagerDialog.UkeyAuthRequest = { keyUri: keyUri }
try {
  certificateManagerDialog.openUkeyAuthDialog(context, ukeyAuthRequest).then(() => {
    console.info(`Succeeded in opening ukey authorization dialog`)
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to open ukey authorization dialog. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to open ukey authorization dialog. Code: ${error.code}, message: ${error.message}`);
}

```

