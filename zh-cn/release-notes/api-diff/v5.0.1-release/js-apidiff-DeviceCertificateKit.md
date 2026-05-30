| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace certificateManagerDialog<br>差异内容：declare namespace certificateManagerDialog|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：certificateManagerDialog；<br>API声明：export enum CertificateDialogErrorCode<br>差异内容：export enum CertificateDialogErrorCode|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：CertificateDialogErrorCode；<br>API声明：ERROR_GENERIC = 29700001<br>差异内容：ERROR_GENERIC = 29700001|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：certificateManagerDialog；<br>API声明：export enum CertificateDialogPageType<br>差异内容：export enum CertificateDialogPageType|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：CertificateDialogPageType；<br>API声明：PAGE_MAIN = 1<br>差异内容：PAGE_MAIN = 1|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：CertificateDialogPageType；<br>API声明：PAGE_CA_CERTIFICATE = 2<br>差异内容：PAGE_CA_CERTIFICATE = 2|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：CertificateDialogPageType；<br>API声明：PAGE_CREDENTIAL = 3<br>差异内容：PAGE_CREDENTIAL = 3|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：CertificateDialogPageType；<br>API声明：PAGE_INSTALL_CERTIFICATE = 4<br>差异内容：PAGE_INSTALL_CERTIFICATE = 4|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：certificateManagerDialog；<br>API声明：function openCertificateManagerDialog(context: common.Context, pageType: CertificateDialogPageType): Promise\<void>;<br>差异内容：function openCertificateManagerDialog(context: common.Context, pageType: CertificateDialogPageType): Promise\<void>;|api/@ohos.security.certManagerDialog.d.ts|
|新增API|NA|类名：certificateManager；<br>API声明：function getPrivateCertificates(): Promise\<CMResult>;<br>差异内容：function getPrivateCertificates(): Promise\<CMResult>;|api/@ohos.security.certManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.security.certManagerDialog.d.ts<br>差异内容：DeviceCertificateKit|api/@ohos.security.certManagerDialog.d.ts|
