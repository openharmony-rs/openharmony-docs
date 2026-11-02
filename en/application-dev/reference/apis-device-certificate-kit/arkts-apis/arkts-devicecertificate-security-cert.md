# @ohos.security.cert(Certificate Framework)

The **cert** module provides APIs for performing certificate operations. The **certFramework** module depends on the basic algorithm capabilities of the Crypto framework. For details, see [cryptoFramework](../../apis-crypto-architecture-kit/arkts-apis/arkts-cryptoarchitecture-security-cryptoframework.md).

**Since:** 9

<!--Device-unnamed-declare namespace cert--><!--Device-unnamed-declare namespace cert-End-->

**System capability:** SystemCapability.Security.Cert

## Modules to Import

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [buildX509CertChain](arkts-devicecertificate-cert-buildx509certchain-f.md#buildx509certchain-1) | Builds an X.509 certificate chain with a **CertChainBuildParameters** object. This API uses a promise to return the result. |
| [createCertChainValidator](arkts-devicecertificate-cert-createcertchainvalidator-f.md#createcertchainvalidator-1) | Creates a certificate chain validator object. |
| [createCertCRLCollection](arkts-devicecertificate-cert-createcertcrlcollection-f.md#createcertcrlcollection-1) | Creates an object for a collection of X.509 certificates and CRLs. |
| [createCertExtension](arkts-devicecertificate-cert-createcertextension-f.md#createcertextension-1) | Creates a certificate extension object. This API uses an asynchronous callback to return the result. |
| [createCertExtension](arkts-devicecertificate-cert-createcertextension-f.md#createcertextension-2) | Creates a certificate extension object. This API uses a promise to return the result. |
| [createCmsGenerator](arkts-devicecertificate-cert-createcmsgenerator-f.md#createcmsgenerator-1) | Creates a **CmsGenerator** object. |
| [createCmsParser](arkts-devicecertificate-cert-createcmsparser-f.md#createcmsparser-1) | Creates a **CmsParser** object. |
| [createPkcs12](arkts-devicecertificate-cert-createpkcs12-f.md#createpkcs12-1) | Creates P12. This API uses a promise to return the result. |
| [createPkcs12Sync](arkts-devicecertificate-cert-createpkcs12sync-f.md#createpkcs12sync-1) | Creates P12. This API returns the result synchronously. |
| [createTrustAnchorsWithKeyStore](arkts-devicecertificate-cert-createtrustanchorswithkeystore-f.md#createtrustanchorswithkeystore-1) | Creates a [TrustAnchor](arkts-devicecertificate-cert-x509trustanchor-i.md) object array by using the CA certificate parsed from a .p12 keystore file. This API uses a promise to return the result. |
| [createX500DistinguishedName](arkts-devicecertificate-cert-createx500distinguishedname-f.md#createx500distinguishedname-1) | Creates an **X500DistinguishedName** object with a name in the form of a string. This API uses a promise to return the result. |
| [createX500DistinguishedName](arkts-devicecertificate-cert-createx500distinguishedname-f.md#createx500distinguishedname-2) | Creates an **X500DistinguishedName** object with a name in DER format. This API uses a promise to return the result. |
| [createX509Cert](arkts-devicecertificate-cert-createx509cert-f.md#createx509cert-1) | Creates an X.509 certificate object. This API uses an asynchronous callback to return the result. |
| [createX509Cert](arkts-devicecertificate-cert-createx509cert-f.md#createx509cert-2) | Creates an X.509 certificate object. This API uses a promise to return the result. |
| [createX509CertChain](arkts-devicecertificate-cert-createx509certchain-f.md#createx509certchain-1) | Creates an X.509 certificate chain object. This API uses a promise to return the result. |
| [createX509CertChain](arkts-devicecertificate-cert-createx509certchain-f.md#createx509certchain-2) | Creates an X.509 certificate chain object. This API uses an asynchronous callback to return the result. |
| [createX509CertChain](arkts-devicecertificate-cert-createx509certchain-f.md#createx509certchain-3) | Creates an X.509 certificate chain object based on the specified certificates. This API returns the result synchronously. |
| [createX509CRL](arkts-devicecertificate-cert-createx509crl-f.md#createx509crl-1) | Creates an X.509 CRL object. This API uses an asynchronous callback to return the result. |
| [createX509CRL](arkts-devicecertificate-cert-createx509crl-f.md#createx509crl-2) | Creates an X.509 CRL object. This API uses a promise to return the result. |
| [generateCsr](arkts-devicecertificate-cert-generatecsr-f.md#generatecsr-1) | Generates a CSR using the specified private key by passing configuration parameters such as the subject, extension, MD algorithm, and output format. |
| [parsePkcs12](arkts-devicecertificate-cert-parsepkcs12-f.md#parsepkcs12-1) | Parse the PKCS #12 file. |
| [parsePkcs12](arkts-devicecertificate-cert-parsepkcs12-f.md#parsepkcs12-2) | Parses P12. This API uses a promise to return the result. |
| [createX509Crl](arkts-devicecertificate-cert-createx509crl-depr-f.md#createx509crl-1) | Creates an **X509Crl** instance. This API uses an asynchronous callback to return the result. |
| [createX509Crl](arkts-devicecertificate-cert-createx509crl-depr-f.md#createx509crl-2) | Creates an **X509Crl** instance. This API uses a promise to return the result. |

### Interfaces

| Name | Description |
| --- | --- |
| [CertChainBuildParameters](arkts-devicecertificate-cert-certchainbuildparameters-i.md) | Defines the parameters for building a certificate chain. |
| [CertChainBuildResult](arkts-devicecertificate-cert-certchainbuildresult-i.md) | Represents the result of building a certificate chain. |
| [CertChainData](arkts-devicecertificate-cert-certchaindata-i.md) | Defines the certificate chain data, which is passed in as input parameters during certificate chain verification. |
| [CertChainValidationParameters](arkts-devicecertificate-cert-certchainvalidationparameters-i.md) | Represents the parameters for certificate chain validation. |
| [CertChainValidationResult](arkts-devicecertificate-cert-certchainvalidationresult-i.md) | Represents the return value of certificate chain validation. |
| [CertChainValidator](arkts-devicecertificate-cert-certchainvalidator-i.md) | Describes a certificate chain validator object. |
| [CertCRLCollection](arkts-devicecertificate-cert-certcrlcollection-i.md) | Certificate and CRL collection. |
| [CertExtension](arkts-devicecertificate-cert-certextension-i.md) | Provides APIs for operating on certificate extensions. |
| [CertValidationParams](arkts-devicecertificate-cert-certvalidationparams-i.md) | Represents the parameters for certificate validation. |
| [CertValidationResult](arkts-devicecertificate-cert-certvalidationresult-i.md) | Represents the certificate verification result. |
| [CmsEnvelopedDecryptionConfig](arkts-devicecertificate-cert-cmsenvelopeddecryptionconfig-i.md) | Represents configuration for decapsulation with CMS. |
| [CmsGenerator](arkts-devicecertificate-cert-cmsgenerator-i.md) | Provide APIs for generating messages in CMS format. |
| [CmsGeneratorOptions](arkts-devicecertificate-cert-cmsgeneratoroptions-i.md) | Represents the configuration for generating a CMS message. |
| [CmsKeyAgreeRecipientInfo](arkts-devicecertificate-cert-cmskeyagreerecipientinfo-i.md) | Represents the recipient information for key agreement encapsulated using CMS. |
| [CmsKeyTransRecipientInfo](arkts-devicecertificate-cert-cmskeytransrecipientinfo-i.md) | Represents the recipient information for key transport encapsulated using CMS. |
| [CmsParser](arkts-devicecertificate-cert-cmsparser-i.md) | Provide APIs for parsing, verifying signatures, and decapsulating CMS messages. |
| [CmsRecipientInfo](arkts-devicecertificate-cert-cmsrecipientinfo-i.md) | Represents the recipient information encapsulated using CMS. |
| [CmsSignerConfig](arkts-devicecertificate-cert-cmssignerconfig-i.md) | Represents the configuration of the CMS signer. |
| [CmsVerificationConfig](arkts-devicecertificate-cert-cmsverificationconfig-i.md) | CMS signature verification configuration. |
| [CsrAttribute](arkts-devicecertificate-cert-csrattribute-i.md) | Defines the CSR attribute. |
| [CsrGenerationConfig](arkts-devicecertificate-cert-csrgenerationconfig-i.md) | Describes the configuration parameters for generating a CSR, including the subject name, extension, message digest (MD) algorithm, and output format. |
| [DataArray](arkts-devicecertificate-cert-dataarray-i.md) | Defines a list of data arrays. |
| [DataBlob](arkts-devicecertificate-cert-datablob-i.md) | Encapsulates binary data. The core field **data** is of the Uint8Array type. |
| [EncodingBlob](arkts-devicecertificate-cert-encodingblob-i.md) | Represents an encoded binary data block. |
| [GeneralName](arkts-devicecertificate-cert-generalname-i.md) | Represents an X.509 general name defined in RFC 5280, which can be used in the subject alternative name and other extensions. |
| [PbesParams](arkts-devicecertificate-cert-pbesparams-i.md) | Enumerates PBES algorithm parameters. Currently, only PBES2 is supported. |
| [Pkcs12CreationConfig](arkts-devicecertificate-cert-pkcs12creationconfig-i.md) | Represents the configuration for creating a PKCS #12 file. |
| [Pkcs12Data](arkts-devicecertificate-cert-pkcs12data-i.md) | Represents the PKCS #12 data, including the private key, certificate, and other certificates. |
| [Pkcs12ParsingConfig](arkts-devicecertificate-cert-pkcs12parsingconfig-i.md) | Represents the configuration for parsing PKCS #12 files. |
| [PrivateKeyInfo](arkts-devicecertificate-cert-privatekeyinfo-i.md) | Represents information about the private key. |
| [RevocationCheckParameter](arkts-devicecertificate-cert-revocationcheckparameter-i.md) | Represents the parameters for checking the certificate revocation status for a certificate chain. |
| [X500DistinguishedName](arkts-devicecertificate-cert-x500distinguishedname-i.md) | Provides APIs for X.500 distinguished name operations. |
| [X509Cert](arkts-devicecertificate-cert-x509cert-i.md) | Provides APIs for X.509 certificate operations. |
| [X509CertChain](arkts-devicecertificate-cert-x509certchain-i.md) | Describes an X.509 certificate chain object. |
| [X509CertMatchParameters](arkts-devicecertificate-cert-x509certmatchparameters-i.md) | Defines the parameters used to match a certificate. If no parameter is specified, all certificates are matched. |
| [X509CertRevokedParams](arkts-devicecertificate-cert-x509certrevokedparams-i.md) | Enumerates the certificate revocation check parameters. |
| [X509CRL](arkts-devicecertificate-cert-x509crl-i.md) | Provides APIs for operations on X.509 CRLs. |
| [X509CRLEntry](arkts-devicecertificate-cert-x509crlentry-i.md) | Provides APIs for operating on a revoked certificate entry in a CRL. |
| [X509CRLMatchParameters](arkts-devicecertificate-cert-x509crlmatchparameters-i.md) | Represents the parameters used to match a certificate revocation list (CRL). If no parameter is specified, all CRLs are matched. |
| [X509TrustAnchor](arkts-devicecertificate-cert-x509trustanchor-i.md) | Represents an X.509 trust anchor, which is used to verify the certificate chain. The certificate or public key in the trust anchor is used as the trusted root to verify the certificate chain. |
| [X509Crl](arkts-devicecertificate-cert-x509crl-depr-i.md) | Provides APIs for X.509 CRL operations. |
| [X509CrlEntry](arkts-devicecertificate-cert-x509crlentry-depr-i.md) | Provides APIs for operating on a revoked certificate entry in a CRL. |

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
| [CmsRecipientEncryptionAlgorithm](arkts-devicecertificate-cert-cmsrecipientencryptionalgorithm-e.md) | Enumerates the encryption algorithms for CMS-encapsulated data. |
| [CmsRsaSignaturePadding](arkts-devicecertificate-cert-cmsrsasignaturepadding-e.md) | Enumerates the RSA CMS signature padding modes. |
| [EncodingBaseFormat](arkts-devicecertificate-cert-encodingbaseformat-e.md) | Enumerates the certificate data encoding formats. |
| [EncodingFormat](arkts-devicecertificate-cert-encodingformat-e.md) | Enumerates the certificate encoding formats. |
| [EncodingType](arkts-devicecertificate-cert-encodingtype-e.md) | Enumerates the obtained encoding formats. |
| [ExtensionEntryType](arkts-devicecertificate-cert-extensionentrytype-e.md) | Enumerates certificate extension types. |
| [ExtensionOidType](arkts-devicecertificate-cert-extensionoidtype-e.md) | Enumerates certificate extension OID types. |
| [GeneralNameType](arkts-devicecertificate-cert-generalnametype-e.md) | Enumerates the general name types defined in X.509. These types can be used in the subject alternative name and other extensions. |
| [KeyUsageType](arkts-devicecertificate-cert-keyusagetype-e.md) | Enumerates the purposes, for which the key in the certificate is used. |
| [OcspDigest](arkts-devicecertificate-cert-ocspdigest-e.md) | Enumerates OCSP digest algorithms. |
| [PbesEncryptionAlgorithm](arkts-devicecertificate-cert-pbesencryptionalgorithm-e.md) | Enumerates password-based encryption scheme (PBES) algorithms. |
| [Pkcs12MacDigestAlgorithm](arkts-devicecertificate-cert-pkcs12macdigestalgorithm-e.md) | Enumerates the PKCS #12 MAC digest algorithms. |
| [RevocationCheckOptions](arkts-devicecertificate-cert-revocationcheckoptions-e.md) | Enumerates the options for checking the certificate revocation status. |
| [ValidationPolicyType](arkts-devicecertificate-cert-validationpolicytype-e.md) | Enumerates the types of the online certificate chain validation policy. |
