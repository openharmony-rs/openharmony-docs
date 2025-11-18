| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增错误码|类名：cert；<br>API声明：function createX509Cert(inStream: EncodingBlob, callback: AsyncCallback\<X509Cert>): void;<br>差异内容：NA|类名：cert；<br>API声明：function createX509Cert(inStream: EncodingBlob, callback: AsyncCallback\<X509Cert>): void;<br>差异内容：19030001|api/@ohos.security.cert.d.ts|
|新增错误码|类名：cert；<br>API声明：function createX509Cert(inStream: EncodingBlob): Promise\<X509Cert>;<br>差异内容：NA|类名：cert；<br>API声明：function createX509Cert(inStream: EncodingBlob): Promise\<X509Cert>;<br>差异内容：19030001|api/@ohos.security.cert.d.ts|
|新增错误码|类名：cert；<br>API声明：function createCertExtension(inStream: EncodingBlob, callback: AsyncCallback\<CertExtension>): void;<br>差异内容：NA|类名：cert；<br>API声明：function createCertExtension(inStream: EncodingBlob, callback: AsyncCallback\<CertExtension>): void;<br>差异内容：19030001|api/@ohos.security.cert.d.ts|
|新增错误码|类名：cert；<br>API声明：function createCertExtension(inStream: EncodingBlob): Promise\<CertExtension>;<br>差异内容：NA|类名：cert；<br>API声明：function createCertExtension(inStream: EncodingBlob): Promise\<CertExtension>;<br>差异内容：19030001|api/@ohos.security.cert.d.ts|
|新增错误码|类名：certificateManagerDialog；<br>API声明：function openInstallCertificateDialog(context: common.Context, certType: CertificateType, certScope: CertificateScope, cert: Uint8Array): Promise\<string>;<br>差异内容：NA|类名：certificateManagerDialog；<br>API声明：function openInstallCertificateDialog(context: common.Context, certType: CertificateType, certScope: CertificateScope, cert: Uint8Array): Promise\<string>;<br>差异内容：29700005|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：CertResult；<br>API声明：ERR_PARAMETER_CHECK_FAILED = 19020003<br>差异内容：ERR_PARAMETER_CHECK_FAILED = 19020003|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CertResult；<br>API声明：ERR_MAYBE_WRONG_PASSWORD = 19030008<br>差异内容：ERR_MAYBE_WRONG_PASSWORD = 19030008|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：enum EncodingBaseFormat<br>差异内容：enum EncodingBaseFormat|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：EncodingBaseFormat；<br>API声明：PEM = 0<br>差异内容：PEM = 0|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：EncodingBaseFormat；<br>API声明：DER = 1<br>差异内容：DER = 1|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：interface Pkcs12Data<br>差异内容：interface Pkcs12Data|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：Pkcs12Data；<br>API声明：privateKey?: string \| Uint8Array;<br>差异内容：privateKey?: string \| Uint8Array;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：Pkcs12Data；<br>API声明：cert?: X509Cert;<br>差异内容：cert?: X509Cert;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：Pkcs12Data；<br>API声明：otherCerts?: Array\<X509Cert>;<br>差异内容：otherCerts?: Array\<X509Cert>;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：interface Pkcs12ParsingConfig<br>差异内容：interface Pkcs12ParsingConfig|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：Pkcs12ParsingConfig；<br>API声明：password: string;<br>差异内容：password: string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：Pkcs12ParsingConfig；<br>API声明：needsPrivateKey?: boolean;<br>差异内容：needsPrivateKey?: boolean;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：Pkcs12ParsingConfig；<br>API声明：privateKeyFormat?: EncodingBaseFormat;<br>差异内容：privateKeyFormat?: EncodingBaseFormat;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：Pkcs12ParsingConfig；<br>API声明：needsCert?: boolean;<br>差异内容：needsCert?: boolean;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：Pkcs12ParsingConfig；<br>API声明：needsOtherCerts?: boolean;<br>差异内容：needsOtherCerts?: boolean;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：function parsePkcs12(data: Uint8Array, config: Pkcs12ParsingConfig): Pkcs12Data;<br>差异内容：function parsePkcs12(data: Uint8Array, config: Pkcs12ParsingConfig): Pkcs12Data;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CertChainValidationParameters；<br>API声明：trustSystemCa?: boolean;<br>差异内容：trustSystemCa?: boolean;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：enum CmsContentType<br>差异内容：enum CmsContentType|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CmsContentType；<br>API声明：SIGNED_DATA = 0<br>差异内容：SIGNED_DATA = 0|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：enum CmsContentDataFormat<br>差异内容：enum CmsContentDataFormat|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CmsContentDataFormat；<br>API声明：BINARY = 0<br>差异内容：BINARY = 0|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CmsContentDataFormat；<br>API声明：TEXT = 1<br>差异内容：TEXT = 1|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：enum CmsFormat<br>差异内容：enum CmsFormat|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CmsFormat；<br>API声明：PEM = 0<br>差异内容：PEM = 0|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CmsFormat；<br>API声明：DER = 1<br>差异内容：DER = 1|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：interface PrivateKeyInfo<br>差异内容：interface PrivateKeyInfo|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：PrivateKeyInfo；<br>API声明：key: string \| Uint8Array;<br>差异内容：key: string \| Uint8Array;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：PrivateKeyInfo；<br>API声明：password?: string;<br>差异内容：password?: string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：interface CmsSignerConfig<br>差异内容：interface CmsSignerConfig|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CmsSignerConfig；<br>API声明：mdName: string;<br>差异内容：mdName: string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CmsSignerConfig；<br>API声明：addCert?: boolean;<br>差异内容：addCert?: boolean;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CmsSignerConfig；<br>API声明：addAttr?: boolean;<br>差异内容：addAttr?: boolean;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CmsSignerConfig；<br>API声明：addSmimeCapAttr?: boolean;<br>差异内容：addSmimeCapAttr?: boolean;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：interface CmsGeneratorOptions<br>差异内容：interface CmsGeneratorOptions|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CmsGeneratorOptions；<br>API声明：contentDataFormat?: CmsContentDataFormat;<br>差异内容：contentDataFormat?: CmsContentDataFormat;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CmsGeneratorOptions；<br>API声明：outFormat?: CmsFormat;<br>差异内容：outFormat?: CmsFormat;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CmsGeneratorOptions；<br>API声明：isDetached?: boolean;<br>差异内容：isDetached?: boolean;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：interface CmsGenerator<br>差异内容：interface CmsGenerator|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CmsGenerator；<br>API声明：addSigner(cert: X509Cert, keyInfo: PrivateKeyInfo, config: CmsSignerConfig): void;<br>差异内容：addSigner(cert: X509Cert, keyInfo: PrivateKeyInfo, config: CmsSignerConfig): void;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CmsGenerator；<br>API声明：addCert(cert: X509Cert): void;<br>差异内容：addCert(cert: X509Cert): void;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CmsGenerator；<br>API声明：doFinal(data: Uint8Array, options?: CmsGeneratorOptions): Promise\<Uint8Array \| string>;<br>差异内容：doFinal(data: Uint8Array, options?: CmsGeneratorOptions): Promise\<Uint8Array \| string>;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CmsGenerator；<br>API声明：doFinalSync(data: Uint8Array, options?: CmsGeneratorOptions): Uint8Array \| string;<br>差异内容：doFinalSync(data: Uint8Array, options?: CmsGeneratorOptions): Uint8Array \| string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：function createCmsGenerator(contentType: CmsContentType): CmsGenerator;<br>差异内容：function createCmsGenerator(contentType: CmsContentType): CmsGenerator;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：interface CsrAttribute<br>差异内容：interface CsrAttribute|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CsrAttribute；<br>API声明：type: string;<br>差异内容：type: string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CsrAttribute；<br>API声明：value: string;<br>差异内容：value: string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：interface CsrGenerationConfig<br>差异内容：interface CsrGenerationConfig|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CsrGenerationConfig；<br>API声明：subject: X500DistinguishedName;<br>差异内容：subject: X500DistinguishedName;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CsrGenerationConfig；<br>API声明：mdName: string;<br>差异内容：mdName: string;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CsrGenerationConfig；<br>API声明：attributes?: Array\<CsrAttribute>;<br>差异内容：attributes?: Array\<CsrAttribute>;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CsrGenerationConfig；<br>API声明：outFormat?: EncodingBaseFormat;<br>差异内容：outFormat?: EncodingBaseFormat;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：cert；<br>API声明：function generateCsr(keyInfo: PrivateKeyInfo, config: CsrGenerationConfig): string \| Uint8Array;<br>差异内容：function generateCsr(keyInfo: PrivateKeyInfo, config: CsrGenerationConfig): string \| Uint8Array;|api/@ohos.security.cert.d.ts|
|新增API|NA|类名：CertificateDialogErrorCode；<br>API声明：ERROR_NOT_COMPLY_SECURITY_POLICY = 29700005<br>差异内容：ERROR_NOT_COMPLY_SECURITY_POLICY = 29700005|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：CertificateScope；<br>API声明：NOT_SPECIFIED = 0<br>差异内容：NOT_SPECIFIED = 0|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：CertificateScope；<br>API声明：GLOBAL_USER = 2<br>差异内容：GLOBAL_USER = 2|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：certificateManagerDialog；<br>API声明：function openUninstallCertificateDialog(context: common.Context, certType: CertificateType, certUri: string): Promise\<void>;<br>差异内容：function openUninstallCertificateDialog(context: common.Context, certType: CertificateType, certUri: string): Promise\<void>;|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：certificateManagerDialog；<br>API声明：export interface CertificateDialogProperty<br>差异内容：export interface CertificateDialogProperty|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：CertificateDialogProperty；<br>API声明：showInstallButton: boolean;<br>差异内容：showInstallButton: boolean;|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：certificateManagerDialog；<br>API声明：function openCertificateDetailDialog(context: common.Context, cert: Uint8Array, property: CertificateDialogProperty): Promise\<void>;<br>差异内容：function openCertificateDetailDialog(context: common.Context, cert: Uint8Array, property: CertificateDialogProperty): Promise\<void>;|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：certificateManagerDialog；<br>API声明：function openAuthorizeDialog(context: common.Context): Promise\<string>;<br>差异内容：function openAuthorizeDialog(context: common.Context): Promise\<string>;|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：CMErrorCode；<br>API声明：CM_ERROR_DEVICE_ENTER_ADVSECMODE = 17500007<br>差异内容：CM_ERROR_DEVICE_ENTER_ADVSECMODE = 17500007|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：CMErrorCode；<br>API声明：CM_ERROR_STORE_PATH_NOT_SUPPORTED = 17500009<br>差异内容：CM_ERROR_STORE_PATH_NOT_SUPPORTED = 17500009|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：CmKeyDigest；<br>API声明：CM_DIGEST_SM3 = 7<br>差异内容：CM_DIGEST_SM3 = 7|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：certificateManager；<br>API声明：export enum CertType<br>差异内容：export enum CertType|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：CertType；<br>API声明：CA_CERT_SYSTEM = 0<br>差异内容：CA_CERT_SYSTEM = 0|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：CertType；<br>API声明：CA_CERT_USER = 1<br>差异内容：CA_CERT_USER = 1|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：certificateManager；<br>API声明：export enum CertScope<br>差异内容：export enum CertScope|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：CertScope；<br>API声明：CURRENT_USER = 1<br>差异内容：CURRENT_USER = 1|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：CertScope；<br>API声明：GLOBAL_USER = 2<br>差异内容：GLOBAL_USER = 2|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：certificateManager；<br>API声明：export enum CertAlgorithm<br>差异内容：export enum CertAlgorithm|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：CertAlgorithm；<br>API声明：INTERNATIONAL = 1<br>差异内容：INTERNATIONAL = 1|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：CertAlgorithm；<br>API声明：SM = 2<br>差异内容：SM = 2|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：certificateManager；<br>API声明：export interface CertStoreProperty<br>差异内容：export interface CertStoreProperty|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：CertStoreProperty；<br>API声明：certType: CertType;<br>差异内容：certType: CertType;|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：CertStoreProperty；<br>API声明：certScope?: CertScope;<br>差异内容：certScope?: CertScope;|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：CertStoreProperty；<br>API声明：certAlg?: CertAlgorithm;<br>差异内容：certAlg?: CertAlgorithm;|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：certificateManager；<br>API声明：function getCertificateStorePath(property: CertStoreProperty): string;<br>差异内容：function getCertificateStorePath(property: CertStoreProperty): string;|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：certificateManager；<br>API声明：function installUserTrustedCertificateSync(cert: Uint8Array, certScope: CertScope): CMResult;<br>差异内容：function installUserTrustedCertificateSync(cert: Uint8Array, certScope: CertScope): CMResult;|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：certificateManager；<br>API声明：function uninstallUserTrustedCertificateSync(certUri: string): void;<br>差异内容：function uninstallUserTrustedCertificateSync(certUri: string): void;|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：certificateManager；<br>API声明：export enum AuthStorageLevel<br>差异内容：export enum AuthStorageLevel|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：AuthStorageLevel；<br>API声明：EL1 = 1<br>差异内容：EL1 = 1|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：AuthStorageLevel；<br>API声明：EL2 = 2<br>差异内容：EL2 = 2|api/@ohos.security.certManager.d.ts|
|新增API|NA|类名：AuthStorageLevel；<br>API声明：EL4 = 4<br>差异内容：EL4 = 4|api/@ohos.security.certManager.d.ts|
|接口新增同名方法且参数类型与已有的参数类型范围是包含关系|类名：X509Cert；<br>API声明：getIssuerName(): DataBlob;<br>差异内容：getIssuerName(): DataBlob;|类名：X509Cert；<br>API声明：getIssuerName(encodingType: EncodingType): string;<br>差异内容：getIssuerName(encodingType: EncodingType): string;|api/@ohos.security.cert.d.ts|
|接口新增同名方法且参数类型与已有的参数类型范围是包含关系|类名：X509Cert；<br>API声明：toString(): string;<br>差异内容：toString(): string;|类名：X509Cert；<br>API声明：toString(encodingType: EncodingType): string;<br>差异内容：toString(encodingType: EncodingType): string;|api/@ohos.security.cert.d.ts|
|接口新增同名方法且参数类型与已有的参数类型范围是包含关系|类名：X509CRLEntry；<br>API声明：getCertIssuer(): DataBlob;<br>差异内容：getCertIssuer(): DataBlob;|类名：X509CRLEntry；<br>API声明：getCertIssuer(encodingType: EncodingType): string;<br>差异内容：getCertIssuer(encodingType: EncodingType): string;|api/@ohos.security.cert.d.ts|
|接口新增同名方法且参数类型与已有的参数类型范围是包含关系|类名：X509CRL；<br>API声明：getIssuerName(): DataBlob;<br>差异内容：getIssuerName(): DataBlob;|类名：X509CRL；<br>API声明：getIssuerName(encodingType: EncodingType): string;<br>差异内容：getIssuerName(encodingType: EncodingType): string;|api/@ohos.security.cert.d.ts|
|接口新增同名方法且参数类型与已有的参数类型范围是包含关系|类名：X509CRL；<br>API声明：toString(): string;<br>差异内容：toString(): string;|类名：X509CRL；<br>API声明：toString(encodingType: EncodingType): string;<br>差异内容：toString(encodingType: EncodingType): string;|api/@ohos.security.cert.d.ts|
|接口新增同名方法且参数类型与已有的参数类型范围是包含关系|类名：X500DistinguishedName；<br>API声明：getName(): string;<br>差异内容：getName(): string;|类名：X500DistinguishedName；<br>API声明：getName(encodingType: EncodingType): string;<br>差异内容：getName(encodingType: EncodingType): string;|api/@ohos.security.cert.d.ts|
