| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增错误码|类名：X509Cert；<br>API声明：getSubjectName(): DataBlob;<br>差异内容：NA|类名：X509Cert；<br>API声明：getSubjectName(encodingType?: EncodingType): DataBlob;<br>差异内容：401|api/@ohos.security.cert.d.ts|
|新增错误码|类名：certificateManager；<br>API声明：function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string, callback: AsyncCallback\<CMResult>): void;<br>差异内容：NA|类名：certificateManager；<br>API声明：function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string, callback: AsyncCallback\<CMResult>): void;<br>差异内容：17500004|api/@ohos.security.certManager.d.ts|
|新增错误码|类名：certificateManager；<br>API声明：function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string): Promise\<CMResult>;<br>差异内容：NA|类名：certificateManager；<br>API声明：function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string): Promise\<CMResult>;<br>差异内容：17500004|api/@ohos.security.certManager.d.ts|
|新增错误码|类名：certificateManager；<br>API声明：function init(authUri: string, spec: CMSignatureSpec, callback: AsyncCallback\<CMHandle>): void;<br>差异内容：NA|类名：certificateManager；<br>API声明：function init(authUri: string, spec: CMSignatureSpec, callback: AsyncCallback\<CMHandle>): void;<br>差异内容：17500005|api/@ohos.security.certManager.d.ts|
|新增错误码|类名：certificateManager；<br>API声明：function init(authUri: string, spec: CMSignatureSpec): Promise\<CMHandle>;<br>差异内容：NA|类名：certificateManager；<br>API声明：function init(authUri: string, spec: CMSignatureSpec): Promise\<CMHandle>;<br>差异内容：17500005|api/@ohos.security.certManager.d.ts|
|函数变更|类名：X509Cert；<br>API声明：getSubjectName(): DataBlob;<br>差异内容：NA|类名：X509Cert；<br>API声明：getSubjectName(encodingType?: EncodingType): DataBlob;<br>差异内容：encodingType?: EncodingType|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：enum EncodingType<br>差异内容：enum EncodingType|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：EncodingType；<br>API声明：ENCODING_UTF8 = 0<br>差异内容：ENCODING_UTF8 = 0|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509Cert；<br>API声明：getCRLDistributionPoint(): DataArray;<br>差异内容：getCRLDistributionPoint(): DataArray;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509Cert；<br>API声明：getIssuerX500DistinguishedName(): X500DistinguishedName;<br>差异内容：getIssuerX500DistinguishedName(): X500DistinguishedName;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509Cert；<br>API声明：getSubjectX500DistinguishedName(): X500DistinguishedName;<br>差异内容：getSubjectX500DistinguishedName(): X500DistinguishedName;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509Cert；<br>API声明：toString(): string;<br>差异内容：toString(): string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509Cert；<br>API声明：hashCode(): Uint8Array;<br>差异内容：hashCode(): Uint8Array;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509Cert；<br>API声明：getExtensionsObject(): CertExtension;<br>差异内容：getExtensionsObject(): CertExtension;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CRLEntry；<br>API声明：getCertIssuerX500DistinguishedName(): X500DistinguishedName;<br>差异内容：getCertIssuerX500DistinguishedName(): X500DistinguishedName;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CRLEntry；<br>API声明：toString(): string;<br>差异内容：toString(): string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CRLEntry；<br>API声明：hashCode(): Uint8Array;<br>差异内容：hashCode(): Uint8Array;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CRLEntry；<br>API声明：getExtensionsObject(): CertExtension;<br>差异内容：getExtensionsObject(): CertExtension;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CRL；<br>API声明：getIssuerX500DistinguishedName(): X500DistinguishedName;<br>差异内容：getIssuerX500DistinguishedName(): X500DistinguishedName;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CRL；<br>API声明：toString(): string;<br>差异内容：toString(): string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CRL；<br>API声明：hashCode(): Uint8Array;<br>差异内容：hashCode(): Uint8Array;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CRL；<br>API声明：getExtensionsObject(): CertExtension;<br>差异内容：getExtensionsObject(): CertExtension;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：enum GeneralNameType<br>差异内容：enum GeneralNameType|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：GeneralNameType；<br>API声明：GENERAL_NAME_TYPE_OTHER_NAME = 0<br>差异内容：GENERAL_NAME_TYPE_OTHER_NAME = 0|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：GeneralNameType；<br>API声明：GENERAL_NAME_TYPE_RFC822_NAME = 1<br>差异内容：GENERAL_NAME_TYPE_RFC822_NAME = 1|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：GeneralNameType；<br>API声明：GENERAL_NAME_TYPE_DNS_NAME = 2<br>差异内容：GENERAL_NAME_TYPE_DNS_NAME = 2|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：GeneralNameType；<br>API声明：GENERAL_NAME_TYPE_X400_ADDRESS = 3<br>差异内容：GENERAL_NAME_TYPE_X400_ADDRESS = 3|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：GeneralNameType；<br>API声明：GENERAL_NAME_TYPE_DIRECTORY_NAME = 4<br>差异内容：GENERAL_NAME_TYPE_DIRECTORY_NAME = 4|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：GeneralNameType；<br>API声明：GENERAL_NAME_TYPE_EDI_PARTY_NAME = 5<br>差异内容：GENERAL_NAME_TYPE_EDI_PARTY_NAME = 5|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：GeneralNameType；<br>API声明：GENERAL_NAME_TYPE_UNIFORM_RESOURCE_ID = 6<br>差异内容：GENERAL_NAME_TYPE_UNIFORM_RESOURCE_ID = 6|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：GeneralNameType；<br>API声明：GENERAL_NAME_TYPE_IP_ADDRESS = 7<br>差异内容：GENERAL_NAME_TYPE_IP_ADDRESS = 7|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：GeneralNameType；<br>API声明：GENERAL_NAME_TYPE_REGISTERED_ID = 8<br>差异内容：GENERAL_NAME_TYPE_REGISTERED_ID = 8|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：interface GeneralName<br>差异内容：interface GeneralName|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：GeneralName；<br>API声明：type: GeneralNameType;<br>差异内容：type: GeneralNameType;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：GeneralName；<br>API声明：name?: Uint8Array;<br>差异内容：name?: Uint8Array;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CertMatchParameters；<br>API声明：subjectAlternativeNames?: Array\<GeneralName>;<br>差异内容：subjectAlternativeNames?: Array\<GeneralName>;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CertMatchParameters；<br>API声明：matchAllSubjectAltNames?: boolean;<br>差异内容：matchAllSubjectAltNames?: boolean;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CertMatchParameters；<br>API声明：authorityKeyIdentifier?: Uint8Array;<br>差异内容：authorityKeyIdentifier?: Uint8Array;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CertMatchParameters；<br>API声明：minPathLenConstraint?: number;<br>差异内容：minPathLenConstraint?: number;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CertMatchParameters；<br>API声明：extendedKeyUsage?: Array\<string>;<br>差异内容：extendedKeyUsage?: Array\<string>;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CertMatchParameters；<br>API声明：nameConstraints?: Uint8Array;<br>差异内容：nameConstraints?: Uint8Array;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CertMatchParameters；<br>API声明：certPolicy?: Array\<string>;<br>差异内容：certPolicy?: Array\<string>;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CertMatchParameters；<br>API声明：privateKeyValid?: string;<br>差异内容：privateKeyValid?: string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CertMatchParameters；<br>API声明：subjectKeyIdentifier?: Uint8Array;<br>差异内容：subjectKeyIdentifier?: Uint8Array;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CRLMatchParameters；<br>API声明：updateDateTime?: string;<br>差异内容：updateDateTime?: string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CRLMatchParameters；<br>API声明：maxCRL?: bigint;<br>差异内容：maxCRL?: bigint;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CRLMatchParameters；<br>API声明：minCRL?: bigint;<br>差异内容：minCRL?: bigint;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CertChain；<br>API声明：toString(): string;<br>差异内容：toString(): string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509CertChain；<br>API声明：hashCode(): Uint8Array;<br>差异内容：hashCode(): Uint8Array;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：function buildX509CertChain(param: CertChainBuildParameters): Promise\<CertChainBuildResult>;<br>差异内容：function buildX509CertChain(param: CertChainBuildParameters): Promise\<CertChainBuildResult>;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：function createTrustAnchorsWithKeyStore(keystore: Uint8Array, pwd: string): Promise\<Array\<X509TrustAnchor>>;<br>差异内容：function createTrustAnchorsWithKeyStore(keystore: Uint8Array, pwd: string): Promise\<Array\<X509TrustAnchor>>;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：function createX500DistinguishedName(nameStr: string): Promise\<X500DistinguishedName>;<br>差异内容：function createX500DistinguishedName(nameStr: string): Promise\<X500DistinguishedName>;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：function createX500DistinguishedName(nameDer: Uint8Array): Promise\<X500DistinguishedName>;<br>差异内容：function createX500DistinguishedName(nameDer: Uint8Array): Promise\<X500DistinguishedName>;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：interface X500DistinguishedName<br>差异内容：interface X500DistinguishedName|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X500DistinguishedName；<br>API声明：getName(): string;<br>差异内容：getName(): string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X500DistinguishedName；<br>API声明：getName(type: string): Array\<string>;<br>差异内容：getName(type: string): Array\<string>;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X500DistinguishedName；<br>API声明：getEncoded(): EncodingBlob;<br>差异内容：getEncoded(): EncodingBlob;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：X509TrustAnchor；<br>API声明：nameConstraints?: Uint8Array;<br>差异内容：nameConstraints?: Uint8Array;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：enum RevocationCheckOptions<br>差异内容：enum RevocationCheckOptions|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：RevocationCheckOptions；<br>API声明：REVOCATION_CHECK_OPTION_PREFER_OCSP = 0<br>差异内容：REVOCATION_CHECK_OPTION_PREFER_OCSP = 0|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：RevocationCheckOptions；<br>API声明：REVOCATION_CHECK_OPTION_ACCESS_NETWORK<br>差异内容：REVOCATION_CHECK_OPTION_ACCESS_NETWORK|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：RevocationCheckOptions；<br>API声明：REVOCATION_CHECK_OPTION_FALLBACK_NO_PREFER<br>差异内容：REVOCATION_CHECK_OPTION_FALLBACK_NO_PREFER|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：RevocationCheckOptions；<br>API声明：REVOCATION_CHECK_OPTION_FALLBACK_LOCAL<br>差异内容：REVOCATION_CHECK_OPTION_FALLBACK_LOCAL|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：enum ValidationPolicyType<br>差异内容：enum ValidationPolicyType|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：ValidationPolicyType；<br>API声明：VALIDATION_POLICY_TYPE_X509 = 0<br>差异内容：VALIDATION_POLICY_TYPE_X509 = 0|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：ValidationPolicyType；<br>API声明：VALIDATION_POLICY_TYPE_SSL<br>差异内容：VALIDATION_POLICY_TYPE_SSL|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：enum KeyUsageType<br>差异内容：enum KeyUsageType|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：KeyUsageType；<br>API声明：KEYUSAGE_DIGITAL_SIGNATURE = 0<br>差异内容：KEYUSAGE_DIGITAL_SIGNATURE = 0|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：KeyUsageType；<br>API声明：KEYUSAGE_NON_REPUDIATION<br>差异内容：KEYUSAGE_NON_REPUDIATION|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：KeyUsageType；<br>API声明：KEYUSAGE_KEY_ENCIPHERMENT<br>差异内容：KEYUSAGE_KEY_ENCIPHERMENT|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：KeyUsageType；<br>API声明：KEYUSAGE_DATA_ENCIPHERMENT<br>差异内容：KEYUSAGE_DATA_ENCIPHERMENT|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：KeyUsageType；<br>API声明：KEYUSAGE_KEY_AGREEMENT<br>差异内容：KEYUSAGE_KEY_AGREEMENT|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：KeyUsageType；<br>API声明：KEYUSAGE_KEY_CERT_SIGN<br>差异内容：KEYUSAGE_KEY_CERT_SIGN|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：KeyUsageType；<br>API声明：KEYUSAGE_CRL_SIGN<br>差异内容：KEYUSAGE_CRL_SIGN|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：KeyUsageType；<br>API声明：KEYUSAGE_ENCIPHER_ONLY<br>差异内容：KEYUSAGE_ENCIPHER_ONLY|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：KeyUsageType；<br>API声明：KEYUSAGE_DECIPHER_ONLY<br>差异内容：KEYUSAGE_DECIPHER_ONLY|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：interface RevocationCheckParameter<br>差异内容：interface RevocationCheckParameter|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：RevocationCheckParameter；<br>API声明：ocspRequestExtension?: Array\<Uint8Array>;<br>差异内容：ocspRequestExtension?: Array\<Uint8Array>;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：RevocationCheckParameter；<br>API声明：ocspResponderURI?: string;<br>差异内容：ocspResponderURI?: string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：RevocationCheckParameter；<br>API声明：ocspResponderCert?: X509Cert;<br>差异内容：ocspResponderCert?: X509Cert;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：RevocationCheckParameter；<br>API声明：ocspResponses?: Uint8Array;<br>差异内容：ocspResponses?: Uint8Array;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：RevocationCheckParameter；<br>API声明：crlDownloadURI?: string;<br>差异内容：crlDownloadURI?: string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：RevocationCheckParameter；<br>API声明：options?: Array\<RevocationCheckOptions>;<br>差异内容：options?: Array\<RevocationCheckOptions>;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：RevocationCheckParameter；<br>API声明：ocspDigest?: string;<br>差异内容：ocspDigest?: string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CertChainValidationParameters；<br>API声明：revocationCheckParam?: RevocationCheckParameter;<br>差异内容：revocationCheckParam?: RevocationCheckParameter;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CertChainValidationParameters；<br>API声明：policy?: ValidationPolicyType;<br>差异内容：policy?: ValidationPolicyType;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CertChainValidationParameters；<br>API声明：sslHostname?: string;<br>差异内容：sslHostname?: string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CertChainValidationParameters；<br>API声明：keyUsage?: Array\<KeyUsageType>;<br>差异内容：keyUsage?: Array\<KeyUsageType>;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：interface CertChainBuildParameters<br>差异内容：interface CertChainBuildParameters|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CertChainBuildParameters；<br>API声明：certMatchParameters: X509CertMatchParameters;<br>差异内容：certMatchParameters: X509CertMatchParameters;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CertChainBuildParameters；<br>API声明：maxLength?: number;<br>差异内容：maxLength?: number;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CertChainBuildParameters；<br>API声明：validationParameters: CertChainValidationParameters;<br>差异内容：validationParameters: CertChainValidationParameters;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：interface CertChainBuildResult<br>差异内容：interface CertChainBuildResult|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CertChainBuildResult；<br>API声明：readonly certChain: X509CertChain;<br>差异内容：readonly certChain: X509CertChain;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CertChainBuildResult；<br>API声明：readonly validationResult: CertChainValidationResult;<br>差异内容：readonly validationResult: CertChainValidationResult;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CMErrorCode；<br>API声明：CM_ERROR_MAX_CERT_COUNT_REACHED = 17500004<br>差异内容：CM_ERROR_MAX_CERT_COUNT_REACHED = 17500004|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：CMErrorCode；<br>API声明：CM_ERROR_NO_AUTHORIZATION = 17500005<br>差异内容：CM_ERROR_NO_AUTHORIZATION = 17500005|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：certificateManager；<br>API声明：function getPublicCertificate(keyUri: string): Promise\<CMResult>;<br>差异内容：function getPublicCertificate(keyUri: string): Promise\<CMResult>;|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：certificateManager；<br>API声明：function isAuthorizedApp(keyUri: string): Promise\<boolean>;<br>差异内容：function isAuthorizedApp(keyUri: string): Promise\<boolean>;|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：certificateManager；<br>API声明：function getAllUserTrustedCertificates(): Promise\<CMResult>;<br>差异内容：function getAllUserTrustedCertificates(): Promise\<CMResult>;|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：certificateManager；<br>API声明：function getUserTrustedCertificate(certUri: string): Promise\<CMResult>;<br>差异内容：function getUserTrustedCertificate(certUri: string): Promise\<CMResult>;|api/@ohos.security.certManager.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace cert<br>差异内容：NA|类名：global；<br>API声明：declare namespace cert<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：enum CertResult<br>差异内容：NA|类名：cert；<br>API声明：enum CertResult<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertResult；<br>API声明：INVALID_PARAMS = 401<br>差异内容：NA|类名：CertResult；<br>API声明：INVALID_PARAMS = 401<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertResult；<br>API声明：NOT_SUPPORT = 801<br>差异内容：NA|类名：CertResult；<br>API声明：NOT_SUPPORT = 801<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertResult；<br>API声明：ERR_OUT_OF_MEMORY = 19020001<br>差异内容：NA|类名：CertResult；<br>API声明：ERR_OUT_OF_MEMORY = 19020001<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertResult；<br>API声明：ERR_RUNTIME_ERROR = 19020002<br>差异内容：NA|类名：CertResult；<br>API声明：ERR_RUNTIME_ERROR = 19020002<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertResult；<br>API声明：ERR_CRYPTO_OPERATION = 19030001<br>差异内容：NA|类名：CertResult；<br>API声明：ERR_CRYPTO_OPERATION = 19030001<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertResult；<br>API声明：ERR_CERT_SIGNATURE_FAILURE = 19030002<br>差异内容：NA|类名：CertResult；<br>API声明：ERR_CERT_SIGNATURE_FAILURE = 19030002<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertResult；<br>API声明：ERR_CERT_NOT_YET_VALID = 19030003<br>差异内容：NA|类名：CertResult；<br>API声明：ERR_CERT_NOT_YET_VALID = 19030003<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertResult；<br>API声明：ERR_CERT_HAS_EXPIRED = 19030004<br>差异内容：NA|类名：CertResult；<br>API声明：ERR_CERT_HAS_EXPIRED = 19030004<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertResult；<br>API声明：ERR_UNABLE_TO_GET_ISSUER_CERT_LOCALLY = 19030005<br>差异内容：NA|类名：CertResult；<br>API声明：ERR_UNABLE_TO_GET_ISSUER_CERT_LOCALLY = 19030005<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertResult；<br>API声明：ERR_KEYUSAGE_NO_CERTSIGN = 19030006<br>差异内容：NA|类名：CertResult；<br>API声明：ERR_KEYUSAGE_NO_CERTSIGN = 19030006<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertResult；<br>API声明：ERR_KEYUSAGE_NO_DIGITAL_SIGNATURE = 19030007<br>差异内容：NA|类名：CertResult；<br>API声明：ERR_KEYUSAGE_NO_DIGITAL_SIGNATURE = 19030007<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：interface DataBlob<br>差异内容：NA|类名：cert；<br>API声明：interface DataBlob<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：DataBlob；<br>API声明：data: Uint8Array;<br>差异内容：NA|类名：DataBlob；<br>API声明：data: Uint8Array;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：interface DataArray<br>差异内容：NA|类名：cert；<br>API声明：interface DataArray<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：DataArray；<br>API声明：data: Array\<Uint8Array>;<br>差异内容：NA|类名：DataArray；<br>API声明：data: Array\<Uint8Array>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：enum EncodingFormat<br>差异内容：NA|类名：cert；<br>API声明：enum EncodingFormat<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：EncodingFormat；<br>API声明：FORMAT_DER = 0<br>差异内容：NA|类名：EncodingFormat；<br>API声明：FORMAT_DER = 0<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：EncodingFormat；<br>API声明：FORMAT_PEM = 1<br>差异内容：NA|类名：EncodingFormat；<br>API声明：FORMAT_PEM = 1<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：EncodingFormat；<br>API声明：FORMAT_PKCS7 = 2<br>差异内容：NA|类名：EncodingFormat；<br>API声明：FORMAT_PKCS7 = 2<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：enum CertItemType<br>差异内容：NA|类名：cert；<br>API声明：enum CertItemType<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertItemType；<br>API声明：CERT_ITEM_TYPE_TBS = 0<br>差异内容：NA|类名：CertItemType；<br>API声明：CERT_ITEM_TYPE_TBS = 0<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertItemType；<br>API声明：CERT_ITEM_TYPE_PUBLIC_KEY = 1<br>差异内容：NA|类名：CertItemType；<br>API声明：CERT_ITEM_TYPE_PUBLIC_KEY = 1<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertItemType；<br>API声明：CERT_ITEM_TYPE_ISSUER_UNIQUE_ID = 2<br>差异内容：NA|类名：CertItemType；<br>API声明：CERT_ITEM_TYPE_ISSUER_UNIQUE_ID = 2<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertItemType；<br>API声明：CERT_ITEM_TYPE_SUBJECT_UNIQUE_ID = 3<br>差异内容：NA|类名：CertItemType；<br>API声明：CERT_ITEM_TYPE_SUBJECT_UNIQUE_ID = 3<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertItemType；<br>API声明：CERT_ITEM_TYPE_EXTENSIONS = 4<br>差异内容：NA|类名：CertItemType；<br>API声明：CERT_ITEM_TYPE_EXTENSIONS = 4<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：enum ExtensionOidType<br>差异内容：NA|类名：cert；<br>API声明：enum ExtensionOidType<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：ExtensionOidType；<br>API声明：EXTENSION_OID_TYPE_ALL = 0<br>差异内容：NA|类名：ExtensionOidType；<br>API声明：EXTENSION_OID_TYPE_ALL = 0<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：ExtensionOidType；<br>API声明：EXTENSION_OID_TYPE_CRITICAL = 1<br>差异内容：NA|类名：ExtensionOidType；<br>API声明：EXTENSION_OID_TYPE_CRITICAL = 1<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：ExtensionOidType；<br>API声明：EXTENSION_OID_TYPE_UNCRITICAL = 2<br>差异内容：NA|类名：ExtensionOidType；<br>API声明：EXTENSION_OID_TYPE_UNCRITICAL = 2<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：enum ExtensionEntryType<br>差异内容：NA|类名：cert；<br>API声明：enum ExtensionEntryType<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：ExtensionEntryType；<br>API声明：EXTENSION_ENTRY_TYPE_ENTRY = 0<br>差异内容：NA|类名：ExtensionEntryType；<br>API声明：EXTENSION_ENTRY_TYPE_ENTRY = 0<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：ExtensionEntryType；<br>API声明：EXTENSION_ENTRY_TYPE_ENTRY_CRITICAL = 1<br>差异内容：NA|类名：ExtensionEntryType；<br>API声明：EXTENSION_ENTRY_TYPE_ENTRY_CRITICAL = 1<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：ExtensionEntryType；<br>API声明：EXTENSION_ENTRY_TYPE_ENTRY_VALUE = 2<br>差异内容：NA|类名：ExtensionEntryType；<br>API声明：EXTENSION_ENTRY_TYPE_ENTRY_VALUE = 2<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：interface EncodingBlob<br>差异内容：NA|类名：cert；<br>API声明：interface EncodingBlob<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：EncodingBlob；<br>API声明：data: Uint8Array;<br>差异内容：NA|类名：EncodingBlob；<br>API声明：data: Uint8Array;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：EncodingBlob；<br>API声明：encodingFormat: EncodingFormat;<br>差异内容：NA|类名：EncodingBlob；<br>API声明：encodingFormat: EncodingFormat;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：interface CertChainData<br>差异内容：NA|类名：cert；<br>API声明：interface CertChainData<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertChainData；<br>API声明：data: Uint8Array;<br>差异内容：NA|类名：CertChainData；<br>API声明：data: Uint8Array;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertChainData；<br>API声明：count: number;<br>差异内容：NA|类名：CertChainData；<br>API声明：count: number;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertChainData；<br>API声明：encodingFormat: EncodingFormat;<br>差异内容：NA|类名：CertChainData；<br>API声明：encodingFormat: EncodingFormat;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：interface X509Cert<br>差异内容：NA|类名：cert；<br>API声明：interface X509Cert<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：verify(key: cryptoFramework.PubKey, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：X509Cert；<br>API声明：verify(key: cryptoFramework.PubKey, callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：verify(key: cryptoFramework.PubKey): Promise\<void>;<br>差异内容：NA|类名：X509Cert；<br>API声明：verify(key: cryptoFramework.PubKey): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getEncoded(callback: AsyncCallback\<EncodingBlob>): void;<br>差异内容：NA|类名：X509Cert；<br>API声明：getEncoded(callback: AsyncCallback\<EncodingBlob>): void;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getEncoded(): Promise\<EncodingBlob>;<br>差异内容：NA|类名：X509Cert；<br>API声明：getEncoded(): Promise\<EncodingBlob>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getPublicKey(): cryptoFramework.PubKey;<br>差异内容：NA|类名：X509Cert；<br>API声明：getPublicKey(): cryptoFramework.PubKey;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：checkValidityWithDate(date: string): void;<br>差异内容：NA|类名：X509Cert；<br>API声明：checkValidityWithDate(date: string): void;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getVersion(): number;<br>差异内容：NA|类名：X509Cert；<br>API声明：getVersion(): number;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getCertSerialNumber(): bigint;<br>差异内容：NA|类名：X509Cert；<br>API声明：getCertSerialNumber(): bigint;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getIssuerName(): DataBlob;<br>差异内容：NA|类名：X509Cert；<br>API声明：getIssuerName(): DataBlob;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getSubjectName(): DataBlob;<br>差异内容：NA|类名：X509Cert；<br>API声明：getSubjectName(encodingType?: EncodingType): DataBlob;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getNotBeforeTime(): string;<br>差异内容：NA|类名：X509Cert；<br>API声明：getNotBeforeTime(): string;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getNotAfterTime(): string;<br>差异内容：NA|类名：X509Cert；<br>API声明：getNotAfterTime(): string;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getSignature(): DataBlob;<br>差异内容：NA|类名：X509Cert；<br>API声明：getSignature(): DataBlob;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getSignatureAlgName(): string;<br>差异内容：NA|类名：X509Cert；<br>API声明：getSignatureAlgName(): string;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getSignatureAlgOid(): string;<br>差异内容：NA|类名：X509Cert；<br>API声明：getSignatureAlgOid(): string;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getSignatureAlgParams(): DataBlob;<br>差异内容：NA|类名：X509Cert；<br>API声明：getSignatureAlgParams(): DataBlob;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getKeyUsage(): DataBlob;<br>差异内容：NA|类名：X509Cert；<br>API声明：getKeyUsage(): DataBlob;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getExtKeyUsage(): DataArray;<br>差异内容：NA|类名：X509Cert；<br>API声明：getExtKeyUsage(): DataArray;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getBasicConstraints(): number;<br>差异内容：NA|类名：X509Cert；<br>API声明：getBasicConstraints(): number;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getSubjectAltNames(): DataArray;<br>差异内容：NA|类名：X509Cert；<br>API声明：getSubjectAltNames(): DataArray;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getIssuerAltNames(): DataArray;<br>差异内容：NA|类名：X509Cert；<br>API声明：getIssuerAltNames(): DataArray;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：getItem(itemType: CertItemType): DataBlob;<br>差异内容：NA|类名：X509Cert；<br>API声明：getItem(itemType: CertItemType): DataBlob;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509Cert；<br>API声明：match(param: X509CertMatchParameters): boolean;<br>差异内容：NA|类名：X509Cert；<br>API声明：match(param: X509CertMatchParameters): boolean;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：function createX509Cert(inStream: EncodingBlob, callback: AsyncCallback\<X509Cert>): void;<br>差异内容：NA|类名：cert；<br>API声明：function createX509Cert(inStream: EncodingBlob, callback: AsyncCallback\<X509Cert>): void;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：function createX509Cert(inStream: EncodingBlob): Promise\<X509Cert>;<br>差异内容：NA|类名：cert；<br>API声明：function createX509Cert(inStream: EncodingBlob): Promise\<X509Cert>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：interface CertExtension<br>差异内容：NA|类名：cert；<br>API声明：interface CertExtension<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertExtension；<br>API声明：getEncoded(): EncodingBlob;<br>差异内容：NA|类名：CertExtension；<br>API声明：getEncoded(): EncodingBlob;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertExtension；<br>API声明：getOidList(valueType: ExtensionOidType): DataArray;<br>差异内容：NA|类名：CertExtension；<br>API声明：getOidList(valueType: ExtensionOidType): DataArray;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertExtension；<br>API声明：getEntry(valueType: ExtensionEntryType, oid: DataBlob): DataBlob;<br>差异内容：NA|类名：CertExtension；<br>API声明：getEntry(valueType: ExtensionEntryType, oid: DataBlob): DataBlob;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertExtension；<br>API声明：checkCA(): number;<br>差异内容：NA|类名：CertExtension；<br>API声明：checkCA(): number;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertExtension；<br>API声明：hasUnsupportedCriticalExtension(): boolean;<br>差异内容：NA|类名：CertExtension；<br>API声明：hasUnsupportedCriticalExtension(): boolean;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：function createCertExtension(inStream: EncodingBlob, callback: AsyncCallback\<CertExtension>): void;<br>差异内容：NA|类名：cert；<br>API声明：function createCertExtension(inStream: EncodingBlob, callback: AsyncCallback\<CertExtension>): void;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：function createCertExtension(inStream: EncodingBlob): Promise\<CertExtension>;<br>差异内容：NA|类名：cert；<br>API声明：function createCertExtension(inStream: EncodingBlob): Promise\<CertExtension>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：interface X509CRLEntry<br>差异内容：NA|类名：cert；<br>API声明：interface X509CRLEntry<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRLEntry；<br>API声明：getEncoded(callback: AsyncCallback\<EncodingBlob>): void;<br>差异内容：NA|类名：X509CRLEntry；<br>API声明：getEncoded(callback: AsyncCallback\<EncodingBlob>): void;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRLEntry；<br>API声明：getEncoded(): Promise\<EncodingBlob>;<br>差异内容：NA|类名：X509CRLEntry；<br>API声明：getEncoded(): Promise\<EncodingBlob>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRLEntry；<br>API声明：getSerialNumber(): bigint;<br>差异内容：NA|类名：X509CRLEntry；<br>API声明：getSerialNumber(): bigint;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRLEntry；<br>API声明：getCertIssuer(): DataBlob;<br>差异内容：NA|类名：X509CRLEntry；<br>API声明：getCertIssuer(): DataBlob;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRLEntry；<br>API声明：getRevocationDate(): string;<br>差异内容：NA|类名：X509CRLEntry；<br>API声明：getRevocationDate(): string;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRLEntry；<br>API声明：getExtensions(): DataBlob;<br>差异内容：NA|类名：X509CRLEntry；<br>API声明：getExtensions(): DataBlob;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRLEntry；<br>API声明：hasExtensions(): boolean;<br>差异内容：NA|类名：X509CRLEntry；<br>API声明：hasExtensions(): boolean;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：interface X509CRL<br>差异内容：NA|类名：cert；<br>API声明：interface X509CRL<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：isRevoked(cert: X509Cert): boolean;<br>差异内容：NA|类名：X509CRL；<br>API声明：isRevoked(cert: X509Cert): boolean;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：getType(): string;<br>差异内容：NA|类名：X509CRL；<br>API声明：getType(): string;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：getEncoded(callback: AsyncCallback\<EncodingBlob>): void;<br>差异内容：NA|类名：X509CRL；<br>API声明：getEncoded(callback: AsyncCallback\<EncodingBlob>): void;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：getEncoded(): Promise\<EncodingBlob>;<br>差异内容：NA|类名：X509CRL；<br>API声明：getEncoded(): Promise\<EncodingBlob>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：verify(key: cryptoFramework.PubKey, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：X509CRL；<br>API声明：verify(key: cryptoFramework.PubKey, callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：verify(key: cryptoFramework.PubKey): Promise\<void>;<br>差异内容：NA|类名：X509CRL；<br>API声明：verify(key: cryptoFramework.PubKey): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：getVersion(): number;<br>差异内容：NA|类名：X509CRL；<br>API声明：getVersion(): number;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：getIssuerName(): DataBlob;<br>差异内容：NA|类名：X509CRL；<br>API声明：getIssuerName(): DataBlob;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：getLastUpdate(): string;<br>差异内容：NA|类名：X509CRL；<br>API声明：getLastUpdate(): string;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：getNextUpdate(): string;<br>差异内容：NA|类名：X509CRL；<br>API声明：getNextUpdate(): string;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：getRevokedCert(serialNumber: bigint): X509CRLEntry;<br>差异内容：NA|类名：X509CRL；<br>API声明：getRevokedCert(serialNumber: bigint): X509CRLEntry;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：getRevokedCertWithCert(cert: X509Cert): X509CRLEntry;<br>差异内容：NA|类名：X509CRL；<br>API声明：getRevokedCertWithCert(cert: X509Cert): X509CRLEntry;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：getRevokedCerts(callback: AsyncCallback\<Array\<X509CRLEntry>>): void;<br>差异内容：NA|类名：X509CRL；<br>API声明：getRevokedCerts(callback: AsyncCallback\<Array\<X509CRLEntry>>): void;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：getRevokedCerts(): Promise\<Array\<X509CRLEntry>>;<br>差异内容：NA|类名：X509CRL；<br>API声明：getRevokedCerts(): Promise\<Array\<X509CRLEntry>>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：getTBSInfo(): DataBlob;<br>差异内容：NA|类名：X509CRL；<br>API声明：getTBSInfo(): DataBlob;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：getSignature(): DataBlob;<br>差异内容：NA|类名：X509CRL；<br>API声明：getSignature(): DataBlob;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：getSignatureAlgName(): string;<br>差异内容：NA|类名：X509CRL；<br>API声明：getSignatureAlgName(): string;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：getSignatureAlgOid(): string;<br>差异内容：NA|类名：X509CRL；<br>API声明：getSignatureAlgOid(): string;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：getSignatureAlgParams(): DataBlob;<br>差异内容：NA|类名：X509CRL；<br>API声明：getSignatureAlgParams(): DataBlob;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：getExtensions(): DataBlob;<br>差异内容：NA|类名：X509CRL；<br>API声明：getExtensions(): DataBlob;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRL；<br>API声明：match(param: X509CRLMatchParameters): boolean;<br>差异内容：NA|类名：X509CRL；<br>API声明：match(param: X509CRLMatchParameters): boolean;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：function createX509CRL(inStream: EncodingBlob, callback: AsyncCallback\<X509CRL>): void;<br>差异内容：NA|类名：cert；<br>API声明：function createX509CRL(inStream: EncodingBlob, callback: AsyncCallback\<X509CRL>): void;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：function createX509CRL(inStream: EncodingBlob): Promise\<X509CRL>;<br>差异内容：NA|类名：cert；<br>API声明：function createX509CRL(inStream: EncodingBlob): Promise\<X509CRL>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：interface CertChainValidator<br>差异内容：NA|类名：cert；<br>API声明：interface CertChainValidator<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertChainValidator；<br>API声明：validate(certChain: CertChainData, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：CertChainValidator；<br>API声明：validate(certChain: CertChainData, callback: AsyncCallback\<void>): void;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertChainValidator；<br>API声明：validate(certChain: CertChainData): Promise\<void>;<br>差异内容：NA|类名：CertChainValidator；<br>API声明：validate(certChain: CertChainData): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertChainValidator；<br>API声明：readonly algorithm: string;<br>差异内容：NA|类名：CertChainValidator；<br>API声明：readonly algorithm: string;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：function createCertChainValidator(algorithm: string): CertChainValidator;<br>差异内容：NA|类名：cert；<br>API声明：function createCertChainValidator(algorithm: string): CertChainValidator;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：interface X509CertMatchParameters<br>差异内容：NA|类名：cert；<br>API声明：interface X509CertMatchParameters<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CertMatchParameters；<br>API声明：x509Cert?: X509Cert;<br>差异内容：NA|类名：X509CertMatchParameters；<br>API声明：x509Cert?: X509Cert;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CertMatchParameters；<br>API声明：validDate?: string;<br>差异内容：NA|类名：X509CertMatchParameters；<br>API声明：validDate?: string;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CertMatchParameters；<br>API声明：issuer?: Uint8Array;<br>差异内容：NA|类名：X509CertMatchParameters；<br>API声明：issuer?: Uint8Array;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CertMatchParameters；<br>API声明：keyUsage?: Array\<boolean>;<br>差异内容：NA|类名：X509CertMatchParameters；<br>API声明：keyUsage?: Array\<boolean>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CertMatchParameters；<br>API声明：serialNumber?: bigint;<br>差异内容：NA|类名：X509CertMatchParameters；<br>API声明：serialNumber?: bigint;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CertMatchParameters；<br>API声明：subject?: Uint8Array;<br>差异内容：NA|类名：X509CertMatchParameters；<br>API声明：subject?: Uint8Array;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CertMatchParameters；<br>API声明：publicKey?: DataBlob;<br>差异内容：NA|类名：X509CertMatchParameters；<br>API声明：publicKey?: DataBlob;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CertMatchParameters；<br>API声明：publicKeyAlgID?: string;<br>差异内容：NA|类名：X509CertMatchParameters；<br>API声明：publicKeyAlgID?: string;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：interface X509CRLMatchParameters<br>差异内容：NA|类名：cert；<br>API声明：interface X509CRLMatchParameters<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRLMatchParameters；<br>API声明：issuer?: Array\<Uint8Array>;<br>差异内容：NA|类名：X509CRLMatchParameters；<br>API声明：issuer?: Array\<Uint8Array>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CRLMatchParameters；<br>API声明：x509Cert?: X509Cert;<br>差异内容：NA|类名：X509CRLMatchParameters；<br>API声明：x509Cert?: X509Cert;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：interface CertCRLCollection<br>差异内容：NA|类名：cert；<br>API声明：interface CertCRLCollection<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertCRLCollection；<br>API声明：selectCerts(param: X509CertMatchParameters): Promise\<Array\<X509Cert>>;<br>差异内容：NA|类名：CertCRLCollection；<br>API声明：selectCerts(param: X509CertMatchParameters): Promise\<Array\<X509Cert>>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertCRLCollection；<br>API声明：selectCerts(param: X509CertMatchParameters, callback: AsyncCallback\<Array\<X509Cert>>): void;<br>差异内容：NA|类名：CertCRLCollection；<br>API声明：selectCerts(param: X509CertMatchParameters, callback: AsyncCallback\<Array\<X509Cert>>): void;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertCRLCollection；<br>API声明：selectCRLs(param: X509CRLMatchParameters): Promise\<Array\<X509CRL>>;<br>差异内容：NA|类名：CertCRLCollection；<br>API声明：selectCRLs(param: X509CRLMatchParameters): Promise\<Array\<X509CRL>>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertCRLCollection；<br>API声明：selectCRLs(param: X509CRLMatchParameters, callback: AsyncCallback\<Array\<X509CRL>>): void;<br>差异内容：NA|类名：CertCRLCollection；<br>API声明：selectCRLs(param: X509CRLMatchParameters, callback: AsyncCallback\<Array\<X509CRL>>): void;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：function createCertCRLCollection(certs: Array\<X509Cert>, crls?: Array\<X509CRL>): CertCRLCollection;<br>差异内容：NA|类名：cert；<br>API声明：function createCertCRLCollection(certs: Array\<X509Cert>, crls?: Array\<X509CRL>): CertCRLCollection;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：interface X509CertChain<br>差异内容：NA|类名：cert；<br>API声明：interface X509CertChain<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CertChain；<br>API声明：getCertList(): Array\<X509Cert>;<br>差异内容：NA|类名：X509CertChain；<br>API声明：getCertList(): Array\<X509Cert>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CertChain；<br>API声明：validate(param: CertChainValidationParameters): Promise\<CertChainValidationResult>;<br>差异内容：NA|类名：X509CertChain；<br>API声明：validate(param: CertChainValidationParameters): Promise\<CertChainValidationResult>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509CertChain；<br>API声明：validate(param: CertChainValidationParameters, callback: AsyncCallback\<CertChainValidationResult>): void;<br>差异内容：NA|类名：X509CertChain；<br>API声明：validate(param: CertChainValidationParameters, callback: AsyncCallback\<CertChainValidationResult>): void;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：function createX509CertChain(inStream: EncodingBlob): Promise\<X509CertChain>;<br>差异内容：NA|类名：cert；<br>API声明：function createX509CertChain(inStream: EncodingBlob): Promise\<X509CertChain>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：function createX509CertChain(inStream: EncodingBlob, callback: AsyncCallback\<X509CertChain>): void;<br>差异内容：NA|类名：cert；<br>API声明：function createX509CertChain(inStream: EncodingBlob, callback: AsyncCallback\<X509CertChain>): void;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：function createX509CertChain(certs: Array\<X509Cert>): X509CertChain;<br>差异内容：NA|类名：cert；<br>API声明：function createX509CertChain(certs: Array\<X509Cert>): X509CertChain;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：interface X509TrustAnchor<br>差异内容：NA|类名：cert；<br>API声明：interface X509TrustAnchor<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509TrustAnchor；<br>API声明：CACert?: X509Cert;<br>差异内容：NA|类名：X509TrustAnchor；<br>API声明：CACert?: X509Cert;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509TrustAnchor；<br>API声明：CAPubKey?: Uint8Array;<br>差异内容：NA|类名：X509TrustAnchor；<br>API声明：CAPubKey?: Uint8Array;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：X509TrustAnchor；<br>API声明：CASubject?: Uint8Array;<br>差异内容：NA|类名：X509TrustAnchor；<br>API声明：CASubject?: Uint8Array;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：interface CertChainValidationParameters<br>差异内容：NA|类名：cert；<br>API声明：interface CertChainValidationParameters<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertChainValidationParameters；<br>API声明：date?: string;<br>差异内容：NA|类名：CertChainValidationParameters；<br>API声明：date?: string;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertChainValidationParameters；<br>API声明：trustAnchors: Array\<X509TrustAnchor>;<br>差异内容：NA|类名：CertChainValidationParameters；<br>API声明：trustAnchors: Array\<X509TrustAnchor>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertChainValidationParameters；<br>API声明：certCRLs?: Array\<CertCRLCollection>;<br>差异内容：NA|类名：CertChainValidationParameters；<br>API声明：certCRLs?: Array\<CertCRLCollection>;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：cert；<br>API声明：interface CertChainValidationResult<br>差异内容：NA|类名：cert；<br>API声明：interface CertChainValidationResult<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertChainValidationResult；<br>API声明：readonly trustAnchor: X509TrustAnchor;<br>差异内容：NA|类名：CertChainValidationResult；<br>API声明：readonly trustAnchor: X509TrustAnchor;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
|API从不支持元服务到支持元服务|类名：CertChainValidationResult；<br>API声明：readonly entityCert: X509Cert;<br>差异内容：NA|类名：CertChainValidationResult；<br>API声明：readonly entityCert: X509Cert;<br>差异内容：atomicservice|api/@ohos.security.cert.d.ts|
