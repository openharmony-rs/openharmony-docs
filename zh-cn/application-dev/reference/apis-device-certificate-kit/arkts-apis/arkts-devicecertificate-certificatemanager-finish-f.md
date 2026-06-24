# finish

## finish

```TypeScript
function finish(handle: Uint8Array, callback: AsyncCallback<CMResult>): void
```

���ǩ���Ĳ�������ǩ�����̵����һ������Ҫ�ȵ���init��update�ӿڡ�ʹ��Callback�첽�ص���

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | Uint8Array | 是 | ��ʾ������������ȵ���init������á� |
| callback | AsyncCallback&lt;CMResult&gt; | 是 | �ص���������ǩ���ɹ�ʱ��errΪnull��dataΪ<br/>[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md#CMResult)�����е�outData���ԣ���ʾǩ�����ݣ�����Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/><br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../../errorcode-universal.md#17500001-Internal) | Internal error. Possible causes: 1. IPC communication failed;<br/><br/>2. Memory operation error; 3. File operation error. Please try again. |

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


## finish

```TypeScript
function finish(handle: Uint8Array, signature: Uint8Array, callback: AsyncCallback<CMResult>): void
```

�����ǩ�Ĳ�����ʹ��Callback�첽�ص���

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | Uint8Array | 是 | ��ʾ������������ȵ���init������á� |
| signature | Uint8Array | 是 | ��ʾǩ�����ݡ� |
| callback | AsyncCallback&lt;CMResult&gt; | 是 | �ص�����������ǩ�ɹ�ʱ��errΪnull������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/><br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../../errorcode-universal.md#17500001-Internal) | Internal error. Possible causes: 1. IPC communication failed;<br/><br/>2. Memory operation error; 3. File operation error. Please try again. |

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


## finish

```TypeScript
function finish(handle: Uint8Array, signature?: Uint8Array): Promise<CMResult>
```

���ǩ������ǩ�Ĳ�����ʹ��Promise�첽�ص���

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | Uint8Array | 是 | ��ʾ������������ȵ���init������á�<br/><br/>��󳤶�Ϊ8�ֽڡ� |
| signature | Uint8Array | 否 | ��ʾ������ǩ������ǩ�����ݡ�ǩ������ʱ���贫��˲����� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CMResult&gt; | Promise����ִ��ǩ������ʱ������ǩ���Ľ��������ֵΪ[CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md#CMResult)�����е�<br/>outData���ԣ�ִ����ǩ����ʱ���޷���ֵ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/><br/>2. Incorrect parameter types; 3. Parameter verification failed. |
| [17500001](../../errorcode-universal.md#17500001-Internal) | Internal error. Possible causes: 1. IPC communication failed;<br/><br/>2. Memory operation error; 3. File operation error. Please try again. |

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

