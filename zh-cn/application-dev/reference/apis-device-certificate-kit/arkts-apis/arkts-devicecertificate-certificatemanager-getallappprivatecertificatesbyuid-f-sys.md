# getAllAppPrivateCertificatesByUid（系统接口）

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## getAllAppPrivateCertificatesByUid

```TypeScript
function getAllAppPrivateCertificatesByUid(appUid: number) : Promise<CMResult>
```

获取指定应用的所有私有凭据，仅证书管理应用调用。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER and ohos.permission.ACCESS_CERT_MANAGER_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-certificateManager-function getAllAppPrivateCertificatesByUid(appUid: int) : Promise<CMResult>--><!--Device-certificateManager-function getAllAppPrivateCertificatesByUid(appUid: int) : Promise<CMResult>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appUid | number | 是 | 表示应用UID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<CMResult> | Promise对象，返回获取指定应用的所有私有凭据的结果，返回值为[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)对象中的credentialDetailList属性。<br>**说明**：私有凭据个数为0时，返回CMResult为undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.<br> The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appUid: number = 1001; /* 应用UID */
try {
  certificateManager.getAllAppPrivateCertificatesByUid(appUid).then((cmResult: certificateManager.CMResult) => {
    if (cmResult === undefined) { // 指定应用的私有凭据个数为0时，返回cmResult为undefined。
      console.info('The count of private certificates is 0.');
    } else if (cmResult.credentialDetailList == undefined) {
      console.info('The result of getting all private certificates is undefined.');
    } else {
      let list: Array<certificateManager.Credential> = cmResult.credentialDetailList;
      console.info('Succeeded in getting all private certificates.');
    }
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to get all private certificates. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to get all private certificates. Code: ${error.code}, message: ${error.message}`);
}

```

