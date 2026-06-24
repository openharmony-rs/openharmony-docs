# @ohos.security.certManager

֤�������Ҫ�ṩϵͳ����֤�����������ʵ��֤��ȫ�������ڣ���װ���洢��ʹ�ã����٣��Ĺ����Ͱ�ȫʹ�á�

������У��Ӧ�÷�������HTTPS֤������ͨ��˫��HTTPS��¼��վ��Ӧ�÷�������

**起始版本：** 11

**系统能力：** SystemCapability.Security.CertificateManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [abort](arkts-devicecertificate-certificatemanager-abort-f.md#abort-1) | ��ʾ��ֹǩ������ǩ�Ĳ�����ʹ��Callback�첽�ص���<br/> |
| [abort](arkts-devicecertificate-certificatemanager-abort-f.md#abort-2) | ��ʾ��ֹǩ������ǩ�Ĳ�����ʹ��Promise�첽�ص���<br/> |
| [finish](arkts-devicecertificate-certificatemanager-finish-f.md#finish-1) | ���ǩ���Ĳ�������ǩ�����̵����һ������Ҫ�ȵ���init��update�ӿڡ�ʹ��Callback�첽�ص���<br/> |
| [finish](arkts-devicecertificate-certificatemanager-finish-f.md#finish-2) | �����ǩ�Ĳ�����ʹ��Callback�첽�ص���<br/> |
| [finish](arkts-devicecertificate-certificatemanager-finish-f.md#finish-3) | ���ǩ������ǩ�Ĳ�����ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getAllAppPrivateCertificates](arkts-devicecertificate-certificatemanager-getallappprivatecertificates-f-sys.md#getAllAppPrivateCertificates-1) | ��ʾ��ȡ����˽��ƾ���б���ʹ��Callback�첽�ص���<br/> |
| <!--DelRow-->[getAllAppPrivateCertificates](arkts-devicecertificate-certificatemanager-getallappprivatecertificates-f-sys.md#getAllAppPrivateCertificates-2) | ��ʾ��ȡ����˽��ƾ���б���ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getAllAppPrivateCertificatesByUid](arkts-devicecertificate-certificatemanager-getallappprivatecertificatesbyuid-f-sys.md#getAllAppPrivateCertificatesByUid-1) | ��ȡָ��Ӧ�õ�����˽��ƾ�ݣ���֤�����Ӧ�õ��á�ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getAllPublicCertificates](arkts-devicecertificate-certificatemanager-getallpubliccertificates-f-sys.md#getAllPublicCertificates-1) | ��ȡ�����û��Ĺ���ƾ�ݣ���֤�����Ӧ�õ��á�ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getAllSystemAppCertificates](arkts-devicecertificate-certificatemanager-getallsystemappcertificates-f-sys.md#getAllSystemAppCertificates-1) | ��ʾ��ȡ����ϵͳƾ���б���ʹ��Promise�첽�ص���<br/> |
| [getAllUserTrustedCertificates](arkts-devicecertificate-certificatemanager-getallusertrustedcertificates-f.md#getAllUserTrustedCertificates-1) | ��ʾ��ȡ��ǰ�û����豸����λ�õ������û���CA֤���б���ʹ��Promise�첽�ص���<br/> |
| [getAllUserTrustedCertificates](arkts-devicecertificate-certificatemanager-getallusertrustedcertificates-f.md#getAllUserTrustedCertificates-2) | ��ʾ����֤���λ�û�ȡ�û���CA֤���б���ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getAuthorizedAppList](arkts-devicecertificate-certificatemanager-getauthorizedapplist-f-sys.md#getAuthorizedAppList-1) | ��ȡ�û�����ƾ�ݵ���ȨӦ���б�����֤�����Ӧ�õ��á�ʹ��Promise�첽�ص���<br/> |
| [getCertificateStorePath](arkts-devicecertificate-certificatemanager-getcertificatestorepath-f.md#getCertificateStorePath-1) | ��ʾ��ȡ֤��Ĵ洢·����<br/> |
| [getPrivateCertificate](arkts-devicecertificate-certificatemanager-getprivatecertificate-f.md#getPrivateCertificate-1) | ��ȡ˽��ƾ�ݵ���ϸ��Ϣ��ʹ��Callback�첽�ص���<br/> |
| [getPrivateCertificate](arkts-devicecertificate-certificatemanager-getprivatecertificate-f.md#getPrivateCertificate-2) | ��ȡ˽��ƾ�����顣ʹ��Promise�첽�ص���<br/> |
| [getPrivateCertificates](arkts-devicecertificate-certificatemanager-getprivatecertificates-f.md#getPrivateCertificates-1) | ��ʾ��ȡӦ�ð�װ��ƾ���б���ʹ��Promise�첽�ص���<br/> |
| [getPublicCertificate](arkts-devicecertificate-certificatemanager-getpubliccertificate-f.md#getPublicCertificate-1) | ��ʾ��ȡ�û�����ƾ�ݵ���ϸ��Ϣ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getSystemAppCertificate](arkts-devicecertificate-certificatemanager-getsystemappcertificate-f-sys.md#getSystemAppCertificate-1) | ��ȡϵͳӦ�õ�ƾ�����飬��֤�����Ӧ�õ��á�ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getSystemTrustedCertificate](arkts-devicecertificate-certificatemanager-getsystemtrustedcertificate-f-sys.md#getSystemTrustedCertificate-1) | ��ȡϵͳ���ε�CA֤�����飬��֤�����Ӧ�õ��á�ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getSystemTrustedCertificateList](arkts-devicecertificate-certificatemanager-getsystemtrustedcertificatelist-f-sys.md#getSystemTrustedCertificateList-1) | ��ȡϵͳ���ε�CA֤���б�����֤�����Ӧ�õ��á�ʹ��Promise�첽�ص���<br/> |
| [getUkeyCertificate](arkts-devicecertificate-certificatemanager-getukeycertificate-f.md#getUkeyCertificate-1) | ��ȡUSB Key֤��ƾ����ϸ��Ϣ��ʹ��Promise�첽�ص���<br/> |
| [getUkeyCertificateList](arkts-devicecertificate-certificatemanager-getukeycertificatelist-f.md#getUkeyCertificateList-1) | ��ȡUSB Key֤��ƾ���б���ʹ��Promise�첽�ص���<br/> |
| [getUserTrustedCertificate](arkts-devicecertificate-certificatemanager-getusertrustedcertificate-f.md#getUserTrustedCertificate-1) | ��ʾ��ȡ�û���CA֤�����ϸ��Ϣ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[grantPublicCertificate](arkts-devicecertificate-certificatemanager-grantpubliccertificate-f-sys.md#grantPublicCertificate-1) | ����Ӧ��ʹ���û�����ƾ�ݵ�Ȩ�ޣ���֤�����Ӧ�õ��á�ʹ��Promise�첽�ص���<br/> |
| [importUkeyCertificate](arkts-devicecertificate-certificatemanager-importukeycertificate-f.md#importUkeyCertificate-1) | ����֤�鵽USB Key<br/> |
| [init](arkts-devicecertificate-certificatemanager-init-f.md#init-1) | ʹ��ƾ�ݽ���ǩ������ǩ�ĳ�ʼ����������ǩ����ǩ���̵ĵ�һ�������������ε���update��finish�ӿ���ɲ�����ʹ��Callback�첽�ص���<br/> |
| [init](arkts-devicecertificate-certificatemanager-init-f.md#init-2) | ʹ��ƾ�ݽ���ǩ������ǩ�ĳ�ʼ��������ʹ��Promise�첽�ص���<br/> |
| [installPrivateCertificate](arkts-devicecertificate-certificatemanager-installprivatecertificate-f.md#installPrivateCertificate-1) | ��װ˽��ƾ�ݡ�ʹ��Callback�첽�ص���<br/> |
| [installPrivateCertificate](arkts-devicecertificate-certificatemanager-installprivatecertificate-f.md#installPrivateCertificate-2) | ��װ˽��ƾ�ݡ�ʹ��Promise�첽�ص���<br/> |
| [installPrivateCertificate](arkts-devicecertificate-certificatemanager-installprivatecertificate-f.md#installPrivateCertificate-3) | ��ʾ��װ˽��ƾ�ݲ�ָ��ƾ�ݵĴ洢����ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[installPublicCertificate](arkts-devicecertificate-certificatemanager-installpubliccertificate-f-sys.md#installPublicCertificate-1) | ��װ�û��Ĺ���ƾ�ݣ���֤�����Ӧ�õ��á�ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[installSystemAppCertificate](arkts-devicecertificate-certificatemanager-installsystemappcertificate-f-sys.md#installSystemAppCertificate-1) | ��װϵͳӦ��ƾ�ݣ���֤�����Ӧ�õ��á�ʹ��Promise�첽�ص���<br/> |
| [installUserTrustedCertificate](arkts-devicecertificate-certificatemanager-installusertrustedcertificate-f.md#installUserTrustedCertificate-1) | ��װ�û�CA֤�顣�����certificate.certFormatΪP7Bʱ�������P7B֤���ļ������ֻ�ܰ���20��֤�顣ʹ��Promise�첽�ص���<br/> |
| [installUserTrustedCertificateSync](arkts-devicecertificate-certificatemanager-installusertrustedcertificatesync-f.md#installUserTrustedCertificateSync-1) | ��װ�û�CA֤�顣<br/> |
| [isAuthorizedApp](arkts-devicecertificate-certificatemanager-isauthorizedapp-f.md#isAuthorizedApp-1) | ��ʾ��ǰӦ���Ƿ���ָ�����û�ƾ����Ȩ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[removeGrantedPublicCertificate](arkts-devicecertificate-certificatemanager-removegrantedpubliccertificate-f-sys.md#removeGrantedPublicCertificate-1) | �Ƴ�Ӧ��ʹ���û�����ƾ�ݵ�Ȩ�ޣ���֤�����Ӧ�õ��á�ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[setCertificateStatus](arkts-devicecertificate-certificatemanager-setcertificatestatus-f-sys.md#setCertificateStatus-1) | ����CA֤���״̬����ǰ��֧�������û�CA֤��״̬����֤�����Ӧ�õ��á�ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[uninstallAllAppCertificate](arkts-devicecertificate-certificatemanager-uninstallallappcertificate-f-sys.md#uninstallAllAppCertificate-1) | ж������ϵͳӦ��ƾ�ݺ��û�����ƾ�ݣ���֤�����Ӧ�õ��á�ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[uninstallAllUserTrustedCertificate](arkts-devicecertificate-certificatemanager-uninstallallusertrustedcertificate-f-sys.md#uninstallAllUserTrustedCertificate-1) | ж�������û����ε�CA֤�飬��֤�����Ӧ�õ��á�ʹ��Promise�첽�ص���<br/> |
| [uninstallPrivateCertificate](arkts-devicecertificate-certificatemanager-uninstallprivatecertificate-f.md#uninstallPrivateCertificate-1) | ж��ָ����˽��ƾ�ݣ�ʹ��Callback�첽�ص���<br/> |
| [uninstallPrivateCertificate](arkts-devicecertificate-certificatemanager-uninstallprivatecertificate-f.md#uninstallPrivateCertificate-2) | ��ʾж��ָ����˽��ƾ�ݡ�ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[uninstallPublicCertificate](arkts-devicecertificate-certificatemanager-uninstallpubliccertificate-f-sys.md#uninstallPublicCertificate-1) | ж���õĻ�����ƾ�ݣ���֤�����Ӧ�õ��á�ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[uninstallSystemAppCertificate](arkts-devicecertificate-certificatemanager-uninstallsystemappcertificate-f-sys.md#uninstallSystemAppCertificate-1) | ж��ϵͳӦ�õ�ƾ�ݣ���֤�����Ӧ�õ��á�ʹ��Promise�첽�ص���<br/> |
| [uninstallUserTrustedCertificateSync](arkts-devicecertificate-certificatemanager-uninstallusertrustedcertificatesync-f.md#uninstallUserTrustedCertificateSync-1) | ж���û�CA֤�顣<br/> |
| [update](arkts-devicecertificate-certificatemanager-update-f.md#update-1) | ǩ������ǩ�����ݸ��²�������Ҫ��init����֮����ã����ڴ����ǩ������ǩ�����ݡ�ʹ��Callback�첽�ص���<br/> |
| [update](arkts-devicecertificate-certificatemanager-update-f.md#update-2) | ǩ������ǩ�����ݸ��²�����ʹ��Promise�첽�ص���<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CMHandle](arkts-devicecertificate-certificatemanager-cmhandle-i.md) | ��ʾǩ������ǩ�ĳ�ʼ�����������<br/> |
| [CMResult](arkts-devicecertificate-certificatemanager-cmresult-i.md) | ��ʾ�ӿڵķ��ؽ����<br/> |
| [CMSignatureSpec](arkts-devicecertificate-certificatemanager-cmsignaturespec-i.md) | ��ʾǩ������ǩ����ʹ�õĲ������ϣ�������Կʹ��Ŀ�ġ���䷽ʽ��ժҪ�㷨��<br/> |
| [CertAbstract](arkts-devicecertificate-certificatemanager-certabstract-i.md) | ��ʾ֤���Ҫ��Ϣ��<br/> |
| [CertBlob](arkts-devicecertificate-certificatemanager-certblob-i.md) | ��ʾ֤���ļ����ݡ�<br/> |
| [CertInfo](arkts-devicecertificate-certificatemanager-certinfo-i.md) | ��ʾ֤����ϸ��Ϣ��<br/> |
| [CertStoreProperty](arkts-devicecertificate-certificatemanager-certstoreproperty-i.md) | ��ʾ��ȡ֤��洢λ�õĲ������ϣ�����֤������ͼ�֤���λ�á�<br/> |
| [Credential](arkts-devicecertificate-certificatemanager-credential-i.md) | ��ʾƾ����ϸ��Ϣ��<br/> |
| [CredentialAbstract](arkts-devicecertificate-certificatemanager-credentialabstract-i.md) | ��ʾƾ�ݵļ�Ҫ��Ϣ��<br/> |
| [UkeyInfo](arkts-devicecertificate-certificatemanager-ukeyinfo-i.md) | �ṩUSB Key֤��ƾ��������Ϣ��<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AuthStorageLevel](arkts-devicecertificate-certificatemanager-authstoragelevel-e.md) | ��ʾƾ�ݵĴ洢����<br/> |
| [CMErrorCode](arkts-devicecertificate-certificatemanager-cmerrorcode-e.md) | ��ʾ����֤��������API�Ĵ����롣<br/> |
| <!--DelRow-->[CMErrorCode](arkts-devicecertificate-certificatemanager-cmerrorcode-e-sys.md) | ��ʾ����֤��������API�Ĵ����롣<br/> |
| [CertAlgorithm](arkts-devicecertificate-certificatemanager-certalgorithm-e.md) | ��ʾ֤����㷨���͡�<br/> |
| [CertFileFormat](arkts-devicecertificate-certificatemanager-certfileformat-e.md) | ��ʾ֤���ļ���ʽ��<br/> |
| [CertScope](arkts-devicecertificate-certificatemanager-certscope-e.md) | ��ʾ֤���λ�á�<br/> |
| [CertType](arkts-devicecertificate-certificatemanager-certtype-e.md) | ��ʾ֤�����͡�<br/> |
| [CertificatePurpose](arkts-devicecertificate-certificatemanager-certificatepurpose-e.md) | ��ʾƾ����;��ö�١�<br/> |
| [CmKeyDigest](arkts-devicecertificate-certificatemanager-cmkeydigest-e.md) | ��ʾǩ������ǩʹ�õ�ժҪ�㷨��ö�١�<br/> |
| [CmKeyPadding](arkts-devicecertificate-certificatemanager-cmkeypadding-e.md) | ��ʾǩ������ǩʹ�õ���䷽ʽ��ö�١�<br/> |
| [CmKeyPurpose](arkts-devicecertificate-certificatemanager-cmkeypurpose-e.md) | ��ʾ��Կʹ��Ŀ�ĵ�ö�٣�����ǩ������ǩ��<br/> |

