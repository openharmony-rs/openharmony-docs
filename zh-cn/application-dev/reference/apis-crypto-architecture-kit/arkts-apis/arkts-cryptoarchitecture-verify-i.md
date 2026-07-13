# Verify

Verify类，使用Verify方法之前需要创建该类的实例进行操作，通过
[createVerify(algName: string): Verify](arkts-cryptoarchitecture-createverify-f.md#createverify-1)方法构造此实例。按序调用本类中的init、update、
verify方法完成签名操作。验签操作的示例代码详见
[签名验签开发指导](../../../../security/CryptoArchitectureKit/crypto-rsa-sign-sig-verify-pkcs1.md)。

Verify类不支持重复初始化，当业务方需要使用新密钥验签时，需要重新创建新Verify对象并调用init初始化。

业务方使用时，在createVerify时确定验签的模式，调用init接口设置密钥。

当被签名的消息较短时，可在init初始化后，（无需update）直接调用verify接口传入被签名的消息和签名（signatureData）进行验签。

当被签名的消息较长时，可通过update接口分段传入被签名的消息，最后调用verify接口对消息全文进行验签。verify接口的data入参在API 10之前只
支持DataBlob， API 10之后增加支持null。业务方可在循环中调用update接口，循环结束后调用verify传入签名（signatureData）进行验签。

当使用DSA算法进行验签，并设置了摘要算法为NoHash时，则不支持update操作，update接口会返回错误码ERR_CRYPTO_OPERATION。

**起始版本：** 9

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework

## getVerifySpec

```TypeScript
getVerifySpec(itemType: SignSpecItem): string | number
```

获取验签参数。当前只支持RSA算法。

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemType | SignSpecItem | 是 | 用于指定需要获取的验签参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回获取的参数值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该操作不支持。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function testGetVerifySpec() {
  let verifier = cryptoFramework.createVerify('RSA2048|PSS|SHA256|MGF1_SHA256');
  let setN = 20;
  verifier.setVerifySpec(cryptoFramework.SignSpecItem.PSS_SALT_LEN_NUM, setN);
  verifier.getVerifySpec(cryptoFramework.SignSpecItem.PSS_SALT_LEN_NUM);
}

```

## init

```TypeScript
init(pubKey: PubKey, callback: AsyncCallback<void>): void
```

传入公钥初始化Verify对象。使用callback异步回调。init、update、verify为三段式接口，需要成组使用。其中init和verify必选，update
可选。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pubKey | PubKey | 是 | 公钥对象，用于Verify的初始化。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当验签初始化成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 密钥类型不正确。<br>**适用版本：** 26.0.0+ |

## init

```TypeScript
init(pubKey: PubKey): Promise<void>
```

传入公钥初始化Verify对象。使用Promise异步回调。init、update、verify为三段式接口，需要成组使用。其中init和verify必选，update
可选。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pubKey | PubKey | 是 | 公钥对象，用于Verify的初始化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 密钥类型不正确。<br>**适用版本：** 26.0.0+ |

## initSync

```TypeScript
initSync(pubKey: PubKey): void
```

传入公钥初始化Verify对象，通过同步方式获取结果。initSync、updateSync、verifySync为三段式接口，需要成组使用。其中initSync和
verifySync必选，updateSync可选。

<br><br>**说明：**
<br>建议优先使用异步API{@link init}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。
因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pubKey | PubKey | 是 | 公钥对象，用于Verify的初始化。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因：<br>1. 密钥类型不正确。<br>**适用版本：** 26.0.0+ |

## recover

```TypeScript
recover(signatureData: DataBlob): Promise<DataBlob | null>
```

对数据进行签名恢复原始数据。使用Promise异步回调。

> **说明：**
>
> - 目前仅RSA支持。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| signatureData | DataBlob | 是 | 签名数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DataBlob \| null&gt; | Promise对象，返回从签名中恢复的原始数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620004](../errorcode-crypto-framework.md#17620004-无效的函数调用) | 无效的函数调用。<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function genKeyPairByData(pubKeyData: Uint8Array, priKeyData: Uint8Array) {
  let pubKeyBlob: cryptoFramework.DataBlob = { data: pubKeyData };
  let priKeyBlob: cryptoFramework.DataBlob = { data: priKeyData };
  let rsaGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
  let keyPair = await rsaGenerator.convertKey(pubKeyBlob, priKeyBlob);
  console.info('convertKey result: success.');
  return keyPair;
}

async function recoverByPromise() {
  // 根据密钥数据生成的密钥和输入的验签数据，这部分代码Verify与Sign中保持一致，保证验签通过。
  let pkData =
    new Uint8Array([48, 129, 159, 48, 13, 6, 9, 42, 134, 72, 134, 247, 13, 1, 1, 1, 5, 0, 3, 129, 141, 0, 48, 129, 137,
      2, 129, 129, 0, 214, 179, 23, 198, 183, 139, 148, 8, 173, 74, 56, 160, 15, 248, 244, 166, 209, 250, 142, 74, 216,
      58, 117, 215, 178, 247, 254, 39, 180, 227, 85, 201, 59, 133, 209, 221, 26, 9, 116, 31, 172, 151, 252, 185, 123,
      20, 25, 7, 92, 129, 5, 196, 239, 214, 126, 254, 154, 188, 239, 144, 161, 171, 65, 42, 31, 214, 93, 115, 247, 69,
      94, 143, 54, 51, 25, 49, 146, 204, 205, 165, 20, 120, 35, 184, 190, 65, 106, 12, 214, 176, 57, 125, 235, 51, 88,
      135, 76, 73, 109, 112, 147, 138, 198, 252, 5, 20, 245, 51, 7, 32, 108, 89, 125, 204, 50, 189, 88, 254, 255, 146,
      244, 244, 149, 79, 54, 216, 45, 89, 2, 3, 1, 0, 1]);
  let skData =
    new Uint8Array([48, 130, 2, 120, 2, 1, 0, 48, 13, 6, 9, 42, 134, 72, 134, 247, 13, 1, 1, 1, 5, 0, 4, 130, 2, 98, 48,
      130, 2, 94, 2, 1, 0, 2, 129, 129, 0, 214, 179, 23, 198, 183, 139, 148, 8, 173, 74, 56, 160, 15, 248, 244, 166,
      209, 250, 142, 74, 216, 58, 117, 215, 178, 247, 254, 39, 180, 227, 85, 201, 59, 133, 209, 221, 26, 9, 116, 31,
      172, 151, 252, 185, 123, 20, 25, 7, 92, 129, 5, 196, 239, 214, 126, 254, 154, 188, 239, 144, 161, 171, 65, 42, 31,
      214, 93, 115, 247, 69, 94, 143, 54, 51, 25, 49, 146, 204, 205, 165, 20, 120, 35, 184, 190, 65, 106, 12, 214, 176,
      57, 125, 235, 51, 88, 135, 76, 73, 109, 112, 147, 138, 198, 252, 5, 20, 245, 51, 7, 32, 108, 89, 125, 204, 50,
      189, 88, 254, 255, 146, 244, 244, 149, 79, 54, 216, 45, 89, 2, 3, 1, 0, 1, 2, 129, 129, 0, 152, 111, 145, 203, 10,
      88, 116, 163, 112, 126, 9, 20, 68, 34, 235, 121, 98, 14, 182, 102, 151, 125, 114, 91, 210, 122, 215, 29, 212, 5,
      176, 203, 238, 146, 5, 190, 41, 21, 91, 56, 125, 239, 111, 133, 53, 200, 192, 56, 132, 202, 42, 145, 120, 3, 224,
      40, 223, 46, 148, 29, 41, 92, 17, 40, 12, 72, 165, 69, 192, 211, 142, 233, 81, 202, 177, 235, 156, 27, 179, 48,
      18, 85, 154, 101, 193, 45, 218, 91, 24, 143, 196, 248, 16, 83, 177, 198, 136, 77, 111, 134, 60, 219, 95, 246, 23,
      5, 45, 14, 83, 29, 137, 248, 159, 28, 132, 142, 205, 99, 226, 213, 84, 232, 57, 130, 156, 81, 191, 237, 2, 65, 0,
      255, 158, 212, 13, 43, 132, 244, 135, 148, 161, 232, 219, 20, 81, 196, 102, 103, 44, 110, 71, 100, 62, 73, 200,
      32, 138, 114, 209, 171, 150, 179, 92, 198, 5, 190, 218, 79, 227, 227, 37, 32, 57, 159, 252, 107, 211, 139, 198,
      202, 248, 137, 143, 186, 205, 106, 81, 85, 207, 134, 148, 110, 204, 243, 27, 2, 65, 0, 215, 4, 181, 121, 57, 224,
      170, 168, 183, 159, 152, 8, 74, 233, 80, 244, 146, 81, 48, 159, 194, 199, 36, 187, 6, 181, 182, 223, 115, 133,
      151, 171, 78, 219, 90, 161, 248, 69, 6, 207, 173, 3, 81, 161, 2, 60, 238, 204, 177, 12, 138, 17, 220, 179, 71,
      113, 200, 248, 159, 153, 252, 150, 180, 155, 2, 65, 0, 190, 202, 185, 211, 170, 171, 238, 40, 84, 84, 21, 13, 144,
      57, 7, 178, 183, 71, 126, 120, 98, 229, 235, 4, 40, 229, 173, 149, 185, 209, 29, 199, 29, 54, 164, 161, 38, 8, 30,
      62, 83, 179, 47, 42, 165, 0, 156, 207, 160, 39, 169, 229, 81, 180, 136, 170, 116, 182, 20, 233, 45, 90, 100, 9, 2,
      65, 0, 152, 255, 47, 198, 15, 201, 238, 133, 89, 11, 133, 153, 184, 252, 37, 239, 177, 65, 118, 80, 231, 190, 222,
      66, 250, 118, 72, 166, 221, 67, 156, 245, 119, 138, 28, 6, 142, 107, 71, 122, 116, 200, 156, 199, 237, 152, 191,
      239, 4, 184, 64, 114, 143, 81, 62, 48, 23, 233, 217, 95, 47, 221, 104, 171, 2, 64, 30, 219, 1, 230, 241, 70, 246,
      243, 121, 174, 67, 66, 11, 99, 202, 17, 52, 234, 78, 29, 3, 57, 51, 123, 149, 86, 64, 192, 73, 199, 108, 101, 55,
      232, 41, 114, 153, 237, 253, 52, 205, 148, 45, 86, 186, 241, 182, 183, 42, 77, 252, 195, 29, 158, 173, 3, 182,
      207, 254, 61, 71, 184, 167, 184]);
  let keyPair = await genKeyPairByData(pkData, skData);
  // 该数据取自Sign中的signData.data。
  let signMessageBlob: cryptoFramework.DataBlob = {
    data: new Uint8Array([9, 68, 164, 161, 230, 155, 255, 153, 10, 12, 14, 22, 146, 115, 209, 167, 223, 133, 89, 173,
      50, 249, 176, 104, 10, 251, 219, 104, 117, 196, 105, 65, 249, 139, 119, 41, 15, 171, 191, 11, 177, 177, 1, 119,
      130, 142, 87, 183, 32, 220, 226, 28, 38, 73, 222, 172, 153, 26, 87, 58, 188, 42, 150, 67, 94, 214, 147, 64, 202,
      87, 155, 125, 254, 112, 95, 176, 255, 207, 106, 43, 228, 153, 131, 240, 120, 88, 253, 179, 207, 207, 110, 223,
      173, 15, 113, 11, 183, 122, 237, 205, 206, 123, 246, 33, 167, 169, 251, 237, 199, 26, 220, 152, 190, 117, 131, 74,
      232, 50, 39, 172, 232, 178, 112, 73, 251, 235, 131, 209])
  };
  let verifier = cryptoFramework.createVerify('RSA1024|PKCS1|SHA256|Recover');
  await verifier.init(keyPair.pubKey);
  try {
    let rawSignData = await verifier.recover(signMessageBlob);
    if (rawSignData != null) {
      console.info('[Promise]: recover result: ' + rawSignData.data);
    } else {
      console.error('[Promise]: get verify recover result: fail.');
    }
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`promise failed: errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

```

## recoverSync

```TypeScript
recoverSync(signatureData: DataBlob): DataBlob | null
```

对数据进行签名恢复原始数据。

> **说明：**
>
> - 目前仅RSA支持。

<br><br>**说明：**
<br>建议优先使用异步API{@link recover}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。
因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| signatureData | DataBlob | 是 | 签名数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 恢复的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620004](../errorcode-crypto-framework.md#17620004-无效的函数调用) | 无效的函数调用。<br>**适用版本：** 26.0.0+ |

## setVerifySpec

```TypeScript
setVerifySpec(itemType: SignSpecItem, itemValue: number): void
```

设置验签参数。常用的验签参数直接通过[createVerify](arkts-cryptoarchitecture-createverify-f.md#createverify-1) 来指定，剩余参数通过本接口指定。

支持RSA算法和SM2算法，从API version 11开始，支持SM2算法设置签名验证参数。

验签的参数应当与签名的参数保持一致。

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemType | SignSpecItem | 是 | 用于指定需要设置的验签参数。 |
| itemValue | number | 是 | 用于指定验签参数的具体值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该操作不支持。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function testSetVerifySpec() {
  let verifier = cryptoFramework.createVerify('RSA2048|PSS|SHA256|MGF1_SHA256');
  let setN = 20;
  verifier.setVerifySpec(cryptoFramework.SignSpecItem.PSS_SALT_LEN_NUM, setN);
}

```

## setVerifySpec

```TypeScript
setVerifySpec(itemType: SignSpecItem, itemValue: number | Uint8Array): void
```

设置签名验证参数。

当前仅支持RSA算法中的PSS_SALT_LEN和SM2签名验证中的USER_ID。

验签的参数应当与签名的参数保持一致。

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemType | SignSpecItem | 是 | 用于指定需要设置的验签参数类型。 |
| itemValue | number \| Uint8Array | 是 | 指定验签参数的具体值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该操作不支持。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。<br>**适用版本：** 26.0.0+ |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |
| [17620004](../errorcode-crypto-framework.md#17620004-无效的函数调用) | 无效的函数调用。<br>**适用版本：** 26.0.0+ |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

## setVerifySpec

```TypeScript
setVerifySpec(itemType: SignSpecItem, itemValue: number | Uint8Array | boolean): void
```

设置签名验证参数。

当前仅支持RSA算法中的PSS_SALT_LEN，SM2算法中的USER_ID以及ML-DSA算法中的ML_DSA_DETERMINISTIC、ML_DSA_MU和ML_DSA_CONTEXT。

验签的参数应当与签名的参数保持一致。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| itemType | SignSpecItem | 是 | 用于指定需要设置的验签参数类型。 |
| itemValue | number \| Uint8Array \| boolean | 是 | 指定验签参数的具体值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | 该操作不支持。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。 |
| [17620004](../errorcode-crypto-framework.md#17620004-无效的函数调用) | 无效的函数调用。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |

**示例：**

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';

function testSetVerifySpec() {
  let verifier = cryptoFramework.createVerify('ML-DSA');
  verifier.setVerifySpec(cryptoFramework.SignSpecItem.ML_DSA_MU_BOOL, false);
}

```

## update

```TypeScript
update(data: DataBlob, callback: AsyncCallback<void>): void
```

追加待验签数据，使用callback异步回调完成更新。

必须在对[Verify](arkts-cryptoarchitecture-verify-i.md)实例使用[init](arkts-cryptoarchitecture-verify-i.md#init-1)或
[initSync](arkts-cryptoarchitecture-verify-i.md#initsync-1)初始化后，才能使用本函数。

> **说明：**
>
> 根据数据量，可以不调用update（即[init](arkts-cryptoarchitecture-verify-i.md#init-1)
> 完成后直接调用
> [verify](arkts-cryptoarchitecture-verify-i.md#verify-2)
> ）或多次调用update。
>
> 算法库目前没有对update（单次或累计）的数据量设置大小限制，建议对于大数据量的验签操作，采用多次update的方式传入数据，避免一次性申请
> 过大内存。
>
> 验签使用多次update操作的示例代码详见
> [使用RSA密钥对分段签名验签](../../../../security/CryptoArchitectureKit/crypto-rsa-sign-sig-verify-pkcs1-by-segment.md)
> ，其余算法操作类似。
>
> OnlyVerify模式下，不支持update操作，直接使用verify传入数据即可。
>
> 当使用DSA算法进行验签，并设置了摘要算法为NoHash时，则不支持update操作，update接口会返回错误码ERR_CRYPTO_OPERATION。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | DataBlob | 是 | 传入的消息。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当验签更新成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620004](../errorcode-crypto-framework.md#17620004-无效的函数调用) | 无效的函数调用。<br>**适用版本：** 26.0.0+ |

## update

```TypeScript
update(data: DataBlob): Promise<void>
```

追加待验签数据，使用Promise异步回调完成更新。

必须在对[Verify](arkts-cryptoarchitecture-verify-i.md)实例使用[init()](arkts-cryptoarchitecture-verify-i.md#init-1)初始化后，才能使
用本函数。

> **说明：**
>
> 根据数据量，可以不调用update（即[init](arkts-cryptoarchitecture-verify-i.md#init-1)完成后直接调用
> [verify](arkts-cryptoarchitecture-verify-i.md#verify-4)）或多次调用update。
>
> 算法库目前没有对update（单次或累计）的数据量设置大小限制，建议对于大数据量的验签操作，采用多次update的方式传入数据，避免一次性申请
> 过大内存。
>
> 验签使用多次update操作的示例代码详见
> [使用RSA密钥对分段签名验签](../../../../security/CryptoArchitectureKit/crypto-rsa-sign-sig-verify-pkcs1-by-segment.md)
> ，其余算法操作类似。
>
> OnlyVerify模式下，不支持update操作，直接使用verify传入数据即可。
>
> 当使用DSA算法进行验签，并设置了摘要算法为NoHash时，则不支持update操作，update接口会返回错误码ERR_CRYPTO_OPERATION。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | DataBlob | 是 | 传入的消息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620004](../errorcode-crypto-framework.md#17620004-无效的函数调用) | 无效的函数调用。<br>**适用版本：** 26.0.0+ |

## updateSync

```TypeScript
updateSync(data: DataBlob): void
```

追加待验签数据，通过同步方式完成更新。

必须在对[Verify](arkts-cryptoarchitecture-verify-i.md)实例使用[initSync()](arkts-cryptoarchitecture-verify-i.md#initsync-1)初始化后，才
能使用本函数。

> **说明：**
>
> 根据数据量，可以不调用updateSync（即[initSync](arkts-cryptoarchitecture-verify-i.md#initsync-1)完成后直接调用
> [verifySync](arkts-cryptoarchitecture-verify-i.md#verifysync-1)）或多次调用updateSync。
>
> 算法库目前没有对updateSync（单次或累计）的数据量设置大小限制，建议对于大数据量的验签操作，采用多次updateSync的方式传入数据，避免
> 一次性申请过大内存。
>
> 验签使用多次updateSync操作的示例代码详见
> [使用RSA密钥对分段签名验签](../../../../security/CryptoArchitectureKit/crypto-rsa-sign-sig-verify-pkcs1-by-segment.md)，
> 其余算法操作类似。
>
> OnlyVerify模式下，不支持updateSync操作，需要直接使用verifySync传入数据。
>
> 当使用DSA算法进行验签，并设置了摘要算法为NoHash时，则不支持updateSync操作，updateSync接口会返回错误码ERR_CRYPTO_OPERATION。

<br><br>**说明：**
<br>建议优先使用异步API{@link update}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。
因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | DataBlob | 是 | 传入的消息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620004](../errorcode-crypto-framework.md#17620004-无效的函数调用) | 无效的函数调用。<br>**适用版本：** 26.0.0+ |

## verify

```TypeScript
verify(data: DataBlob, signatureData: DataBlob, callback: AsyncCallback<boolean>): void
```

对数据进行验签，包含update的数据。使用callback异步回调。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | DataBlob | 是 | 待验签的数据。 |
| signatureData | DataBlob | 是 | 签名数据。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。返回true表示验签通过；返回false表示验签失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

## verify

```TypeScript
verify(data: DataBlob | null, signatureData: DataBlob, callback: AsyncCallback<boolean>): void
```

对数据进行验签。使用callback异步回调。

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | DataBlob \| null | 是 | 传入的消息。API 10之前只支持DataBlob， API 10之后增加支持null。 |
| signatureData | DataBlob | 是 | 签名数据。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。返回true表示验签通过；返回false表示验签不通过。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

## verify

```TypeScript
verify(data: DataBlob, signatureData: DataBlob): Promise<boolean>
```

对数据进行验签，包含update的数据。使用Promise异步回调。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | DataBlob | 是 | 待验签的数据。 |
| signatureData | DataBlob | 是 | 签名数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回验签结果。返回true表示验签成功，返回false表示验签失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

## verify

```TypeScript
verify(data: DataBlob | null, signatureData: DataBlob): Promise<boolean>
```

对数据进行验签。使用Promise异步回调。

**起始版本：** 10

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本10-11：SystemCapability.Security.CryptoFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | DataBlob \| null | 是 | 传入的消息。API 10之前只支持DataBlob， API 10之后增加支持null。 |
| signatureData | DataBlob | 是 | 签名数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示验签成功，返回false表示验签失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

## verifySync

```TypeScript
verifySync(data: DataBlob | null, signatureData: DataBlob): boolean
```

对数据进行验签，通过同步方式返回验签结果。

<br><br>**说明：**
<br>建议优先使用异步API{@link verify}。同步API可能因系统繁忙、高负载等原因耗时较长而阻塞主线程。
因此建议在子线程中调用同步API，以避免阻塞主线程。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | DataBlob \| null | 是 | 传入的消息。 |
| signatureData | DataBlob | 是 | 签名数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 同步返回值，表示验签是否通过。true为通过，false为不通过。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | 非法入参。可能的原因：<br>1. 必填参数未指定；<br>2. 参数类型不正确；<br>3. 参数验证失败。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。<br>**适用版本：** 26.0.0+ |

**示例：**

此外，更多签名验签的完整示例可参考[签名验签开发指导](../../security/CryptoArchitectureKit/crypto-rsa-sign-sig-verify-pkcs1.md)。

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

function verifyByCallback() {
  let inputUpdate: cryptoFramework.DataBlob =
    { data: new Uint8Array(buffer.from('This is Sign test plan1', 'utf-8').buffer) };
  let inputVerify: cryptoFramework.DataBlob =
    { data: new Uint8Array(buffer.from('This is Sign test plan2', 'utf-8').buffer) };
  // 根据密钥数据生成的密钥和输入的验签数据，这部分代码Verify与Sign中保持一致，保证验签通过。
  let pkData =
    new Uint8Array([48, 129, 159, 48, 13, 6, 9, 42, 134, 72, 134, 247, 13, 1, 1, 1, 5, 0, 3, 129, 141, 0, 48, 129, 137,
      2, 129, 129, 0, 214, 179, 23, 198, 183, 139, 148, 8, 173, 74, 56, 160, 15, 248, 244, 166, 209, 250, 142, 74, 216,
      58, 117, 215, 178, 247, 254, 39, 180, 227, 85, 201, 59, 133, 209, 221, 26, 9, 116, 31, 172, 151, 252, 185, 123,
      20, 25, 7, 92, 129, 5, 196, 239, 214, 126, 254, 154, 188, 239, 144, 161, 171, 65, 42, 31, 214, 93, 115, 247, 69,
      94, 143, 54, 51, 25, 49, 146, 204, 205, 165, 20, 120, 35, 184, 190, 65, 106, 12, 214, 176, 57, 125, 235, 51, 88,
      135, 76, 73, 109, 112, 147, 138, 198, 252, 5, 20, 245, 51, 7, 32, 108, 89, 125, 204, 50, 189, 88, 254, 255, 146,
      244, 244, 149, 79, 54, 216, 45, 89, 2, 3, 1, 0, 1]);
  let skData =
    new Uint8Array([48, 130, 2, 120, 2, 1, 0, 48, 13, 6, 9, 42, 134, 72, 134, 247, 13, 1, 1, 1, 5, 0, 4, 130, 2, 98, 48,
      130, 2, 94, 2, 1, 0, 2, 129, 129, 0, 214, 179, 23, 198, 183, 139, 148, 8, 173, 74, 56, 160, 15, 248, 244, 166,
      209, 250, 142, 74, 216, 58, 117, 215, 178, 247, 254, 39, 180, 227, 85, 201, 59, 133, 209, 221, 26, 9, 116, 31,
      172, 151, 252, 185, 123, 20, 25, 7, 92, 129, 5, 196, 239, 214, 126, 254, 154, 188, 239, 144, 161, 171, 65, 42, 31,
      214, 93, 115, 247, 69, 94, 143, 54, 51, 25, 49, 146, 204, 205, 165, 20, 120, 35, 184, 190, 65, 106, 12, 214, 176,
      57, 125, 235, 51, 88, 135, 76, 73, 109, 112, 147, 138, 198, 252, 5, 20, 245, 51, 7, 32, 108, 89, 125, 204, 50,
      189, 88, 254, 255, 146, 244, 244, 149, 79, 54, 216, 45, 89, 2, 3, 1, 0, 1, 2, 129, 129, 0, 152, 111, 145, 203, 10,
      88, 116, 163, 112, 126, 9, 20, 68, 34, 235, 121, 98, 14, 182, 102, 151, 125, 114, 91, 210, 122, 215, 29, 212, 5,
      176, 203, 238, 146, 5, 190, 41, 21, 91, 56, 125, 239, 111, 133, 53, 200, 192, 56, 132, 202, 42, 145, 120, 3, 224,
      40, 223, 46, 148, 29, 41, 92, 17, 40, 12, 72, 165, 69, 192, 211, 142, 233, 81, 202, 177, 235, 156, 27, 179, 48,
      18, 85, 154, 101, 193, 45, 218, 91, 24, 143, 196, 248, 16, 83, 177, 198, 136, 77, 111, 134, 60, 219, 95, 246, 23,
      5, 45, 14, 83, 29, 137, 248, 159, 28, 132, 142, 205, 99, 226, 213, 84, 232, 57, 130, 156, 81, 191, 237, 2, 65, 0,
      255, 158, 212, 13, 43, 132, 244, 135, 148, 161, 232, 219, 20, 81, 196, 102, 103, 44, 110, 71, 100, 62, 73, 200,
      32, 138, 114, 209, 171, 150, 179, 92, 198, 5, 190, 218, 79, 227, 227, 37, 32, 57, 159, 252, 107, 211, 139, 198,
      202, 248, 137, 143, 186, 205, 106, 81, 85, 207, 134, 148, 110, 204, 243, 27, 2, 65, 0, 215, 4, 181, 121, 57, 224,
      170, 168, 183, 159, 152, 8, 74, 233, 80, 244, 146, 81, 48, 159, 194, 199, 36, 187, 6, 181, 182, 223, 115, 133,
      151, 171, 78, 219, 90, 161, 248, 69, 6, 207, 173, 3, 81, 161, 2, 60, 238, 204, 177, 12, 138, 17, 220, 179, 71,
      113, 200, 248, 159, 153, 252, 150, 180, 155, 2, 65, 0, 190, 202, 185, 211, 170, 171, 238, 40, 84, 84, 21, 13, 144,
      57, 7, 178, 183, 71, 126, 120, 98, 229, 235, 4, 40, 229, 173, 149, 185, 209, 29, 199, 29, 54, 164, 161, 38, 8, 30,
      62, 83, 179, 47, 42, 165, 0, 156, 207, 160, 39, 169, 229, 81, 180, 136, 170, 116, 182, 20, 233, 45, 90, 100, 9, 2,
      65, 0, 152, 255, 47, 198, 15, 201, 238, 133, 89, 11, 133, 153, 184, 252, 37, 239, 177, 65, 118, 80, 231, 190, 222,
      66, 250, 118, 72, 166, 221, 67, 156, 245, 119, 138, 28, 6, 142, 107, 71, 122, 116, 200, 156, 199, 237, 152, 191,
      239, 4, 184, 64, 114, 143, 81, 62, 48, 23, 233, 217, 95, 47, 221, 104, 171, 2, 64, 30, 219, 1, 230, 241, 70, 246,
      243, 121, 174, 67, 66, 11, 99, 202, 17, 52, 234, 78, 29, 3, 57, 51, 123, 149, 86, 64, 192, 73, 199, 108, 101, 55,
      232, 41, 114, 153, 237, 253, 52, 205, 148, 45, 86, 186, 241, 182, 183, 42, 77, 252, 195, 29, 158, 173, 3, 182,
      207, 254, 61, 71, 184, 167, 184]);
  let pubKeyBlob: cryptoFramework.DataBlob = { data: pkData };
  let priKeyBlob: cryptoFramework.DataBlob = { data: skData };
  // 该数据取自Sign中的signData.data。
  let signMessageBlob: cryptoFramework.DataBlob = {
    data: new Uint8Array([9, 68, 164, 161, 230, 155, 255, 153, 10, 12, 14, 22, 146, 115, 209, 167, 223, 133, 89, 173,
      50, 249, 176, 104, 10, 251, 219, 104, 117, 196, 105, 65, 249, 139, 119, 41, 15, 171, 191, 11, 177, 177, 1, 119,
      130, 142, 87, 183, 32, 220, 226, 28, 38, 73, 222, 172, 153, 26, 87, 58, 188, 42, 150, 67, 94, 214, 147, 64, 202,
      87, 155, 125, 254, 112, 95, 176, 255, 207, 106, 43, 228, 153, 131, 240, 120, 88, 253, 179, 207, 207, 110, 223,
      173, 15, 113, 11, 183, 122, 237, 205, 206, 123, 246, 33, 167, 169, 251, 237, 199, 26, 220, 152, 190, 117, 131, 74,
      232, 50, 39, 172, 232, 178, 112, 73, 251, 235, 131, 209])
  }
  let rsaGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
  let verifier = cryptoFramework.createVerify('RSA1024|PKCS1|SHA256');
  rsaGenerator.convertKey(pubKeyBlob, priKeyBlob, (err, keyPair) => {
    verifier.init(keyPair.pubKey, err => {
      verifier.update(inputUpdate, err => {
        verifier.verify(inputVerify, signMessageBlob, (err, res) => {
          console.info('verify result = ' + res);
        });
      });
    });
  });
}

```

更多示例请参见[签名验签开发指导](../../security/CryptoArchitectureKit/crypto-rsa-sign-sig-verify-pkcs1.md)。

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

async function genKeyPairByData(pubKeyData: Uint8Array, priKeyData: Uint8Array) {
  let pubKeyBlob: cryptoFramework.DataBlob = { data: pubKeyData };
  let priKeyBlob: cryptoFramework.DataBlob = { data: priKeyData };
  let rsaGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
  let keyPair = await rsaGenerator.convertKey(pubKeyBlob, priKeyBlob);
  console.info('convertKey result: success.');
  return keyPair;
}

async function verifyByPromise() {
  // 根据密钥数据生成的密钥和输入的验签数据，这部分代码Verify与Sign中保持一致，保证验签通过。
  let pkData =
    new Uint8Array([48, 129, 159, 48, 13, 6, 9, 42, 134, 72, 134, 247, 13, 1, 1, 1, 5, 0, 3, 129, 141, 0, 48, 129, 137,
      2, 129, 129, 0, 214, 179, 23, 198, 183, 139, 148, 8, 173, 74, 56, 160, 15, 248, 244, 166, 209, 250, 142, 74, 216,
      58, 117, 215, 178, 247, 254, 39, 180, 227, 85, 201, 59, 133, 209, 221, 26, 9, 116, 31, 172, 151, 252, 185, 123,
      20, 25, 7, 92, 129, 5, 196, 239, 214, 126, 254, 154, 188, 239, 144, 161, 171, 65, 42, 31, 214, 93, 115, 247, 69,
      94, 143, 54, 51, 25, 49, 146, 204, 205, 165, 20, 120, 35, 184, 190, 65, 106, 12, 214, 176, 57, 125, 235, 51, 88,
      135, 76, 73, 109, 112, 147, 138, 198, 252, 5, 20, 245, 51, 7, 32, 108, 89, 125, 204, 50, 189, 88, 254, 255, 146,
      244, 244, 149, 79, 54, 216, 45, 89, 2, 3, 1, 0, 1]);
  let skData =
    new Uint8Array([48, 130, 2, 120, 2, 1, 0, 48, 13, 6, 9, 42, 134, 72, 134, 247, 13, 1, 1, 1, 5, 0, 4, 130, 2, 98, 48,
      130, 2, 94, 2, 1, 0, 2, 129, 129, 0, 214, 179, 23, 198, 183, 139, 148, 8, 173, 74, 56, 160, 15, 248, 244, 166,
      209, 250, 142, 74, 216, 58, 117, 215, 178, 247, 254, 39, 180, 227, 85, 201, 59, 133, 209, 221, 26, 9, 116, 31,
      172, 151, 252, 185, 123, 20, 25, 7, 92, 129, 5, 196, 239, 214, 126, 254, 154, 188, 239, 144, 161, 171, 65, 42, 31,
      214, 93, 115, 247, 69, 94, 143, 54, 51, 25, 49, 146, 204, 205, 165, 20, 120, 35, 184, 190, 65, 106, 12, 214, 176,
      57, 125, 235, 51, 88, 135, 76, 73, 109, 112, 147, 138, 198, 252, 5, 20, 245, 51, 7, 32, 108, 89, 125, 204, 50,
      189, 88, 254, 255, 146, 244, 244, 149, 79, 54, 216, 45, 89, 2, 3, 1, 0, 1, 2, 129, 129, 0, 152, 111, 145, 203, 10,
      88, 116, 163, 112, 126, 9, 20, 68, 34, 235, 121, 98, 14, 182, 102, 151, 125, 114, 91, 210, 122, 215, 29, 212, 5,
      176, 203, 238, 146, 5, 190, 41, 21, 91, 56, 125, 239, 111, 133, 53, 200, 192, 56, 132, 202, 42, 145, 120, 3, 224,
      40, 223, 46, 148, 29, 41, 92, 17, 40, 12, 72, 165, 69, 192, 211, 142, 233, 81, 202, 177, 235, 156, 27, 179, 48,
      18, 85, 154, 101, 193, 45, 218, 91, 24, 143, 196, 248, 16, 83, 177, 198, 136, 77, 111, 134, 60, 219, 95, 246, 23,
      5, 45, 14, 83, 29, 137, 248, 159, 28, 132, 142, 205, 99, 226, 213, 84, 232, 57, 130, 156, 81, 191, 237, 2, 65, 0,
      255, 158, 212, 13, 43, 132, 244, 135, 148, 161, 232, 219, 20, 81, 196, 102, 103, 44, 110, 71, 100, 62, 73, 200,
      32, 138, 114, 209, 171, 150, 179, 92, 198, 5, 190, 218, 79, 227, 227, 37, 32, 57, 159, 252, 107, 211, 139, 198,
      202, 248, 137, 143, 186, 205, 106, 81, 85, 207, 134, 148, 110, 204, 243, 27, 2, 65, 0, 215, 4, 181, 121, 57, 224,
      170, 168, 183, 159, 152, 8, 74, 233, 80, 244, 146, 81, 48, 159, 194, 199, 36, 187, 6, 181, 182, 223, 115, 133,
      151, 171, 78, 219, 90, 161, 248, 69, 6, 207, 173, 3, 81, 161, 2, 60, 238, 204, 177, 12, 138, 17, 220, 179, 71,
      113, 200, 248, 159, 153, 252, 150, 180, 155, 2, 65, 0, 190, 202, 185, 211, 170, 171, 238, 40, 84, 84, 21, 13, 144,
      57, 7, 178, 183, 71, 126, 120, 98, 229, 235, 4, 40, 229, 173, 149, 185, 209, 29, 199, 29, 54, 164, 161, 38, 8, 30,
      62, 83, 179, 47, 42, 165, 0, 156, 207, 160, 39, 169, 229, 81, 180, 136, 170, 116, 182, 20, 233, 45, 90, 100, 9, 2,
      65, 0, 152, 255, 47, 198, 15, 201, 238, 133, 89, 11, 133, 153, 184, 252, 37, 239, 177, 65, 118, 80, 231, 190, 222,
      66, 250, 118, 72, 166, 221, 67, 156, 245, 119, 138, 28, 6, 142, 107, 71, 122, 116, 200, 156, 199, 237, 152, 191,
      239, 4, 184, 64, 114, 143, 81, 62, 48, 23, 233, 217, 95, 47, 221, 104, 171, 2, 64, 30, 219, 1, 230, 241, 70, 246,
      243, 121, 174, 67, 66, 11, 99, 202, 17, 52, 234, 78, 29, 3, 57, 51, 123, 149, 86, 64, 192, 73, 199, 108, 101, 55,
      232, 41, 114, 153, 237, 253, 52, 205, 148, 45, 86, 186, 241, 182, 183, 42, 77, 252, 195, 29, 158, 173, 3, 182,
      207, 254, 61, 71, 184, 167, 184]);
  let keyPair = await genKeyPairByData(pkData, skData);
  let inputUpdate: cryptoFramework.DataBlob =
    { data: new Uint8Array(buffer.from('This is Sign test plan1', 'utf-8').buffer) };
  let inputVerify: cryptoFramework.DataBlob =
    { data: new Uint8Array(buffer.from('This is Sign test plan2', 'utf-8').buffer) };
  // 该数据取自Sign中的signData.data。
  let signMessageBlob: cryptoFramework.DataBlob = {
    data: new Uint8Array([9, 68, 164, 161, 230, 155, 255, 153, 10, 12, 14, 22, 146, 115, 209, 167, 223, 133, 89, 173,
      50, 249, 176, 104, 10, 251, 219, 104, 117, 196, 105, 65, 249, 139, 119, 41, 15, 171, 191, 11, 177, 177, 1, 119,
      130, 142, 87, 183, 32, 220, 226, 28, 38, 73, 222, 172, 153, 26, 87, 58, 188, 42, 150, 67, 94, 214, 147, 64, 202,
      87, 155, 125, 254, 112, 95, 176, 255, 207, 106, 43, 228, 153, 131, 240, 120, 88, 253, 179, 207, 207, 110, 223,
      173, 15, 113, 11, 183, 122, 237, 205, 206, 123, 246, 33, 167, 169, 251, 237, 199, 26, 220, 152, 190, 117, 131, 74,
      232, 50, 39, 172, 232, 178, 112, 73, 251, 235, 131, 209])
  };
  let verifier = cryptoFramework.createVerify('RSA1024|PKCS1|SHA256');
  await verifier.init(keyPair.pubKey);
  await verifier.update(inputUpdate);
  let res = await verifier.verify(inputVerify, signMessageBlob);
  console.info('verify result: ' + res);
}

```

此外，更多签名验签的完整示例可参考[签名验签开发指导](../../security/CryptoArchitectureKit/crypto-rsa-sign-sig-verify-pkcs1.md)。

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { buffer } from '@kit.ArkTS';

function genKeyPairByData(pubKeyData: Uint8Array, priKeyData: Uint8Array) {
  let pubKeyBlob: cryptoFramework.DataBlob = { data: pubKeyData };
  let priKeyBlob: cryptoFramework.DataBlob = { data: priKeyData };
  let rsaGenerator = cryptoFramework.createAsyKeyGenerator('RSA1024');
  let keyPair = rsaGenerator.convertKeySync(pubKeyBlob, priKeyBlob);
  console.info('convertKey result: success.');
  return keyPair;
}

function verifyBySync() {
  // 根据密钥数据生成的密钥和输入的验签数据，这部分代码Verify与Sign中保持一致，保证验签通过。
  let pkData =
    new Uint8Array([48, 129, 159, 48, 13, 6, 9, 42, 134, 72, 134, 247, 13, 1, 1, 1, 5, 0, 3, 129, 141, 0, 48, 129, 137,
      2, 129, 129, 0, 214, 179, 23, 198, 183, 139, 148, 8, 173, 74, 56, 160, 15, 248, 244, 166, 209, 250, 142, 74, 216,
      58, 117, 215, 178, 247, 254, 39, 180, 227, 85, 201, 59, 133, 209, 221, 26, 9, 116, 31, 172, 151, 252, 185, 123,
      20, 25, 7, 92, 129, 5, 196, 239, 214, 126, 254, 154, 188, 239, 144, 161, 171, 65, 42, 31, 214, 93, 115, 247, 69,
      94, 143, 54, 51, 25, 49, 146, 204, 205, 165, 20, 120, 35, 184, 190, 65, 106, 12, 214, 176, 57, 125, 235, 51, 88,
      135, 76, 73, 109, 112, 147, 138, 198, 252, 5, 20, 245, 51, 7, 32, 108, 89, 125, 204, 50, 189, 88, 254, 255, 146,
      244, 244, 149, 79, 54, 216, 45, 89, 2, 3, 1, 0, 1]);
  let skData =
    new Uint8Array([48, 130, 2, 120, 2, 1, 0, 48, 13, 6, 9, 42, 134, 72, 134, 247, 13, 1, 1, 1, 5, 0, 4, 130, 2, 98, 48,
      130, 2, 94, 2, 1, 0, 2, 129, 129, 0, 214, 179, 23, 198, 183, 139, 148, 8, 173, 74, 56, 160, 15, 248, 244, 166,
      209, 250, 142, 74, 216, 58, 117, 215, 178, 247, 254, 39, 180, 227, 85, 201, 59, 133, 209, 221, 26, 9, 116, 31,
      172, 151, 252, 185, 123, 20, 25, 7, 92, 129, 5, 196, 239, 214, 126, 254, 154, 188, 239, 144, 161, 171, 65, 42, 31,
      214, 93, 115, 247, 69, 94, 143, 54, 51, 25, 49, 146, 204, 205, 165, 20, 120, 35, 184, 190, 65, 106, 12, 214, 176,
      57, 125, 235, 51, 88, 135, 76, 73, 109, 112, 147, 138, 198, 252, 5, 20, 245, 51, 7, 32, 108, 89, 125, 204, 50,
      189, 88, 254, 255, 146, 244, 244, 149, 79, 54, 216, 45, 89, 2, 3, 1, 0, 1, 2, 129, 129, 0, 152, 111, 145, 203, 10,
      88, 116, 163, 112, 126, 9, 20, 68, 34, 235, 121, 98, 14, 182, 102, 151, 125, 114, 91, 210, 122, 215, 29, 212, 5,
      176, 203, 238, 146, 5, 190, 41, 21, 91, 56, 125, 239, 111, 133, 53, 200, 192, 56, 132, 202, 42, 145, 120, 3, 224,
      40, 223, 46, 148, 29, 41, 92, 17, 40, 12, 72, 165, 69, 192, 211, 142, 233, 81, 202, 177, 235, 156, 27, 179, 48,
      18, 85, 154, 101, 193, 45, 218, 91, 24, 143, 196, 248, 16, 83, 177, 198, 136, 77, 111, 134, 60, 219, 95, 246, 23,
      5, 45, 14, 83, 29, 137, 248, 159, 28, 132, 142, 205, 99, 226, 213, 84, 232, 57, 130, 156, 81, 191, 237, 2, 65, 0,
      255, 158, 212, 13, 43, 132, 244, 135, 148, 161, 232, 219, 20, 81, 196, 102, 103, 44, 110, 71, 100, 62, 73, 200,
      32, 138, 114, 209, 171, 150, 179, 92, 198, 5, 190, 218, 79, 227, 227, 37, 32, 57, 159, 252, 107, 211, 139, 198,
      202, 248, 137, 143, 186, 205, 106, 81, 85, 207, 134, 148, 110, 204, 243, 27, 2, 65, 0, 215, 4, 181, 121, 57, 224,
      170, 168, 183, 159, 152, 8, 74, 233, 80, 244, 146, 81, 48, 159, 194, 199, 36, 187, 6, 181, 182, 223, 115, 133,
      151, 171, 78, 219, 90, 161, 248, 69, 6, 207, 173, 3, 81, 161, 2, 60, 238, 204, 177, 12, 138, 17, 220, 179, 71,
      113, 200, 248, 159, 153, 252, 150, 180, 155, 2, 65, 0, 190, 202, 185, 211, 170, 171, 238, 40, 84, 84, 21, 13, 144,
      57, 7, 178, 183, 71, 126, 120, 98, 229, 235, 4, 40, 229, 173, 149, 185, 209, 29, 199, 29, 54, 164, 161, 38, 8, 30,
      62, 83, 179, 47, 42, 165, 0, 156, 207, 160, 39, 169, 229, 81, 180, 136, 170, 116, 182, 20, 233, 45, 90, 100, 9, 2,
      65, 0, 152, 255, 47, 198, 15, 201, 238, 133, 89, 11, 133, 153, 184, 252, 37, 239, 177, 65, 118, 80, 231, 190, 222,
      66, 250, 118, 72, 166, 221, 67, 156, 245, 119, 138, 28, 6, 142, 107, 71, 122, 116, 200, 156, 199, 237, 152, 191,
      239, 4, 184, 64, 114, 143, 81, 62, 48, 23, 233, 217, 95, 47, 221, 104, 171, 2, 64, 30, 219, 1, 230, 241, 70, 246,
      243, 121, 174, 67, 66, 11, 99, 202, 17, 52, 234, 78, 29, 3, 57, 51, 123, 149, 86, 64, 192, 73, 199, 108, 101, 55,
      232, 41, 114, 153, 237, 253, 52, 205, 148, 45, 86, 186, 241, 182, 183, 42, 77, 252, 195, 29, 158, 173, 3, 182,
      207, 254, 61, 71, 184, 167, 184]);
  let keyPair = genKeyPairByData(pkData, skData);
  let inputUpdate: cryptoFramework.DataBlob =
    { data: new Uint8Array(buffer.from('This is Sign test plan1', 'utf-8').buffer) };
  let inputVerify: cryptoFramework.DataBlob =
    { data: new Uint8Array(buffer.from('This is Sign test plan2', 'utf-8').buffer) };
  // 该数据取自Sign中的signData.data。
  let signMessageBlob: cryptoFramework.DataBlob = {
    data: new Uint8Array([9, 68, 164, 161, 230, 155, 255, 153, 10, 12, 14, 22, 146, 115, 209, 167, 223, 133, 89, 173,
      50, 249, 176, 104, 10, 251, 219, 104, 117, 196, 105, 65, 249, 139, 119, 41, 15, 171, 191, 11, 177, 177, 1, 119,
      130, 142, 87, 183, 32, 220, 226, 28, 38, 73, 222, 172, 153, 26, 87, 58, 188, 42, 150, 67, 94, 214, 147, 64, 202,
      87, 155, 125, 254, 112, 95, 176, 255, 207, 106, 43, 228, 153, 131, 240, 120, 88, 253, 179, 207, 207, 110, 223,
      173, 15, 113, 11, 183, 122, 237, 205, 206, 123, 246, 33, 167, 169, 251, 237, 199, 26, 220, 152, 190, 117, 131, 74,
      232, 50, 39, 172, 232, 178, 112, 73, 251, 235, 131, 209])
  };
  let verifier = cryptoFramework.createVerify('RSA1024|PKCS1|SHA256');
  verifier.initSync(keyPair.pubKey);
  verifier.updateSync(inputUpdate);
  let res = verifier.verifySync(inputVerify, signMessageBlob);
  console.info('verify result: ' + res);
}

```

## algName

```TypeScript
readonly algName: string
```

验签指定的算法名称。

**类型：** string

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本9-11：SystemCapability.Security.CryptoFramework

