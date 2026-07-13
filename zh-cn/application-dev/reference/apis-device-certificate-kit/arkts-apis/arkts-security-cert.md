# @ohos.security.cert

证书算法库框架提供证书相关接口。其中，依赖加解密算法库框架的基础算法能力的部分，详细接口说明可参考
[cryptoFramework API参考](../../apis-crypto-architecture-kit/arkts-apis/arkts-security-cryptoframework.md)。

**起始版本：** 9

**系统能力：** SystemCapability.Security.Cert

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [buildX509CertChain](arkts-devicecertificate-buildx509certchain-f.md#buildx509certchain-1) | 表示使用CertChainBuildParameters对象方式创建X509证书链对象。使用Promise方式返回结果。 |
| [createCertCRLCollection](arkts-devicecertificate-createcertcrlcollection-f.md#createcertcrlcollection-1) | 表示创建证书和证书吊销列表集合对象，并返回相应的结果。 |
| [createCertChainValidator](arkts-devicecertificate-createcertchainvalidator-f.md#createcertchainvalidator-1) | 表示创建证书链校验器对象。 |
| [createCertExtension](arkts-devicecertificate-createcertextension-f.md#createcertextension-1) | 表示创建证书扩展域段的对象。使用Callback异步回调。 |
| [createCertExtension](arkts-devicecertificate-createcertextension-f.md#createcertextension-2) | 表示创建证书扩展域段的对象。使用Promise方式返回结果。 |
| [createCmsGenerator](arkts-devicecertificate-createcmsgenerator-f.md#createcmsgenerator-1) | 表示创建CmsGenerator对象。 |
| [createCmsParser](arkts-devicecertificate-createcmsparser-f.md#createcmsparser-1) | 表示创建CmsParser对象。 |
| [createPkcs12](arkts-devicecertificate-createpkcs12-f.md#createpkcs12-1) | 表示创建P12。使用Promise方式返回结果。 |
| [createPkcs12Sync](arkts-devicecertificate-createpkcs12sync-f.md#createpkcs12sync-1) | 表示创建P12，同步返回结果。 |
| [createTrustAnchorsWithKeyStore](arkts-devicecertificate-createtrustanchorswithkeystore-f.md#createtrustanchorswithkeystore-1) | 表示从P12中读取ca证书来构造[TrustAnchor](arkts-devicecertificate-x509trustanchor-i.md)对象数组。使用Promise方式返回结果。 |
| [createX500DistinguishedName](arkts-devicecertificate-createx500distinguishedname-f.md#createx500distinguishedname-1) | 表示使用字符串格式的名称创建X500DistinguishedName对象。使用Promise方式返回结果。 |
| [createX500DistinguishedName](arkts-devicecertificate-createx500distinguishedname-f.md#createx500distinguishedname-2) | 表示使用DER格式的名称创建X500DistinguishedName对象。使用Promise方式返回结果。 |
| [createX509CRL](arkts-devicecertificate-createx509crl-f.md#createx509crl-1) | 表示创建X509证书吊销列表的对象。使用Callback异步回调。 |
| [createX509CRL](arkts-devicecertificate-createx509crl-f.md#createx509crl-2) | 表示创建X509证书吊销列表的对象。使用Promise方式返回结果。 |
| [createX509Cert](arkts-devicecertificate-createx509cert-f.md#createx509cert-1) | 表示创建X509证书对象。使用Callback异步回调。 |
| [createX509Cert](arkts-devicecertificate-createx509cert-f.md#createx509cert-2) | 表示创建X509证书对象。使用Promise方式返回结果。 |
| [createX509CertChain](arkts-devicecertificate-createx509certchain-f.md#createx509certchain-1) | 表示创建X509证书链对象。使用Promise方式返回结果。 |
| [createX509CertChain](arkts-devicecertificate-createx509certchain-f.md#createx509certchain-2) | 表示创建X509证书链对象。使用Callback异步回调。 |
| [createX509CertChain](arkts-devicecertificate-createx509certchain-f.md#createx509certchain-3) | 表示使用X509Cert数组方式创建X509证书链对象，并同步返回结果。 |
| [createX509Crl](arkts-devicecertificate-createx509crl-f.md#createx509crl-1) | 表示创建X509证书吊销列表的对象。使用Callback异步回调。@link cert.createX509CRL(inStream: EncodingBlob, callback: AsyncCallback&lt;X509CRL&gt;)}替代。 |
| [createX509Crl](arkts-devicecertificate-createx509crl-f.md#createx509crl-2) | 表示创建X509证书吊销列表的对象。使用Promise方式返回结果。@link cert.createX509CRL(inStream: EncodingBlob)}替代。 |
| [generateCsr](arkts-devicecertificate-generatecsr-f.md#generatecsr-1) | 表示使用指定的私钥，传入主体、扩展、摘要算法、输出格式等配置参数去生成CSR。 |
| [parsePkcs12](arkts-devicecertificate-parsepkcs12-f.md#parsepkcs12-1) | 解析P12。 |
| [parsePkcs12](arkts-devicecertificate-parsepkcs12-f.md#parsepkcs12-2) | 解析P12。使用Promise方式返回结果。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CertCRLCollection](arkts-devicecertificate-certcrlcollection-i.md) | 证书和证书吊销列表集合对象。 |
| [CertChainBuildParameters](arkts-devicecertificate-certchainbuildparameters-i.md) | 用于指定证书链创建参数。 |
| [CertChainBuildResult](arkts-devicecertificate-certchainbuildresult-i.md) | 用于指定证书链创建结果。 |
| [CertChainData](arkts-devicecertificate-certchaindata-i.md) | 证书链数据，在证书链校验时，作为入参传入。 |
| [CertChainValidationParameters](arkts-devicecertificate-certchainvalidationparameters-i.md) | 表示证书链校验的参数。 |
| [CertChainValidationResult](arkts-devicecertificate-certchainvalidationresult-i.md) | 表示证书链校验的返回值。 |
| [CertChainValidator](arkts-devicecertificate-certchainvalidator-i.md) | 证书链校验器对象。 |
| [CertExtension](arkts-devicecertificate-certextension-i.md) | 证书扩展域段类。 |
| [CertValidationParams](arkts-devicecertificate-certvalidationparams-i.md) | 证书验证的参数。 |
| [CertValidationResult](arkts-devicecertificate-certvalidationresult-i.md) | 证书验证的结果。 |
| [CmsEnvelopedDecryptionConfig](arkts-devicecertificate-cmsenvelopeddecryptionconfig-i.md) | CMS解封装的配置。 |
| [CmsGenerator](arkts-devicecertificate-cmsgenerator-i.md) | CmsGenerator对象用于生成CMS（Cryptographic Message Syntax）格式的消息。 |
| [CmsGeneratorOptions](arkts-devicecertificate-cmsgeneratoroptions-i.md) | 表示生成CMS消息的配置选项。 |
| [CmsKeyAgreeRecipientInfo](arkts-devicecertificate-cmskeyagreerecipientinfo-i.md) | CMS封装数据的KeyAgree接收方信息。 |
| [CmsKeyTransRecipientInfo](arkts-devicecertificate-cmskeytransrecipientinfo-i.md) | CMS封装数据的KeyTrans接收方信息。 |
| [CmsParser](arkts-devicecertificate-cmsparser-i.md) | CmsParser对象用于对CMS签名或封装数据进行验签或解封装。 |
| [CmsRecipientInfo](arkts-devicecertificate-cmsrecipientinfo-i.md) | CMS封装数据的接收者信息。 |
| [CmsSignerConfig](arkts-devicecertificate-cmssignerconfig-i.md) | 表示Cms签名者的配置选项。 |
| [CmsVerificationConfig](arkts-devicecertificate-cmsverificationconfig-i.md) | CMS验签的配置。 |
| [CsrAttribute](arkts-devicecertificate-csrattribute-i.md) | 定义CSR属性表示。CSR属性字段，当前仅支持字符串类型的属性字段，属性值添加到CSR中编码为utf-8。常见的type为challengePassword。 |
| [CsrGenerationConfig](arkts-devicecertificate-csrgenerationconfig-i.md) | 用于生成CSR的配置参数，包含主体名称、扩展、摘要算法、输出格式等。 |
| [DataArray](arkts-devicecertificate-dataarray-i.md) | buffer数组的列表。 |
| [DataBlob](arkts-devicecertificate-datablob-i.md) | 二进制数据的封装接口，核心字段data为Uint8Array类型。 |
| [EncodingBlob](arkts-devicecertificate-encodingblob-i.md) | 定义编码格式的二进制数据数组。 |
| [GeneralName](arkts-devicecertificate-generalname-i.md) | 用于表示GeneralName。 |
| [PbesParams](arkts-devicecertificate-pbesparams-i.md) | 表示基于密码的加密算法参数，当前仅支持PBES2。 |
| [Pkcs12CreationConfig](arkts-devicecertificate-pkcs12creationconfig-i.md) | 表示创建P12的配置。 |
| [Pkcs12Data](arkts-devicecertificate-pkcs12data-i.md) | P12（PKCS #12）数据，包含私钥、证书和其他证书。 |
| [Pkcs12ParsingConfig](arkts-devicecertificate-pkcs12parsingconfig-i.md) | 表示解析P12的配置。 |
| [PrivateKeyInfo](arkts-devicecertificate-privatekeyinfo-i.md) | 表示私钥信息。 |
| [RevocationCheckParameter](arkts-devicecertificate-revocationcheckparameter-i.md) | 表示证书链校验证书吊销状态的参数。 |
| [X500DistinguishedName](arkts-devicecertificate-x500distinguishedname-i.md) | X509定义的Name类型的对象。 |
| [X509CRL](arkts-devicecertificate-x509crl-i.md) | X.509 CRL操作。 |
| [X509CRLEntry](arkts-devicecertificate-x509crlentry-i.md) | 证书吊销条目。 |
| [X509CRLMatchParameters](arkts-devicecertificate-x509crlmatchparameters-i.md) | 用于匹配证书吊销列表的过滤参数。如果参数中任一项都未指定，则匹配所有证书吊销列表。 |
| [X509Cert](arkts-devicecertificate-x509cert-i.md) | X509证书类。 |
| [X509CertChain](arkts-devicecertificate-x509certchain-i.md) | X509证书链对象。 |
| [X509CertMatchParameters](arkts-devicecertificate-x509certmatchparameters-i.md) | 用于匹配证书的过滤参数。如果参数中任一项都未指定，则匹配所有证书。 |
| [X509CertRevokedParams](arkts-devicecertificate-x509certrevokedparams-i.md) | 表示证书吊销检查参数。 |
| [X509Crl](arkts-devicecertificate-x509crl-i.md) | X.509 CRL操作。@link cert.X509CRL}替代。 |
| [X509CrlEntry](arkts-devicecertificate-x509crlentry-i.md) | 证书吊销条目。@link cert.X509CRLEntry}替代。 |
| [X509TrustAnchor](arkts-devicecertificate-x509trustanchor-i.md) | 表示X509信任锚，用于校验证书链。使用信任锚中的证书或者公钥作为可信根，对证书链进行校验。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CertItemType](arkts-devicecertificate-certitemtype-e.md) | 表示获取证书字段的枚举。 |
| [CertResult](arkts-devicecertificate-certresult-e.md) | 表示执行结果的枚举。 |
| [CertRevocationFlag](arkts-devicecertificate-certrevocationflag-e.md) | 表示证书吊销检查标志的枚举。 |
| [CmsCertType](arkts-devicecertificate-cmscerttype-e.md) | 从CMS中获取证书不同类型的枚举。 |
| [CmsContentDataFormat](arkts-devicecertificate-cmscontentdataformat-e.md) | 表示Cms内容数据格式的枚举。 |
| [CmsContentType](arkts-devicecertificate-cmscontenttype-e.md) | 表示Cms内容类型的枚举。 |
| [CmsFormat](arkts-devicecertificate-cmsformat-e.md) | 表示CMS编码格式的枚举。 |
| [CmsKeyAgreeRecipientDigestAlgorithm](arkts-devicecertificate-cmskeyagreerecipientdigestalgorithm-e.md) | CMS KeyAgree类型接收者摘要算法的枚举。 |
| [CmsRecipientEncryptionAlgorithm](arkts-devicecertificate-cmsrecipientencryptionalgorithm-e.md) | CMS封装数据的内容加密算法的枚举。 |
| [CmsRsaSignaturePadding](arkts-devicecertificate-cmsrsasignaturepadding-e.md) | 表示RSA类型CMS签名填充方式的枚举。 |
| [EncodingBaseFormat](arkts-devicecertificate-encodingbaseformat-e.md) | 表示生成证书相关数据的编码格式的枚举。 |
| [EncodingFormat](arkts-devicecertificate-encodingformat-e.md) | 表示证书编码格式的枚举。 |
| [EncodingType](arkts-devicecertificate-encodingtype-e.md) | 表示编码格式的枚举。 |
| [ExtensionEntryType](arkts-devicecertificate-extensionentrytype-e.md) | 表示获取扩展域中对象类型的枚举。 |
| [ExtensionOidType](arkts-devicecertificate-extensionoidtype-e.md) | 表示获取扩展域中对象标识符类型的枚举。 |
| [GeneralNameType](arkts-devicecertificate-generalnametype-e.md) | X.509中定义的GeneralName类型的枚举，这些类型可出现在“使用者备用名称”（Subject Alternative Name）及其他扩展项中。 |
| [KeyUsageType](arkts-devicecertificate-keyusagetype-e.md) | 表示证书中密钥用途的枚举。 |
| [OcspDigest](arkts-devicecertificate-ocspdigest-e.md) | 表示OCSP摘要算法的枚举。 |
| [PbesEncryptionAlgorithm](arkts-devicecertificate-pbesencryptionalgorithm-e.md) | 表示基于密码的加密算法枚举。 |
| [Pkcs12MacDigestAlgorithm](arkts-devicecertificate-pkcs12macdigestalgorithm-e.md) | 表示P12的MAC摘要算法枚举。 |
| [RevocationCheckOptions](arkts-devicecertificate-revocationcheckoptions-e.md) | 表示证书链在线校验证书吊销状态选项的枚举。 |
| [ValidationPolicyType](arkts-devicecertificate-validationpolicytype-e.md) | 表示证书链在线校验策略的枚举。 |

