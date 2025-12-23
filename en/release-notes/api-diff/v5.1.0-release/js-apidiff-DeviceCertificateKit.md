| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|Deleted error code|Class name: cert;<br>API declaration: function createX509Cert(inStream: EncodingBlob, callback: AsyncCallback\<X509Cert>): void;<br>DIfferences: 19030001|Class name: cert;<br>API declaration: function createX509Cert(inStream: EncodingBlob, callback: AsyncCallback\<X509Cert>): void;<br>DIfferences: NA|api/@ohos.security.cert.d.ts|
|Deleted error code|Class name: cert;<br>API declaration: function createX509Cert(inStream: EncodingBlob): Promise\<X509Cert>;<br>DIfferences: 19030001|Class name: cert;<br>API declaration: function createX509Cert(inStream: EncodingBlob): Promise\<X509Cert>;<br>DIfferences: NA|api/@ohos.security.cert.d.ts|
|Deleted error code|Class name: cert;<br>API declaration: function createCertExtension(inStream: EncodingBlob, callback: AsyncCallback\<CertExtension>): void;<br>DIfferences: 19030001|Class name: cert;<br>API declaration: function createCertExtension(inStream: EncodingBlob, callback: AsyncCallback\<CertExtension>): void;<br>DIfferences: NA|api/@ohos.security.cert.d.ts|
|Deleted error code|Class name: cert;<br>API declaration: function createCertExtension(inStream: EncodingBlob): Promise\<CertExtension>;<br>DIfferences: 19030001|Class name: cert;<br>API declaration: function createCertExtension(inStream: EncodingBlob): Promise\<CertExtension>;<br>DIfferences: NA|api/@ohos.security.cert.d.ts|
|Deleted error code|Class name: certificateManagerDialog;<br>API declaration: function openInstallCertificateDialog(context: common.Context, certType: CertificateType, certScope: CertificateScope, cert: Uint8Array): Promise\<string>;<br>DIfferences: 29700005|Class name: certificateManagerDialog;<br>API declaration: function openInstallCertificateDialog(context: common.Context, certType: CertificateType, certScope: CertificateScope, cert: Uint8Array): Promise\<string>;<br>DIfferences: NA|api/@ohos.security.certManagerDialog.d.ts|
| Deleted API|Class name: CertResult;<br>API declaration: ERR_PARAMETER_CHECK_FAILED = 19020003<br>DIfferences: ERR_PARAMETER_CHECK_FAILED = 19020003|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CertResult;<br>API declaration: ERR_MAYBE_WRONG_PASSWORD = 19030008<br>DIfferences: ERR_MAYBE_WRONG_PASSWORD = 19030008|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: cert;<br>API declaration: enum EncodingBaseFormat<br>DIfferences: enum EncodingBaseFormat|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: EncodingBaseFormat;<br>API declaration: PEM = 0<br>DIfferences: PEM = 0|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: EncodingBaseFormat;<br>API declaration: DER = 1<br>DIfferences: DER = 1|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: cert;<br>API declaration: interface Pkcs12Data<br>DIfferences: interface Pkcs12Data|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: Pkcs12Data;<br>API declaration: privateKey?: string \| Uint8Array;<br>DIfferences: privateKey?: string \| Uint8Array;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: Pkcs12Data;<br>API declaration: cert?: X509Cert;<br>DIfferences: cert?: X509Cert;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: Pkcs12Data;<br>API declaration: otherCerts?: Array\<X509Cert>;<br>DIfferences: otherCerts?: Array\<X509Cert>;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: cert;<br>API declaration: interface Pkcs12ParsingConfig<br>DIfferences: interface Pkcs12ParsingConfig|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: Pkcs12ParsingConfig;<br>API declaration: password: string;<br>DIfferences: password: string;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: Pkcs12ParsingConfig;<br>API declaration: needsPrivateKey?: boolean;<br>DIfferences: needsPrivateKey?: boolean;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: Pkcs12ParsingConfig;<br>API declaration: privateKeyFormat?: EncodingBaseFormat;<br>DIfferences: privateKeyFormat?: EncodingBaseFormat;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: Pkcs12ParsingConfig;<br>API declaration: needsCert?: boolean;<br>DIfferences: needsCert?: boolean;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: Pkcs12ParsingConfig;<br>API declaration: needsOtherCerts?: boolean;<br>DIfferences: needsOtherCerts?: boolean;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: cert;<br>API declaration: function parsePkcs12(data: Uint8Array, config: Pkcs12ParsingConfig): Pkcs12Data;<br>DIfferences: function parsePkcs12(data: Uint8Array, config: Pkcs12ParsingConfig): Pkcs12Data;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CertChainValidationParameters;<br>API declaration: trustSystemCa?: boolean;<br>DIfferences: trustSystemCa?: boolean;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: cert;<br>API declaration: enum CmsContentType<br>DIfferences: enum CmsContentType|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CmsContentType;<br>API declaration: SIGNED_DATA = 0<br>DIfferences: SIGNED_DATA = 0|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: cert;<br>API declaration: enum CmsContentDataFormat<br>DIfferences: enum CmsContentDataFormat|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CmsContentDataFormat;<br>API declaration: BINARY = 0<br>DIfferences: BINARY = 0|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CmsContentDataFormat;<br>API declaration: TEXT = 1<br>DIfferences: TEXT = 1|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: cert;<br>API declaration: enum CmsFormat<br>DIfferences: enum CmsFormat|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CmsFormat;<br>API declaration: PEM = 0<br>DIfferences: PEM = 0|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CmsFormat;<br>API declaration: DER = 1<br>DIfferences: DER = 1|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: cert;<br>API declaration: interface PrivateKeyInfo<br>DIfferences: interface PrivateKeyInfo|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: PrivateKeyInfo;<br>API declaration: key: string \| Uint8Array;<br>DIfferences: key: string \| Uint8Array;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: PrivateKeyInfo;<br>API declaration: password?: string;<br>DIfferences: password?: string;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: cert;<br>API declaration: interface CmsSignerConfig<br>DIfferences: interface CmsSignerConfig|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CmsSignerConfig;<br>API declaration: mdName: string;<br>DIfferences: mdName: string;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CmsSignerConfig;<br>API declaration: addCert?: boolean;<br>DIfferences: addCert?: boolean;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CmsSignerConfig;<br>API declaration: addAttr?: boolean;<br>DIfferences: addAttr?: boolean;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CmsSignerConfig;<br>API declaration: addSmimeCapAttr?: boolean;<br>DIfferences: addSmimeCapAttr?: boolean;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: cert;<br>API declaration: interface CmsGeneratorOptions<br>DIfferences: interface CmsGeneratorOptions|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CmsGeneratorOptions;<br>API declaration: contentDataFormat?: CmsContentDataFormat;<br>DIfferences: contentDataFormat?: CmsContentDataFormat;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CmsGeneratorOptions;<br>API declaration: outFormat?: CmsFormat;<br>DIfferences: outFormat?: CmsFormat;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CmsGeneratorOptions;<br>API declaration: isDetached?: boolean;<br>DIfferences: isDetached?: boolean;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: cert;<br>API declaration: interface CmsGenerator<br>DIfferences: interface CmsGenerator|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CmsGenerator;<br>API declaration: addSigner(cert: X509Cert, keyInfo: PrivateKeyInfo, config: CmsSignerConfig): void;<br>DIfferences: addSigner(cert: X509Cert, keyInfo: PrivateKeyInfo, config: CmsSignerConfig): void;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CmsGenerator;<br>API declaration: addCert(cert: X509Cert): void;<br>DIfferences: addCert(cert: X509Cert): void;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CmsGenerator;<br>API declaration: doFinal(data: Uint8Array, options?: CmsGeneratorOptions): Promise\<Uint8Array \| string>;<br>DIfferences: doFinal(data: Uint8Array, options?: CmsGeneratorOptions): Promise\<Uint8Array \| string>;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CmsGenerator;<br>API declaration: doFinalSync(data: Uint8Array, options?: CmsGeneratorOptions): Uint8Array \| string;<br>DIfferences: doFinalSync(data: Uint8Array, options?: CmsGeneratorOptions): Uint8Array \| string;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: cert;<br>API declaration: function createCmsGenerator(contentType: CmsContentType): CmsGenerator;<br>DIfferences: function createCmsGenerator(contentType: CmsContentType): CmsGenerator;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: cert;<br>API declaration: interface CsrAttribute<br>DIfferences: interface CsrAttribute|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CsrAttribute;<br>API declaration: type: string;<br>DIfferences: type: string;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CsrAttribute;<br>API declaration: value: string;<br>DIfferences: value: string;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: cert;<br>API declaration: interface CsrGenerationConfig<br>DIfferences: interface CsrGenerationConfig|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CsrGenerationConfig;<br>API declaration: subject: X500DistinguishedName;<br>DIfferences: subject: X500DistinguishedName;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CsrGenerationConfig;<br>API declaration: mdName: string;<br>DIfferences: mdName: string;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CsrGenerationConfig;<br>API declaration: attributes?: Array\<CsrAttribute>;<br>DIfferences: attributes?: Array\<CsrAttribute>;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CsrGenerationConfig;<br>API declaration: outFormat?: EncodingBaseFormat;<br>DIfferences: outFormat?: EncodingBaseFormat;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: cert;<br>API declaration: function generateCsr(keyInfo: PrivateKeyInfo, config: CsrGenerationConfig): string \| Uint8Array;<br>DIfferences: function generateCsr(keyInfo: PrivateKeyInfo, config: CsrGenerationConfig): string \| Uint8Array;|NA|api/@ohos.security.cert.d.ts|
| Deleted API|Class name: CMErrorCode;<br>API declaration: CM_ERROR_DEVICE_ENTER_ADVSECMODE = 17500007<br>DIfferences: CM_ERROR_DEVICE_ENTER_ADVSECMODE = 17500007|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: CMErrorCode;<br>API declaration: CM_ERROR_STORE_PATH_NOT_SUPPORTED = 17500009<br>DIfferences: CM_ERROR_STORE_PATH_NOT_SUPPORTED = 17500009|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: CmKeyDigest;<br>API declaration: CM_DIGEST_SM3 = 7<br>DIfferences: CM_DIGEST_SM3 = 7|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: certificateManager;<br>API declaration: export enum CertType<br>DIfferences: export enum CertType|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: CertType;<br>API declaration: CA_CERT_SYSTEM = 0<br>DIfferences: CA_CERT_SYSTEM = 0|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: CertType;<br>API declaration: CA_CERT_USER = 1<br>DIfferences: CA_CERT_USER = 1|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: certificateManager;<br>API declaration: export enum CertScope<br>DIfferences: export enum CertScope|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: CertScope;<br>API declaration: CURRENT_USER = 1<br>DIfferences: CURRENT_USER = 1|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: CertScope;<br>API declaration: GLOBAL_USER = 2<br>DIfferences: GLOBAL_USER = 2|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: certificateManager;<br>API declaration: export enum CertAlgorithm<br>DIfferences: export enum CertAlgorithm|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: CertAlgorithm;<br>API declaration: INTERNATIONAL = 1<br>DIfferences: INTERNATIONAL = 1|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: CertAlgorithm;<br>API declaration: SM = 2<br>DIfferences: SM = 2|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: certificateManager;<br>API declaration: export interface CertStoreProperty<br>DIfferences: export interface CertStoreProperty|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: CertStoreProperty;<br>API declaration: certType: CertType;<br>DIfferences: certType: CertType;|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: CertStoreProperty;<br>API declaration: certScope?: CertScope;<br>DIfferences: certScope?: CertScope;|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: CertStoreProperty;<br>API declaration: certAlg?: CertAlgorithm;<br>DIfferences: certAlg?: CertAlgorithm;|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: certificateManager;<br>API declaration: function getCertificateStorePath(property: CertStoreProperty): string;<br>DIfferences: function getCertificateStorePath(property: CertStoreProperty): string;|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: certificateManager;<br>API declaration: function installUserTrustedCertificateSync(cert: Uint8Array, certScope: CertScope): CMResult;<br>DIfferences: function installUserTrustedCertificateSync(cert: Uint8Array, certScope: CertScope): CMResult;|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: certificateManager;<br>API declaration: function uninstallUserTrustedCertificateSync(certUri: string): void;<br>DIfferences: function uninstallUserTrustedCertificateSync(certUri: string): void;|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: certificateManager;<br>API declaration: export enum AuthStorageLevel<br>DIfferences: export enum AuthStorageLevel|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: AuthStorageLevel;<br>API declaration: EL1 = 1<br>DIfferences: EL1 = 1|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: AuthStorageLevel;<br>API declaration: EL2 = 2<br>DIfferences: EL2 = 2|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: AuthStorageLevel;<br>API declaration: EL4 = 4<br>DIfferences: EL4 = 4|NA|api/@ohos.security.certManager.d.ts|
| Deleted API|Class name: CertificateDialogErrorCode;<br>API declaration: ERROR_NOT_COMPLY_SECURITY_POLICY = 29700005<br>DIfferences: ERROR_NOT_COMPLY_SECURITY_POLICY = 29700005|NA|api/@ohos.security.certManagerDialog.d.ts|
| Deleted API|Class name: CertificateScope;<br>API declaration: NOT_SPECIFIED = 0<br>DIfferences: NOT_SPECIFIED = 0|NA|api/@ohos.security.certManagerDialog.d.ts|
| Deleted API|Class name: CertificateScope;<br>API declaration: GLOBAL_USER = 2<br>DIfferences: GLOBAL_USER = 2|NA|api/@ohos.security.certManagerDialog.d.ts|
| Deleted API|Class name: certificateManagerDialog;<br>API declaration: function openUninstallCertificateDialog(context: common.Context, certType: CertificateType, certUri: string): Promise\<void>;<br>DIfferences: function openUninstallCertificateDialog(context: common.Context, certType: CertificateType, certUri: string): Promise\<void>;|NA|api/@ohos.security.certManagerDialog.d.ts|
| Deleted API|Class name: certificateManagerDialog;<br>API declaration: export interface CertificateDialogProperty<br>DIfferences: export interface CertificateDialogProperty|NA|api/@ohos.security.certManagerDialog.d.ts|
| Deleted API|Class name: CertificateDialogProperty;<br>API declaration: showInstallButton: boolean;<br>DIfferences: showInstallButton: boolean;|NA|api/@ohos.security.certManagerDialog.d.ts|
| Deleted API|Class name: certificateManagerDialog;<br>API declaration: function openCertificateDetailDialog(context: common.Context, cert: Uint8Array, property: CertificateDialogProperty): Promise\<void>;<br>DIfferences: function openCertificateDetailDialog(context: common.Context, cert: Uint8Array, property: CertificateDialogProperty): Promise\<void>;|NA|api/@ohos.security.certManagerDialog.d.ts|
| Deleted API|Class name: certificateManagerDialog;<br>API declaration: function openAuthorizeDialog(context: common.Context): Promise\<string>;<br>DIfferences: function openAuthorizeDialog(context: common.Context): Promise\<string>;|NA|api/@ohos.security.certManagerDialog.d.ts|
|Deleted duplicate function|Class name: X509Cert;<br>API declaration: getIssuerName(encodingType: EncodingType): string;<br>DIfferences: getIssuerName(encodingType: EncodingType): string;|Class name: global;<br>API declaration: <br>DIfferences: NA|api/@ohos.security.cert.d.ts|
|Deleted duplicate function|Class name: X509Cert;<br>API declaration: toString(encodingType: EncodingType): string;<br>DIfferences: toString(encodingType: EncodingType): string;|Class name: global;<br>API declaration: <br>DIfferences: NA|api/@ohos.security.cert.d.ts|
|Deleted duplicate function|Class name: X509CRLEntry;<br>API declaration: getCertIssuer(encodingType: EncodingType): string;<br>DIfferences: getCertIssuer(encodingType: EncodingType): string;|Class name: global;<br>API declaration: <br>DIfferences: NA|api/@ohos.security.cert.d.ts|
|Deleted duplicate function|Class name: X509CRL;<br>API declaration: getIssuerName(encodingType: EncodingType): string;<br>DIfferences: getIssuerName(encodingType: EncodingType): string;|Class name: global;<br>API declaration: <br>DIfferences: NA|api/@ohos.security.cert.d.ts|
|Deleted duplicate function|Class name: X509CRL;<br>API declaration: toString(encodingType: EncodingType): string;<br>DIfferences: toString(encodingType: EncodingType): string;|Class name: global;<br>API declaration: <br>DIfferences: NA|api/@ohos.security.cert.d.ts|
|Deleted duplicate function|Class name: X500DistinguishedName;<br>API declaration: getName(encodingType: EncodingType): string;<br>DIfferences: getName(encodingType: EncodingType): string;|Class name: global;<br>API declaration: <br>DIfferences: NA|api/@ohos.security.cert.d.ts|
|Deleted duplicate function|Class name: certificateManager;<br>API declaration: function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string, level: AuthStorageLevel): Promise\<CMResult>;<br>DIfferences: function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string, level: AuthStorageLevel): Promise\<CMResult>;|Class name: global;<br>API declaration: <br>DIfferences: NA|api/@ohos.security.certManager.d.ts|
|Deleted duplicate function|Class name: certificateManager;<br>API declaration: function getAllUserTrustedCertificates(scope: CertScope): Promise\<CMResult>;<br>DIfferences: function getAllUserTrustedCertificates(scope: CertScope): Promise\<CMResult>;|Class name: global;<br>API declaration: <br>DIfferences: NA|api/@ohos.security.certManager.d.ts|
