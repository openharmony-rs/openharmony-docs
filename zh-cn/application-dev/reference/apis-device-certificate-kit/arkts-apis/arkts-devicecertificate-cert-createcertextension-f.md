# createCertExtension

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { certificateManager } from '@kit.DeviceCertificateKit';
import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
```

## createCertExtension

```TypeScript
function createCertExtension(inStream: EncodingBlob, callback: AsyncCallback<CertExtension>): void
```

创建一个证书扩展对象。使用Callback异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-cert-function createCertExtension(inStream: EncodingBlob, callback: AsyncCallback<CertExtension>): void--><!--Device-cert-function createCertExtension(inStream: EncodingBlob, callback: AsyncCallback<CertExtension>): void-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inStream | [EncodingBlob](arkts-devicecertificate-cert-encodingblob-i.md) | 是 | 表示序列化的证书扩展数据。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[CertExtension](arkts-devicecertificate-cert-certextension-i.md)&gt; | 是 | 回调函数。当创建证书扩展对象成功时，err为undefined，data为获取 到的CertExtension实例；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This operation is not supported. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';

// 证书扩展域段二进制数据，需业务自行赋值。
let extData = new Uint8Array([
  0x30, 0x40, 0x30, 0x0F, 0x06, 0x03, 0x55, 0x1D,
  0x13, 0x01, 0x01, 0xFF, 0x04, 0x05, 0x30, 0x03,
  0x01, 0x01, 0xFF, 0x30, 0x0E, 0x06, 0x03, 0x55,
  0x1D, 0x0F, 0x01, 0x01, 0xFF, 0x04, 0x04, 0x03,
  0x02, 0x01, 0xC6, 0x30, 0x1D, 0x06, 0x03, 0x55,
  0x1D, 0x0E, 0x04, 0x16, 0x04, 0x14, 0xE0, 0x8C,
  0x9B, 0xDB, 0x25, 0x49, 0xB3, 0xF1, 0x7C, 0x86,
  0xD6, 0xB2, 0x42, 0x87, 0x0B, 0xD0, 0x6B, 0xA0,
  0xD9, 0xE4
]);

let encodingBlob: cert.EncodingBlob = {
  data: extData,
  // 根据encodingData的格式进行赋值，仅支持FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_DER
};

cert.createCertExtension(encodingBlob, (error, _certExt) => {
  if (error) {
    console.error(`createCertExtension failed, errCode: ${error.code}, errMsg: ${error.message}`);
  } else {
    console.info('createCertExtension result: success.');
  }
});
```


## createCertExtension

```TypeScript
function createCertExtension(inStream: EncodingBlob): Promise<CertExtension>
```

创建一个证书扩展对象。使用Promise方式返回结果。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-cert-function createCertExtension(inStream: EncodingBlob): Promise<CertExtension>--><!--Device-cert-function createCertExtension(inStream: EncodingBlob): Promise<CertExtension>-End-->

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inStream | [EncodingBlob](arkts-devicecertificate-cert-encodingblob-i.md) | 是 | 表示序列化的证书扩展数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CertExtension](arkts-devicecertificate-cert-certextension-i.md)&gt; | Promise对象，返回创建的CertExtension实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This operation is not supported. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 证书扩展域段二进制数据，需业务自行赋值。
let extData = new Uint8Array([
  0x30, 0x40, 0x30, 0x0F, 0x06, 0x03, 0x55, 0x1D,
  0x13, 0x01, 0x01, 0xFF, 0x04, 0x05, 0x30, 0x03,
  0x01, 0x01, 0xFF, 0x30, 0x0E, 0x06, 0x03, 0x55,
  0x1D, 0x0F, 0x01, 0x01, 0xFF, 0x04, 0x04, 0x03,
  0x02, 0x01, 0xC6, 0x30, 0x1D, 0x06, 0x03, 0x55,
  0x1D, 0x0E, 0x04, 0x16, 0x04, 0x14, 0xE0, 0x8C,
  0x9B, 0xDB, 0x25, 0x49, 0xB3, 0xF1, 0x7C, 0x86,
  0xD6, 0xB2, 0x42, 0x87, 0x0B, 0xD0, 0x6B, 0xA0,
  0xD9, 0xE4
]);

let encodingBlob: cert.EncodingBlob = {
  data: extData,
  // 根据encodingData的格式进行赋值，仅支持FORMAT_DER。
  encodingFormat: cert.EncodingFormat.FORMAT_DER
};

cert.createCertExtension(encodingBlob).then(_certExt => {
  console.info('createCertExtension result: success.');
}).catch((error: BusinessError) => {
  console.error(`createCertExtension failed, errCode: ${error.code}, errMsg: ${error.message}`);
});
```

ArkTS-Sta示例：

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@ohos.base';


async function TestCreateCertExtension() {
  // 证书扩展域段二进制数据，需业务自行赋值。
  let extData = new Uint8Array([
    0x30, 0x40, 0x30, 0x0F, 0x06, 0x03, 0x55, 0x1D,
    0x13, 0x01, 0x01, 0xFF, 0x04, 0x05, 0x30, 0x03,
    0x01, 0x01, 0xFF, 0x30, 0x0E, 0x06, 0x03, 0x55,
    0x1D, 0x0F, 0x01, 0x01, 0xFF, 0x04, 0x04, 0x03,
    0x02, 0x01, 0xC6, 0x30, 0x1D, 0x06, 0x03, 0x55,
    0x1D, 0x0E, 0x04, 0x16, 0x04, 0x14, 0xE0, 0x8C,
    0x9B, 0xDB, 0x25, 0x49, 0xB3, 0xF1, 0x7C, 0x86,
    0xD6, 0xB2, 0x42, 0x87, 0x0B, 0xD0, 0x6B, 0xA0,
    0xD9, 0xE4
  ]);

  let encodingBlob: cert.EncodingBlob = {
    data: extData,
    // 根据encodingData的格式进行赋值，仅支持FORMAT_DER。
    encodingFormat: cert.EncodingFormat.FORMAT_DER
  };
  try {
    await cert.createCertExtension(encodingBlob);
    console.info('createCertExtension result: success.');
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`createCertExtension failed, ${e.code}, ${e.message}`);
  }
}
```

