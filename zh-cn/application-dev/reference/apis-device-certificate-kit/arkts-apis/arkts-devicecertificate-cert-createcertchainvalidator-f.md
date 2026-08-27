# createCertChainValidator

## 导入模块

```TypeScript
```

## createCertChainValidator

```TypeScript
function createCertChainValidator(algorithm: string): CertChainValidator
```

表示创建证书链校验器对象。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Security.Cert

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algorithm | string | 是 | 表示证书链校验器算法。当前仅支持输入"PKIX"。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CertChainValidator](arkts-devicecertificate-cert-certchainvalidator-i.md) | 表示证书链校验器对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes:  1. Mandatory parameters are left unspecified;  2. Incorrect parameter types;  3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This operation is not supported. |
| [19020001](../errorcode-cert.md#19020001-内存错误) | Memory malloc failed. |
| [19020002](../errorcode-cert.md#19020002-运行时错误) | Runtime error. Possible causes:  1. Memory copy failed;  2. A null pointer occurs inside the system;  3. Failed to obtain the native object or convert parameters. |
| [19030001](../errorcode-cert.md#19030001-调用三方算法库api出错) | Crypto operation error. |

**示例**

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  cert.createCertChainValidator('PKIX');
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`createCertChainValidator failed, errCode: ${e.code}, errMsg: ${e.message}`);
}
```
