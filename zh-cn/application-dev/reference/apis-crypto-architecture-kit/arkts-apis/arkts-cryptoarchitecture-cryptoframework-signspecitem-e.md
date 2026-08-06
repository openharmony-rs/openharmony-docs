# SignSpecItem

表示签名验签参数的枚举。这些参数支持通过 [setSignSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_、 [setVerifySpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_接口设置，通过 [getSignSpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_、[getVerifySpec]\_\_\_JSDOC\_LINK\_DESC\_USD\_4\_\_\_ 接口获取。 \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_当前只支持RSA算法和SM2算法。详细规格请参考 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-cryptoFramework-enum SignSpecItem--><!--Device-cryptoFramework-enum SignSpecItem-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本10-11：SystemCapability.Security.CryptoFramework

## PSS_MD_NAME_STR

```TypeScript
PSS_MD_NAME_STR = 100
```

表示RSA算法中，使用PSS模式时，消息摘要功能的算法名。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SignSpecItem-PSS_MD_NAME_STR = 100--><!--Device-SignSpecItem-PSS_MD_NAME_STR = 100-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本10-11：SystemCapability.Security.CryptoFramework

## PSS_MGF_NAME_STR

```TypeScript
PSS_MGF_NAME_STR = 101
```

表示RSA算法中，使用PSS模式时，掩码生成算法（目前仅支持MGF1）。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SignSpecItem-PSS_MGF_NAME_STR = 101--><!--Device-SignSpecItem-PSS_MGF_NAME_STR = 101-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本10-11：SystemCapability.Security.CryptoFramework

## PSS_MGF1_MD_STR

```TypeScript
PSS_MGF1_MD_STR = 102
```

表示RSA算法中，使用PSS模式时，MGF1掩码生成功能的消息摘要算法。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SignSpecItem-PSS_MGF1_MD_STR = 102--><!--Device-SignSpecItem-PSS_MGF1_MD_STR = 102-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本10-11：SystemCapability.Security.CryptoFramework

## PSS_SALT_LEN_NUM

```TypeScript
PSS_SALT_LEN_NUM = 103
```

表示RSA算法中，使用PSS模式时，盐值的长度，长度以字节为单位。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_根据 FIPS 186-4 标准，sLen 应大于等于 0 且小于等于哈希长度。 \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_默认值： - 对于签名操作，自动计算最大盐值长度。 - 对于验证操作，自动计算盐值长度。 \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_特殊值： - 对于签名操作，您也可以将值设置为 -1，以使用摘要长度作为盐值长度；或设置为 -2 或 -3，以自动计算最大盐值长度。推荐使用 -1。 - 对于验证操作，您也可以将值设置为 -1，以使用摘要长度作为盐值长度；设置为 -2，以自动计算盐值长度；或设置为 -3，以使用最大盐值长度。 推荐使用 -2。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SignSpecItem-PSS_SALT_LEN_NUM = 103--><!--Device-SignSpecItem-PSS_SALT_LEN_NUM = 103-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本10-11：SystemCapability.Security.CryptoFramework

## PSS_TRAILER_FIELD_NUM

```TypeScript
PSS_TRAILER_FIELD_NUM = 104
```

表示RSA算法中，使用PSS模式时，用于编码操作的整数。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SignSpecItem-PSS_TRAILER_FIELD_NUM = 104--><!--Device-SignSpecItem-PSS_TRAILER_FIELD_NUM = 104-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本10-11：SystemCapability.Security.CryptoFramework

## SM2_USER_ID_UINT8ARR

```TypeScript
SM2_USER_ID_UINT8ARR = 105
```

表示SM2算法中，用户身份标识字段。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SignSpecItem-SM2_USER_ID_UINT8ARR = 105--><!--Device-SignSpecItem-SM2_USER_ID_UINT8ARR = 105-End-->

**系统能力：** 
- API版本12+：SystemCapability.Security.CryptoFramework.Signature
- API版本11：SystemCapability.Security.CryptoFramework

## ML_DSA_DETERMINISTIC_BOOL

```TypeScript
ML_DSA_DETERMINISTIC_BOOL = 106
```

指示ML-DSA签名和验证过程中是否使用确定性签名。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SignSpecItem-ML_DSA_DETERMINISTIC_BOOL = 106--><!--Device-SignSpecItem-ML_DSA_DETERMINISTIC_BOOL = 106-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

## ML_DSA_MU_BOOL

```TypeScript
ML_DSA_MU_BOOL = 107
```

指示ML-DSA签名和验证过程中的mu参数值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SignSpecItem-ML_DSA_MU_BOOL = 107--><!--Device-SignSpecItem-ML_DSA_MU_BOOL = 107-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

## ML_DSA_CONTEXT_UINT8ARR

```TypeScript
ML_DSA_CONTEXT_UINT8ARR = 108
```

指示ML-DSA签名和验证过程中的上下文数据。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SignSpecItem-ML_DSA_CONTEXT_UINT8ARR = 108--><!--Device-SignSpecItem-ML_DSA_CONTEXT_UINT8ARR = 108-End-->

**系统能力：** SystemCapability.Security.CryptoFramework.Signature

