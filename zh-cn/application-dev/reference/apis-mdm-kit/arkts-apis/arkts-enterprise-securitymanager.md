# @ohos.enterprise.securityManager

��ģ���ṩ�豸��ȫ������������������ѯ��ȫ����״̬����ѯ�ļ�����״̬�ȡ�

> **˵����**
>
> ��ģ��ӿڽ�����Stageģ����ʹ�á�
>
> ��ģ��ӿڽ����豸����Ӧ�ÿ��ţ��ҵ��ýӿ�ǰ�輤���豸����Ӧ�ã�������ο�[MDM Kit����ָ��](../../../../mdm/mdm-kit-guide.md)��

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addAllowedPermissionBundle](arkts-mdm-securitymanager-addallowedpermissionbundle-f.md#addAllowedPermissionBundle-1) |  ��������ʹ���ѽ���ָ��Ȩ�޵�Ӧ�õ�Ȩ��ʹ������������Ȩ��ʹ�����������е�Ӧ�ÿ��Բ���[setDisallowedPermission](arkts-mdm-securitymanager-setdisallowedpermission-f.md#setDisallowedPermission-1)�Ĳ������ơ�<br/> |
| [addUserExtCredential](arkts-mdm-securitymanager-adduserextcredential-f.md#addUserExtCredential-1) | ������չ�û���֤ƾ��<br/> |
| [cancelScreenWatermarkImage](arkts-mdm-securitymanager-cancelscreenwatermarkimage-f.md#cancelScreenWatermarkImage-1) | ȡ����Ļˮӡ<br/> |
| [cancelWatermarkImage](arkts-mdm-securitymanager-cancelwatermarkimage-f.md#cancelWatermarkImage-1) | ȡ��ָ���û���ˮӡ���ԡ�<br/> |
| [closeSession](arkts-mdm-securitymanager-closesession-f.md#closeSession-1) | �ر�ָ���û���ƾ�ݱ���Ự<br/> |
| [getAllowedPermissionBundles](arkts-mdm-securitymanager-getallowedpermissionbundles-f.md#getAllowedPermissionBundles-1) | ��ȡȨ��ʹ������������Ӧ���б���<br/> |
| [getAppClipboardPolicy](arkts-mdm-securitymanager-getappclipboardpolicy-f.md#getAppClipboardPolicy-1) | ��ȡ�豸��������ԡ�<br/> |
| [getAppClipboardPolicy](arkts-mdm-securitymanager-getappclipboardpolicy-f.md#getAppClipboardPolicy-2) | ��ȡָ���û���ָ��Ӧ�õ��豸��������ԡ�<br/> |
| <!--DelRow-->[getDeviceEncryptionStatus](arkts-mdm-securitymanager-getdeviceencryptionstatus-f-sys.md#getDeviceEncryptionStatus-1) | ��ѯ�豸�ļ�ϵͳ����״̬��<br/> |
| [getDeviceSecurityLevelPolicy](arkts-mdm-securitymanager-getdevicesecuritylevelpolicy-f.md#getDeviceSecurityLevelPolicy-1) | ��ѯDSL�л�����<br/> |
| [getDisallowedPermissions](arkts-mdm-securitymanager-getdisallowedpermissions-f.md#getDisallowedPermissions-1) | ��ȡָ���û��½��õ�Ȩ���б���<br/> |
| [getExternalSourceExtensionsPolicy](arkts-mdm-securitymanager-getexternalsourceextensionspolicy-f.md#getExternalSourceExtensionsPolicy-1) | ��ȡ�ⲿ��Դ��չ����Ĺܿز��ԡ�<br/> |
| [getPasswordPolicy](arkts-mdm-securitymanager-getpasswordpolicy-f.md#getPasswordPolicy-1) | ��ȡ�豸����������ԡ�<br/> |
| <!--DelRow-->[getPasswordPolicy](arkts-mdm-securitymanager-getpasswordpolicy-f-sys.md#getPasswordPolicy-2) | ��ȡ�豸����������ԡ�<br/> |
| [getPermissionManagedState](arkts-mdm-securitymanager-getpermissionmanagedstate-f.md#getPermissionManagedState-1) | ��ȡָ��Ӧ�õ�ָ��[user_grantȨ��](permissions:Permissions)�Ĺ������ԡ�<br/> |
| <!--DelRow-->[getSecurityPatchTag](arkts-mdm-securitymanager-getsecuritypatchtag-f-sys.md#getSecurityPatchTag-1) | ��ѯ�豸��ȫ����Tag��<br/> |
| [getSecurityStatus](arkts-mdm-securitymanager-getsecuritystatus-f.md#getSecurityStatus-1) | ��ȡ��ǰ�豸��ȫ������Ϣ��<br/> |
| [getUnlockPolicy](arkts-mdm-securitymanager-getunlockpolicy-f.md#getUnlockPolicy-1) | ��ѯ��������<br/> |
| [getUserCertificates](arkts-mdm-securitymanager-getusercertificates-f.md#getUserCertificates-1) | ��ȡָ��ϵͳ�˻��µ��û�֤����Ϣ��<br/> |
| [getUserExtCredential](arkts-mdm-securitymanager-getuserextcredential-f.md#getUserExtCredential-1) | ��ѯָ���û���װ����չ�û�ƾ��<br/> |
| [getWatermarkImageApps](arkts-mdm-securitymanager-getwatermarkimageapps-f.md#getWatermarkImageApps-1) | ��ѯ������ˮӡ��Ӧ���б�<br/> |
| [installEnterpriseReSignatureCertificate](arkts-mdm-securitymanager-installenterpriseresignaturecertificate-f.md#installEnterpriseReSignatureCertificate-1) | ��װ��ҵӦ����ǩ��֤�顣<br/><br/>ͬһ�û��������·�10����֤ͬ�顣֤�������Ϊ֤���Ψһ��ʶ����֧���ظ��·���ͬ������֤�顣�������ͬһ������֤�飬���ȵ���<br/>[uninstallEnterpriseReSignatureCertificate](arkts-mdm-securitymanager-uninstallenterpriseresignaturecertificate-f.md#uninstallEnterpriseReSignatureCertificate-1)����ж�ء�<br/><br/>��MDMӦ��ж�ػ�adminȡ��������£��Ѱ�װ��֤��ᱣ�����豸�ϣ����ᱻ�Ƴ���<br/><br/>����ҵӦ�÷ַ������£�&lt;!--RP2--&gt;&lt;!--RP2End--&gt;�����߿���ʹ����ǩ��֤�����ҵӦ�ý��ж���ǩ����ǩ����ɺ�Ӧ�ð��ṩ����ҵ����Ա����ҵ����Ա���Խ���ǩ�����Ӧ�ð�װ���Ѳ�����ǩ��֤�����ҵ�豸�ϡ�<br/><br/>��ҵӦ����ǩ��֤��ʹ�����̣�&lt;!--RP3--&gt;&lt;!--RP3End--&gt;<br/><br/>1.ͨ��MDMӦ�ð�װ��ҵӦ����ǩ��֤�飻<br/><br/>2.����������ǩ�����ߣ���ohos-signer��DevEco Studioǩ�����������ԭʼHAP�����ж���ǩ����<br/><br/>3.��װ��ǩ��Ӧ�ã�����ͨ����ҵ˽��Ӧ���г���װ����<br/><br/>4.����Ӧ�á�<br/><br/>���Լ����<br/><br/>1.��װ�µ�ǩ��֤��֮��ʹ�þ�ǩ��֤���Ӧ�ÿ��Լ������У�<br/><br/>2.�Ѿ���װ����ҵӦ�ã���װ���µ���ҵǩ��֤����Ѱ�װ��Ӧ��������£�����ֱ�Ӹ��ǰ�װ��������ж��ԭӦ�ã�<br/><br/>3.��ҵ�����£��ر������漰��Ϣ��ȫ�ĳ����У���ҵ��Ҫȷ��Ա��ʹ�õ��ƶ��豸�н���װ�������ض����ڲ������͹��ߡ���ҵӦ����ǩ��֤��ͨ��ͳһ��Ӧ�����ݱ�ʶ����ϵͳ��Ӧ�ù�����Ȩ�޿��ƻ������ʹ�ã���֧����ҵӦ�õľ�Ĭ��װ���ܿص�ϵͳ<br/>�������ü����з�Χ���ƣ��Ӷ�ʵ����ҵ�������ܿ��ն��ϵ�׼������밲ȫ������<br/> |
| [installUserCertificate](arkts-mdm-securitymanager-installusercertificate-f.md#installUserCertificate-1) | ��װ�û�֤�飬ʹ��Promise�첽�ص���<br/> |
| [installUserCertificate](arkts-mdm-securitymanager-installusercertificate-f.md#installUserCertificate-2) | ֧�ְ�ϵͳ�˻���װ�û�֤�顣<br/> |
| [isScreenLockDisabledForAccount](arkts-mdm-securitymanager-isscreenlockdisabledforaccount-f.md#isScreenLockDisabledForAccount-1) | ��ѯ��ǰ�û��Ļ������������Ƿ񱻽��á�<br/> |
| [openSession](arkts-mdm-securitymanager-opensession-f.md#openSession-1) | ����ָ���û���ƾ�ݱ���Ự<br/> |
| [removeAllowedPermissionBundle](arkts-mdm-securitymanager-removeallowedpermissionbundle-f.md#removeAllowedPermissionBundle-1) | ��Ȩ��ʹ�������������Ƴ�ָ��Ӧ�ã��Ƴ����Ӧ�����ܼ���ʹ�ö�Ӧ��Ȩ�ޡ�<br/> |
| [removeUserExtCredential](arkts-mdm-securitymanager-removeuserextcredential-f.md#removeUserExtCredential-1) | �Ƴ���չ�û���֤ƾ��<br/> |
| [setAppClipboardPolicy](arkts-mdm-securitymanager-setappclipboardpolicy-f.md#setAppClipboardPolicy-1) | �����豸��������ԡ�<br/> |
| [setAppClipboardPolicy](arkts-mdm-securitymanager-setappclipboardpolicy-f.md#setAppClipboardPolicy-2) | ����ָ���û���ָ��Ӧ�õ��豸��������ԡ�<br/> |
| [setDeviceSecurityLevelPolicy](arkts-mdm-securitymanager-setdevicesecuritylevelpolicy-f.md#setDeviceSecurityLevelPolicy-1) | �豸DSL�л�����<br/> |
| [setDisallowedPermission](arkts-mdm-securitymanager-setdisallowedpermission-f.md#setDisallowedPermission-1) | ����ָ���û��µ�ָ��Ȩ�ޣ����ú�ָ���û��µ�����Ӧ�������ʹ��ָ��Ȩ��ʱĬ�Ͼܾ���<br/> |
| [setExternalSourceExtensionsPolicy](arkts-mdm-securitymanager-setexternalsourceextensionspolicy-f.md#setExternalSourceExtensionsPolicy-1) | �����ⲿ��Դ��չ����Ĺܿز��ԡ�<br/><br/>- DEFAULT��<br/><br/> Ĭ�ϣ���ʾ�޹ܿز��ԣ��û�����ͨ��������-��˽�밲ȫ-�߼����еġ������ⲿ��Դ����չ���򡱿����������Ƿ�������չ�������С�<br/>- DISALLOW��<br/><br/> ���á����ô˲��Ժ󣬽�ֹ�����ⲿ��Դ����չ���������е���չ����ɼ������У���չ����رպ��޷��������С��û��޷�����������-��˽�Ͱ�ȫ-�߼����еġ������ⲿ��Դ����չ���򡱿��ء�<br/>- FORCE_OPEN��<br/><br/> ǿ�ƿ��������ô˲��Ժ����������ⲿ��Դ����չ�����û��޷��رա�����-��˽�Ͱ�ȫ-�߼����еġ������ⲿ��Դ����չ���򡱿��ء�<br/> |
| [setPasswordPolicy](arkts-mdm-securitymanager-setpasswordpolicy-f.md#setPasswordPolicy-1) | �����豸����������ԡ����û�������������ʱ��������õ������������Ҫ�󣬻��а�ȫ��ʾ���������������<br/> |
| [setPermissionManagedState](arkts-mdm-securitymanager-setpermissionmanagedstate-f.md#setPermissionManagedState-1) | ����ָ��Ӧ�õ�[user_grantȨ��](permissions:Permissions)�Ĺ������ԡ�<br/> |
| [setScreenLockDisabledForAccount](arkts-mdm-securitymanager-setscreenlockdisabledforaccount-f.md#setScreenLockDisabledForAccount-1) | ����/���õ�ǰ�û��Ļ�����������������ʱ���豸���������������û���Ҫ����Ļ�ϻ�������ܽ������档����ʱ���豸��������������ֱ�ӽ������档<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; 1.�ýӿ����������豸����������ʱ��Ч��<br/>&gt;<br/>&gt; 2.�豸Ĭ���������û���������״̬��<br/>&gt;<br/>&gt; 3.�豸�ϴ�������ʱ�����ý��û���������ʧ�ܣ��׳�9201021�����롣<br/>&gt;<br/>&gt; 4.�·����û��������Ĳ��Ժ��û��������豸���룬��ʱ�������Ч���豸��Ҫ��֤�������ܽ������棬֮ǰ�·��Ĳ���ʧЧ��<br/> |
| [setScreenWatermarkImage](arkts-mdm-securitymanager-setscreenwatermarkimage-f.md#setScreenWatermarkImage-1) | ������Ļˮӡ<br/> |
| [setUnlockPolicy](arkts-mdm-securitymanager-setunlockpolicy-f.md#setUnlockPolicy-1) | ���ý�������<br/> |
| [setWatermarkImage](arkts-mdm-securitymanager-setwatermarkimage-f.md#setWatermarkImage-1) | Ϊָ���û���ָ��Ӧ������ˮӡ���ԡ���ǰֻ֧����ౣ��100�����ԡ�<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ���ӿ���������ҵ������Ϊ����Ӧ������ˮӡ��������ҵ��Ϣй¶���ա�������ΪϵͳӦ������ˮӡ���磺����Ӧ�ã������ܴ���δ֪�쳣��<br/> |
| [setWatermarkImage](arkts-mdm-securitymanager-setwatermarkimage-f.md#setWatermarkImage-2) | Ϊָ���û���ָ��Ӧ������ˮӡ���ԡ�<br/> |
| [uninstallEnterpriseReSignatureCertificate](arkts-mdm-securitymanager-uninstallenterpriseresignaturecertificate-f.md#uninstallEnterpriseReSignatureCertificate-1) | ж����ҵӦ����ǩ��֤�顣<br/> |
| [uninstallUserCertificate](arkts-mdm-securitymanager-uninstallusercertificate-f.md#uninstallUserCertificate-1) | ж���û�֤�飬ʹ��Promise�첽�ص���<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AddCredentialInfo](arkts-mdm-securitymanager-addcredentialinfo-i.md) | ����ƾ֤��Ϣ<br/> |
| [ApplicationInstance](arkts-mdm-securitymanager-applicationinstance-i.md) | Ӧ��ʵ����<br/> |
| [CertBlob](arkts-mdm-securitymanager-certblob-i.md) | ֤����Ϣ��<br/> |
| <!--DelRow-->[DeviceEncryptionStatus](arkts-mdm-securitymanager-deviceencryptionstatus-i-sys.md) |  |
| [PasswordPolicy](arkts-mdm-securitymanager-passwordpolicy-i.md) | �豸����������ԡ�<br/> |
| [WatermarkProperties](arkts-mdm-securitymanager-watermarkproperties-i.md) | ˮӡ����<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ClipboardPolicy](arkts-mdm-securitymanager-clipboardpolicy-e.md) | �豸��������ԡ�<br/> |
| [PermissionManagedState](arkts-mdm-securitymanager-permissionmanagedstate-e.md) | Ӧ��Ȩ�޵Ĺ���״̬��<br/> |

