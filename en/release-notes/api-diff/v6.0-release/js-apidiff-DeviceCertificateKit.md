| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New error code|Class name: cert;<br>API declaration: function createX509Cert(inStream: EncodingBlob, callback: AsyncCallback\<X509Cert>): void;<br>DIfferences: NA|Class name: cert;<br>API declaration: function createX509Cert(inStream: EncodingBlob, callback: AsyncCallback\<X509Cert>): void;<br>DIfferences: 19030001|api/@ohos.security.cert.d.ts|
|New error code|Class name: cert;<br>API declaration: function createX509Cert(inStream: EncodingBlob): Promise\<X509Cert>;<br>DIfferences: NA|Class name: cert;<br>API declaration: function createX509Cert(inStream: EncodingBlob): Promise\<X509Cert>;<br>DIfferences: 19030001|api/@ohos.security.cert.d.ts|
|New error code|Class name: cert;<br>API declaration: function createCertExtension(inStream: EncodingBlob, callback: AsyncCallback\<CertExtension>): void;<br>DIfferences: NA|Class name: cert;<br>API declaration: function createCertExtension(inStream: EncodingBlob, callback: AsyncCallback\<CertExtension>): void;<br>DIfferences: 19030001|api/@ohos.security.cert.d.ts|
|New error code|Class name: cert;<br>API declaration: function createCertExtension(inStream: EncodingBlob): Promise\<CertExtension>;<br>DIfferences: NA|Class name: cert;<br>API declaration: function createCertExtension(inStream: EncodingBlob): Promise\<CertExtension>;<br>DIfferences: 19030001|api/@ohos.security.cert.d.ts|
|New error code|Class name: certificateManagerDialog;<br>API declaration: function openInstallCertificateDialog(context: common.Context, certType: CertificateType, certScope: CertificateScope, cert: Uint8Array): Promise\<string>;<br>DIfferences: NA|Class name: certificateManagerDialog;<br>API declaration: function openInstallCertificateDialog(context: common.Context, certType: CertificateType, certScope: CertificateScope, cert: Uint8Array): Promise\<string>;<br>DIfferences: 29700005|api/@ohos.security.certManagerDialog.d.ts|
|New API |NA|Class name: CertResult;<br>API declaration: ERR_MAYBE_WRONG_PASSWORD = 19030008<br>DIfferences: ERR_MAYBE_WRONG_PASSWORD = 19030008|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: cert;<br>API declaration: enum EncodingBaseFormat<br>DIfferences: enum EncodingBaseFormat|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: EncodingBaseFormat;<br>API declaration: PEM = 0<br>DIfferences: PEM = 0|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: EncodingBaseFormat;<br>API declaration: DER = 1<br>DIfferences: DER = 1|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: cert;<br>API declaration: interface Pkcs12Data<br>DIfferences: interface Pkcs12Data|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: Pkcs12Data;<br>API declaration: privateKey?: string \| Uint8Array;<br>DIfferences: privateKey?: string \| Uint8Array;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: Pkcs12Data;<br>API declaration: cert?: X509Cert;<br>DIfferences: cert?: X509Cert;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: Pkcs12Data;<br>API declaration: otherCerts?: Array\<X509Cert>;<br>DIfferences: otherCerts?: Array\<X509Cert>;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: cert;<br>API declaration: interface Pkcs12ParsingConfig<br>DIfferences: interface Pkcs12ParsingConfig|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: Pkcs12ParsingConfig;<br>API declaration: password: string;<br>DIfferences: password: string;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: Pkcs12ParsingConfig;<br>API declaration: needsPrivateKey?: boolean;<br>DIfferences: needsPrivateKey?: boolean;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: Pkcs12ParsingConfig;<br>API declaration: privateKeyFormat?: EncodingBaseFormat;<br>DIfferences: privateKeyFormat?: EncodingBaseFormat;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: Pkcs12ParsingConfig;<br>API declaration: needsCert?: boolean;<br>DIfferences: needsCert?: boolean;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: Pkcs12ParsingConfig;<br>API declaration: needsOtherCerts?: boolean;<br>DIfferences: needsOtherCerts?: boolean;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: cert;<br>API declaration: function parsePkcs12(data: Uint8Array, config: Pkcs12ParsingConfig): Pkcs12Data;<br>DIfferences: function parsePkcs12(data: Uint8Array, config: Pkcs12ParsingConfig): Pkcs12Data;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: cert;<br>API declaration: enum CmsContentType<br>DIfferences: enum CmsContentType|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CmsContentType;<br>API declaration: SIGNED_DATA = 0<br>DIfferences: SIGNED_DATA = 0|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: cert;<br>API declaration: enum CmsContentDataFormat<br>DIfferences: enum CmsContentDataFormat|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CmsContentDataFormat;<br>API declaration: BINARY = 0<br>DIfferences: BINARY = 0|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CmsContentDataFormat;<br>API declaration: TEXT = 1<br>DIfferences: TEXT = 1|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: cert;<br>API declaration: enum CmsFormat<br>DIfferences: enum CmsFormat|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CmsFormat;<br>API declaration: PEM = 0<br>DIfferences: PEM = 0|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CmsFormat;<br>API declaration: DER = 1<br>DIfferences: DER = 1|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: cert;<br>API declaration: interface PrivateKeyInfo<br>DIfferences: interface PrivateKeyInfo|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: PrivateKeyInfo;<br>API declaration: key: string \| Uint8Array;<br>DIfferences: key: string \| Uint8Array;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: PrivateKeyInfo;<br>API declaration: password?: string;<br>DIfferences: password?: string;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: cert;<br>API declaration: interface CmsSignerConfig<br>DIfferences: interface CmsSignerConfig|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CmsSignerConfig;<br>API declaration: mdName: string;<br>DIfferences: mdName: string;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CmsSignerConfig;<br>API declaration: addCert?: boolean;<br>DIfferences: addCert?: boolean;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CmsSignerConfig;<br>API declaration: addAttr?: boolean;<br>DIfferences: addAttr?: boolean;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CmsSignerConfig;<br>API declaration: addSmimeCapAttr?: boolean;<br>DIfferences: addSmimeCapAttr?: boolean;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: cert;<br>API declaration: interface CmsGeneratorOptions<br>DIfferences: interface CmsGeneratorOptions|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CmsGeneratorOptions;<br>API declaration: contentDataFormat?: CmsContentDataFormat;<br>DIfferences: contentDataFormat?: CmsContentDataFormat;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CmsGeneratorOptions;<br>API declaration: outFormat?: CmsFormat;<br>DIfferences: outFormat?: CmsFormat;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CmsGeneratorOptions;<br>API declaration: isDetached?: boolean;<br>DIfferences: isDetached?: boolean;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: cert;<br>API declaration: interface CmsGenerator<br>DIfferences: interface CmsGenerator|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CmsGenerator;<br>API declaration: addSigner(cert: X509Cert, keyInfo: PrivateKeyInfo, config: CmsSignerConfig): void;<br>DIfferences: addSigner(cert: X509Cert, keyInfo: PrivateKeyInfo, config: CmsSignerConfig): void;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CmsGenerator;<br>API declaration: addCert(cert: X509Cert): void;<br>DIfferences: addCert(cert: X509Cert): void;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CmsGenerator;<br>API declaration: doFinal(data: Uint8Array, options?: CmsGeneratorOptions): Promise\<Uint8Array \| string>;<br>DIfferences: doFinal(data: Uint8Array, options?: CmsGeneratorOptions): Promise\<Uint8Array \| string>;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CmsGenerator;<br>API declaration: doFinalSync(data: Uint8Array, options?: CmsGeneratorOptions): Uint8Array \| string;<br>DIfferences: doFinalSync(data: Uint8Array, options?: CmsGeneratorOptions): Uint8Array \| string;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: cert;<br>API declaration: function createCmsGenerator(contentType: CmsContentType): CmsGenerator;<br>DIfferences: function createCmsGenerator(contentType: CmsContentType): CmsGenerator;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: cert;<br>API declaration: interface CsrAttribute<br>DIfferences: interface CsrAttribute|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CsrAttribute;<br>API declaration: type: string;<br>DIfferences: type: string;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CsrAttribute;<br>API declaration: value: string;<br>DIfferences: value: string;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: cert;<br>API declaration: interface CsrGenerationConfig<br>DIfferences: interface CsrGenerationConfig|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CsrGenerationConfig;<br>API declaration: subject: X500DistinguishedName;<br>DIfferences: subject: X500DistinguishedName;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CsrGenerationConfig;<br>API declaration: mdName: string;<br>DIfferences: mdName: string;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CsrGenerationConfig;<br>API declaration: attributes?: Array\<CsrAttribute>;<br>DIfferences: attributes?: Array\<CsrAttribute>;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: CsrGenerationConfig;<br>API declaration: outFormat?: EncodingBaseFormat;<br>DIfferences: outFormat?: EncodingBaseFormat;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: cert;<br>API declaration: function generateCsr(keyInfo: PrivateKeyInfo, config: CsrGenerationConfig): string \| Uint8Array;<br>DIfferences: function generateCsr(keyInfo: PrivateKeyInfo, config: CsrGenerationConfig): string \| Uint8Array;|api/@ohos.security.cert.d.ts|
|New API |NA|Class name: certificateManager;<br>API declaration: function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string, level: AuthStorageLevel): Promise\<CMResult>;<br>DIfferences: function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string, level: AuthStorageLevel): Promise\<CMResult>;|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: certificateManager;<br>API declaration: function getAllUserTrustedCertificates(scope: CertScope): Promise\<CMResult>;<br>DIfferences: function getAllUserTrustedCertificates(scope: CertScope): Promise\<CMResult>;|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: CMErrorCode;<br>API declaration: CM_ERROR_DEVICE_ENTER_ADVSECMODE = 17500007<br>DIfferences: CM_ERROR_DEVICE_ENTER_ADVSECMODE = 17500007|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: CmKeyDigest;<br>API declaration: CM_DIGEST_SM3 = 7<br>DIfferences: CM_DIGEST_SM3 = 7|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: certificateManager;<br>API declaration: export enum CertType<br>DIfferences: export enum CertType|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: CertType;<br>API declaration: CA_CERT_SYSTEM = 0<br>DIfferences: CA_CERT_SYSTEM = 0|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: CertType;<br>API declaration: CA_CERT_USER = 1<br>DIfferences: CA_CERT_USER = 1|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: certificateManager;<br>API declaration: export enum CertScope<br>DIfferences: export enum CertScope|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: CertScope;<br>API declaration: CURRENT_USER = 1<br>DIfferences: CURRENT_USER = 1|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: CertScope;<br>API declaration: GLOBAL_USER = 2<br>DIfferences: GLOBAL_USER = 2|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: certificateManager;<br>API declaration: export interface CertStoreProperty<br>DIfferences: export interface CertStoreProperty|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: CertStoreProperty;<br>API declaration: certType: CertType;<br>DIfferences: certType: CertType;|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: CertStoreProperty;<br>API declaration: certScope?: CertScope;<br>DIfferences: certScope?: CertScope;|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: certificateManager;<br>API declaration: function getCertificateStorePath(property: CertStoreProperty): string;<br>DIfferences: function getCertificateStorePath(property: CertStoreProperty): string;|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: certificateManager;<br>API declaration: function installUserTrustedCertificateSync(cert: Uint8Array, certScope: CertScope): CMResult;<br>DIfferences: function installUserTrustedCertificateSync(cert: Uint8Array, certScope: CertScope): CMResult;|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: certificateManager;<br>API declaration: function uninstallUserTrustedCertificateSync(certUri: string): void;<br>DIfferences: function uninstallUserTrustedCertificateSync(certUri: string): void;|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: certificateManager;<br>API declaration: export enum AuthStorageLevel<br>DIfferences: export enum AuthStorageLevel|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: AuthStorageLevel;<br>API declaration: EL1 = 1<br>DIfferences: EL1 = 1|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: AuthStorageLevel;<br>API declaration: EL2 = 2<br>DIfferences: EL2 = 2|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: AuthStorageLevel;<br>API declaration: EL4 = 4<br>DIfferences: EL4 = 4|api/@ohos.security.certManager.d.ts|
|New API |NA|Class name: CertificateDialogErrorCode;<br>API declaration: ERROR_NOT_COMPLY_SECURITY_POLICY = 29700005<br>DIfferences: ERROR_NOT_COMPLY_SECURITY_POLICY = 29700005|api/@ohos.security.certManagerDialog.d.ts|
|New API |NA|Class name: CertificateScope;<br>API declaration: NOT_SPECIFIED = 0<br>DIfferences: NOT_SPECIFIED = 0|api/@ohos.security.certManagerDialog.d.ts|
|New API |NA|Class name: CertificateScope;<br>API declaration: GLOBAL_USER = 2<br>DIfferences: GLOBAL_USER = 2|api/@ohos.security.certManagerDialog.d.ts|
|New API |NA|Class name: certificateManagerDialog;<br>API declaration: function openUninstallCertificateDialog(context: common.Context, certType: CertificateType, certUri: string): Promise\<void>;<br>DIfferences: function openUninstallCertificateDialog(context: common.Context, certType: CertificateType, certUri: string): Promise\<void>;|api/@ohos.security.certManagerDialog.d.ts|
|New API |NA|Class name: certificateManagerDialog;<br>API declaration: export interface CertificateDialogProperty<br>DIfferences: export interface CertificateDialogProperty|api/@ohos.security.certManagerDialog.d.ts|
|New API |NA|Class name: CertificateDialogProperty;<br>API declaration: showInstallButton: boolean;<br>DIfferences: showInstallButton: boolean;|api/@ohos.security.certManagerDialog.d.ts|
|New API |NA|Class name: certificateManagerDialog;<br>API declaration: function openCertificateDetailDialog(context: common.Context, cert: Uint8Array, property: CertificateDialogProperty): Promise\<void>;<br>DIfferences: function openCertificateDetailDialog(context: common.Context, cert: Uint8Array, property: CertificateDialogProperty): Promise\<void>;|api/@ohos.security.certManagerDialog.d.ts|
