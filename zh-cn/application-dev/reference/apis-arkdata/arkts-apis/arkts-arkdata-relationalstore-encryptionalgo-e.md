# EncryptionAlgo

数据库的加密方式枚举。请使用枚举名称而非枚举值。

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-relationalStore-enum EncryptionAlgo--><!--Device-relationalStore-enum EncryptionAlgo-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## AES_256_GCM

```TypeScript
AES_256_GCM = 0
```

数据库使用AES\_256\_GCM加密。

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-EncryptionAlgo-AES_256_GCM = 0--><!--Device-EncryptionAlgo-AES_256_GCM = 0-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## AES_256_CBC

```TypeScript
AES_256_CBC = 1
```

数据库使用AES\_256\_CBC加密。

**起始版本：** 14

**ArkTS模式：** ArkTS-Dyn起始版本为14；ArkTS-Sta起始版本为23。

<!--Device-EncryptionAlgo-AES_256_CBC = 1--><!--Device-EncryptionAlgo-AES_256_CBC = 1-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## PLAIN_TEXT

```TypeScript
PLAIN_TEXT = 2
```

数据库不进行加密。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

<!--Device-EncryptionAlgo-PLAIN_TEXT = 2--><!--Device-EncryptionAlgo-PLAIN_TEXT = 2-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

