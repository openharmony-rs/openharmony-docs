# createCipher

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## createCipher

```TypeScript
function createCipher(transformation: string): Cipher
```

创建加解密实例。 <br>支持的规格详见[加解密算法规格](../../../security/CryptoArchitectureKit/crypto-encryption-decryption.md)。 > **说明：** > > 1. 在对称加解密中，PKCS #5和PKCS #7的实现方式相同，即补位长度和块大小保持一致。3DES补位为8字节，AES补位为16字节。**NoPadding** > 表示不进行补位。 > 需要了解不同分组模式的区别，使用正确的参数规格。例如，ECB和CBC模式需要补位，否则需保证明文长度为块大小的整数倍。其他模式建议不补位， > 此时密文长度和明文长度一致。 > 2. 使用RSA或SM2进行非对称加解密时，需要创建两个**Cipher**对象分别进行加密和解密。对称加解密不需要如此，算法规格相同时，可以使用同 > 一个**Cipher**对象进行加解密。

**起始版本：** 23

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-cryptoFramework-function createCipher(transformation: string): Cipher--><!--Device-cryptoFramework-function createCipher(transformation: string): Cipher-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transformation | string | 是 | 待生成Cipher的算法名称（含密钥长度）、加密模式以及填充方法的组合。<br>支持的规格详见 [对称密钥加解密算法规格](../../../security/CryptoArchitectureKit/crypto-encryption-decryption.md)和 [非对称密钥加解密算法规格](../../../security/CryptoArchitectureKit/crypto-encryption-decryption.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Cipher | 返回对应算法的Cipher实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | This operation is not supported. |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | Memory operation failed. |

**示例**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

let cipherAlgName = '3DES192|ECB|PKCS7';
try {
  let cipher = cryptoFramework.createCipher(cipherAlgName);
  console.info('cipher algName: ' + cipher.algName);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`sync failed: errCode: ${e.code}, errMsg: ${e.message}`);
}
```

