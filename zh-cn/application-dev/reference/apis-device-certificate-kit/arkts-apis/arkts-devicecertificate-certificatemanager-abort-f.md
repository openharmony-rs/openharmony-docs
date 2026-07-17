# abort

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

## abort

```TypeScript
function abort(handle: Uint8Array, callback: AsyncCallback<void>): void
```

中止签名、验签的操作。与finish方法互斥，一个签名验签流程只能选择调用其中一个方法。使用Callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function abort(handle: Uint8Array, callback: AsyncCallback<void>): void--><!--Device-certificateManager-function abort(handle: Uint8Array, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | [Uint8Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-uint8array-c.md) | 是 | 表示初始化操作返回的句柄，。<br>最大长度为8。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当中止签名、验签成功时，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';

/* cmHandle为业务调用init接口的返回值，此处仅为示例 */
let cmHandle: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
try {
  certificateManager.abort(cmHandle, (err, cmResult) => {
    if (err != null) {
      console.error(`Failed to abort. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in aborting.');
    }
  });
} catch(error) {
  console.error(`Failed to abort. Code: ${error.code}, message: ${error.message}`);
}

```


## abort

```TypeScript
function abort(handle: Uint8Array): Promise<void>
```

中止签名、验签的操作。与finish方法互斥，一个签名验签流程只能选择调用其中一个方法。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function abort(handle: Uint8Array): Promise<void>--><!--Device-certificateManager-function abort(handle: Uint8Array): Promise<void>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | [Uint8Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-uint8array-c.md) | 是 | 表示初始化操作返回的句柄，。<br>最大长度为8。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

/* cmHandle为业务调用init接口的返回值，此处仅为示例 */
let cmHandle: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
try {
  certificateManager.abort(cmHandle).then((result) => {
    console.info('Succeeded in aborting.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to abort. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to abort. Code: ${error.code}, message: ${error.message}`);
}

```

