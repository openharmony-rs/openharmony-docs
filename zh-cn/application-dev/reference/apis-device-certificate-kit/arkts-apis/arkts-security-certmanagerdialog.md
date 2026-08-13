# @ohos.security.certManagerDialog

证书管理对话框主要提供打开证书管理界面的能力，用户在打开的证书管理对话框可对证书进行查看和管理（安装，卸载、授权）。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace certificateManagerDialog--><!--Device-unnamed-declare namespace certificateManagerDialog-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [openAuthorizeDialog](arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md#openAuthorizeDialog) | 打开证书管理对话框的证书凭据授权页面。在弹出的页面中，用户可以为应用授权使用证书凭据。调用成功后，应用可通过接口返回的授权证书凭据uri进行签名、验签和查询详情操作。使用Promise异步回调。 |
| [openAuthorizeDialog](arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md#openAuthorizeDialog) | 打开证书管理对话框的证书凭据授权页面。在弹出的页面中，用户可以为应用授权使用证书凭据。调用成功后，应用可通过接口返回的授权证书凭据uri进行签名、验签和查询详情操作。可授权的证书类型包括应用证书凭据、用户证书凭据和USB Key证书凭据。使用Promise异步回调。 |
| [openCertificateDetailDialog](arkts-devicecertificate-certificatemanagerdialog-opencertificatedetaildialog-f.md#openCertificateDetailDialog) | 打开证书管理对话框显示证书的详情。调用成功后，将显示证书的基本信息、有效期、颁发者、使用者等详细信息。使用Promise异步回调。 |
| [openCertificateManagerDialog](arkts-devicecertificate-certificatemanagerdialog-opencertificatemanagerdialog-f.md#openCertificateManagerDialog) | 打开证书管理对话框，显示相应的页面。调用成功后，用户可以在弹出的对话框中对证书进行查看、安装、卸载等操作。使用Promise异步回调。 |
| [openInstallCertificateDialog](arkts-devicecertificate-certificatemanagerdialog-openinstallcertificatedialog-f.md#openInstallCertificateDialog) | 打开证书管理安装证书向导，显示相应的页面。证书安装成功后，返回证书的唯一标识符，应用可通过该标识符对证书进行使用。使用Promise异步回调。 |
| [openUkeyAuthDialog](arkts-devicecertificate-certificatemanagerdialog-openukeyauthdialog-f.md#openUkeyAuthDialog) | 打开证书管理对话框的USB Key证书凭据PIN码认证页面。在弹出的页面中，用户可以输入PIN码授权USB Key证书凭据。调用成功后，USB Key证书凭据将被解锁，应用可使用该凭据进行签名、加密等操作。使用Promise异步回调。 |
| [openUninstallCertificateDialog](arkts-devicecertificate-certificatemanagerdialog-openuninstallcertificatedialog-f.md#openUninstallCertificateDialog) | 打开证书管理卸载证书向导，显示相应的页面。使用Promise异步回调。 |
| [supportsCACertDialog](arkts-devicecertificate-certificatemanagerdialog-supportscacertdialog-f.md#supportsCACertDialog) | 判断设备是否支持[openCertificateDetailDialog](arkts-devicecertificate-certificatemanagerdialog-opencertificatedetaildialog-f.md#openCertificateDetailDialog)，[openInstallCertificateDialog](arkts-devicecertificate-certificatemanagerdialog-openinstallcertificatedialog-f.md#openInstallCertificateDialog)和[openUninstallCertificateDialog](arkts-devicecertificate-certificatemanagerdialog-openuninstallcertificatedialog-f.md#openUninstallCertificateDialog)接口打开管理CA证书的对话框。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AuthorizeRequest](arkts-devicecertificate-certificatemanagerdialog-authorizerequest-i.md) | 证书凭据授权请求信息。 |
| [CertReference](arkts-devicecertificate-certificatemanagerdialog-certreference-i.md) | 表示证书凭据的引用信息。 |
| [CertificateDialogProperty](arkts-devicecertificate-certificatemanagerdialog-certificatedialogproperty-i.md) | 表示证书管理对话框的属性。 |
| [UkeyAuthRequest](arkts-devicecertificate-certificatemanagerdialog-ukeyauthrequest-i.md) | USB Key PIN码认证请求。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CertificateDialogErrorCode](arkts-devicecertificate-certificatemanagerdialog-certificatedialogerrorcode-e.md) | 表示调用证书管理对话框相关API的错误码。 |
| [CertificateDialogPageType](arkts-devicecertificate-certificatemanagerdialog-certificatedialogpagetype-e.md) | 表示证书管理对话框的页面类型。 |
| [CertificateScope](arkts-devicecertificate-certificatemanagerdialog-certificatescope-e.md) | 表示安装证书的使用范围。 |
| [CertificateType](arkts-devicecertificate-certificatemanagerdialog-certificatetype-e.md) | 表示安装证书的类型。 |

