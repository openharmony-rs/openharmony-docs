# X963KdfSpec

密钥派生函数参数[KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md#KdfSpec)的子类，作为X963KDF密钥派生函数进行密钥派生时的输入。 > **说明：** > > key指的是用户输入的最初的密钥材料。

**继承/实现关系：** X963KdfSpec extends [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md#KdfSpec)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cryptoFramework-interface X963KdfSpec--><!--Device-cryptoFramework-interface X963KdfSpec-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## info

```TypeScript
info: Uint8Array
```

共享信息。

**类型：** Uint8Array

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X963KdfSpec-info: Uint8Array--><!--Device-X963KdfSpec-info: Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## key

```TypeScript
key: string | Uint8Array
```

密钥材料。

**类型：** string \| Uint8Array

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X963KdfSpec-key: string | Uint8Array--><!--Device-X963KdfSpec-key: string | Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## keySize

```TypeScript
keySize: int
```

派生得到的密钥字节长度，需要为正整数，单位为bytes。 取值应为正整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-X963KdfSpec-keySize: int--><!--Device-X963KdfSpec-keySize: int-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

