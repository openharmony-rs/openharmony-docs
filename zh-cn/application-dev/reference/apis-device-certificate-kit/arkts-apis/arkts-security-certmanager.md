# @ohos.security.certManager

证书管理主要提供系统级的证书管理能力，实现证书全生命周期（安装，存储，使用，销毁）的管理和安全使用。

可用于校验应用服务器的HTTPS证书链、通过双向HTTPS登录网站或应用服务器。

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [abort](arkts-devicecertificate-abort-f.md#abort-1) | 中止签名、验签的操作。与finish方法互斥，一个签名验签流程只能选择调用其中一个方法。使用Callback异步回调。 |
| [abort](arkts-devicecertificate-abort-f.md#abort-2) | 中止签名、验签的操作。与finish方法互斥，一个签名验签流程只能选择调用其中一个方法。使用Promise异步回调。 |
| [finish](arkts-devicecertificate-finish-f.md#finish-1) | 完成签名的操作，是签名流程的最后一步，需要先调用init和update接口。使用Callback异步回调。 |
| [finish](arkts-devicecertificate-finish-f.md#finish-2) | 完成验签的操作，是验签流程的最后一步，需要先调用init和update接口。使用Callback异步回调。 |
| [finish](arkts-devicecertificate-finish-f.md#finish-3) | 完成签名、验签的操作。使用Promise异步回调。 |
| [getAllUserTrustedCertificates](arkts-devicecertificate-getallusertrustedcertificates-f.md#getallusertrustedcertificates-1) | 表示获取当前用户和设备公共位置的所有用户根CA证书列表。使用Promise异步回调。 |
| [getAllUserTrustedCertificates](arkts-devicecertificate-getallusertrustedcertificates-f.md#getallusertrustedcertificates-2) | 表示根据证书的位置获取用户根CA证书列表。使用Promise异步回调。 |
| [getCertificateStorePath](arkts-devicecertificate-getcertificatestorepath-f.md#getcertificatestorepath-1) | 表示获取证书的存储路径。 |
| [getPrivateCertificate](arkts-devicecertificate-getprivatecertificate-f.md#getprivatecertificate-1) | 获取私有凭据的详细信息，使用Callback异步回调。 |
| [getPrivateCertificate](arkts-devicecertificate-getprivatecertificate-f.md#getprivatecertificate-2) | 获取私有凭据详情。使用Promise异步回调。 |
| [getPrivateCertificates](arkts-devicecertificate-getprivatecertificates-f.md#getprivatecertificates-1) | 表示获取应用安装的凭据列表。使用Promise异步回调。 |
| [getPublicCertificate](arkts-devicecertificate-getpubliccertificate-f.md#getpubliccertificate-1) | 表示获取用户公共凭据的详细信息。使用Promise异步回调。 |
| [getUkeyCertificate](arkts-devicecertificate-getukeycertificate-f.md#getukeycertificate-1) | 获取USB Key证书凭据详细信息。使用Promise异步回调。 |
| [getUkeyCertificateList](arkts-devicecertificate-getukeycertificatelist-f.md#getukeycertificatelist-1) | 获取USB Key证书凭据列表。使用Promise异步回调。 |
| [getUserTrustedCertificate](arkts-devicecertificate-getusertrustedcertificate-f.md#getusertrustedcertificate-1) | 表示获取用户根CA证书的详细信息。使用Promise异步回调。 |
| [importUkeyCertificate](arkts-devicecertificate-importukeycertificate-f.md#importukeycertificate-1) | 导入证书到USB Key |
| [init](arkts-devicecertificate-init-f.md#init-1) | 使用凭据进行签名、验签的初始化操作，是签名验签流程的第一步，后续需依次调用update和finish接口完成操作。使用Callback异步回调。 |
| [init](arkts-devicecertificate-init-f.md#init-2) | 使用凭据进行签名、验签的初始化操作。使用Promise异步回调。 |
| [installPrivateCertificate](arkts-devicecertificate-installprivatecertificate-f.md#installprivatecertificate-1) | 安装私有凭据。使用Callback异步回调。 |
| [installPrivateCertificate](arkts-devicecertificate-installprivatecertificate-f.md#installprivatecertificate-2) | 安装私有凭据。使用Promise异步回调。 |
| [installPrivateCertificate](arkts-devicecertificate-installprivatecertificate-f.md#installprivatecertificate-3) | 表示安装私有凭据并指定凭据的存储级别。使用Promise异步回调。 |
| [installUserTrustedCertificate](arkts-devicecertificate-installusertrustedcertificate-f.md#installusertrustedcertificate-1) | 安装用户CA证书。使用Promise异步回调。 |
| [installUserTrustedCertificateSync](arkts-devicecertificate-installusertrustedcertificatesync-f.md#installusertrustedcertificatesync-1) | 安装用户CA证书。 |
| [isAuthorizedApp](arkts-devicecertificate-isauthorizedapp-f.md#isauthorizedapp-1) | 表示当前应用是否由指定的用户凭据授权。使用Promise异步回调。 |
| [uninstallPrivateCertificate](arkts-devicecertificate-uninstallprivatecertificate-f.md#uninstallprivatecertificate-1) | 卸载指定的私有凭据，使用Callback异步回调。 |
| [uninstallPrivateCertificate](arkts-devicecertificate-uninstallprivatecertificate-f.md#uninstallprivatecertificate-2) | 表示卸载指定的私有凭据。使用Promise异步回调。 |
| [uninstallUserTrustedCertificateSync](arkts-devicecertificate-uninstallusertrustedcertificatesync-f.md#uninstallusertrustedcertificatesync-1) | 卸载用户CA证书。 |
| [update](arkts-devicecertificate-update-f.md#update-1) | 签名、验签的数据更新操作，需要在init操作之后调用，用于传入待签名、验签的数据。使用Callback异步回调。 |
| [update](arkts-devicecertificate-update-f.md#update-2) | 签名、验签的数据更新操作。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getAllAppPrivateCertificates](arkts-devicecertificate-getallappprivatecertificates-f-sys.md#getallappprivatecertificates-1) | 表示获取所有私有凭据列表，使用Callback异步回调。 |
| [getAllAppPrivateCertificates](arkts-devicecertificate-getallappprivatecertificates-f-sys.md#getallappprivatecertificates-2) | 表示获取所有私有凭据列表。使用Promise异步回调。 |
| [getAllAppPrivateCertificatesByUid](arkts-devicecertificate-getallappprivatecertificatesbyuid-f-sys.md#getallappprivatecertificatesbyuid-1) | 获取指定应用的所有私有凭据，仅证书管理应用调用。使用Promise异步回调。 |
| [getAllPublicCertificates](arkts-devicecertificate-getallpubliccertificates-f-sys.md#getallpubliccertificates-1) | 获取所有用户的公共凭据，仅证书管理应用调用。使用Promise异步回调。 |
| [getAllSystemAppCertificates](arkts-devicecertificate-getallsystemappcertificates-f-sys.md#getallsystemappcertificates-1) | 表示获取所有系统凭据列表。使用Promise异步回调。 |
| [getAuthorizedAppList](arkts-devicecertificate-getauthorizedapplist-f-sys.md#getauthorizedapplist-1) | 获取用户公共凭据的授权应用列表，仅证书管理应用调用。使用Promise异步回调。 |
| [getSystemAppCertificate](arkts-devicecertificate-getsystemappcertificate-f-sys.md#getsystemappcertificate-1) | 获取系统应用的凭据详情，仅证书管理应用调用。使用Promise异步回调。 |
| [getSystemTrustedCertificate](arkts-devicecertificate-getsystemtrustedcertificate-f-sys.md#getsystemtrustedcertificate-1) | 获取系统信任的CA证书详情，仅证书管理应用调用。使用Promise异步回调。 |
| [getSystemTrustedCertificateList](arkts-devicecertificate-getsystemtrustedcertificatelist-f-sys.md#getsystemtrustedcertificatelist-1) | 获取系统信任的CA证书列表，仅证书管理应用调用。使用Promise异步回调。 |
| [grantPublicCertificate](arkts-devicecertificate-grantpubliccertificate-f-sys.md#grantpubliccertificate-1) | 授予应用使用用户公共凭据的权限，仅证书管理应用调用。使用Promise异步回调。 |
| [installPublicCertificate](arkts-devicecertificate-installpubliccertificate-f-sys.md#installpubliccertificate-1) | 安装用户的公共凭据，仅证书管理应用调用。使用Promise异步回调。 |
| [installSystemAppCertificate](arkts-devicecertificate-installsystemappcertificate-f-sys.md#installsystemappcertificate-1) | 安装系统应用凭据，仅证书管理应用调用。使用Promise异步回调。 |
| [removeGrantedPublicCertificate](arkts-devicecertificate-removegrantedpubliccertificate-f-sys.md#removegrantedpubliccertificate-1) | 移除应用使用用户公共凭据的权限，仅证书管理应用调用。使用Promise异步回调。 |
| [setCertificateStatus](arkts-devicecertificate-setcertificatestatus-f-sys.md#setcertificatestatus-1) | 设置CA证书的状态，当前仅支持设置用户CA证书状态，仅证书管理应用调用。使用Promise异步回调。 |
| [uninstallAllAppCertificate](arkts-devicecertificate-uninstallallappcertificate-f-sys.md#uninstallallappcertificate-1) | 卸载所有系统应用凭据和用户公共凭据，仅证书管理应用调用。使用Promise异步回调。 |
| [uninstallAllUserTrustedCertificate](arkts-devicecertificate-uninstallallusertrustedcertificate-f-sys.md#uninstallallusertrustedcertificate-1) | 卸载所有用户信任的CA证书，仅证书管理应用调用。使用Promise异步回调。 |
| [uninstallPublicCertificate](arkts-devicecertificate-uninstallpubliccertificate-f-sys.md#uninstallpubliccertificate-1) | 卸载用的户公共凭据，仅证书管理应用调用。使用Promise异步回调。 |
| [uninstallSystemAppCertificate](arkts-devicecertificate-uninstallsystemappcertificate-f-sys.md#uninstallsystemappcertificate-1) | 卸载系统应用的凭据，仅证书管理应用调用。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [CMHandle](arkts-devicecertificate-cmhandle-i.md) | 表示签名、验签的初始化操作句柄。 |
| [CMResult](arkts-devicecertificate-cmresult-i.md) | 表示接口的返回结果。 |
| [CMSignatureSpec](arkts-devicecertificate-cmsignaturespec-i.md) | 表示签名、验签操作使用的参数集合，包括密钥使用目的、填充方式和摘要算法。 |
| [CertAbstract](arkts-devicecertificate-certabstract-i.md) | 表示证书简要信息。 |
| [CertBlob](arkts-devicecertificate-certblob-i.md) | 表示证书文件数据。 |
| [CertInfo](arkts-devicecertificate-certinfo-i.md) | 表示证书详细信息。 |
| [CertStoreProperty](arkts-devicecertificate-certstoreproperty-i.md) | 表示获取证书存储位置的参数集合，包括证书的类型及证书的位置。 |
| [Credential](arkts-devicecertificate-credential-i.md) | 表示凭据详细信息。 |
| [CredentialAbstract](arkts-devicecertificate-credentialabstract-i.md) | 表示凭据的简要信息。 |
| [UkeyInfo](arkts-devicecertificate-ukeyinfo-i.md) | 提供USB Key证书凭据属性信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AuthStorageLevel](arkts-devicecertificate-authstoragelevel-e.md) | 表示凭据的存储级别。 |
| [CMErrorCode](arkts-devicecertificate-cmerrorcode-e.md) | 表示调用证书管理相关API的错误码。 |
| [CertAlgorithm](arkts-devicecertificate-certalgorithm-e.md) | 表示证书的算法类型。 |
| [CertFileFormat](arkts-devicecertificate-certfileformat-e.md) | 表示证书文件格式。 |
| [CertScope](arkts-devicecertificate-certscope-e.md) | 表示证书的位置。 |
| [CertType](arkts-devicecertificate-certtype-e.md) | 表示证书类型。 |
| [CertificatePurpose](arkts-devicecertificate-certificatepurpose-e.md) | 表示凭据用途的枚举。 |
| [CmKeyDigest](arkts-devicecertificate-cmkeydigest-e.md) | 表示签名、验签使用的摘要算法的枚举。 |
| [CmKeyPadding](arkts-devicecertificate-cmkeypadding-e.md) | 表示签名、验签使用的填充方式的枚举。 |
| [CmKeyPurpose](arkts-devicecertificate-cmkeypurpose-e.md) | 表示密钥使用目的的枚举，用于签名、验签。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CMErrorCode](arkts-devicecertificate-cmerrorcode-e-sys.md) | 表示调用证书管理相关API的错误码。 |
<!--DelEnd-->

