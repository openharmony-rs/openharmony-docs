# SignatureUtils

用于ECC/SM2签名数据转换的工具类。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cryptoFramework-class SignatureUtils--><!--Device-cryptoFramework-class SignatureUtils-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

## genEccSignature

```TypeScript
static genEccSignature(spec: EccSignatureSpec): Uint8Array
```

将（r、s）的ECC/SM2签名数据转换为ASN.1 DER编码。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SignatureUtils-static genEccSignature(spec: EccSignatureSpec): Uint8Array--><!--Device-SignatureUtils-static genEccSignature(spec: EccSignatureSpec): Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| spec | [EccSignatureSpec](arkts-cryptoarchitecture-cryptoframework-eccsignaturespec-i.md) | 是 | （r、s）的ECC/SM2签名数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | ASN.1 DER编码的签名数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因： &lt;br&gt;1. spec参数的r或s值为0或过大。 |

## 示例

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

function testGenEccSignature() {
  try {
    let spec: cryptoFramework.EccSignatureSpec = {
      r: BigInt('97726608965854271693043443511967021777934035174185659091642456228829830775155'),
      s: BigInt('23084224202834231287427338597254751764391338275617140205467537273296855150376'),
    }

    let data = cryptoFramework.SignatureUtils.genEccSignature(spec)
    console.info('genEccSignature result: success.');
    console.info('data = ' + data)
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`ecc failed: errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

## genEccSignatureSpec

```TypeScript
static genEccSignatureSpec(data: Uint8Array): EccSignatureSpec
```

从ASN.1 DER编码的ECC/SM2签名数据获取r和s。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SignatureUtils-static genEccSignatureSpec(data: Uint8Array): EccSignatureSpec--><!--Device-SignatureUtils-static genEccSignatureSpec(data: Uint8Array): EccSignatureSpec-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Uint8Array | 是 | ASN.1 DER编码的签名数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [EccSignatureSpec](arkts-cryptoarchitecture-cryptoframework-eccsignaturespec-i.md) | 包含r和s的数据对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |
| [17620002](../errorcode-crypto-framework.md#17620002-获取native对象失败或参数转换失败) | 获取Native对象失败或参数转换失败。 |
| [17620003](../errorcode-crypto-framework.md#17620003-参数检查失败) | 参数检查失败。可能的原因： &lt;br&gt;1. data参数长度为0或过大。 |

## 示例

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
import { BusinessError } from '@kit.BasicServicesKit';

function testGenEccSignatureSpec() {
  try {
    let data =
      new Uint8Array([48, 69, 2, 33, 0, 216, 15, 76, 238, 158, 165, 108, 76, 72, 63, 115, 52, 255, 51, 149, 54, 224,
        179, 49, 225, 70, 36, 117, 88, 154, 154, 27, 194, 161, 3, 1, 115, 2, 32, 51, 9, 53, 55, 248, 82, 7, 159, 179,
        144, 57, 151, 195, 17, 31, 106, 123, 32, 139, 219, 6, 253, 62, 240, 181, 134, 214, 107, 27, 230, 175, 40])
    let spec: cryptoFramework.EccSignatureSpec = cryptoFramework.SignatureUtils.genEccSignatureSpec(data)
    console.info('genEccSignatureSpec result: success.');
  } catch (err) {
    let e: BusinessError = err as BusinessError;
    console.error(`ecc failed: errCode: ${e.code}, errMsg: ${e.message}`);
  }
}
```

