| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|删除错误码|类名：cert；<br>API声明：function createX509Cert(inStream: EncodingBlob, callback: AsyncCallback\<X509Cert>): void;<br>差异内容：19030001|类名：cert；<br>API声明：function createX509Cert(inStream: EncodingBlob, callback: AsyncCallback\<X509Cert>): void;<br>差异内容：NA|api/@ohos.security.cert.d.ts|
|删除错误码|类名：cert；<br>API声明：function createX509Cert(inStream: EncodingBlob): Promise\<X509Cert>;<br>差异内容：19030001|类名：cert；<br>API声明：function createX509Cert(inStream: EncodingBlob): Promise\<X509Cert>;<br>差异内容：NA|api/@ohos.security.cert.d.ts|
|删除错误码|类名：cert；<br>API声明：function createCertExtension(inStream: EncodingBlob, callback: AsyncCallback\<CertExtension>): void;<br>差异内容：19030001|类名：cert；<br>API声明：function createCertExtension(inStream: EncodingBlob, callback: AsyncCallback\<CertExtension>): void;<br>差异内容：NA|api/@ohos.security.cert.d.ts|
|删除错误码|类名：cert；<br>API声明：function createCertExtension(inStream: EncodingBlob): Promise\<CertExtension>;<br>差异内容：19030001|类名：cert；<br>API声明：function createCertExtension(inStream: EncodingBlob): Promise\<CertExtension>;<br>差异内容：NA|api/@ohos.security.cert.d.ts|
|删除错误码|类名：certificateManagerDialog；<br>API声明：function openInstallCertificateDialog(context: common.Context, certType: CertificateType, certScope: CertificateScope, cert: Uint8Array): Promise\<string>;<br>差异内容：29700005|类名：certificateManagerDialog；<br>API声明：function openInstallCertificateDialog(context: common.Context, certType: CertificateType, certScope: CertificateScope, cert: Uint8Array): Promise\<string>;<br>差异内容：NA|api/@ohos.security.certManagerDialog.d.ts|
|删除API|类名：CertResult；<br>API声明：ERR_PARAMETER_CHECK_FAILED = 19020003<br>差异内容：ERR_PARAMETER_CHECK_FAILED = 19020003|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CertResult；<br>API声明：ERR_MAYBE_WRONG_PASSWORD = 19030008<br>差异内容：ERR_MAYBE_WRONG_PASSWORD = 19030008|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：cert；<br>API声明：enum EncodingBaseFormat<br>差异内容：enum EncodingBaseFormat|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：EncodingBaseFormat；<br>API声明：PEM = 0<br>差异内容：PEM = 0|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：EncodingBaseFormat；<br>API声明：DER = 1<br>差异内容：DER = 1|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：cert；<br>API声明：interface Pkcs12Data<br>差异内容：interface Pkcs12Data|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：Pkcs12Data；<br>API声明：privateKey?: string \| Uint8Array;<br>差异内容：privateKey?: string \| Uint8Array;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：Pkcs12Data；<br>API声明：cert?: X509Cert;<br>差异内容：cert?: X509Cert;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：Pkcs12Data；<br>API声明：otherCerts?: Array\<X509Cert>;<br>差异内容：otherCerts?: Array\<X509Cert>;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：cert；<br>API声明：interface Pkcs12ParsingConfig<br>差异内容：interface Pkcs12ParsingConfig|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：Pkcs12ParsingConfig；<br>API声明：password: string;<br>差异内容：password: string;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：Pkcs12ParsingConfig；<br>API声明：needsPrivateKey?: boolean;<br>差异内容：needsPrivateKey?: boolean;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：Pkcs12ParsingConfig；<br>API声明：privateKeyFormat?: EncodingBaseFormat;<br>差异内容：privateKeyFormat?: EncodingBaseFormat;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：Pkcs12ParsingConfig；<br>API声明：needsCert?: boolean;<br>差异内容：needsCert?: boolean;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：Pkcs12ParsingConfig；<br>API声明：needsOtherCerts?: boolean;<br>差异内容：needsOtherCerts?: boolean;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：cert；<br>API声明：function parsePkcs12(data: Uint8Array, config: Pkcs12ParsingConfig): Pkcs12Data;<br>差异内容：function parsePkcs12(data: Uint8Array, config: Pkcs12ParsingConfig): Pkcs12Data;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CertChainValidationParameters；<br>API声明：trustSystemCa?: boolean;<br>差异内容：trustSystemCa?: boolean;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：cert；<br>API声明：enum CmsContentType<br>差异内容：enum CmsContentType|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CmsContentType；<br>API声明：SIGNED_DATA = 0<br>差异内容：SIGNED_DATA = 0|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：cert；<br>API声明：enum CmsContentDataFormat<br>差异内容：enum CmsContentDataFormat|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CmsContentDataFormat；<br>API声明：BINARY = 0<br>差异内容：BINARY = 0|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CmsContentDataFormat；<br>API声明：TEXT = 1<br>差异内容：TEXT = 1|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：cert；<br>API声明：enum CmsFormat<br>差异内容：enum CmsFormat|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CmsFormat；<br>API声明：PEM = 0<br>差异内容：PEM = 0|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CmsFormat；<br>API声明：DER = 1<br>差异内容：DER = 1|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：cert；<br>API声明：interface PrivateKeyInfo<br>差异内容：interface PrivateKeyInfo|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：PrivateKeyInfo；<br>API声明：key: string \| Uint8Array;<br>差异内容：key: string \| Uint8Array;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：PrivateKeyInfo；<br>API声明：password?: string;<br>差异内容：password?: string;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：cert；<br>API声明：interface CmsSignerConfig<br>差异内容：interface CmsSignerConfig|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CmsSignerConfig；<br>API声明：mdName: string;<br>差异内容：mdName: string;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CmsSignerConfig；<br>API声明：addCert?: boolean;<br>差异内容：addCert?: boolean;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CmsSignerConfig；<br>API声明：addAttr?: boolean;<br>差异内容：addAttr?: boolean;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CmsSignerConfig；<br>API声明：addSmimeCapAttr?: boolean;<br>差异内容：addSmimeCapAttr?: boolean;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：cert；<br>API声明：interface CmsGeneratorOptions<br>差异内容：interface CmsGeneratorOptions|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CmsGeneratorOptions；<br>API声明：contentDataFormat?: CmsContentDataFormat;<br>差异内容：contentDataFormat?: CmsContentDataFormat;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CmsGeneratorOptions；<br>API声明：outFormat?: CmsFormat;<br>差异内容：outFormat?: CmsFormat;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CmsGeneratorOptions；<br>API声明：isDetached?: boolean;<br>差异内容：isDetached?: boolean;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：cert；<br>API声明：interface CmsGenerator<br>差异内容：interface CmsGenerator|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CmsGenerator；<br>API声明：addSigner(cert: X509Cert, keyInfo: PrivateKeyInfo, config: CmsSignerConfig): void;<br>差异内容：addSigner(cert: X509Cert, keyInfo: PrivateKeyInfo, config: CmsSignerConfig): void;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CmsGenerator；<br>API声明：addCert(cert: X509Cert): void;<br>差异内容：addCert(cert: X509Cert): void;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CmsGenerator；<br>API声明：doFinal(data: Uint8Array, options?: CmsGeneratorOptions): Promise\<Uint8Array \| string>;<br>差异内容：doFinal(data: Uint8Array, options?: CmsGeneratorOptions): Promise\<Uint8Array \| string>;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CmsGenerator；<br>API声明：doFinalSync(data: Uint8Array, options?: CmsGeneratorOptions): Uint8Array \| string;<br>差异内容：doFinalSync(data: Uint8Array, options?: CmsGeneratorOptions): Uint8Array \| string;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：cert；<br>API声明：function createCmsGenerator(contentType: CmsContentType): CmsGenerator;<br>差异内容：function createCmsGenerator(contentType: CmsContentType): CmsGenerator;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：cert；<br>API声明：interface CsrAttribute<br>差异内容：interface CsrAttribute|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CsrAttribute；<br>API声明：type: string;<br>差异内容：type: string;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CsrAttribute；<br>API声明：value: string;<br>差异内容：value: string;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：cert；<br>API声明：interface CsrGenerationConfig<br>差异内容：interface CsrGenerationConfig|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CsrGenerationConfig；<br>API声明：subject: X500DistinguishedName;<br>差异内容：subject: X500DistinguishedName;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CsrGenerationConfig；<br>API声明：mdName: string;<br>差异内容：mdName: string;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CsrGenerationConfig；<br>API声明：attributes?: Array\<CsrAttribute>;<br>差异内容：attributes?: Array\<CsrAttribute>;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CsrGenerationConfig；<br>API声明：outFormat?: EncodingBaseFormat;<br>差异内容：outFormat?: EncodingBaseFormat;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：cert；<br>API声明：function generateCsr(keyInfo: PrivateKeyInfo, config: CsrGenerationConfig): string \| Uint8Array;<br>差异内容：function generateCsr(keyInfo: PrivateKeyInfo, config: CsrGenerationConfig): string \| Uint8Array;|NA|api/@ohos.security.cert.d.ts|
|删除API|类名：CMErrorCode；<br>API声明：CM_ERROR_DEVICE_ENTER_ADVSECMODE = 17500007<br>差异内容：CM_ERROR_DEVICE_ENTER_ADVSECMODE = 17500007|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：CMErrorCode；<br>API声明：CM_ERROR_STORE_PATH_NOT_SUPPORTED = 17500009<br>差异内容：CM_ERROR_STORE_PATH_NOT_SUPPORTED = 17500009|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：CmKeyDigest；<br>API声明：CM_DIGEST_SM3 = 7<br>差异内容：CM_DIGEST_SM3 = 7|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：certificateManager；<br>API声明：export enum CertType<br>差异内容：export enum CertType|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：CertType；<br>API声明：CA_CERT_SYSTEM = 0<br>差异内容：CA_CERT_SYSTEM = 0|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：CertType；<br>API声明：CA_CERT_USER = 1<br>差异内容：CA_CERT_USER = 1|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：certificateManager；<br>API声明：export enum CertScope<br>差异内容：export enum CertScope|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：CertScope；<br>API声明：CURRENT_USER = 1<br>差异内容：CURRENT_USER = 1|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：CertScope；<br>API声明：GLOBAL_USER = 2<br>差异内容：GLOBAL_USER = 2|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：certificateManager；<br>API声明：export enum CertAlgorithm<br>差异内容：export enum CertAlgorithm|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：CertAlgorithm；<br>API声明：INTERNATIONAL = 1<br>差异内容：INTERNATIONAL = 1|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：CertAlgorithm；<br>API声明：SM = 2<br>差异内容：SM = 2|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：certificateManager；<br>API声明：export interface CertStoreProperty<br>差异内容：export interface CertStoreProperty|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：CertStoreProperty；<br>API声明：certType: CertType;<br>差异内容：certType: CertType;|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：CertStoreProperty；<br>API声明：certScope?: CertScope;<br>差异内容：certScope?: CertScope;|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：CertStoreProperty；<br>API声明：certAlg?: CertAlgorithm;<br>差异内容：certAlg?: CertAlgorithm;|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：certificateManager；<br>API声明：function getCertificateStorePath(property: CertStoreProperty): string;<br>差异内容：function getCertificateStorePath(property: CertStoreProperty): string;|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：certificateManager；<br>API声明：function installUserTrustedCertificateSync(cert: Uint8Array, certScope: CertScope): CMResult;<br>差异内容：function installUserTrustedCertificateSync(cert: Uint8Array, certScope: CertScope): CMResult;|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：certificateManager；<br>API声明：function uninstallUserTrustedCertificateSync(certUri: string): void;<br>差异内容：function uninstallUserTrustedCertificateSync(certUri: string): void;|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：certificateManager；<br>API声明：export enum AuthStorageLevel<br>差异内容：export enum AuthStorageLevel|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：AuthStorageLevel；<br>API声明：EL1 = 1<br>差异内容：EL1 = 1|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：AuthStorageLevel；<br>API声明：EL2 = 2<br>差异内容：EL2 = 2|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：AuthStorageLevel；<br>API声明：EL4 = 4<br>差异内容：EL4 = 4|NA|api/@ohos.security.certManager.d.ts|
|删除API|类名：CertificateDialogErrorCode；<br>API声明：ERROR_NOT_COMPLY_SECURITY_POLICY = 29700005<br>差异内容：ERROR_NOT_COMPLY_SECURITY_POLICY = 29700005|NA|api/@ohos.security.certManagerDialog.d.ts|
|删除API|类名：CertificateScope；<br>API声明：NOT_SPECIFIED = 0<br>差异内容：NOT_SPECIFIED = 0|NA|api/@ohos.security.certManagerDialog.d.ts|
|删除API|类名：CertificateScope；<br>API声明：GLOBAL_USER = 2<br>差异内容：GLOBAL_USER = 2|NA|api/@ohos.security.certManagerDialog.d.ts|
|删除API|类名：certificateManagerDialog；<br>API声明：function openUninstallCertificateDialog(context: common.Context, certType: CertificateType, certUri: string): Promise\<void>;<br>差异内容：function openUninstallCertificateDialog(context: common.Context, certType: CertificateType, certUri: string): Promise\<void>;|NA|api/@ohos.security.certManagerDialog.d.ts|
|删除API|类名：certificateManagerDialog；<br>API声明：export interface CertificateDialogProperty<br>差异内容：export interface CertificateDialogProperty|NA|api/@ohos.security.certManagerDialog.d.ts|
|删除API|类名：CertificateDialogProperty；<br>API声明：showInstallButton: boolean;<br>差异内容：showInstallButton: boolean;|NA|api/@ohos.security.certManagerDialog.d.ts|
|删除API|类名：certificateManagerDialog；<br>API声明：function openCertificateDetailDialog(context: common.Context, cert: Uint8Array, property: CertificateDialogProperty): Promise\<void>;<br>差异内容：function openCertificateDetailDialog(context: common.Context, cert: Uint8Array, property: CertificateDialogProperty): Promise\<void>;|NA|api/@ohos.security.certManagerDialog.d.ts|
|删除API|类名：certificateManagerDialog；<br>API声明：function openAuthorizeDialog(context: common.Context): Promise\<string>;<br>差异内容：function openAuthorizeDialog(context: common.Context): Promise\<string>;|NA|api/@ohos.security.certManagerDialog.d.ts|
|删除同名函数|类名：X509Cert；<br>API声明：getIssuerName(encodingType: EncodingType): string;<br>差异内容：getIssuerName(encodingType: EncodingType): string;|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.security.cert.d.ts|
|删除同名函数|类名：X509Cert；<br>API声明：toString(encodingType: EncodingType): string;<br>差异内容：toString(encodingType: EncodingType): string;|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.security.cert.d.ts|
|删除同名函数|类名：X509CRLEntry；<br>API声明：getCertIssuer(encodingType: EncodingType): string;<br>差异内容：getCertIssuer(encodingType: EncodingType): string;|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.security.cert.d.ts|
|删除同名函数|类名：X509CRL；<br>API声明：getIssuerName(encodingType: EncodingType): string;<br>差异内容：getIssuerName(encodingType: EncodingType): string;|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.security.cert.d.ts|
|删除同名函数|类名：X509CRL；<br>API声明：toString(encodingType: EncodingType): string;<br>差异内容：toString(encodingType: EncodingType): string;|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.security.cert.d.ts|
|删除同名函数|类名：X500DistinguishedName；<br>API声明：getName(encodingType: EncodingType): string;<br>差异内容：getName(encodingType: EncodingType): string;|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.security.cert.d.ts|
|删除同名函数|类名：certificateManager；<br>API声明：function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string, level: AuthStorageLevel): Promise\<CMResult>;<br>差异内容：function installPrivateCertificate(keystore: Uint8Array, keystorePwd: string, certAlias: string, level: AuthStorageLevel): Promise\<CMResult>;|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.security.certManager.d.ts|
|删除同名函数|类名：certificateManager；<br>API声明：function getAllUserTrustedCertificates(scope: CertScope): Promise\<CMResult>;<br>差异内容：function getAllUserTrustedCertificates(scope: CertScope): Promise\<CMResult>;|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.security.certManager.d.ts|
