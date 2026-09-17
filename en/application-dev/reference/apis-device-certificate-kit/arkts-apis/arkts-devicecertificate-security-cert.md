# @ohos.security.cert(Certificate Framework)

The certificate algorithm library framework provides certificate-related APIs. The **certFramework** module depends on the basic algorithm capabilities of the Crypto framework. For details, see [cryptoFramework](../../apis-crypto-architecture-kit/arkts-apis/arkts-cryptoarchitecture-security-cryptoframework.md).

**Since:** 9

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [buildX509CertChain](arkts-devicecertificate-cert-buildx509certchain-f.md) | Builds an X.509 certificate chain with a CertChainBuildParameters object. This API uses a promise to return the result. |
| [createCertChainValidator](arkts-devicecertificate-cert-createcertchainvalidator-f.md) | Creates a **CertChainValidator** object. |
| [createCertCRLCollection](arkts-devicecertificate-cert-createcertcrlcollection-f.md) | Creates an object for a collection of X.509 certificates and CRLs. |
| [createCertExtension](arkts-devicecertificate-cert-createcertextension-f.md) | Creates a certificate extension object. This API uses an asynchronous callback to return the result. |
| [createCertExtension](arkts-devicecertificate-cert-createcertextension-f.md) | Creates a certificate extension object. This API uses a promise to return the result. |
| [createCmsGenerator](arkts-devicecertificate-cert-createcmsgenerator-f.md) | Creates a **CmsGenerator** object. |
| [createCmsParser](arkts-devicecertificate-cert-createcmsparser-f.md) | Creates a **CmsParser** object. |
| [createPkcs12](arkts-devicecertificate-cert-createpkcs12-f.md) | Creates P12. This API uses a promise to return the result. |
| [createPkcs12Sync](arkts-devicecertificate-cert-createpkcs12sync-f.md) | Creates P12. This API returns the result synchronously. |
| [createTrustAnchorsWithKeyStore](arkts-devicecertificate-cert-createtrustanchorswithkeystore-f.md) | Creates a [TrustAnchor](arkts-devicecertificate-cert-x509trustanchor-i.md) object array by using the CA certificate parsed from a .p12 keystore file. This API uses a promise to return the result. |
| [createX500DistinguishedName](arkts-devicecertificate-cert-createx500distinguishedname-f.md) | Creates an **X500DistinguishedName** object with a name in the form of a string. This API uses a promise to return the result. |
| [createX500DistinguishedName](arkts-devicecertificate-cert-createx500distinguishedname-f.md) | Creates an **X500DistinguishedName** object with a name in DER format. This API uses a promise to return the result. |
| [createX509Cert](arkts-devicecertificate-cert-createx509cert-f.md) | Creates an **X509Cert** instance. This API uses an asynchronous callback to return the result. |
| [createX509Cert](arkts-devicecertificate-cert-createx509cert-f.md) | Creates an **X509Cert** instance. This API uses a promise to return the result. |
| [createX509CertChain](arkts-devicecertificate-cert-createx509certchain-f.md) | Creates an **X509CertChain** instance. This API uses a promise to return the result. |
| [createX509CertChain](arkts-devicecertificate-cert-createx509certchain-f.md) | Creates an **X509CertChain** instance. This API uses an asynchronous callback to return the result. |
| [createX509CertChain](arkts-devicecertificate-cert-createx509certchain-f.md) | Creates an X.509 certificate chain object based on the specified certificates. This API returns the result synchronously. |
| [createX509Crl](arkts-devicecertificate-cert-createx509crl-depr-f.md#createx509crl) | Creates an **X509Crl** instance. This API uses an asynchronous callback to return the result. |
| [createX509Crl](arkts-devicecertificate-cert-createx509crl-depr-f.md#createx509crl) | Creates an **X509Crl** instance. This API uses a promise to return the result. |
| [createX509CRL](arkts-devicecertificate-cert-createx509crl-f.md) | Creates an **X509CRL** instance. This API uses an asynchronous callback to return the result. |
| [createX509CRL](arkts-devicecertificate-cert-createx509crl-f.md) | Creates an **X509CRL** instance. This API uses a promise to return the result. |
| [generateCsr](arkts-devicecertificate-cert-generatecsr-f.md) | Generates a CSR. |
| [parsePkcs12](arkts-devicecertificate-cert-parsepkcs12-f.md) | Parses P12. |
| [parsePkcs12](arkts-devicecertificate-cert-parsepkcs12-f.md) | Parses P12. This API uses a promise to return the result. |

### Interfaces

| Name | Description |
| --- | --- |
| [CertChainBuildParameters](arkts-devicecertificate-cert-certchainbuildparameters-i.md) | Represents the parameters for building a certificate chain. |
| [CertChainBuildResult](arkts-devicecertificate-cert-certchainbuildresult-i.md) | Represents the certificate chain build result. |
| [CertChainData](arkts-devicecertificate-cert-certchaindata-i.md) | Defines the certificate chain data, which is passed in as input parameters during certificate chain verification. |
| [CertChainValidationParameters](arkts-devicecertificate-cert-certchainvalidationparameters-i.md) | Represents the parameters for certificate chain validation. |
| [CertChainValidationResult](arkts-devicecertificate-cert-certchainvalidationresult-i.md) | Represents the return value of certificate chain validation. |
| [CertChainValidator](arkts-devicecertificate-cert-certchainvalidator-i.md) | Provides APIs for certificate chain validator operations. |
| [CertCRLCollection](arkts-devicecertificate-cert-certcrlcollection-i.md) | Provides APIs for locating certificates or CRLs in a **CertCRLCollection** object. |
| [CertExtension](arkts-devicecertificate-cert-certextension-i.md) | Provides APIs for operating on certificate extensions. |
| [CertValidationParams](arkts-devicecertificate-cert-certvalidationparams-i.md) | Parameters for certificate validation. |
| [CertValidationResult](arkts-devicecertificate-cert-certvalidationresult-i.md) | Result of certificate validation. |
| [CmsEnvelopedDecryptionConfig](arkts-devicecertificate-cert-cmsenvelopeddecryptionconfig-i.md) | Configuration used for decrypting CMS enveloped data. |
| [CmsGenerator](arkts-devicecertificate-cert-cmsgenerator-i.md) | Provides APIs for generating the messages in CMS format. |
| [CmsGeneratorOptions](arkts-devicecertificate-cert-cmsgeneratoroptions-i.md) | Represents the configuration for generating a CMS message. |
| [CmsKeyAgreeRecipientInfo](arkts-devicecertificate-cert-cmskeyagreerecipientinfo-i.md) | Represents KeyAgree recipient information for CMS enveloped data. |
| [CmsKeyTransRecipientInfo](arkts-devicecertificate-cert-cmskeytransrecipientinfo-i.md) | Represents KeyTrans recipient information for CMS enveloped data. |
| [CmsParser](arkts-devicecertificate-cert-cmsparser-i.md) | Provides APIs for parsing, verifying, and decrypting CMS messages. |
| [CmsRecipientInfo](arkts-devicecertificate-cert-cmsrecipientinfo-i.md) | Represents recipient information for the CMS message. |
| [CmsSignerConfig](arkts-devicecertificate-cert-cmssignerconfig-i.md) | Represents the configuration of the CMS signer. |
| [CmsVerificationConfig](arkts-devicecertificate-cert-cmsverificationconfig-i.md) | Represents CMS verification configuration. |
| [CsrAttribute](arkts-devicecertificate-cert-csrattribute-i.md) | Defines the CSR attribute representation. |
| [CsrGenerationConfig](arkts-devicecertificate-cert-csrgenerationconfig-i.md) | Configuration parameters for generating a CSR, including the subject name, digest algorithm, attribute, and output format. |
| [DataArray](arkts-devicecertificate-cert-dataarray-i.md) | Defines a list of data arrays. |
| [DataBlob](arkts-devicecertificate-cert-datablob-i.md) | Encapsulates binary data. The core field **data** is of the Uint8Array type. |
| [EncodingBlob](arkts-devicecertificate-cert-encodingblob-i.md) | Represents an encoded binary data block. |
| [GeneralName](arkts-devicecertificate-cert-generalname-i.md) | Represents an X.509 GeneralName as defined in RFC 5280, which can appear in Subject Alternative Name and other extensions. |
| [PbesParams](arkts-devicecertificate-cert-pbesparams-i.md) | Represents PBES algorithm parameters. Currently, only PBES2 is supported. |
| [Pkcs12CreationConfig](arkts-devicecertificate-cert-pkcs12creationconfig-i.md) | Represents the configuration for creating .p12 files. |
| [Pkcs12Data](arkts-devicecertificate-cert-pkcs12data-i.md) | P12(PKCS #12) data, which includes private key, certificate, and other certificates. |
| [Pkcs12ParsingConfig](arkts-devicecertificate-cert-pkcs12parsingconfig-i.md) | Represents the configuration for parsing P12. |
| [PrivateKeyInfo](arkts-devicecertificate-cert-privatekeyinfo-i.md) | Represents the private key information. |
| [RevocationCheckParameter](arkts-devicecertificate-cert-revocationcheckparameter-i.md) | Represents the parameters for checking the certificate revocation status for a certificate chain. |
| [X500DistinguishedName](arkts-devicecertificate-cert-x500distinguishedname-i.md) | Provides APIs for X.500 distinguished name operations. |
| [X509Cert](arkts-devicecertificate-cert-x509cert-i.md) | Provides APIs for X.509 certificate operations. |
| [X509CertChain](arkts-devicecertificate-cert-x509certchain-i.md) | Provides APIs for managing the X.509 certificate chain. |
| [X509CertMatchParameters](arkts-devicecertificate-cert-x509certmatchparameters-i.md) | Defines the parameters used to match a certificate. If no parameter is specified, all certificates are matched. |
| [X509CertRevokedParams](arkts-devicecertificate-cert-x509certrevokedparams-i.md) | Parameters for checking certificate revocation status. |
| [X509Crl](arkts-devicecertificate-cert-x509crl-depr-i.md) | Provides APIs for X.509 CRL operations. |
| [X509CRL](arkts-devicecertificate-cert-x509crl-i.md) | Provides APIs for X.509 CRL operations. |
| [X509CrlEntry](arkts-devicecertificate-cert-x509crlentry-depr-i.md) | Provides APIs for operating on a revoked certificate entry in a CRL. |
| [X509CRLEntry](arkts-devicecertificate-cert-x509crlentry-i.md) | Provides APIs for operating on a revoked certificate entry in a CRL. |
| [X509CRLMatchParameters](arkts-devicecertificate-cert-x509crlmatchparameters-i.md) | Represents the parameters used to match a certificate revocation list (CRL). If no parameter is specified, all CRLs are matched. |
| [X509TrustAnchor](arkts-devicecertificate-cert-x509trustanchor-i.md) | Represents an X.509 trust anchor, which is used to verify the certificate chain. The certificate or public key in the trust anchor is used as the trusted root to verify the certificate chain. |

### Enums

| Name | Description |
| --- | --- |
| [CertItemType](arkts-devicecertificate-cert-certitemtype-e.md) | Enumerates the certificate fields that can be obtained. |
| [CertResult](arkts-devicecertificate-cert-certresult-e.md) | Enumerates the error codes. |
| [CertRevocationFlag](arkts-devicecertificate-cert-certrevocationflag-e.md) | Enumerates the certificate revocation flags. |
| [CmsCertType](arkts-devicecertificate-cert-cmscerttype-e.md) | Enumerates certificate types obtained from CMS. |
| [CmsContentDataFormat](arkts-devicecertificate-cert-cmscontentdataformat-e.md) | Enumerates the CMS message formats. |
| [CmsContentType](arkts-devicecertificate-cert-cmscontenttype-e.md) | Enumerates the Cryptographic Message Syntax (CMS) message types. |
| [CmsFormat](arkts-devicecertificate-cert-cmsformat-e.md) | Enumerates the CMS encoding formats. |
| [CmsKeyAgreeRecipientDigestAlgorithm](arkts-devicecertificate-cert-cmskeyagreerecipientdigestalgorithm-e.md) | Enumerates the digest algorithms of the CMS KeyAgree type. |
| [CmsRecipientEncryptionAlgorithm](arkts-devicecertificate-cert-cmsrecipientencryptionalgorithm-e.md) | Enumerates the content-encryption algorithms for CMS enveloped data. |
| [CmsRsaSignaturePadding](arkts-devicecertificate-cert-cmsrsasignaturepadding-e.md) | Enumerates the RSA CMS signature padding modes. |
| [EncodingBaseFormat](arkts-devicecertificate-cert-encodingbaseformat-e.md) | Enumerates the encoding formats for certificate-related data. |
| [EncodingFormat](arkts-devicecertificate-cert-encodingformat-e.md) | Enumerates the certificate encoding formats. |
| [EncodingType](arkts-devicecertificate-cert-encodingtype-e.md) | Enumerates the encoding formats. |
| [ExtensionEntryType](arkts-devicecertificate-cert-extensionentrytype-e.md) | Enumerates the entry types in certificate extensions that can be obtained. |
| [ExtensionOidType](arkts-devicecertificate-cert-extensionoidtype-e.md) | Enumerates the OID types of the certificate extensions that can be obtained. |
| [GeneralNameType](arkts-devicecertificate-cert-generalnametype-e.md) | Enumerates the types of GeneralName as defined in X.509, which can appear in Subject Alternative Name and other extensions. |
| [KeyUsageType](arkts-devicecertificate-cert-keyusagetype-e.md) | Enumerates the purposes for which the key in the certificate is used. |
| [OcspDigest](arkts-devicecertificate-cert-ocspdigest-e.md) | Enumerates the OCSP digest algorithm. |
| [PbesEncryptionAlgorithm](arkts-devicecertificate-cert-pbesencryptionalgorithm-e.md) | Enumerates password-based encryption scheme (PBES) algorithms. |
| [Pkcs12MacDigestAlgorithm](arkts-devicecertificate-cert-pkcs12macdigestalgorithm-e.md) | Enumerates the P12 MAC digest algorithms. |
| [RevocationCheckOptions](arkts-devicecertificate-cert-revocationcheckoptions-e.md) | Enumerates the options for checking the certificate revocation status. |
| [ValidationPolicyType](arkts-devicecertificate-cert-validationpolicytype-e.md) | Enumerates the types of the online certificate chain validation policy. |
