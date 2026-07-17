# getUkeyCertificateList

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## getUkeyCertificateList

```TypeScript
function getUkeyCertificateList(ukeyProvider: string, ukeyInfo: UkeyInfo): Promise<CMResult>
```

获取USB Key证书凭据列表。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-certificateManager-function getUkeyCertificateList(ukeyProvider: string, ukeyInfo: UkeyInfo): Promise<CMResult>--><!--Device-certificateManager-function getUkeyCertificateList(ukeyProvider: string, ukeyInfo: UkeyInfo): Promise<CMResult>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ukeyProvider | string | 是 | 表示USB Key的设备提供商 |
| ukeyInfo | [UkeyInfo](arkts-devicecertificate-certificatemanager-ukeyinfo-i.md) | 是 | 表示USB Key证书凭据的属性信息 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<CMResult> | Promise对象，返回获取USB Key证书凭据列表的结果，返回值为[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)对象中的credentialDetailList属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.<br>The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. |
| [17500010](../errorcode-certManager.md#17500010-访问usb证书凭据失败) | Indicates that access USB Key service failed. |
| [17500011](../errorcode-certManager.md#17500011-入参校验失败) | Parameter verification failed.<br> Possible causes: the ukeyInfo parameter is invalid.For example, the parameter format is incorrect or the value range is invalid. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ukeyProvider: string = 'testProvider'; /* USB凭据提供商，此处省略 */
let ukeyInfo: certificateManager.UkeyInfo = { /* USB凭据的属性信息，此处省略 */
  certPurpose: certificateManager.CertificatePurpose.PURPOSE_DEFAULT,
}
try {
  certificateManager.getUkeyCertificateList(ukeyProvider, ukeyInfo).then((cmResult) => {
    let list: Array<certificateManager.Credential> = cmResult.credentialDetailList ?? [];
    console.info('Succeeded in getting USB Key certificate list.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to get USB Key certificate list. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get USB Key certificate list. Code: ${error.code}, message: ${error.message}`);
}

```

