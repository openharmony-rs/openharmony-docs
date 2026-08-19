# CryptoParam

数据库加密参数配置。此配置只有在StoreConfig的encrypt选项设置为true或密钥非空时有效。

**起始版本：** 23

<!--Device-relationalStore-interface CryptoParam--><!--Device-relationalStore-interface CryptoParam-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## cryptoPageSize

```TypeScript
cryptoPageSize?: int
```

整数类型，指定数据库加解密使用的页大小，单位：字节。如不指定，默认值为1024字节。 用户指定的页大小应为1024到65536范围内的整数，并且为2&lt;sup&gt;n&lt;/sup&gt;。若指定值非整数，则向下取整。

**类型：** int

**起始版本：** 23

<!--Device-CryptoParam-cryptoPageSize?: int--><!--Device-CryptoParam-cryptoPageSize?: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## encryptionAlgo

```TypeScript
encryptionAlgo?: EncryptionAlgo
```

指定数据库加解密使用的加密算法。如不指定，默认值为 AES_256_GCM。

**类型：** [EncryptionAlgo](arkts-arkdata-relationalstore-encryptionalgo-e.md)

**起始版本：** 23

<!--Device-CryptoParam-encryptionAlgo?: EncryptionAlgo--><!--Device-CryptoParam-encryptionAlgo?: EncryptionAlgo-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## encryptionKey

```TypeScript
encryptionKey: Uint8Array
```

指定数据库加/解密使用的密钥。 如传入密钥为空，则由数据库负责生成并保存密钥，并使用生成的密钥打开数据库文件。 使用完后用户需要将密钥内容全部置为零。

**类型：** Uint8Array

**起始版本：** 23

<!--Device-CryptoParam-encryptionKey: Uint8Array--><!--Device-CryptoParam-encryptionKey: Uint8Array-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## hmacAlgo

```TypeScript
hmacAlgo?: HmacAlgo
```

指定数据库加解密使用的HMAC算法。如不指定，默认值为SHA256。

**类型：** [HmacAlgo](arkts-arkdata-relationalstore-hmacalgo-e.md)

**起始版本：** 23

<!--Device-CryptoParam-hmacAlgo?: HmacAlgo--><!--Device-CryptoParam-hmacAlgo?: HmacAlgo-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## iterationCount

```TypeScript
iterationCount?: int
```

整数类型，指定数据库PBKDF2算法的迭代次数，默认值为10000。 迭代次数应当为大于零的整数，若非整数则向下取整，若小于零则抛出错误码401，请参见[通用错误码](../../errorcode-universal.md)。 不指定此参数或指定为零时，使用默认值10000，并使用默认加密算法AES_256_GCM。

**类型：** int

**起始版本：** 23

<!--Device-CryptoParam-iterationCount?: int--><!--Device-CryptoParam-iterationCount?: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## kdfAlgo

```TypeScript
kdfAlgo?: KdfAlgo
```

指定数据库加解密使用的PBKDF2算法。如不指定，默认使用和HMAC算法相等的算法。

**类型：** [KdfAlgo](arkts-arkdata-relationalstore-kdfalgo-e.md)

**起始版本：** 23

<!--Device-CryptoParam-kdfAlgo?: KdfAlgo--><!--Device-CryptoParam-kdfAlgo?: KdfAlgo-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

