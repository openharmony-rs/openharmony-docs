# Key

密钥（父类），在运行密码算法（如加解密）时需要提前生成其子类对象，并传入[Cipher](arkts-cryptoarchitecture-cryptoframework-cipher-i.md)实例的[init()](arkts-cryptoarchitecture-cryptoframework-cipher-i.md#init-1)方法。

密钥通过子类密钥生成器来生成，详见子类描述。具体子类有：[SymKey](arkts-cryptoarchitecture-cryptoframework-symkey-i.md)、[PubKey](arkts-cryptoarchitecture-cryptoframework-pubkey-i.md)、[PriKey](arkts-cryptoarchitecture-cryptoframework-prikey-i.md)。

**起始版本：** 9

<!--Device-cryptoFramework-interface Key--><!--Device-cryptoFramework-interface Key-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key
- API版本9-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

<a id="getencoded"></a>
## getEncoded

```TypeScript
getEncoded(): DataBlob
```

同步方法，获取密钥数据的字节流。密钥可以是对称密钥、公钥或私钥。公钥格式需符合ASN.1语法、X.509规范和DER编码；私钥格式需符合ASN.1语法、PKCS#8规范和DER编码。

> **说明：**  
>  
> RSA算法使用密钥参数生成私钥时，私钥对象支持getEncoded。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Key-getEncoded(): DataBlob--><!--Device-Key-getEncoded(): DataBlob-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key
- API版本9-11：SystemCapability.Security.CryptoFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 获取的密钥数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该操作不支持。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

async function testGenerateAesKey() {
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES256');
  let symKey = await symKeyGenerator.generateSymKey();
  let encodedKey = symKey.getEncoded();
  console.info('key hex: ' + encodedKey.data);
}

```

<a id="getkeysize"></a>
## getKeySize

```TypeScript
getKeySize(): number
```

以同步方式获取密钥的比特长度。密钥可以是对称密钥、公钥或私钥。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-Key-getKeySize(): int--><!--Device-Key-getKeySize(): int-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取密钥的比特长度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

async function testGenerateAesKey() {
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES256');
  let symKey = await symKeyGenerator.generateSymKey();
  let symKeyLen = symKey.getKeySize();
  console.info('keysize is: ' + symKeyLen);
}

```

## algName

```TypeScript
readonly algName: string
```

密钥对应的算法名（如果是对称密钥，则含密钥长度，否则不含密钥长度）。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Key-readonly algName: string--><!--Device-Key-readonly algName: string-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key
- API版本9-11：SystemCapability.Security.CryptoFramework

## format

```TypeScript
readonly format: string
```

密钥的格式。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Key-readonly format: string--><!--Device-Key-readonly format: string-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key
- API版本9-11：SystemCapability.Security.CryptoFramework

