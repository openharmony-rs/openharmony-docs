# @ohos.security.huks

向应用提供密钥库能力，包括密钥管理及密钥的密码学操作等功能。 HUKS所管理的密钥可以由应用导入或者由应用调用HUKS接口生成。

**起始版本：** 8

<!--Device-unnamed-declare namespace huks--><!--Device-unnamed-declare namespace huks-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## 导入模块

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [abort](arkts-universalkeystore-huks-abort-f.md) | abort终止密钥操作。使用callback异步回调。 |
| [abort](arkts-universalkeystore-huks-abort-f.md) | abort终止密钥操作。使用Promise异步回调。 |
| [abortSession](arkts-universalkeystore-huks-abortsession-f.md) | abortSession终止密钥操作。使用callback异步回调。 |
| [abortSession](arkts-universalkeystore-huks-abortsession-f.md) | abortSession终止密钥操作。使用Promise异步回调。 |
| [anonAttestKeyItem](arkts-universalkeystore-huks-anonattestkeyitem-f.md) | 获取匿名化密钥证书。使用callback异步回调。 该操作需要联网进行，且耗时较长。返回12000012错误码时，可能是由于网络异常导致。此时如果没有联网，需要提示用户网络没有连接，如果已经联网，可能是由于网络抖动导致失败，建议重试。 |
| [anonAttestKeyItem](arkts-universalkeystore-huks-anonattestkeyitem-f.md) | 获取匿名化密钥证书。使用Promise异步回调。 该操作需要联网进行，且耗时较长。返回12000012错误码时，可能是由于网络异常导致。此时如果没有联网，需要提示用户网络没有连接，如果已经联网，可能是由于网络抖动导致失败，建议重试。 |
| [anonAttestKeyItemOffline](arkts-universalkeystore-huks-anonattestkeyitemoffline-f.md) | 离线模式下获取匿名化密钥证书。使用Promise异步回调。 |
| [attestKeyItem](arkts-universalkeystore-huks-attestkeyitem-f.md) | 获取密钥证书。使用callback异步回调。 <!--RP6--> |
| [attestKeyItem](arkts-universalkeystore-huks-attestkeyitem-f.md) | 获取密钥证书。使用Promise异步回调。 <!--RP6--> |
| [decapsulate](arkts-universalkeystore-huks-decapsulate-f.md) | Post-Quantum Cryptography密钥解封装操作，支持HUKS密钥管理 或由应用程序本身决定。如果应用程序选择管理密钥， 对称密钥包含在HuksReturnResult的outData字段中。 |
| [deleteKey](arkts-universalkeystore-huks-deletekey-f.md) | 删除密钥。使用callback异步回调。 |
| [deleteKey](arkts-universalkeystore-huks-deletekey-f.md) | 删除密钥。使用Promise异步回调。 |
| [deleteKeyItem](arkts-universalkeystore-huks-deletekeyitem-f.md) | 删除密钥。使用callback异步回调。 |
| [deleteKeyItem](arkts-universalkeystore-huks-deletekeyitem-f.md) | 删除密钥。使用Promise异步回调。 |
| [encapsulate](arkts-universalkeystore-huks-encapsulate-f.md) | 后量子加密密钥封装操作，支持HUKS密钥管理 或由应用程序本身决定。如果应用程序选择管理密钥， 对称密钥携带在HuksReturnResult的outData字段中。 |
| [exportKey](arkts-universalkeystore-huks-exportkey-f.md) | 导出密钥，使用Callback方式回调异步返回的结果。 |
| [exportKey](arkts-universalkeystore-huks-exportkey-f.md) | 导出密钥。使用Promise异步回调。 |
| [exportKeyItem](arkts-universalkeystore-huks-exportkeyitem-f.md) | 导出密钥。使用callback异步回调。 |
| [exportKeyItem](arkts-universalkeystore-huks-exportkeyitem-f.md) | 导出密钥。使用Promise异步回调。 |
| [finish](arkts-universalkeystore-huks-finish-f.md) | finish操作密钥接口。使用callback异步回调。 huks.init、huks.update、huks.finish为三段式接口，需要一起使用。 |
| [finish](arkts-universalkeystore-huks-finish-f.md) | finish操作密钥接口。使用Promise异步回调。 huks.init、huks.update、huks.finish为三段式接口，需要一起使用。 |
| [finishSession](arkts-universalkeystore-huks-finishsession-f.md) | finishSession操作密钥接口。使用callback异步回调。 huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。 |
| [finishSession](arkts-universalkeystore-huks-finishsession-f.md) | Finishes the key operation. This API uses an asynchronous callback to return the result. huks.initSession, huks.updateSession, and huks.finishSession must be used together. |
| [finishSession](arkts-universalkeystore-huks-finishsession-f.md) | finishSession操作密钥接口。使用Promise异步回调。 huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。 |
| [generateKey](arkts-universalkeystore-huks-generatekey-f.md) | 生成密钥。使用callback异步回调。 |
| [generateKey](arkts-universalkeystore-huks-generatekey-f.md) | 生成密钥。使用Promise异步回调。 |
| [generateKeyItem](arkts-universalkeystore-huks-generatekeyitem-f.md) | 生成密钥。使用callback异步回调。 基于密钥不出[TEE](../../../security/UniversalKeystoreKit/huks-concepts.md#可信执行环境tee)原则，此接口不会返回密钥材料内容，只用于表示此次调用是否成功。 |
| [generateKeyItem](arkts-universalkeystore-huks-generatekeyitem-f.md) | 生成密钥。使用Promise异步回调。 基于密钥不出[TEE](../../../security/UniversalKeystoreKit/huks-concepts.md#可信执行环境tee)原则，此接口不会返回密钥材料内容，只用于表示此次调用是否成功。 |
| [getKeyItemProperties](arkts-universalkeystore-huks-getkeyitemproperties-f.md) | Obtains key properties. This API uses an asynchronous callback to return the result. |
| [getKeyItemProperties](arkts-universalkeystore-huks-getkeyitemproperties-f.md) | 获取密钥属性。使用Promise异步回调。 |
| [getKeyProperties](arkts-universalkeystore-huks-getkeyproperties-f.md) | 获取密钥属性。使用callback异步回调。 |
| [getKeyProperties](arkts-universalkeystore-huks-getkeyproperties-f.md) | 获取密钥属性。使用Promise异步回调。 |
| [getSdkVersion](arkts-universalkeystore-huks-getsdkversion-f.md) | 获取当前系统sdk版本。 |
| [hasKeyItem](arkts-universalkeystore-huks-haskeyitem-f.md) | 判断密钥是否存在。使用callback异步回调。 若密钥不存在，则通过callback返回false。 |
| [hasKeyItem](arkts-universalkeystore-huks-haskeyitem-f.md) | 判断密钥是否存在。使用Promise异步回调。 若密钥不存在，则通过Promise返回false。 |
| [importKey](arkts-universalkeystore-huks-importkey-f.md) | 导入明文密钥，使用Callback方式回调异步返回结果。 |
| [importKey](arkts-universalkeystore-huks-importkey-f.md) | 导入明文密钥。使用Promise异步回调。 |
| [importKeyItem](arkts-universalkeystore-huks-importkeyitem-f.md) | Imports a key in plaintext. This API uses an asynchronous callback to return the result. |
| [importKeyItem](arkts-universalkeystore-huks-importkeyitem-f.md) | Imports a key in plaintext. This API uses a promise to return the result. |
| [importWrappedKeyItem](arkts-universalkeystore-huks-importwrappedkeyitem-f.md) | Imports a wrapped key. This API uses an asynchronous callback to return the result. |
| [importWrappedKeyItem](arkts-universalkeystore-huks-importwrappedkeyitem-f.md) | Imports a wrapped key. This API uses a promise to return the result. |
| [init](arkts-universalkeystore-huks-init-f.md) | init操作密钥接口。使用callback异步回调。 huks.init、huks.update、huks.finish为三段式接口，需要一起使用。 |
| [init](arkts-universalkeystore-huks-init-f.md) | init操作密钥接口。使用Promise异步回调。 huks.init、huks.update、huks.finish为三段式接口，需要一起使用。 |
| [initSession](arkts-universalkeystore-huks-initsession-f.md) | initSession操作密钥接口。使用callback异步回调。 huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。 |
| [initSession](arkts-universalkeystore-huks-initsession-f.md) | initSession操作密钥接口。使用Promise异步回调。 huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。 |
| [isKeyExist](arkts-universalkeystore-huks-iskeyexist-f.md) | 判断密钥是否存在。使用callback异步回调。 |
| [isKeyExist](arkts-universalkeystore-huks-iskeyexist-f.md) | 判断密钥是否存在。使用Promise异步回调。 |
| [isKeyItemExist](arkts-universalkeystore-huks-iskeyitemexist-f.md) | 判断密钥是否存在。使用callback异步回调。 若密钥不存在，则抛出错误码为12000011的异常。 |
| [isKeyItemExist](arkts-universalkeystore-huks-iskeyitemexist-f.md) | 判断密钥是否存在。使用Promise异步回调。 若密钥不存在，则抛出错误码为12000011的异常。 |
| [listAliases](arkts-universalkeystore-huks-listaliases-f.md) | 查询密钥别名集接口。使用Promise异步回调。 |
| [unwrapKeyItem](arkts-universalkeystore-huks-unwrapkeyitem-f.md) | 加密导入密钥。使用Promise异步回调。 |
| [update](arkts-universalkeystore-huks-update-f.md) | update操作密钥接口。使用callback异步回调。 huks.init、huks.update、huks.finish为三段式接口，需要一起使用。 |
| [update](arkts-universalkeystore-huks-update-f.md) | update操作密钥接口。使用Promise异步回调。 huks.init、huks.update、huks.finish为三段式接口，需要一起使用。 |
| [updateSession](arkts-universalkeystore-huks-updatesession-f.md) | updateSession操作密钥接口。使用callback异步回调。 huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。 |
| [updateSession](arkts-universalkeystore-huks-updatesession-f.md) | Updates the key operation by segment. This API uses an asynchronous callback to return the result. huks.initSession, huks.updateSession, and huks.finishSession must be used together. |
| [updateSession](arkts-universalkeystore-huks-updatesession-f.md) | updateSession操作密钥接口。使用Promise异步回调。 huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。 |
| [wrapKeyItem](arkts-universalkeystore-huks-wrapkeyitem-f.md) | 加密导出密钥。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [anonAttestKeyItemAsUser](arkts-universalkeystore-huks-anonattestkeyitemasuser-f-sys.md) | 指定用户身份获取匿名化密钥证书，使用Promise方式异步返回结果。 该操作需要联网进行，且耗时较长。 |
| [anonAttestKeyItemOfflineAsUser](arkts-universalkeystore-huks-anonattestkeyitemofflineasuser-f-sys.md) | 离线获取匿名证明证书。该接口使用promise返回结果。此操作不需要每次都需要网络连接， 比anonAttestKeyItemAsUser函数性能高。 |
| [attestKeyItemAsUser](arkts-universalkeystore-huks-attestkeyitemasuser-f-sys.md) | 指定用户身份获取密钥证书，使用Promise方式异步返回结果。 |
| [deleteKeyItemAsUser](arkts-universalkeystore-huks-deletekeyitemasuser-f-sys.md) | 指定用户身份删除密钥，使用Promise方式异步返回结果。 |
| [exportKeyItemAsUser](arkts-universalkeystore-huks-exportkeyitemasuser-f-sys.md) | 指定用户身份导出密钥，使用Promise方式回调异步返回的结果。 |
| [generateKeyItemAsUser](arkts-universalkeystore-huks-generatekeyitemasuser-f-sys.md) | 指定用户身份生成密钥，使用Promise方式异步返回结果。基于密钥不出[TEE](../../../security/UniversalKeystoreKit/huks-concepts.md#可信执行环境tee)原则，通过 promise不会返回密钥材料内容，只用于表示此次调用是否成功。 |
| [getKeyItemPropertiesAsUser](arkts-universalkeystore-huks-getkeyitempropertiesasuser-f-sys.md) | Get properties of the key as user. |
| [hasKeyItemAsUser](arkts-universalkeystore-huks-haskeyitemasuser-f-sys.md) | 指定用户身份判断密钥是否存在，使用Promise回调异步返回结果。 |
| [importKeyItemAsUser](arkts-universalkeystore-huks-importkeyitemasuser-f-sys.md) | 指定用户身份导入明文密钥，使用Promise方式异步返回结果。 |
| [importWrappedKeyItemAsUser](arkts-universalkeystore-huks-importwrappedkeyitemasuser-f-sys.md) | Import Wrapped Key As User. |
| [initSessionAsUser](arkts-universalkeystore-huks-initsessionasuser-f-sys.md) | 指定用户身份操作密钥接口，使用Promise方式异步返回结果。huks.initSessionAsUser, huks.updateSession, huks.finishSession为三段式接口，需要一起使用。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [HuksHandle](arkts-universalkeystore-huks-hukshandle-i.md) | huks Handle结构体。 |
| [HuksListAliasesReturnResult](arkts-universalkeystore-huks-hukslistaliasesreturnresult-i.md) | 返回的密钥别名数组。 |
| [HuksOptions](arkts-universalkeystore-huks-huksoptions-i.md) | 调用接口使用的options。 |
| [HuksParam](arkts-universalkeystore-huks-huksparam-i.md) | 调用接口使用的options中的properties数组中的param。 |
| [HuksResult](arkts-universalkeystore-huks-huksresult-i.md) | 调用接口返回的result。 |
| [HuksReturnResult](arkts-universalkeystore-huks-huksreturnresult-i.md) | 调用接口返回的result。 |
| [HuksSessionHandle](arkts-universalkeystore-huks-hukssessionhandle-i.md) | HUKS handle结构体。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [HuksAuthAccessType](arkts-universalkeystore-huks-huksauthaccesstype-e.md) | 表示安全访问控制类型。 |
| [HuksAuthStorageLevel](arkts-universalkeystore-huks-huksauthstoragelevel-e.md) | 表示生成或导入密钥时，指定该密钥的存储安全等级。 |
| [HuksChallengePosition](arkts-universalkeystore-huks-hukschallengeposition-e.md) | 表示challenge类型为用户自定义类型时，生成的challenge有效长度仅为8字节连续的数据，且仅支持4种位置。 |
| [HuksChallengeType](arkts-universalkeystore-huks-hukschallengetype-e.md) | 表示密钥使用时生成challenge的类型。 |
| [HuksCipherMode](arkts-universalkeystore-huks-huksciphermode-e.md) | 表示加密模式。 |
| [HuksErrorCode](arkts-universalkeystore-huks-hukserrorcode-e.md) | 表示错误码的枚举。 |
| [HuksExceptionErrCode](arkts-universalkeystore-huks-huksexceptionerrcode-e.md) | 表示错误码的枚举以及对应的错误信息，错误码表示错误类型，错误信息展示错误详情。 关于错误码的具体信息，可在[通用错误码](../../errorcode-universal.md)和 [HUKS错误码](../errorcode-huks.md)中查看。 |
| [HuksImportKeyType](arkts-universalkeystore-huks-huksimportkeytype-e.md) | 表示导入密钥的密钥类型，默认为导入公钥，导入对称密钥时不需要该字段。 |
| [HuksKeyAlg](arkts-universalkeystore-huks-hukskeyalg-e.md) | 表示密钥使用的算法。 |
| [HuksKeyClassType](arkts-universalkeystore-huks-hukskeyclasstype-e.md) | 表示密钥的来源。 |
| [HuksKeyDigest](arkts-universalkeystore-huks-hukskeydigest-e.md) | 表示摘要算法。 |
| [HuksKeyFlag](arkts-universalkeystore-huks-hukskeyflag-e.md) | 表示密钥的产生方式。 |
| [HuksKeyGenerateType](arkts-universalkeystore-huks-hukskeygeneratetype-e.md) | 表示生成密钥的类型。 |
| [HuksKeyPadding](arkts-universalkeystore-huks-hukskeypadding-e.md) | 表示填充算法。 |
| [HuksKeyPurpose](arkts-universalkeystore-huks-hukskeypurpose-e.md) | 表示密钥用途。 一个密钥仅能用于单类用途，不能既用于加解密又用于签名验签。 |
| [HuksKeySecurityLevel](arkts-universalkeystore-huks-hukskeysecuritylevel-e.md) | 表示密钥安全级别的枚举。 |
| [HuksKeySize](arkts-universalkeystore-huks-hukskeysize-e.md) | 表示密钥长度。 |
| [HuksKeyStorageType](arkts-universalkeystore-huks-hukskeystoragetype-e.md) | 表示密钥存储方式。 |
| [HuksKeyWrapType](arkts-universalkeystore-huks-hukskeywraptype-e.md) | 表示密钥加密类型（加密导出或导入密钥）的枚举。 |
| [HuksRsaPssSaltLenType](arkts-universalkeystore-huks-huksrsapsssaltlentype-e.md) | 表示Rsa在签名验签、padding为pss时需指定的salt_len类型。 |
| [HuksSecureSignType](arkts-universalkeystore-huks-hukssecuresigntype-e.md) | 表示生成或导入密钥时，指定该密钥的签名类型。 |
| [HuksSendType](arkts-universalkeystore-huks-hukssendtype-e.md) | 表示发送TAG的方式。 |
| [HuksTag](arkts-universalkeystore-huks-hukstag-e.md) | 表示调用参数的Tag。 |
| [HuksTagType](arkts-universalkeystore-huks-hukstagtype-e.md) | 表示Tag的数据类型。 |
| [HuksUnwrapSuite](arkts-universalkeystore-huks-huksunwrapsuite-e.md) | 表示安全导入密钥的算法套件。 |
| [HuksUserAuthMode](arkts-universalkeystore-huks-huksuserauthmode-e.md) | 表示用户认证模式。 |
| [HuksUserAuthType](arkts-universalkeystore-huks-huksuserauthtype-e.md) | 表示用户认证类型。 |

