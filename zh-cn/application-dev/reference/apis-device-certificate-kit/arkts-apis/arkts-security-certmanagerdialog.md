# @ohos.security.certManagerDialog

证书管理对话框主要提供打开证书管理界面的能力，用户在打开的证书管理对话框可对证书进行查看和管理（安装，卸载、授权）。

**起始版本：** 13

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [openAuthorizeDialog](arkts-devicecertificate-openauthorizedialog-f.md#openauthorizedialog-1) | 打开证书管理对话框的证书凭据授权页面。在弹出的页面中，用户可以为应用授权使用证书凭据。调用成功后，应用可通过接口返回的授权证书凭据uri进行签名、验签和查询详情操作。使用Promise异步回调。 |
| [openAuthorizeDialog](arkts-devicecertificate-openauthorizedialog-f.md#openauthorizedialog-2) | 打开证书管理对话框的证书凭据授权页面。在弹出的页面中，用户可以为应用授权使用证书凭据。调用成功后，应用可通过接口返回的授权证书凭据uri进行签名、验签和查询详情操作。可授权的证书类型包括应用证书凭据、用户证书凭据和USBKey证书凭据。使用Promise异步回调。 |
| [openCertificateDetailDialog](arkts-devicecertificate-opencertificatedetaildialog-f.md#opencertificatedetaildialog-1) | 打开证书管理对话框显示证书的详情。调用成功后，将显示证书的基本信息、有效期、颁发者、使用者等详细信息。使用Promise异步回调。 |
| [openCertificateManagerDialog](arkts-devicecertificate-opencertificatemanagerdialog-f.md#opencertificatemanagerdialog-1) | 打开证书管理对话框，显示相应的页面。调用成功后，用户可以在弹出的对话框中对证书进行查看、安装、卸载等操作。使用Promise异步回调。 |
| [openInstallCertificateDialog](arkts-devicecertificate-openinstallcertificatedialog-f.md#openinstallcertificatedialog-1) | 打开证书管理安装证书向导，显示相应的页面。证书安装成功后，返回证书的唯一标识符，应用可通过该标识符对证书进行使用。使用Promise异步回调。 |
| [openUkeyAuthDialog](arkts-devicecertificate-openukeyauthdialog-f.md#openukeyauthdialog-1) | 打开证书管理对话框的USB Key证书凭据PIN码认证页面。在弹出的页面中，用户可以输入PIN码授权USB Key证书凭据。调用成功后，USBKey证书凭据将被解锁，应用可使用该凭据进行签名、加密等操作。使用Promise异步回调。 |
| [openUninstallCertificateDialog](arkts-devicecertificate-openuninstallcertificatedialog-f.md#openuninstallcertificatedialog-1) | 打开证书管理卸载证书向导，显示相应的页面。使用Promise异步回调。 |
| [supportsCACertDialog](arkts-devicecertificate-supportscacertdialog-f.md#supportscacertdialog-1) | 判断设备是否支持[openCertificateDetailDialog]{@linkcertificateManagerDialog.openCertificateDetailDialog}，[openInstallCertificateDialog]{@linkcertificateManagerDialog.openInstallCertificateDialog}和[openUninstallCertificateDialog]{@linkcertificateManagerDialog.openUninstallCertificateDialog}接口打开管理CA证书的对话框。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AuthorizeRequest](arkts-devicecertificate-authorizerequest-i.md) | 证书凭据授权请求信息。 |
| [CertReference](arkts-devicecertificate-certreference-i.md) | 表示证书凭据的引用信息。 |
| [CertificateDialogProperty](arkts-devicecertificate-certificatedialogproperty-i.md) | 表示证书管理对话框的属性。 |
| [UkeyAuthRequest](arkts-devicecertificate-ukeyauthrequest-i.md) | USB Key PIN码认证请求。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CertificateDialogErrorCode](arkts-devicecertificate-certificatedialogerrorcode-e.md) | 表示调用证书管理对话框相关API的错误码。 |
| [CertificateDialogPageType](arkts-devicecertificate-certificatedialogpagetype-e.md) | 表示证书管理对话框的页面类型。 |
| [CertificateScope](arkts-devicecertificate-certificatescope-e.md) | 表示安装证书的使用范围。 |
| [CertificateType](arkts-devicecertificate-certificatetype-e.md) | 表示安装证书的类型。 |

