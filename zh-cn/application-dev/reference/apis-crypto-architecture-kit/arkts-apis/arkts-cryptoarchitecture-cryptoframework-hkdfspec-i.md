# HKDFSpec

密钥派生函数参数[KdfSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的子类，作为HKDF密钥派生函数进行密钥派生时的输入。 > **说明：** > > key指的是用户输入的最初的密钥材料。根据模式的不同info与salt可以传空，但是不可不传。 > > 例如：EXTRACT\_AND\_EXPAND模式需要输入全部的值，EXTRACT\_ONLY模式info可以为空，在构建HKDFSpec的时候，info传入null值。 > > 默认的模式为EXTRACT\_AND\_EXPAND，"HKDF|SHA256|EXTRACT\_AND\_EXPAND"等价于"HKDF|SHA256"。

**继承/实现关系：** HKDFSpec extends [KdfSpec](arkts-cryptoarchitecture-cryptoframework-kdfspec-i.md)

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-cryptoFramework-interface HKDFSpec extends KdfSpec--><!--Device-cryptoFramework-interface HKDFSpec extends KdfSpec-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## info

```TypeScript
info: Uint8Array
```

拓展信息。

**类型：** Uint8Array

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HKDFSpec-info: Uint8Array--><!--Device-HKDFSpec-info: Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## key

```TypeScript
key: string | Uint8Array
```

密钥材料。

**类型：** string \| Uint8Array

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HKDFSpec-key: string | Uint8Array--><!--Device-HKDFSpec-key: string | Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## keySize

```TypeScript
keySize: int
```

派生得到的密钥字节长度，单位为bytes。

**类型：** int

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HKDFSpec-keySize: int--><!--Device-HKDFSpec-keySize: int-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

## salt

```TypeScript
salt: Uint8Array
```

盐值。

**类型：** Uint8Array

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HKDFSpec-salt: Uint8Array--><!--Device-HKDFSpec-salt: Uint8Array-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Kdf

