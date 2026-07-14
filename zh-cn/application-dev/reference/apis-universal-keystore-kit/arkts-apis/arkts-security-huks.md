# @ohos.security.huks

向应用提供密钥库能力，包括密钥管理及密钥的密码学操作等功能。

HUKS所管理的密钥可以由应用导入或者由应用调用HUKS接口生成。

**起始版本：** 8

**系统能力：** SystemCapability.Security.Huks.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [abort](arkts-universalkeystore-abort-f.md#abort-1) | abort终止密钥操作。使用callback异步回调。@link huks.abortSession(handle: number, options: HuksOptions, callback: AsyncCallback&lt;void&gt;)}&gt; 替代。 |
| [abort](arkts-universalkeystore-abort-f.md#abort-2) | abort终止密钥操作。使用Promise异步回调。@link huks.abortSession(handle: number, options: HuksOptions)}替代。 |
| [abortSession](arkts-universalkeystore-abortsession-f.md#abortsession-1) | abortSession终止密钥操作。使用callback异步回调。 |
| [abortSession](arkts-universalkeystore-abortsession-f.md#abortsession-2) | abortSession终止密钥操作。使用Promise异步回调。 |
| [anonAttestKeyItem](arkts-universalkeystore-anonattestkeyitem-f.md#anonattestkeyitem-1) | 获取匿名化密钥证书。使用callback异步回调。该操作需要联网进行，且耗时较长。返回12000012错误码时，可能是由于网络异常导致。此时如果没有联网，需要提示用户网络没有连接，如果已经联网，可能是由于网络抖动导致失败，建议重试。&lt;!--RP1--&gt;&lt;!--RP1End--&gt; |
| [anonAttestKeyItem](arkts-universalkeystore-anonattestkeyitem-f.md#anonattestkeyitem-2) | 获取匿名化密钥证书。使用Promise异步回调。该操作需要联网进行，且耗时较长。返回12000012错误码时，可能是由于网络异常导致。此时如果没有联网，需要提示用户网络没有连接，如果已经联网，可能是由于网络抖动导致失败，建议重试。&lt;!--RP1--&gt;&lt;!--RP1End--&gt; |
| [anonAttestKeyItemOffline](arkts-universalkeystore-anonattestkeyitemoffline-f.md#anonattestkeyitemoffline-1) | 离线模式下获取匿名化密钥证书。使用Promise异步回调。 |
| [attestKeyItem](arkts-universalkeystore-attestkeyitem-f.md#attestkeyitem-1) | 获取密钥证书。使用callback异步回调。&lt;!--RP6--&gt; |
| [attestKeyItem](arkts-universalkeystore-attestkeyitem-f.md#attestkeyitem-2) | 获取密钥证书。使用Promise异步回调。&lt;!--RP6--&gt; |
| [decapsulate](arkts-universalkeystore-decapsulate-f.md#decapsulate-1) | Post-Quantum Cryptography密钥解封装操作，支持HUKS密钥管理或由应用程序本身决定。如果应用程序选择管理密钥，对称密钥包含在HuksReturnResult的outData字段中。 |
| [deleteKey](arkts-universalkeystore-deletekey-f.md#deletekey-1) | 删除密钥。使用callback异步回调。@link huks.deleteKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback&lt;void&gt;)}&gt; 替代。 |
| [deleteKey](arkts-universalkeystore-deletekey-f.md#deletekey-2) | 删除密钥。使用Promise异步回调。@link huks.deleteKeyItem(keyAlias: string, options: HuksOptions)}替代。 |
| [deleteKeyItem](arkts-universalkeystore-deletekeyitem-f.md#deletekeyitem-1) | 删除密钥。使用callback异步回调。 |
| [deleteKeyItem](arkts-universalkeystore-deletekeyitem-f.md#deletekeyitem-2) | 删除密钥。使用Promise异步回调。 |
| [encapsulate](arkts-universalkeystore-encapsulate-f.md#encapsulate-1) | 后量子加密密钥封装操作，支持HUKS密钥管理或由应用程序本身决定。如果应用程序选择管理密钥，对称密钥携带在HuksReturnResult的outData字段中。 |
| [exportKey](arkts-universalkeystore-exportkey-f.md#exportkey-1) | 导出密钥，使用Callback方式回调异步返回的结果。@link huks.exportKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback&lt;HuksReturnResult&gt;)}&gt; 替代。 |
| [exportKey](arkts-universalkeystore-exportkey-f.md#exportkey-2) | 导出密钥。使用Promise异步回调。@link huks.exportKeyItem(keyAlias: string, options: HuksOptions)}替代。 |
| [exportKeyItem](arkts-universalkeystore-exportkeyitem-f.md#exportkeyitem-1) | 导出密钥。使用callback异步回调。 |
| [exportKeyItem](arkts-universalkeystore-exportkeyitem-f.md#exportkeyitem-2) | 导出密钥。使用Promise异步回调。 |
| [finish](arkts-universalkeystore-finish-f.md#finish-1) | finish操作密钥接口。使用callback异步回调。huks.init、huks.update、huks.finish为三段式接口，需要一起使用。@link huks.finishSession(handle: number, options: HuksOptions, callback: AsyncCallback&lt;HuksReturnResult&gt;)}&gt; 替代。 |
| [finish](arkts-universalkeystore-finish-f.md#finish-2) | finish操作密钥接口。使用Promise异步回调。huks.init、huks.update、huks.finish为三段式接口，需要一起使用。@link huks.finishSession( handle: number, options: HuksOptions, token: Uint8Array, callback: AsyncCallback&lt;HuksReturnResult&gt; )}&gt; 替代。 |
| [finishSession](arkts-universalkeystore-finishsession-f.md#finishsession-1) | finishSession操作密钥接口。使用callback异步回调。huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。 |
| [finishSession](arkts-universalkeystore-finishsession-f.md#finishsession-2) | Finishes the key operation. This API uses an asynchronous callback to return the result.huks.initSession, huks.updateSession, and huks.finishSession must be used together. |
| [finishSession](arkts-universalkeystore-finishsession-f.md#finishsession-3) | finishSession操作密钥接口。使用Promise异步回调。huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。 |
| [generateKey](arkts-universalkeystore-generatekey-f.md#generatekey-1) | 生成密钥。使用callback异步回调。@link huks.generateKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback&lt;void&gt;)}&gt; 替代。 |
| [generateKey](arkts-universalkeystore-generatekey-f.md#generatekey-2) | 生成密钥。使用Promise异步回调。@link huks.generateKeyItem(keyAlias: string, options: HuksOptions)}替代。 |
| [generateKeyItem](arkts-universalkeystore-generatekeyitem-f.md#generatekeyitem-1) | 生成密钥。使用callback异步回调。基于密钥不出[TEE](../../../../security/UniversalKeystoreKit/huks-concepts.md#可信执行环境tee)原则，此接口不会返回密钥材料内容，只用于表示此次调用是否成功。 |
| [generateKeyItem](arkts-universalkeystore-generatekeyitem-f.md#generatekeyitem-2) | 生成密钥。使用Promise异步回调。基于密钥不出[TEE](../../../../security/UniversalKeystoreKit/huks-concepts.md#可信执行环境tee)原则，此接口不会返回密钥材料内容，只用于表示此次调用是否成功。 |
| [getKeyItemProperties](arkts-universalkeystore-getkeyitemproperties-f.md#getkeyitemproperties-1) | Obtains key properties. This API uses an asynchronous callback to return the result. |
| [getKeyItemProperties](arkts-universalkeystore-getkeyitemproperties-f.md#getkeyitemproperties-2) | 获取密钥属性。使用Promise异步回调。 |
| [getKeyProperties](arkts-universalkeystore-getkeyproperties-f.md#getkeyproperties-1) | 获取密钥属性。使用callback异步回调。@link huks.getKeyItemProperties( keyAlias: string, options: HuksOptions, callback: AsyncCallback&lt;HuksReturnResult&gt; )}&gt; 替代。 |
| [getKeyProperties](arkts-universalkeystore-getkeyproperties-f.md#getkeyproperties-2) | 获取密钥属性。使用Promise异步回调。@link huks.getKeyItemProperties(keyAlias: string, options: HuksOptions)}&gt; 替代。 |
| [getSdkVersion](arkts-universalkeystore-getsdkversion-f.md#getsdkversion-1) | 获取当前系统sdk版本。 |
| [hasKeyItem](arkts-universalkeystore-haskeyitem-f.md#haskeyitem-1) | 判断密钥是否存在。使用callback异步回调。若密钥不存在，则通过callback返回false。 |
| [hasKeyItem](arkts-universalkeystore-haskeyitem-f.md#haskeyitem-2) | 判断密钥是否存在。使用Promise异步回调。若密钥不存在，则通过Promise返回false。 |
| [importKey](arkts-universalkeystore-importkey-f.md#importkey-1) | 导入明文密钥，使用Callback方式回调异步返回结果。@link huks.importKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback&lt;void&gt;)}&gt; 替代。 |
| [importKey](arkts-universalkeystore-importkey-f.md#importkey-2) | 导入明文密钥。使用Promise异步回调。@link huks.importKeyItem(keyAlias: string, options: HuksOptions)}替代。 |
| [importKeyItem](arkts-universalkeystore-importkeyitem-f.md#importkeyitem-1) | Imports a key in plaintext. This API uses an asynchronous callback to return the result. |
| [importKeyItem](arkts-universalkeystore-importkeyitem-f.md#importkeyitem-2) | Imports a key in plaintext. This API uses a promise to return the result. |
| [importWrappedKeyItem](arkts-universalkeystore-importwrappedkeyitem-f.md#importwrappedkeyitem-1) | Imports a wrapped key. This API uses an asynchronous callback to return the result. |
| [importWrappedKeyItem](arkts-universalkeystore-importwrappedkeyitem-f.md#importwrappedkeyitem-2) | Imports a wrapped key. This API uses a promise to return the result. |
| [init](arkts-universalkeystore-init-f.md#init-1) | init操作密钥接口。使用callback异步回调。huks.init、huks.update、huks.finish为三段式接口，需要一起使用。@link huks.initSession(keyAlias: string, options: HuksOptions)}替代。 |
| [init](arkts-universalkeystore-init-f.md#init-2) | init操作密钥接口。使用Promise异步回调。huks.init、huks.update、huks.finish为三段式接口，需要一起使用。@link huks.initSession(keyAlias: string, options: HuksOptions)}替代。 |
| [initSession](arkts-universalkeystore-initsession-f.md#initsession-1) | initSession操作密钥接口。使用callback异步回调。huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。 |
| [initSession](arkts-universalkeystore-initsession-f.md#initsession-2) | initSession操作密钥接口。使用Promise异步回调。huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。 |
| [isKeyExist](arkts-universalkeystore-iskeyexist-f.md#iskeyexist-1) | 判断密钥是否存在。使用callback异步回调。@link huks.isKeyItemExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback&lt;boolean&gt;)}&gt; 替代。 |
| [isKeyExist](arkts-universalkeystore-iskeyexist-f.md#iskeyexist-2) | 判断密钥是否存在。使用Promise异步回调。@link huks.isKeyItemExist(keyAlias: string, options: HuksOptions)}替代。 |
| [isKeyItemExist](arkts-universalkeystore-iskeyitemexist-f.md#iskeyitemexist-1) | 判断密钥是否存在。使用callback异步回调。若密钥不存在，则抛出错误码为12000011的异常。 |
| [isKeyItemExist](arkts-universalkeystore-iskeyitemexist-f.md#iskeyitemexist-2) | 判断密钥是否存在。使用Promise异步回调。若密钥不存在，则抛出错误码为12000011的异常。 |
| [listAliases](arkts-universalkeystore-listaliases-f.md#listaliases-1) | 查询密钥别名集接口。使用Promise异步回调。 |
| [unwrapKeyItem](arkts-universalkeystore-unwrapkeyitem-f.md#unwrapkeyitem-1) | 加密导入密钥。使用Promise异步回调。&lt;!--Del--&gt;该功能暂不支持。&lt;!--DelEnd--&gt; |
| [update](arkts-universalkeystore-update-f.md#update-1) | update操作密钥接口。使用callback异步回调。huks.init、huks.update、huks.finish为三段式接口，需要一起使用。@link huks.updateSession( handle: long, options: HuksOptions, token: Uint8Array, callback: AsyncCallback&lt;HuksReturnResult&gt; )}&gt; 替代。 |
| [update](arkts-universalkeystore-update-f.md#update-2) | update操作密钥接口。使用Promise异步回调。huks.init、huks.update、huks.finish为三段式接口，需要一起使用。@link huks.updateSession(handle: long, options: HuksOptions, token?: Uint8Array)}&gt; 替代。 |
| [updateSession](arkts-universalkeystore-updatesession-f.md#updatesession-1) | updateSession操作密钥接口。使用callback异步回调。huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。 |
| [updateSession](arkts-universalkeystore-updatesession-f.md#updatesession-2) | Updates the key operation by segment. This API uses an asynchronous callback to return the result.huks.initSession, huks.updateSession, and huks.finishSession must be used together. |
| [updateSession](arkts-universalkeystore-updatesession-f.md#updatesession-3) | updateSession操作密钥接口。使用Promise异步回调。huks.initSession、huks.updateSession、huks.finishSession为三段式接口，需要一起使用。 |
| [wrapKeyItem](arkts-universalkeystore-wrapkeyitem-f.md#wrapkeyitem-1) | 加密导出密钥。使用Promise异步回调。&lt;!--Del--&gt;该功能暂不支持。&lt;!--DelEnd--&gt; |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [anonAttestKeyItemAsUser](arkts-universalkeystore-anonattestkeyitemasuser-f-sys.md#anonattestkeyitemasuser-1) | 指定用户身份获取匿名化密钥证书，使用Promise方式异步返回结果。该操作需要联网进行，且耗时较长。 |
| [anonAttestKeyItemOfflineAsUser](arkts-universalkeystore-anonattestkeyitemofflineasuser-f-sys.md#anonattestkeyitemofflineasuser-1) | 离线获取匿名证明证书。该接口使用promise返回结果。此操作不需要每次都需要网络连接，比anonAttestKeyItemAsUser函数性能高。&gt; **说明**&gt; &gt;&gt; -离线密钥证明依赖于网络。您需要定期连接网络才能使用此API更新离线证书。&gt; &gt;&gt; -离线匿名密钥证明要求本地时间准确。否则，可能导致对端无法正常工作。验证证书过期。 |
| [attestKeyItemAsUser](arkts-universalkeystore-attestkeyitemasuser-f-sys.md#attestkeyitemasuser-1) | 指定用户身份获取密钥证书，使用Promise方式异步返回结果。 |
| [deleteKeyItemAsUser](arkts-universalkeystore-deletekeyitemasuser-f-sys.md#deletekeyitemasuser-1) | 指定用户身份删除密钥，使用Promise方式异步返回结果。 |
| [exportKeyItemAsUser](arkts-universalkeystore-exportkeyitemasuser-f-sys.md#exportkeyitemasuser-1) | 指定用户身份导出密钥，使用Promise方式回调异步返回的结果。 |
| [generateKeyItemAsUser](arkts-universalkeystore-generatekeyitemasuser-f-sys.md#generatekeyitemasuser-1) | 指定用户身份生成密钥，使用Promise方式异步返回结果。基于密钥不出[TEE](../../../../security/UniversalKeystoreKit/huks-concepts.md#可信执行环境tee)原则，通过promise不会返回密钥材料内容，只用于表示此次调用是否成功。 |
| [getKeyItemPropertiesAsUser](arkts-universalkeystore-getkeyitempropertiesasuser-f-sys.md#getkeyitempropertiesasuser-1) | Get properties of the key as user. |
| [hasKeyItemAsUser](arkts-universalkeystore-haskeyitemasuser-f-sys.md#haskeyitemasuser-1) | 指定用户身份判断密钥是否存在，使用Promise回调异步返回结果。 |
| [importKeyItemAsUser](arkts-universalkeystore-importkeyitemasuser-f-sys.md#importkeyitemasuser-1) | 指定用户身份导入明文密钥，使用Promise方式异步返回结果。 |
| [importWrappedKeyItemAsUser](arkts-universalkeystore-importwrappedkeyitemasuser-f-sys.md#importwrappedkeyitemasuser-1) | Import Wrapped Key As User. |
| [initSessionAsUser](arkts-universalkeystore-initsessionasuser-f-sys.md#initsessionasuser-1) | 指定用户身份操作密钥接口，使用Promise方式异步返回结果。huks.initSessionAsUser, huks.updateSession, huks.finishSession为三段式接口，需要一起使用。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [HuksHandle](arkts-universalkeystore-hukshandle-i.md) | huks Handle结构体。@link huks.HuksSessionHandle}替代。 |
| [HuksListAliasesReturnResult](arkts-universalkeystore-hukslistaliasesreturnresult-i.md) | 返回的密钥别名数组。 |
| [HuksOptions](arkts-universalkeystore-huksoptions-i.md) | 调用接口使用的options。 |
| [HuksParam](arkts-universalkeystore-huksparam-i.md) | 调用接口使用的options中的properties数组中的param。 |
| [HuksResult](arkts-universalkeystore-huksresult-i.md) | 调用接口返回的result。@link huks.HuksReturnResult}替代。&gt;&gt; - errorCode的具体信息，请参考[HUKS错误码](../../../../reference/apis-universal-keystore-kit/errorcode-huks.md)。 |
| [HuksReturnResult](arkts-universalkeystore-huksreturnresult-i.md) | 调用接口返回的result。 |
| [HuksSessionHandle](arkts-universalkeystore-hukssessionhandle-i.md) | HUKS handle结构体。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [HuksAuthAccessType](arkts-universalkeystore-huksauthaccesstype-e.md) | 表示安全访问控制类型。 |
| [HuksAuthStorageLevel](arkts-universalkeystore-huksauthstoragelevel-e.md) | 表示生成或导入密钥时，指定该密钥的存储安全等级。 |
| [HuksChallengePosition](arkts-universalkeystore-hukschallengeposition-e.md) | 表示challenge类型为用户自定义类型时，生成的challenge有效长度仅为8字节连续的数据，且仅支持4种位置。 |
| [HuksChallengeType](arkts-universalkeystore-hukschallengetype-e.md) | 表示密钥使用时生成challenge的类型。 |
| [HuksCipherMode](arkts-universalkeystore-huksciphermode-e.md) | 表示加密模式。 |
| [HuksErrorCode](arkts-universalkeystore-hukserrorcode-e.md) | 表示错误码的枚举。@link huks.HuksExceptionErrCode}替代。 |
| [HuksExceptionErrCode](arkts-universalkeystore-huksexceptionerrcode-e.md) | 表示错误码的枚举以及对应的错误信息，错误码表示错误类型，错误信息展示错误详情。关于错误码的具体信息，可在[通用错误码](../../../../reference/errorcode-universal.md)和[HUKS错误码](../../../../reference/apis-universal-keystore-kit/errorcode-huks.md)中查看。 |
| [HuksImportKeyType](arkts-universalkeystore-huksimportkeytype-e.md) | 表示导入密钥的密钥类型，默认为导入公钥，导入对称密钥时不需要该字段。 |
| [HuksKeyAlg](arkts-universalkeystore-hukskeyalg-e.md) | 表示密钥使用的算法。 |
| [HuksKeyClassType](arkts-universalkeystore-hukskeyclasstype-e.md) | 表示密钥的来源。 |
| [HuksKeyDigest](arkts-universalkeystore-hukskeydigest-e.md) | 表示摘要算法。 |
| [HuksKeyFlag](arkts-universalkeystore-hukskeyflag-e.md) | 表示密钥的产生方式。 |
| [HuksKeyGenerateType](arkts-universalkeystore-hukskeygeneratetype-e.md) | 表示生成密钥的类型。 |
| [HuksKeyPadding](arkts-universalkeystore-hukskeypadding-e.md) | 表示填充算法。 |
| [HuksKeyPurpose](arkts-universalkeystore-hukskeypurpose-e.md) | 表示密钥用途。一个密钥仅能用于单类用途，不能既用于加解密又用于签名验签。 |
| [HuksKeySecurityLevel](arkts-universalkeystore-hukskeysecuritylevel-e.md) | 表示密钥安全级别的枚举。 |
| [HuksKeySize](arkts-universalkeystore-hukskeysize-e.md) | 表示密钥长度。 |
| [HuksKeyStorageType](arkts-universalkeystore-hukskeystoragetype-e.md) | 表示密钥存储方式。 |
| [HuksKeyWrapType](arkts-universalkeystore-hukskeywraptype-e.md) | 表示密钥加密类型（加密导出或导入密钥）的枚举。 |
| [HuksRsaPssSaltLenType](arkts-universalkeystore-huksrsapsssaltlentype-e.md) | 表示Rsa在签名验签、padding为pss时需指定的salt_len类型。 |
| [HuksSecureSignType](arkts-universalkeystore-hukssecuresigntype-e.md) | 表示生成或导入密钥时，指定该密钥的签名类型。 |
| [HuksSendType](arkts-universalkeystore-hukssendtype-e.md) | 表示发送TAG的方式。 |
| [HuksTag](arkts-universalkeystore-hukstag-e.md) | 表示调用参数的Tag。 |
| [HuksTagType](arkts-universalkeystore-hukstagtype-e.md) | 表示Tag的数据类型。 |
| [HuksUnwrapSuite](arkts-universalkeystore-huksunwrapsuite-e.md) | 表示安全导入密钥的算法套件。 |
| [HuksUserAuthMode](arkts-universalkeystore-huksuserauthmode-e.md) | 表示用户认证模式。 |
| [HuksUserAuthType](arkts-universalkeystore-huksuserauthtype-e.md) | 表示用户认证类型。 |

