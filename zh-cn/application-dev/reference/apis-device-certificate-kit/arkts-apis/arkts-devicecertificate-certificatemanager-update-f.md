# update

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

<a id="update"></a>
## update

```TypeScript
function update(handle: Uint8Array, data: Uint8Array, callback: AsyncCallback<void>): void
```

签名、验签的数据更新操作，需要在init操作之后调用，用于传入待签名、验签的数据。使用Callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function update(handle: Uint8Array, data: Uint8Array, callback: AsyncCallback<void>): void--><!--Device-certificateManager-function update(handle: Uint8Array, data: Uint8Array, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | Uint8Array | 是 | 表示操作句柄，需先调用init方法获得 |
| data | Uint8Array | 是 | 表示待签名、验签的数据。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当签名、验签的数据更新操作成功时，err为null，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';

/* cmHandle为业务调用init接口的返回值，此处仅为示例 */
let cmHandle: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
let srcData: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
try {
  certificateManager.update(cmHandle, srcData, (err, result) => {
    if (err != null) {
      console.error(`Failed to update. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in updating.');
    }
  });
} catch (error) {
  console.error(`Failed to update. Code: ${error.code}, message: ${error.message}`);
}

```


<a id="update-1"></a>
## update

```TypeScript
function update(handle: Uint8Array, data: Uint8Array): Promise<void>
```

签名、验签的数据更新操作。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function update(handle: Uint8Array, data: Uint8Array): Promise<void>--><!--Device-certificateManager-function update(handle: Uint8Array, data: Uint8Array): Promise<void>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | Uint8Array | 是 | 表示操作句柄，需先调用init方法获得 |
| data | Uint8Array | 是 | 表示待签名、验签的数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../errorcode-certManager.md#17500001-内部错误) | Internal error. Possible causes: 1. IPC communication failed;<br>2. Memory operation error; 3. File operation error. Please try again. |

**示例：**

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

/* cmHandle为业务调用init接口的返回值，此处仅为示例 */
let cmHandle: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
let srcData: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
try {
  certificateManager.update(cmHandle, srcData).then((result) => {
    console.info('Succeeded in updating.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to update. Code: ${err.code}, message: ${err.message}`);
  })
} catch (error) {
  console.error(`Failed to update. Code: ${error.code}, message: ${error.message}`);
}

```

