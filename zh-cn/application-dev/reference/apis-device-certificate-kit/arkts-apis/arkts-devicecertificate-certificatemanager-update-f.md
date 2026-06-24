# update

## update

```TypeScript
function update(handle: Uint8Array, data: Uint8Array, callback: AsyncCallback<void>): void
```

ǩ������ǩ�����ݸ��²�������Ҫ��init����֮����ã����ڴ����ǩ������ǩ�����ݡ�ʹ��Callback�첽�ص���

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | Uint8Array | 是 | ��ʾ������������ȵ���init������� |
| data | Uint8Array | 是 | ��ʾ��ǩ������ǩ�����ݡ� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص���������ǩ������ǩ�����ݸ��²����ɹ�ʱ��errΪnull������Ϊ������� |

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


## update

```TypeScript
function update(handle: Uint8Array, data: Uint8Array): Promise<void>
```

ǩ������ǩ�����ݸ��²�����ʹ��Promise�첽�ص���

**起始版本：** 11

**需要权限：** ohos.permission.ACCESS_CERT_MANAGER

**系统能力：** SystemCapability.Security.CertificateManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handle | Uint8Array | 是 | ��ʾ������������ȵ���init������� |
| data | Uint8Array | 是 | ��ʾ��ǩ������ǩ�����ݡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ���� |

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

