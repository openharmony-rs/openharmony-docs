# CipherSpecItem

表示加解密参数的枚举。这些参数支持通过[setCipherSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口设置，通过 [getCipherSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_接口获取。 \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_当前只支持RSA算法和SM2算法。详细规格请参考 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-cryptoFramework-enum CipherSpecItem--><!--Device-cryptoFramework-enum CipherSpecItem-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本10-11：SystemCapability.Security.CryptoFramework

## OAEP_MD_NAME_STR

```TypeScript
OAEP_MD_NAME_STR = 100
```

表示RSA算法中，使用PKCS1\_OAEP模式时，消息摘要功能的算法名。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CipherSpecItem-OAEP_MD_NAME_STR = 100--><!--Device-CipherSpecItem-OAEP_MD_NAME_STR = 100-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本10-11：SystemCapability.Security.CryptoFramework

## OAEP_MGF_NAME_STR

```TypeScript
OAEP_MGF_NAME_STR = 101
```

表示RSA算法中，使用PKCS1\_OAEP模式时，掩码生成算法（目前仅支持MGF1）。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CipherSpecItem-OAEP_MGF_NAME_STR = 101--><!--Device-CipherSpecItem-OAEP_MGF_NAME_STR = 101-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本10-11：SystemCapability.Security.CryptoFramework

## OAEP_MGF1_MD_STR

```TypeScript
OAEP_MGF1_MD_STR = 102
```

表示RSA算法中，使用PKCS1\_OAEP模式时，MGF1掩码生成功能的消息摘要算法。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CipherSpecItem-OAEP_MGF1_MD_STR = 102--><!--Device-CipherSpecItem-OAEP_MGF1_MD_STR = 102-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本10-11：SystemCapability.Security.CryptoFramework

## OAEP_MGF1_PSRC_UINT8ARR

```TypeScript
OAEP_MGF1_PSRC_UINT8ARR = 103
```

表示RSA算法中，使用PKCS1\_OAEP模式时，pSource的字节流。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CipherSpecItem-OAEP_MGF1_PSRC_UINT8ARR = 103--><!--Device-CipherSpecItem-OAEP_MGF1_PSRC_UINT8ARR = 103-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本10-11：SystemCapability.Security.CryptoFramework

## SM2_MD_NAME_STR

```TypeScript
SM2_MD_NAME_STR = 104
```

表示SM2算法中，使用的摘要算法名。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CipherSpecItem-SM2_MD_NAME_STR = 104--><!--Device-CipherSpecItem-SM2_MD_NAME_STR = 104-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Cipher
- API版本11：SystemCapability.Security.CryptoFramework

