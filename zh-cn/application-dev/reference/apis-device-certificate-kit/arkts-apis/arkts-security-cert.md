# @ohos.security.cert

证书算法库框架提供证书相关接口。其中，依赖加解密算法库框架的基础算法能力的部分，详细接口说明可参考
[cryptoFramework API参考](../../apis-crypto-architecture-kit/arkts-apis/arkts-security-cryptoframework.md#cryptoFramework)。

**起始版本：** 9

**系统能力：** SystemCapability.Security.Cert

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [buildX509CertChain](arkts-devicecertificate-cert-buildx509certchain-f.md#buildX509CertChain-1) | 表示使用CertChainBuildParameters对象方式创建X509证书链对象。使用Promise方式返回结果。<br/> |
| [createCertCRLCollection](arkts-devicecertificate-cert-createcertcrlcollection-f.md#createCertCRLCollection-1) | 表示创建证书和证书吊销列表集合对象，并返回相应的结果。<br/> |
| [createCertChainValidator](arkts-devicecertificate-cert-createcertchainvalidator-f.md#createCertChainValidator-1) | 表示创建证书链校验器对象。<br/> |
| [createCertExtension](arkts-devicecertificate-cert-createcertextension-f.md#createCertExtension-1) | 表示创建证书扩展域段的对象。使用Callback异步回调。<br/> |
| [createCertExtension](arkts-devicecertificate-cert-createcertextension-f.md#createCertExtension-2) | 表示创建证书扩展域段的对象。使用Promise方式返回结果。<br/> |
| [createCmsGenerator](arkts-devicecertificate-cert-createcmsgenerator-f.md#createCmsGenerator-1) | 表示创建CmsGenerator对象。<br/> |
| [createCmsParser](arkts-devicecertificate-cert-createcmsparser-f.md#createCmsParser-1) | 表示创建CmsParser对象。<br/> |
| [createPkcs12](arkts-devicecertificate-cert-createpkcs12-f.md#createPkcs12-1) | 表示创建Pkcs12数据。使用Promise方式返回结果。<br/> |
| [createPkcs12Sync](arkts-devicecertificate-cert-createpkcs12sync-f.md#createPkcs12Sync-1) | 表示创建Pkcs12数据，同步返回结果。<br/> |
| [createTrustAnchorsWithKeyStore](arkts-devicecertificate-cert-createtrustanchorswithkeystore-f.md#createTrustAnchorsWithKeyStore-1) | 表示从P12文件中读取ca证书来构造[TrustAnchor](arkts-devicecertificate-cert-x509trustanchor-i.md#X509TrustAnchor)对象数组。使用Promise方式返回结果。<br/> |
| [createX500DistinguishedName](arkts-devicecertificate-cert-createx500distinguishedname-f.md#createX500DistinguishedName-1) | 表示使用字符串格式的名称创建X500DistinguishedName对象。使用Promise方式返回结果。<br/> |
| [createX500DistinguishedName](arkts-devicecertificate-cert-createx500distinguishedname-f.md#createX500DistinguishedName-2) | 表示使用DER格式的名称创建X500DistinguishedName对象。使用Promise方式返回结果。<br/> |
| [createX509CRL](arkts-devicecertificate-cert-createx509crl-f.md#createX509CRL-1) | 表示创建X509证书吊销列表的对象。使用Callback异步回调。<br/> |
| [createX509CRL](arkts-devicecertificate-cert-createx509crl-f.md#createX509CRL-2) | 表示创建X509证书吊销列表的对象。使用Promise方式返回结果。<br/> |
| [createX509Cert](arkts-devicecertificate-cert-createx509cert-f.md#createX509Cert-1) | 表示创建X509证书对象。使用Callback异步回调。<br/> |
| [createX509Cert](arkts-devicecertificate-cert-createx509cert-f.md#createX509Cert-2) | 表示创建X509证书对象。使用Promise方式返回结果。<br/> |
| [createX509CertChain](arkts-devicecertificate-cert-createx509certchain-f.md#createX509CertChain-1) | 表示创建X509证书链对象。使用Promise方式返回结果。<br/> |
| [createX509CertChain](arkts-devicecertificate-cert-createx509certchain-f.md#createX509CertChain-2) | 表示创建X509证书链对象。使用Callback异步回调。<br/> |
| [createX509CertChain](arkts-devicecertificate-cert-createx509certchain-f.md#createX509CertChain-3) | 表示使用X509Cert数组方式创建X509证书链对象，并同步返回结果。<br/> |
| [createX509Crl](arkts-devicecertificate-cert-createx509crl-f.md#createX509Crl-1) | 表示创建X509证书吊销列表的对象。使用Callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 9开始支持，从API version 11开始废弃，建议使用<br/>&gt; [cert.createX509CRL()](cert.createX509CRL(inStream: EncodingBlob, callback: AsyncCallback&lt;X509CRL&gt;))替代。<br/> |
| [createX509Crl](arkts-devicecertificate-cert-createx509crl-f.md#createX509Crl-2) | 表示创建X509证书吊销列表的对象。使用Promise方式返回结果。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 9开始支持，从API version 11开始废弃，建议使用[cert.createX509CRL()](arkts-devicecertificate-cert-createx509crl-f.md#createX509CRL-2)<br/>&gt; 替代。<br/> |
| [generateCsr](arkts-devicecertificate-cert-generatecsr-f.md#generateCsr-1) | 表示使用指定的RSA私钥，传入主体、扩展、摘要算法、输出格式等配置参数去生成CSR。<br/> |
| [parsePkcs12](arkts-devicecertificate-cert-parsepkcs12-f.md#parsePkcs12-1) | 表示从P12文件中解析证书、私钥及其他证书合集，并返回结果。<br/> |
| [parsePkcs12](arkts-devicecertificate-cert-parsepkcs12-f.md#parsePkcs12-2) | 表示从Pkcs12文件中解析证书、私钥及其他证书合集。使用Promise方式返回结果。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CertCRLCollection](arkts-devicecertificate-cert-certcrlcollection-i.md) | 证书和证书吊销列表集合对象。<br/> |
| [CertChainBuildParameters](arkts-devicecertificate-cert-certchainbuildparameters-i.md) | 用于指定证书链创建参数。<br/> |
| [CertChainBuildResult](arkts-devicecertificate-cert-certchainbuildresult-i.md) | 用于指定证书链创建结果。<br/> |
| [CertChainData](arkts-devicecertificate-cert-certchaindata-i.md) | 证书链数据，在证书链校验时，作为入参传入。<br/> |
| [CertChainValidationParameters](arkts-devicecertificate-cert-certchainvalidationparameters-i.md) | 表示证书链校验的参数。<br/> |
| [CertChainValidationResult](arkts-devicecertificate-cert-certchainvalidationresult-i.md) | 表示证书链校验的返回值。<br/> |
| [CertChainValidator](arkts-devicecertificate-cert-certchainvalidator-i.md) | 证书链校验器对象。<br/> |
| [CertExtension](arkts-devicecertificate-cert-certextension-i.md) | 证书扩展域段类。<br/> |
| [CertValidationParams](arkts-devicecertificate-cert-certvalidationparams-i.md) | 证书验证的参数。<br/> |
| [CertValidationResult](arkts-devicecertificate-cert-certvalidationresult-i.md) | 证书验证的结果。<br/> |
| [CmsEnvelopedDecryptionConfig](arkts-devicecertificate-cert-cmsenvelopeddecryptionconfig-i.md) | CMS解封装的配置。<br/> |
| [CmsGenerator](arkts-devicecertificate-cert-cmsgenerator-i.md) | CmsGenerator对象用于生成CMS（Cryptographic Message Syntax）格式的消息。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; PKCS#7是用于存储签名或加密数据的标准语法。注意CMS是PKCS#7的扩展，PKCS#7支持的数据类型包括数据、签名数据、信封数据、<br/>&gt; 签名和信封数据、摘要数据、加密数据。常用于保护数据的完整性和机密性。<br/> |
| [CmsGeneratorOptions](arkts-devicecertificate-cert-cmsgeneratoroptions-i.md) | 表示生成Cms签名结果的配置选项。<br/> |
| [CmsKeyAgreeRecipientInfo](arkts-devicecertificate-cert-cmskeyagreerecipientinfo-i.md) | CMS封装数据的KeyAgree接收方信息。<br/> |
| [CmsKeyTransRecipientInfo](arkts-devicecertificate-cert-cmskeytransrecipientinfo-i.md) | CMS封装数据的KeyTrans接收方信息。<br/> |
| [CmsParser](arkts-devicecertificate-cert-cmsparser-i.md) | CmsParser对象用于对已签名跟封装的CMS（Cryptographic Message Syntax）格式的消息进行验签和解封装。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; PKCS#7是用于存储签名或加密数据的标准语法。注意CMS是PKCS#7的扩展，PKCS#7支持的数据类型包括数据、签名数据、信封数据、<br/>&gt; 签名和信封数据、摘要数据、加密数据。常用于保护数据的完整性和机密性。<br/> |
| [CmsRecipientInfo](arkts-devicecertificate-cert-cmsrecipientinfo-i.md) | CMS封装数据的接收者信息。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 至少需要设置一个接收者。<br/> |
| [CmsSignerConfig](arkts-devicecertificate-cert-cmssignerconfig-i.md) | 表示Cms签名者的配置选项。<br/> |
| [CmsVerificationConfig](arkts-devicecertificate-cert-cmsverificationconfig-i.md) | CMS验证的配置。<br/> |
| [CsrAttribute](arkts-devicecertificate-cert-csrattribute-i.md) | 定义CSR属性表示。<br/><br/>CSR属性字段，当前仅支持字符串类型的属性字段，属性值添加到CSR中编码为utf-8。常见的type为challengePassword。<br/> |
| [CsrGenerationConfig](arkts-devicecertificate-cert-csrgenerationconfig-i.md) | RSA私钥生成CSR时的配置参数，包含主体、扩展、摘要算法、输出格式等。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; - subject是X509定义的Name类型的对象。<br/>&gt;<br/>&gt; - mdName是摘要算法名，当前支持SHA1、SHA256、SHA384、SHA512。<br/>&gt;<br/>&gt; - attributes是可选参数，指定**PKCS #9**中规定的扩展类型跟扩展值生成CSR。例如challengePassword。<br/>&gt;<br/>&gt; - outFormat指定输出CSR的格式，若不指定默认为PEM格式。<br/> |
| [DataArray](arkts-devicecertificate-cert-dataarray-i.md) | buffer数组的列表。<br/> |
| [DataBlob](arkts-devicecertificate-cert-datablob-i.md) | 二进制数据的封装接口，核心字段data为Uint8Array类型。<br/> |
| [EncodingBlob](arkts-devicecertificate-cert-encodingblob-i.md) | 带编码格式的证书二进制数组。<br/> |
| [GeneralName](arkts-devicecertificate-cert-generalname-i.md) | 用于表示证书主体信息对象。<br/> |
| [PbesParams](arkts-devicecertificate-cert-pbesparams-i.md) | 表示基于密码的加密算法参数，当前仅支持PBES2。<br/> |
| [Pkcs12CreationConfig](arkts-devicecertificate-cert-pkcs12creationconfig-i.md) | 表示创建P12文件的配置。<br/> |
| [Pkcs12Data](arkts-devicecertificate-cert-pkcs12data-i.md) | 表示返回P12文件的解析后的证书、私钥及其他证书合集。<br/> |
| [Pkcs12ParsingConfig](arkts-devicecertificate-cert-pkcs12parsingconfig-i.md) | 表示解析P12文件的配置。<br/> |
| [PrivateKeyInfo](arkts-devicecertificate-cert-privatekeyinfo-i.md) | 表示私钥信息。<br/> |
| [RevocationCheckParameter](arkts-devicecertificate-cert-revocationcheckparameter-i.md) | 表示证书链校验证书吊销状态的参数。<br/> |
| [X500DistinguishedName](arkts-devicecertificate-cert-x500distinguishedname-i.md) | X509定义的Name类型的对象。<br/> |
| [X509CRL](arkts-devicecertificate-cert-x509crl-i.md) | 被吊销证书列表对象。<br/> |
| [X509CRLEntry](arkts-devicecertificate-cert-x509crlentry-i.md) | 被吊销证书对象。<br/> |
| [X509CRLMatchParameters](arkts-devicecertificate-cert-x509crlmatchparameters-i.md) | 用于匹配证书吊销列表的过滤参数。如果参数中任一项都未指定，则匹配所有证书吊销列表。<br/> |
| [X509Cert](arkts-devicecertificate-cert-x509cert-i.md) | X509证书类。<br/> |
| [X509CertChain](arkts-devicecertificate-cert-x509certchain-i.md) | X509证书链对象。<br/> |
| [X509CertMatchParameters](arkts-devicecertificate-cert-x509certmatchparameters-i.md) | 用于匹配证书的过滤参数。如果参数中任一项都未指定，则匹配所有证书。<br/> |
| [X509CertRevokedParams](arkts-devicecertificate-cert-x509certrevokedparams-i.md) | 表示证书吊销检查参数。<br/> |
| [X509Crl](arkts-devicecertificate-cert-x509crl-i.md) | X509证书吊销列表对象。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 9开始支持，从API version 11开始废弃，建议使用[X509CRL()](arkts-devicecertificate-cert-x509crl-i.md#X509CRL)替代。<br/> |
| [X509CrlEntry](arkts-devicecertificate-cert-x509crlentry-i.md) | 被吊销证书对象。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 9开始支持，从API version 11开始废弃，建议使用[X509CRLEntry()](arkts-devicecertificate-cert-x509crlentry-i.md#X509CRLEntry)替代。<br/> |
| [X509TrustAnchor](arkts-devicecertificate-cert-x509trustanchor-i.md) | 表示X509信任锚，用于校验证书链。使用信任锚中的证书或者公钥作为可信根，对证书链进行校验。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CertItemType](arkts-devicecertificate-cert-certitemtype-e.md) | 表示获取证书字段的枚举。<br/> |
| [CertResult](arkts-devicecertificate-cert-certresult-e.md) | 表示执行结果的枚举。<br/> |
| [CertRevocationFlag](arkts-devicecertificate-cert-certrevocationflag-e.md) | 表示证书吊销检查标志的枚举。<br/> |
| [CmsCertType](arkts-devicecertificate-cert-cmscerttype-e.md) | 从CMS中获取证书不同类型的枚举。<br/> |
| [CmsContentDataFormat](arkts-devicecertificate-cert-cmscontentdataformat-e.md) | 表示Cms内容数据格式的枚举。<br/> |
| [CmsContentType](arkts-devicecertificate-cert-cmscontenttype-e.md) | 表示Cms内容类型的枚举。<br/> |
| [CmsFormat](arkts-devicecertificate-cert-cmsformat-e.md) | 表示Cms签名格式的枚举。<br/> |
| [CmsKeyAgreeRecipientDigestAlgorithm](arkts-devicecertificate-cert-cmskeyagreerecipientdigestalgorithm-e.md) | CMS KeyAgree类型接收者摘要算法的枚举。<br/> |
| [CmsRecipientEncryptionAlgorithm](arkts-devicecertificate-cert-cmsrecipientencryptionalgorithm-e.md) | CMS接收者对称算法的枚举。<br/> |
| [CmsRsaSignaturePadding](arkts-devicecertificate-cert-cmsrsasignaturepadding-e.md) | 表示RSA类型CMS签名填充方式的枚举。<br/> |
| [EncodingBaseFormat](arkts-devicecertificate-cert-encodingbaseformat-e.md) | 表示生成CSR的编码格式的枚举。<br/> |
| [EncodingFormat](arkts-devicecertificate-cert-encodingformat-e.md) | 表示证书编码格式的枚举。<br/> |
| [EncodingType](arkts-devicecertificate-cert-encodingtype-e.md) | 表示编码格式的枚举。<br/> |
| [ExtensionEntryType](arkts-devicecertificate-cert-extensionentrytype-e.md) | 表示获取扩展域中对象类型的枚举。<br/> |
| [ExtensionOidType](arkts-devicecertificate-cert-extensionoidtype-e.md) | 表示获取扩展域中对象标识符类型的枚举。<br/> |
| [GeneralNameType](arkts-devicecertificate-cert-generalnametype-e.md) | 表示证书主体用途的枚举。<br/> |
| [KeyUsageType](arkts-devicecertificate-cert-keyusagetype-e.md) | 表示证书中密钥用途的枚举。<br/> |
| [OcspDigest](arkts-devicecertificate-cert-ocspdigest-e.md) | 表示OCSP摘要算法的枚举。<br/> |
| [PbesEncryptionAlgorithm](arkts-devicecertificate-cert-pbesencryptionalgorithm-e.md) | 表示基于密码的加密算法枚举。<br/> |
| [Pkcs12MacDigestAlgorithm](arkts-devicecertificate-cert-pkcs12macdigestalgorithm-e.md) | 表示PKCS12 MAC摘要算法枚举。<br/> |
| [RevocationCheckOptions](arkts-devicecertificate-cert-revocationcheckoptions-e.md) | 表示证书链在线校验证书吊销状态选项的枚举。<br/> |
| [ValidationPolicyType](arkts-devicecertificate-cert-validationpolicytype-e.md) | 表示证书链在线校验策略的枚举。<br/> |

