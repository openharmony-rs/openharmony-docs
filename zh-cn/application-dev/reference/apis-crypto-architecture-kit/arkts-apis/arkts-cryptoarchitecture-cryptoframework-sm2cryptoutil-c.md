# SM2CryptoUtil

用于SM2密码学运算的工具类。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cryptoFramework-class SM2CryptoUtil--><!--Device-cryptoFramework-class SM2CryptoUtil-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

## genCipherTextBySpec

```TypeScript
static genCipherTextBySpec(spec: SM2CipherTextSpec, mode?: string): DataBlob
```

根据指定的SM2密文参数，生成符合国密标准的ASN.1格式SM2密文。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SM2CryptoUtil-static genCipherTextBySpec(spec: SM2CipherTextSpec, mode?: string): DataBlob--><!--Device-SM2CryptoUtil-static genCipherTextBySpec(spec: SM2CipherTextSpec, mode?: string): DataBlob-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| spec | [SM2CipherTextSpec](arkts-cryptoarchitecture-cryptoframework-sm2ciphertextspec-i.md) | 是 | 指定的SM2密文参数。 |
| mode | string | 否 | 可选的密文转换模式，可用于指定密文参数的拼接顺序，当前仅支持默认值"C1C3C2"。为空或空字符串时使用 默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DataBlob | 返回符合国密标准的ASN.1格式的SM2密文。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因： &lt;br&gt;1. 必填参数未指定； &lt;br&gt;2. 参数类型不正确； &lt;br&gt;3. 参数验证失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |

## getCipherTextSpec

```TypeScript
static getCipherTextSpec(cipherText: DataBlob, mode?: string): SM2CipherTextSpec
```

从符合国密标准的ASN.1格式的SM2密文中，获取具体的SM2密文参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-SM2CryptoUtil-static getCipherTextSpec(cipherText: DataBlob, mode?: string): SM2CipherTextSpec--><!--Device-SM2CryptoUtil-static getCipherTextSpec(cipherText: DataBlob, mode?: string): SM2CipherTextSpec-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Cipher

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cipherText | DataBlob | 是 | 符合国密标准的ASN.1格式的SM2密文。 |
| mode | string | 否 | 可选的密文转换模式，可用于指定密文参数的拼接顺序，当前仅支持默认值"C1C3C2"。为空或空字符串时使用 默认值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SM2CipherTextSpec](arkts-cryptoarchitecture-cryptoframework-sm2ciphertextspec-i.md) | 返回SM2密文参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 非法入参。可能的原因： &lt;br&gt;1. 必填参数未指定； &lt;br&gt;2. 参数类型不正确； &lt;br&gt;3. 参数验证失败。 |
| [17630001](../errorcode-crypto-framework.md#17630001-密码操作错误) | 密码操作错误。 |
| [17620001](../errorcode-crypto-framework.md#17620001-内存操作失败) | 内存操作失败。 |

