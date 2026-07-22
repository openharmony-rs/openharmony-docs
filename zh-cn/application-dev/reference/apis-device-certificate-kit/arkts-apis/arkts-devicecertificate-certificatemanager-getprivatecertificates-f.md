# getPrivateCertificates

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## getPrivateCertificates

```TypeScript
function getPrivateCertificates(): Promise<CMResult>
```

表示获取应用安装的凭据列表。使用Promise异步回调。

**起始版本：** 13

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function getPrivateCertificates(): Promise<CMResult>--><!--Device-certificateManager-function getPrivateCertificates(): Promise<CMResult>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CMResult&gt; | Promise对象，返回获取应用安装的凭据列表的结果，返回值为[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)对象中的credentialList属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  certificateManager.getPrivateCertificates().then((cmResult) => {
    if (cmResult === undefined) { // 应用安装的凭据个数为0时，返回cmResult为undefined。
      console.info('The count of the private certificates is 0.');
    } else if (cmResult.credentialList == undefined) {
      console.info('The result of getting all private certificates installed by the application is undefined.');
    } else {
      let list = cmResult.credentialList;
      console.info('Succeeded in getting all private certificates installed by the application.');
    }
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to get all private certificates installed by the application. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get all private certificates installed by the application. Code: ${error.code}, message: ${error.message}`);
}

```

