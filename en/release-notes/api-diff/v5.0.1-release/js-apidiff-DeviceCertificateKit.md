| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: global;<br>API declaration: declare namespace certificateManagerDialog<br>Differences: declare namespace certificateManagerDialog|api/@ohos.security.certManagerDialog.d.ts|
|New API |NA|Class name: certificateManagerDialog;<br>API declaration: export enum CertificateDialogErrorCode<br>Differences: export enum CertificateDialogErrorCode|api/@ohos.security.certManagerDialog.d.ts|
|New API |NA|Class name: CertificateDialogErrorCode;<br>API declaration: ERROR_GENERIC = 29700001<br>Differences: ERROR_GENERIC = 29700001|api/@ohos.security.certManagerDialog.d.ts|
|New API |NA|Class name: certificateManagerDialog;<br>API declaration: export enum CertificateDialogPageType<br>Differences: export enum CertificateDialogPageType|api/@ohos.security.certManagerDialog.d.ts|
|New API |NA|Class name: CertificateDialogPageType;<br>API declaration: PAGE_MAIN = 1<br>Differences: PAGE_MAIN = 1|api/@ohos.security.certManagerDialog.d.ts|
|New API |NA|Class name: CertificateDialogPageType;<br>API declaration: PAGE_CA_CERTIFICATE = 2<br>Differences: PAGE_CA_CERTIFICATE = 2|api/@ohos.security.certManagerDialog.d.ts|
|New API |NA|Class name: CertificateDialogPageType;<br>API declaration: PAGE_CREDENTIAL = 3<br>Differences: PAGE_CREDENTIAL = 3|api/@ohos.security.certManagerDialog.d.ts|
|New API |NA|Class name: CertificateDialogPageType;<br>API declaration: PAGE_INSTALL_CERTIFICATE = 4<br>Differences: PAGE_INSTALL_CERTIFICATE = 4|api/@ohos.security.certManagerDialog.d.ts|
|New API |NA|Class name: certificateManagerDialog;<br>API declaration: function openCertificateManagerDialog(context: common.Context, pageType: CertificateDialogPageType): Promise\<void>;<br>Differences: function openCertificateManagerDialog(context: common.Context, pageType: CertificateDialogPageType): Promise\<void>;|api/@ohos.security.certManagerDialog.d.ts|
|New API |NA|Class name: certificateManager;<br>API declaration: function getPrivateCertificates(): Promise\<CMResult>;<br>Differences: function getPrivateCertificates(): Promise\<CMResult>;|api/@ohos.security.certManager.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.security.certManagerDialog.d.ts<br>Differences: DeviceCertificateKit|api/@ohos.security.certManagerDialog.d.ts|
