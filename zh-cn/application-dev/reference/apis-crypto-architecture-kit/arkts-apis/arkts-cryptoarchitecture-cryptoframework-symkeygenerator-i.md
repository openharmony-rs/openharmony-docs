# SymKeyGenerator

对称密钥生成器。

在使用该类的方法前，先使用[createSymKeyGenerator](arkts-cryptoarchitecture-cryptoframework-createsymkeygenerator-f.md#createsymkeygenerator-1)构建SymKeyGenerator实例。

**起始版本：** 9

<!--Device-cryptoFramework-interface SymKeyGenerator--><!--Device-cryptoFramework-interface SymKeyGenerator-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.SymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

## 导入模块

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

<a id="convertkey"></a>
## convertKey

```TypeScript
convertKey(key: DataBlob, callback: AsyncCallback<SymKey>): void
```

将指定数据转换为对称密钥。使用callback异步回调。

必须在使用[createSymKeyGenerator](arkts-cryptoarchitecture-cryptoframework-createsymkeygenerator-f.md#createsymkeygenerator-1)创建对称密钥生成器后，才能使用本函数。

> **说明：**  
>  
> 对于HMAC算法的对称密钥，如果已经在创建对称密钥生成器时指定了具体哈希算法（如指定"HMAC|SHA256"），则需要传入与哈希长度一致的二进制  
> 密钥数据（如传入SHA256对应256位的密钥数据）。

如果在创建对称密钥生成器时没有指定具体哈希算法，如仅指定"HMAC"，则支持传入长度在[1,4096]范围内（单位为bytes）的任意二进制密钥数据。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SymKeyGenerator-convertKey(key: DataBlob, callback: AsyncCallback<SymKey>): void--><!--Device-SymKeyGenerator-convertKey(key: DataBlob, callback: AsyncCallback<SymKey>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.SymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 是 | 指定的对称密钥材料。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;SymKey&gt; | 是 | 回调函数。当生成对称密钥成功时，err为undefined，data为获取到的SymKey；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function genKeyMaterialBlob(): cryptoFramework.DataBlob {
  let arr = [
    0xba, 0x3d, 0xc2, 0x71, 0x21, 0x1e, 0x30, 0x56,
    0xad, 0x47, 0xfc, 0x5a, 0x46, 0x39, 0xee, 0x7c,
    0xba, 0x3b, 0xc2, 0x71, 0xab, 0xa0, 0x30, 0x72]; // keyLen = 192 (24 bytes)
  let keyMaterial = new Uint8Array(arr);
  return { data: keyMaterial };
}

function testConvertKey() {
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('3DES192');
  let keyMaterialBlob = genKeyMaterialBlob();
  symKeyGenerator.convertKey(keyMaterialBlob, (err, symKey) => {
    console.info('Convert symKey result: success, algName: ' + symKey.algName);
  });
}

```

<a id="convertkey-1"></a>
## convertKey

```TypeScript
convertKey(key: DataBlob): Promise<SymKey>
```

将指定数据转换为对称密钥。使用Promise异步回调。

在使用本函数前，需先通过[createSymKeyGenerator](arkts-cryptoarchitecture-cryptoframework-createsymkeygenerator-f.md#createsymkeygenerator-1)创建对称密钥生成器。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SymKeyGenerator-convertKey(key: DataBlob): Promise<SymKey>--><!--Device-SymKeyGenerator-convertKey(key: DataBlob): Promise<SymKey>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.SymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 是 | 指定的密钥材料数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SymKey&gt; | Promise对象，返回对称密钥SymKey。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

function genKeyMaterialBlob(): cryptoFramework.DataBlob {
  let arr = [
    0xba, 0x3d, 0xc2, 0x71, 0x21, 0x1e, 0x30, 0x56,
    0xad, 0x47, 0xfc, 0x5a, 0x46, 0x39, 0xee, 0x7c,
    0xba, 0x3b, 0xc2, 0x71, 0xab, 0xa0, 0x30, 0x72]; // keyLen = 192 (24 bytes)
  let keyMaterial = new Uint8Array(arr);
  return { data: keyMaterial };
}

function testConvertKey() {
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('3DES192');
  let keyMaterialBlob = genKeyMaterialBlob();
  symKeyGenerator.convertKey(keyMaterialBlob)
    .then(symKey => {
      console.info('Convert symKey result: success, algName：' + symKey.algName);
    }).catch((error: BusinessError) => {
      console.error(`Convert symKey failed, ${error.code}, ${error.message}`);
    });
}

```

<a id="convertkeysync"></a>
## convertKeySync

```TypeScript
convertKeySync(key: DataBlob): SymKey
```

将指定数据转换为对称密钥。

必须在使用[createSymKeyGenerator](arkts-cryptoarchitecture-cryptoframework-createsymkeygenerator-f.md#createsymkeygenerator-1)创建对称密钥生成器后，才能使用本函数。

> **说明：**  
>  
> 对于HMAC算法的对称密钥，如果在创建对称密钥生成器时指定了具体哈希算法（如"HMAC|SHA256"），则需要传入与哈希长度一致的二进制密钥数据  
>（如传入SHA256对应的256位密钥数据）。如果在创建对称密钥生成器时未指定具体哈希算法，如仅指定"HMAC"，则支持传入长度在1到4096字节范围  
> 内的任意二进制密钥数据。

<br><br>**说明：**<br>建议优先使用异步API{@link convertKey}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SymKeyGenerator-convertKeySync(key: DataBlob): SymKey--><!--Device-SymKeyGenerator-convertKeySync(key: DataBlob): SymKey-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.SymKey

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | [DataBlob](../../apis-device-certificate-kit/arkts-apis/arkts-devicecertificate-cert-datablob-i.md) | 是 | 指定的对称密钥材料。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SymKey](arkts-cryptoarchitecture-cryptoframework-symkey-i.md) | 对称密钥。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

function testConvertKeySync() {
  // 对称密钥长度为64字节，512比特。
  let keyMessage = '87654321abcdefgh87654321abcdefgh87654321abcdefgh87654321abcdefgh';
  let keyBlob: cryptoFramework.DataBlob = {
    data : new Uint8Array(buffer.from(keyMessage, 'utf-8').buffer)
  }
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('HMAC');
  let key = symKeyGenerator.convertKeySync(keyBlob);
  let encodedKey = key.getEncoded();
  console.info('key encoded data：' + encodedKey.data);
}

```

<a id="generatesymkey"></a>
## generateSymKey

```TypeScript
generateSymKey(callback: AsyncCallback<SymKey>): void
```

获取对称密钥生成器随机生成的密钥。使用callback异步回调。

必须在使用[createSymKeyGenerator](arkts-cryptoarchitecture-cryptoframework-createsymkeygenerator-f.md#createsymkeygenerator-1)创建对称密钥生成器后，才能使用本函数。

目前支持使用OpenSSL的RAND_priv_bytes()作为底层能力生成随机密钥。

> **说明：**  
>  
> 对于HMAC算法的对称密钥，如果在创建对称密钥生成器时指定了具体哈希算法（如"HMAC|SHA256"），则会随机生成与哈希长度一致的二进制密钥  
> 数据（如256位的密钥数据）。如果未指定具体哈希算法，如仅指定"HMAC"，则不支持随机生成对称密钥数据，可通过  
> [convertKey](arkts-cryptoarchitecture-cryptoframework-symkeygenerator-i.md#convertkey-1)  
> 方式生成对称密钥数据。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SymKeyGenerator-generateSymKey(callback: AsyncCallback<SymKey>): void--><!--Device-SymKeyGenerator-generateSymKey(callback: AsyncCallback<SymKey>): void-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.SymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;SymKey&gt; | 是 | 回调函数。当生成对称密钥成功时，err为undefined，data为获取到的SymKey；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620004](../errorcode-crypto-framework.md#17620004-无效的函数调用) | 无效的函数调用。<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

let symKeyGenerator = cryptoFramework.createSymKeyGenerator('3DES192');
  symKeyGenerator.generateSymKey((err, symKey) => {
    console.info('Generate symKey result: success, algName：' + symKey.algName);
  });

```

<a id="generatesymkey-1"></a>
## generateSymKey

```TypeScript
generateSymKey(): Promise<SymKey>
```

获取该对称密钥生成器随机生成的密钥。使用Promise异步回调。

必须在使用[createSymKeyGenerator](arkts-cryptoarchitecture-cryptoframework-createsymkeygenerator-f.md#createsymkeygenerator-1)创建对称密钥生成器后，才能使用本函数。

目前支持使用OpenSSL的RAND_priv_bytes()作为底层能力生成随机密钥。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SymKeyGenerator-generateSymKey(): Promise<SymKey>--><!--Device-SymKeyGenerator-generateSymKey(): Promise<SymKey>-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.SymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SymKey&gt; | Promise对象，返回对称密钥SymKey。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620004](../errorcode-crypto-framework.md#17620004-无效的函数调用) | 无效的函数调用。<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES128');
  symKeyGenerator.generateSymKey()
    .then(symKey => {
      console.info('Generate symKey result: success, algName: ' + symKey.algName);
    }).catch((error: BusinessError) => {
      console.error(`Generate symKey failed, ${error.code}, ${error.message}`);
    });

```

<a id="generatesymkeysync"></a>
## generateSymKeySync

```TypeScript
generateSymKeySync(): SymKey
```

同步获取对称密钥生成器随机生成的密钥。

必须在使用[createSymKeyGenerator](arkts-cryptoarchitecture-cryptoframework-createsymkeygenerator-f.md#createsymkeygenerator-1)创建对称密钥生成器后，才能使用本函数。

目前支持使用OpenSSL的RAND_priv_bytes()作为底层能力生成随机密钥。

> **说明：**  
>  
> 对于HMAC算法的对称密钥，如果已经在创建对称密钥生成器时指定了具体哈希算法（如指定"HMAC|SHA256"），则会随机生成与哈希长度一致的  
> 二进制密钥数据（如指定"HMAC|SHA256"会随机生成256位的密钥数据）。

如果在创建对称密钥生成器时没有指定具体哈希算法，如仅指定"HMAC"，则不支持随机生成对称密钥数据，可通过[convertKeySync](arkts-cryptoarchitecture-cryptoframework-symkeygenerator-i.md#convertkeysync-1)方式生成对称密钥数据。

<br><br>**说明：**<br>建议优先使用异步API{@link generateSymKey}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SymKeyGenerator-generateSymKeySync(): SymKey--><!--Device-SymKeyGenerator-generateSymKeySync(): SymKey-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Key.SymKey

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SymKey](arkts-cryptoarchitecture-cryptoframework-symkey-i.md) | 返回对称密钥SymKey。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620004](../errorcode-crypto-framework.md#17620004-无效的函数调用) | 无效的函数调用。<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function testGenerateSymKeySync() {
  // 创建SymKeyGenerator实例。
  let symKeyGenerator = cryptoFramework.createSymKeyGenerator('AES256');
  // 使用密钥生成器随机生成对称密钥。
  let key = symKeyGenerator.generateSymKeySync();
  let encodedKey = key.getEncoded();
  console.info('key hex:' + encodedKey.data);
}

```

## algName

```TypeScript
readonly algName: string
```

对称密钥生成器指定的算法名称。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SymKeyGenerator-readonly algName: string--><!--Device-SymKeyGenerator-readonly algName: string-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Key.SymKey
- API版本9-11：SystemCapability.Security.CryptoFramework

