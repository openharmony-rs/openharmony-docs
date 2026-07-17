# @ohos.security.cert

证书算法库框架提供证书相关接口。其中，依赖加解密算法库框架的基础算法能力的部分，详细接口说明可参考[cryptoFramework API参考](../../apis-crypto-architecture-kit/arkts-apis/arkts-security-cryptoframework.md)。

**起始版本：** 9

<!--Device-unnamed-declare namespace cert--><!--Device-unnamed-declare namespace cert-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [buildX509CertChain](arkts-devicecertificate-cert-buildx509certchain-f.md#buildx509certchain-1) | 表示使用CertChainBuildParameters对象方式创建X509证书链对象。使用Promise方式返回结果。 |
| [createCertCRLCollection](arkts-devicecertificate-cert-createcertcrlcollection-f.md#createcertcrlcollection-1) | 表示创建证书和证书吊销列表集合对象，并返回相应的结果。 |
| [createCertChainValidator](arkts-devicecertificate-cert-createcertchainvalidator-f.md#createcertchainvalidator-1) | 表示创建证书链校验器对象。 |
| [createCertExtension](arkts-devicecertificate-cert-createcertextension-f.md#createcertextension-1) | 表示创建证书扩展域段的对象。使用Callback异步回调。 |
| [createCertExtension](arkts-devicecertificate-cert-createcertextension-f.md#createcertextension-2) | 表示创建证书扩展域段的对象。使用Promise方式返回结果。 |
| [createCmsGenerator](arkts-devicecertificate-cert-createcmsgenerator-f.md#createcmsgenerator-1) | 表示创建CmsGenerator对象。 |
| [createCmsParser](arkts-devicecertificate-cert-createcmsparser-f.md#createcmsparser-1) | 表示创建CmsParser对象。 |
| [createPkcs12](arkts-devicecertificate-cert-createpkcs12-f.md#createpkcs12-1) | 表示创建P12。使用Promise方式返回结果。 |
| [createPkcs12Sync](arkts-devicecertificate-cert-createpkcs12sync-f.md#createpkcs12sync-1) | 表示创建P12，同步返回结果。 |
| [createTrustAnchorsWithKeyStore](arkts-devicecertificate-cert-createtrustanchorswithkeystore-f.md#createtrustanchorswithkeystore-1) | 表示从P12中读取ca证书来构造[TrustAnchor](arkts-devicecertificate-cert-x509trustanchor-i.md)对象数组。使用Promise方式返回结果。 |
| [createX500DistinguishedName](arkts-devicecertificate-cert-createx500distinguishedname-f.md#createx500distinguishedname-1) | 表示使用字符串格式的名称创建X500DistinguishedName对象。使用Promise方式返回结果。 |
| [createX500DistinguishedName](arkts-devicecertificate-cert-createx500distinguishedname-f.md#createx500distinguishedname-2) | 表示使用DER格式的名称创建X500DistinguishedName对象。使用Promise方式返回结果。 |
| [createX509CRL](arkts-devicecertificate-cert-createx509crl-f.md#createx509crl-1) | 表示创建X509证书吊销列表的对象。使用Callback异步回调。 |
| [createX509CRL](arkts-devicecertificate-cert-createx509crl-f.md#createx509crl-2) | 表示创建X509证书吊销列表的对象。使用Promise方式返回结果。 |
| [createX509Cert](arkts-devicecertificate-cert-createx509cert-f.md#createx509cert-1) | 表示创建X509证书对象。使用Callback异步回调。 |
| [createX509Cert](arkts-devicecertificate-cert-createx509cert-f.md#createx509cert-2) | 表示创建X509证书对象。使用Promise方式返回结果。 |
| [createX509CertChain](arkts-devicecertificate-cert-createx509certchain-f.md#createx509certchain-1) | 表示创建X509证书链对象。使用Promise方式返回结果。 |
| [createX509CertChain](arkts-devicecertificate-cert-createx509certchain-f.md#createx509certchain-2) | 表示创建X509证书链对象。使用Callback异步回调。 |
| [createX509CertChain](arkts-devicecertificate-cert-createx509certchain-f.md#createx509certchain-3) | 表示使用X509Cert数组方式创建X509证书链对象，并同步返回结果。 |
| [createX509Crl](arkts-devicecertificate-cert-createx509crl-f.md#createx509crl-1) | 表示创建X509证书吊销列表的对象。使用Callback异步回调。 |
| [createX509Crl](arkts-devicecertificate-cert-createx509crl-f.md#createx509crl-2) | 表示创建X509证书吊销列表的对象。使用Promise方式返回结果。 |
| [generateCsr](arkts-devicecertificate-cert-generatecsr-f.md#generatecsr-1) | 表示使用指定的私钥，传入主体、扩展、摘要算法、输出格式等配置参数去生成CSR。 |
| [parsePkcs12](arkts-devicecertificate-cert-parsepkcs12-f.md#parsepkcs12-1) | 解析P12。 |
| [parsePkcs12](arkts-devicecertificate-cert-parsepkcs12-f.md#parsepkcs12-2) | 解析P12。使用Promise方式返回结果。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CertCRLCollection](arkts-devicecertificate-cert-certcrlcollection-i.md) | 证书和证书吊销列表集合对象。 |
| [CertChainBuildParameters](arkts-devicecertificate-cert-certchainbuildparameters-i.md) | 用于指定证书链创建参数。 |
| [CertChainBuildResult](arkts-devicecertificate-cert-certchainbuildresult-i.md) | 用于指定证书链创建结果。 |
| [CertChainData](arkts-devicecertificate-cert-certchaindata-i.md) | 证书链数据，在证书链校验时，作为入参传入。 |
| [CertChainValidationParameters](arkts-devicecertificate-cert-certchainvalidationparameters-i.md) | 表示证书链校验的参数。 |
| [CertChainValidationResult](arkts-devicecertificate-cert-certchainvalidationresult-i.md) | 表示证书链校验的返回值。 |
| [CertChainValidator](arkts-devicecertificate-cert-certchainvalidator-i.md) | 证书链校验器对象。 |
| [CertExtension](arkts-devicecertificate-cert-certextension-i.md) | 证书扩展域段类。 |
| [CertValidationParams](arkts-devicecertificate-cert-certvalidationparams-i.md) | 证书验证的参数。 |
| [CertValidationResult](arkts-devicecertificate-cert-certvalidationresult-i.md) | 证书验证的结果。 |
| [CmsEnvelopedDecryptionConfig](arkts-devicecertificate-cert-cmsenvelopeddecryptionconfig-i.md) | CMS解封装的配置。 |
| [CmsGenerator](arkts-devicecertificate-cert-cmsgenerator-i.md) | CmsGenerator对象用于生成CMS（Cryptographic Message Syntax）格式的消息。 |
| [CmsGeneratorOptions](arkts-devicecertificate-cert-cmsgeneratoroptions-i.md) | 表示生成CMS消息的配置选项。 |
| [CmsKeyAgreeRecipientInfo](arkts-devicecertificate-cert-cmskeyagreerecipientinfo-i.md) | CMS封装数据的KeyAgree接收方信息。 |
| [CmsKeyTransRecipientInfo](arkts-devicecertificate-cert-cmskeytransrecipientinfo-i.md) | CMS封装数据的KeyTrans接收方信息。 |
| [CmsParser](arkts-devicecertificate-cert-cmsparser-i.md) | CmsParser对象用于对CMS签名或封装数据进行验签或解封装。 |
| [CmsRecipientInfo](arkts-devicecertificate-cert-cmsrecipientinfo-i.md) | CMS封装数据的接收者信息。 |
| [CmsSignerConfig](arkts-devicecertificate-cert-cmssignerconfig-i.md) | 表示Cms签名者的配置选项。 |
| [CmsVerificationConfig](arkts-devicecertificate-cert-cmsverificationconfig-i.md) | CMS验签的配置。 |
| [CsrAttribute](arkts-devicecertificate-cert-csrattribute-i.md) | 定义CSR属性表示。CSR属性字段，当前仅支持字符串类型的属性字段，属性值添加到CSR中编码为utf-8。常见的type为challengePassword。 |
| [CsrGenerationConfig](arkts-devicecertificate-cert-csrgenerationconfig-i.md) | 用于生成CSR的配置参数，包含主体名称、扩展、摘要算法、输出格式等。 |
| [DataArray](arkts-devicecertificate-cert-dataarray-i.md) | buffer数组的列表。 |
| [DataBlob](arkts-devicecertificate-cert-datablob-i.md) | 二进制数据的封装接口，核心字段data为Uint8Array类型。 |
| [EncodingBlob](arkts-devicecertificate-cert-encodingblob-i.md) | 定义编码格式的二进制数据数组。 |
| [GeneralName](arkts-devicecertificate-cert-generalname-i.md) | 用于表示GeneralName。 |
| [PbesParams](arkts-devicecertificate-cert-pbesparams-i.md) | 表示基于密码的加密算法参数，当前仅支持PBES2。 |
| [Pkcs12CreationConfig](arkts-devicecertificate-cert-pkcs12creationconfig-i.md) | 表示创建P12的配置。 |
| [Pkcs12Data](arkts-devicecertificate-cert-pkcs12data-i.md) | P12（PKCS #12）数据，包含私钥、证书和其他证书。 |
| [Pkcs12ParsingConfig](arkts-devicecertificate-cert-pkcs12parsingconfig-i.md) | 表示解析P12的配置。 |
| [PrivateKeyInfo](arkts-devicecertificate-cert-privatekeyinfo-i.md) | 表示私钥信息。 |
| [RevocationCheckParameter](arkts-devicecertificate-cert-revocationcheckparameter-i.md) | 表示证书链校验证书吊销状态的参数。 |
| [X500DistinguishedName](arkts-devicecertificate-cert-x500distinguishedname-i.md) | X509定义的Name类型的对象。 |
| [X509CRL](arkts-devicecertificate-cert-x509crl-i.md) | X.509 CRL操作。 |
| [X509CRLEntry](arkts-devicecertificate-cert-x509crlentry-i.md) | 证书吊销条目。 |
| [X509CRLMatchParameters](arkts-devicecertificate-cert-x509crlmatchparameters-i.md) | 用于匹配证书吊销列表的过滤参数。如果参数中任一项都未指定，则匹配所有证书吊销列表。 |
| [X509Cert](arkts-devicecertificate-cert-x509cert-i.md) | X509证书类。 |
| [X509CertChain](arkts-devicecertificate-cert-x509certchain-i.md) | X509证书链对象。 |
| [X509CertMatchParameters](arkts-devicecertificate-cert-x509certmatchparameters-i.md) | 用于匹配证书的过滤参数。如果参数中任一项都未指定，则匹配所有证书。 |
| [X509CertRevokedParams](arkts-devicecertificate-cert-x509certrevokedparams-i.md) | 表示证书吊销检查参数。 |
| [X509Crl](arkts-devicecertificate-cert-x509crl-i.md) | X.509 CRL操作。 |
| [X509CrlEntry](arkts-devicecertificate-cert-x509crlentry-i.md) | 证书吊销条目。 |
| [X509TrustAnchor](arkts-devicecertificate-cert-x509trustanchor-i.md) | 表示X509信任锚，用于校验证书链。使用信任锚中的证书或者公钥作为可信根，对证书链进行校验。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CertItemType](arkts-devicecertificate-cert-certitemtype-e.md) | 表示获取证书字段的枚举。 |
| [CertResult](arkts-devicecertificate-cert-certresult-e.md) | 表示执行结果的枚举。 |
| [CertRevocationFlag](arkts-devicecertificate-cert-certrevocationflag-e.md) | 表示证书吊销检查标志的枚举。 |
| [CmsCertType](arkts-devicecertificate-cert-cmscerttype-e.md) | 从CMS中获取证书不同类型的枚举。 |
| [CmsContentDataFormat](arkts-devicecertificate-cert-cmscontentdataformat-e.md) | 表示Cms内容数据格式的枚举。 |
| [CmsContentType](arkts-devicecertificate-cert-cmscontenttype-e.md) | 表示Cms内容类型的枚举。 |
| [CmsFormat](arkts-devicecertificate-cert-cmsformat-e.md) | 表示CMS编码格式的枚举。 |
| [CmsKeyAgreeRecipientDigestAlgorithm](arkts-devicecertificate-cert-cmskeyagreerecipientdigestalgorithm-e.md) | CMS KeyAgree类型接收者摘要算法的枚举。 |
| [CmsRecipientEncryptionAlgorithm](arkts-devicecertificate-cert-cmsrecipientencryptionalgorithm-e.md) | CMS封装数据的内容加密算法的枚举。 |
| [CmsRsaSignaturePadding](arkts-devicecertificate-cert-cmsrsasignaturepadding-e.md) | 表示RSA类型CMS签名填充方式的枚举。 |
| [EncodingBaseFormat](arkts-devicecertificate-cert-encodingbaseformat-e.md) | 表示生成证书相关数据的编码格式的枚举。 |
| [EncodingFormat](arkts-devicecertificate-cert-encodingformat-e.md) | 表示证书编码格式的枚举。 |
| [EncodingType](arkts-devicecertificate-cert-encodingtype-e.md) | 表示编码格式的枚举。 |
| [ExtensionEntryType](arkts-devicecertificate-cert-extensionentrytype-e.md) | 表示获取扩展域中对象类型的枚举。 |
| [ExtensionOidType](arkts-devicecertificate-cert-extensionoidtype-e.md) | 表示获取扩展域中对象标识符类型的枚举。 |
| [GeneralNameType](arkts-devicecertificate-cert-generalnametype-e.md) | X.509中定义的GeneralName类型的枚举，这些类型可出现在“使用者备用名称”（Subject Alternative Name）及其他扩展项中。 |
| [KeyUsageType](arkts-devicecertificate-cert-keyusagetype-e.md) | 表示证书中密钥用途的枚举。 |
| [OcspDigest](arkts-devicecertificate-cert-ocspdigest-e.md) | 表示OCSP摘要算法的枚举。 |
| [PbesEncryptionAlgorithm](arkts-devicecertificate-cert-pbesencryptionalgorithm-e.md) | 表示基于密码的加密算法枚举。 |
| [Pkcs12MacDigestAlgorithm](arkts-devicecertificate-cert-pkcs12macdigestalgorithm-e.md) | 表示P12的MAC摘要算法枚举。 |
| [RevocationCheckOptions](arkts-devicecertificate-cert-revocationcheckoptions-e.md) | 表示证书链在线校验证书吊销状态选项的枚举。 |
| [ValidationPolicyType](arkts-devicecertificate-cert-validationpolicytype-e.md) | 表示证书链在线校验策略的枚举。 |

