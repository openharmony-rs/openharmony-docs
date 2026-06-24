# @ohos.security.certManagerDialog

֤������Ի�����Ҫ�ṩ��֤�����������������û��ڴ򿪵�֤������Ի���ɶ�֤����в鿴�͹�������װ��ж�ء���Ȩ����

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [openAuthorizeDialog](arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md#openAuthorizeDialog-1) | ��֤������Ի����֤��ƾ����Ȩҳ�档�ڵ�����ҳ���У��û�����ΪӦ����Ȩʹ��֤��ƾ�ݡ����óɹ���Ӧ�ÿ�ͨ���ӿڷ��ص���Ȩ֤��ƾ��uri����ǩ������ǩ�Ͳ�ѯ���������ʹ��Promise�첽�ص���<br/> |
| [openAuthorizeDialog](arkts-devicecertificate-certificatemanagerdialog-openauthorizedialog-f.md#openAuthorizeDialog-2) | ��֤������Ի����֤��ƾ����Ȩҳ�档�ڵ�����ҳ���У��û�����ΪӦ����Ȩʹ��֤��ƾ�ݡ����óɹ���Ӧ�ÿ�ͨ���ӿڷ��ص���Ȩ֤��ƾ��uri����ǩ������ǩ�Ͳ�ѯ�������������Ȩ��֤�����Ͱ���Ӧ��֤��ƾ�ݡ��û�֤��ƾ�ݺ�USB<br/>Key֤��ƾ�ݡ�ʹ��Promise�첽�ص���<br/> |
| [openCertificateDetailDialog](arkts-devicecertificate-certificatemanagerdialog-opencertificatedetaildialog-f.md#openCertificateDetailDialog-1) | ��֤������Ի�����ʾ֤������顣���óɹ��󣬽���ʾ֤��Ļ�����Ϣ����Ч�ڡ��䷢�ߡ�ʹ���ߵ���ϸ��Ϣ��ʹ��Promise�첽�ص���<br/> |
| [openCertificateManagerDialog](arkts-devicecertificate-certificatemanagerdialog-opencertificatemanagerdialog-f.md#openCertificateManagerDialog-1) | ��֤������Ի�����ʾ��Ӧ��ҳ�档���óɹ����û������ڵ����ĶԻ����ж�֤����в鿴����װ��ж�صȲ�����ʹ��Promise�첽�ص���<br/> |
| [openInstallCertificateDialog](arkts-devicecertificate-certificatemanagerdialog-openinstallcertificatedialog-f.md#openInstallCertificateDialog-1) | ��֤�������װ֤���򵼣���ʾ��Ӧ��ҳ�档֤�鰲װ�ɹ��󣬷���֤���Ψһ��ʶ����Ӧ�ÿ�ͨ���ñ�ʶ����֤�����ʹ�á�ʹ��Promise�첽�ص���<br/> |
| [openUkeyAuthDialog](arkts-devicecertificate-certificatemanagerdialog-openukeyauthdialog-f.md#openUkeyAuthDialog-1) | ��֤������Ի����USB Key֤��ƾ��PIN����֤ҳ�档�ڵ�����ҳ���У��û���������PIN����ȨUSB Key֤��ƾ�ݡ����óɹ���USB<br/>Key֤��ƾ�ݽ���������Ӧ�ÿ�ʹ�ø�ƾ�ݽ���ǩ�������ܵȲ�����ʹ��Promise�첽�ص���<br/> |
| [openUninstallCertificateDialog](arkts-devicecertificate-certificatemanagerdialog-openuninstallcertificatedialog-f.md#openUninstallCertificateDialog-1) | ��֤�����ж��֤���򵼣���ʾ��Ӧ��ҳ�档ʹ��Promise�첽�ص���<br/> |
| [supportsCACertDialog](arkts-devicecertificate-certificatemanagerdialog-supportscacertdialog-f.md#supportsCACertDialog-1) | �ж��豸�Ƿ�֧��[openCertificateDetailDialog]{@link<br/>certificateManagerDialog.openCertificateDetailDialog}��[openInstallCertificateDialog]{@link<br/>certificateManagerDialog.openInstallCertificateDialog}��[openUninstallCertificateDialog]{@link<br/>certificateManagerDialog.openUninstallCertificateDialog}�ӿڴ򿪹���CA֤��ĶԻ���<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AuthorizeRequest](arkts-devicecertificate-certificatemanagerdialog-authorizerequest-i.md) | ֤��ƾ����Ȩ������Ϣ��<br/> |
| [CertReference](arkts-devicecertificate-certificatemanagerdialog-certreference-i.md) | ��ʾ֤��ƾ�ݵ�������Ϣ��<br/> |
| [CertificateDialogProperty](arkts-devicecertificate-certificatemanagerdialog-certificatedialogproperty-i.md) | ��ʾ֤������Ի�������ԡ�<br/> |
| [UkeyAuthRequest](arkts-devicecertificate-certificatemanagerdialog-ukeyauthrequest-i.md) | USB Key PIN����֤����<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CertificateDialogErrorCode](arkts-devicecertificate-certificatemanagerdialog-certificatedialogerrorcode-e.md) | ��ʾ����֤������Ի������API�Ĵ����롣<br/> |
| [CertificateDialogPageType](arkts-devicecertificate-certificatemanagerdialog-certificatedialogpagetype-e.md) | ��ʾ֤������Ի����ҳ�����͡�<br/> |
| [CertificateScope](arkts-devicecertificate-certificatemanagerdialog-certificatescope-e.md) | ��ʾ��װ֤���ʹ�÷�Χ��<br/> |
| [CertificateType](arkts-devicecertificate-certificatemanagerdialog-certificatetype-e.md) | ��ʾ��װ֤������͡�<br/> |

