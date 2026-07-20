# finish

## 导入模块

```TypeScript
import { certificateManager } from '@kit.DeviceCertificateKit';
```

<a id="finish"></a>
## finish

```TypeScript
function finish(handle: Uint8Array, callback: AsyncCallback<CMResult>): void
```

完成签名的操作，是签名流程的最后一步，需要先调用init和update接口。使用Callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function finish(handle: Uint8Array, callback: AsyncCallback<CMResult>): void--><!--Device-certificateManager-function finish(handle: Uint8Array, callback: AsyncCallback<CMResult>): void-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | Uint8Array | 是 | 表示操作句柄，需先调用init方法获得。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;CMResult&gt; | 是 | 回调函数。当签名成功时，err为null，data为[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)对象中的outData属性，表示签名数据；否则为错误对象。 |

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
  certificateManager.finish(cmHandle, (err, cmResult) => {
    if (err != null) {
      console.error(`Failed to finish. Code: ${err.code}, message: ${err.message}`);
    } else {
      if (cmResult?.outData != undefined) {
        let signRes = cmResult?.outData;
        console.info('Succeeded in finishing.');
      } else {
        console.info('The result of finishing is undefined.');
      }
    }
  });
} catch(error) {
  console.error(`Failed to finish. Code: ${error.code}, message: ${error.message}`);
}

```


<a id="finish-1"></a>
## finish

```TypeScript
function finish(handle: Uint8Array, signature: Uint8Array, callback: AsyncCallback<CMResult>): void
```

完成验签的操作，是验签流程的最后一步，需要先调用init和update接口。使用Callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function finish(handle: Uint8Array, signature: Uint8Array, callback: AsyncCallback<CMResult>): void--><!--Device-certificateManager-function finish(handle: Uint8Array, signature: Uint8Array, callback: AsyncCallback<CMResult>): void-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | Uint8Array | 是 | 表示操作句柄，需先调用init方法获得。 |
| signature | Uint8Array | 是 | 表示签名数据。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;CMResult&gt; | 是 | 回调函数。当验签成功时，err为null；否则为错误对象。 |

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
let signRes: Uint8Array = new Uint8Array([
  0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
]);
try {
  certificateManager.finish(cmHandle, signRes, (err, cmResult) => {
    if (err != null) {
      console.error(`Failed to finish. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in finishing.');
    }
  });
} catch(error) {
  console.error(`Failed to finish. Code: ${error.code}, message: ${error.message}`);
}

```


<a id="finish-2"></a>
## finish

```TypeScript
function finish(handle: Uint8Array, signature?: Uint8Array): Promise<CMResult>
```

完成签名、验签的操作。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

<!--Device-certificateManager-function finish(handle: Uint8Array, signature?: Uint8Array): Promise<CMResult>--><!--Device-certificateManager-function finish(handle: Uint8Array, signature?: Uint8Array): Promise<CMResult>-End-->

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | Uint8Array | 是 | 表示操作句柄，需先调用init方法获得。<br>最大长度为8字节。 |
| signature | Uint8Array | 否 | 表示用于验签操作的签名数据。签名操作时无需传入此参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CMResult&gt; | Promise对象。执行签名操作时，返回签名的结果，返回值为[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md)对象中的outData属性；执行验签操作时，无返回值。 |

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
  /* 签名的finish操作 */
  certificateManager.finish(cmHandle).then((cmResult) => {
    if (cmResult?.outData != undefined) {
      let signRes1 = cmResult?.outData;
      console.info('Succeeded in finishing signature.');
    } else {
      console.info('The result of signature is undefined.');
    }
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to finish signature. Code: ${err.code}, message: ${err.message}`);
  })

  /* 签名的结果 */
  let signRes: Uint8Array = new Uint8Array([
    0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08
  ]);
  /* 验签的finish操作 */
  certificateManager.finish(cmHandle, signRes).then((cmResult) => {
    console.info('Succeeded in finishing verification.');
  }).catch((error: Error) => {
    let err = error as BusinessError;
    console.error(`Failed to finish verification. Code: ${err.code}, message: ${err.message}`);
  })
} catch(error) {
  console.error(`Failed to finish. Code: ${error.code}, message: ${error.message}`);
}

```

