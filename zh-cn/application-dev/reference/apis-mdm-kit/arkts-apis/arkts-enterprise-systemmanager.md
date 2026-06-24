# @ohos.enterprise.systemManager

��ģ���ṩϵͳ����������

> **˵��**��
>
> ��ģ��ӿڽ�����Stageģ����ʹ�á�
>
> ��ģ��ӿڽ����豸����Ӧ�ÿ��ţ��ҵ��ýӿ�ǰ�輤���豸����Ӧ�ã�������ο�[MDM Kit����ָ��](../../../../mdm/mdm-kit-guide.md)��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[addDisallowedNearLinkProtocols](arkts-mdm-systemmanager-adddisallowednearlinkprotocols-f.md#addDisallowedNearLinkProtocols-1) | Ϊָ���û����ӽ��õ�����Э��������NearLink Kit�����������ṩһ�ֵ͹��ġ������ʵĶ̾���ͨ�ŷ���֧�������豸֮������ӡ����ݽ�����&lt;!--RP3--&gt;&lt;!--RP3End--&gt;���ӿڶԼ��̡���д�ʵ�ϵͳ�����ϵͳӦ��<br/>����Ч��<br/> |
| <!--DelRow-->[addKeyEventPolicies](arkts-mdm-systemmanager-addkeyeventpolicies-f.md#addKeyEventPolicies-1) | ���Ӱ����¼��������ԡ�ϵͳ���������¼�ʱ����ƥ���·��İ����¼����ԣ���ͨ��<br/>[EnterpriseAdminExtensionAbility.onKeyEvent](arkts-mdm-enterpriseadminextensionability-c.md#onKeyEvent-1)<br/>�ص�֪ͨMDMӦ�ã���Я��ƥ����Եİ����¼���Ϣ��<br/> |
| <!--DelRow-->[finishLogCollected](arkts-mdm-systemmanager-finishlogcollected-f.md#finishLogCollected-1) | ɾ����MDMӦ���ڵ�ǰ�û����ռ������豸��־��<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��Ӧ�õ���[startCollectLog](arkts-mdm-systemmanager-startcollectlog-f.md#startCollectLog-1)��ʼ�ռ���־���յ�<br/>&gt; [EnterpriseAdminExtensionAbility.onLogCollected](arkts-mdm-enterpriseadminextensionability-c.md#onLogCollected-1)<br/>&gt; �ص�ʱ�����������������ߴ�����־�������ô˽ӿ�ɾ���ռ�������־��<br/>&gt;<br/>&gt; ���������ӿڣ��豸��־��ռ��ϵͳ�洢�ռ䣬��Ӱ����һ�ε���[startCollectLog](arkts-mdm-systemmanager-startcollectlog-f.md#startCollectLog-1)������־�ռ�����<br/> |
| <!--DelRow-->[getAutoUnlockAfterReboot](arkts-mdm-systemmanager-getautounlockafterreboot-f.md#getAutoUnlockAfterReboot-1) | ��ȡ�豸�Ƿ������Զ�������<br/> |
| <!--DelRow-->[getDisallowedNearLinkProtocols](arkts-mdm-systemmanager-getdisallowednearlinkprotocols-f.md#getDisallowedNearLinkProtocols-1) | ��ȡָ���û��½��õ�����Э��������<br/> |
| <!--DelRow-->[getInstallLocalEnterpriseAppEnabled](arkts-mdm-systemmanager-getinstalllocalenterpriseappenabled-f.md#getInstallLocalEnterpriseAppEnabled-1) | ��ѯ�Ƿ�֧�ֱ��ذ�װ��ҵӦ�á�<br/> |
| <!--DelRow-->[getInstallLocalEnterpriseAppEnabledForAccount](arkts-mdm-systemmanager-getinstalllocalenterpriseappenabledforaccount-f.md#getInstallLocalEnterpriseAppEnabledForAccount-1) | ��ѯָ���û��Ƿ�֧�ֱ��ذ�װ��ҵӦ�á�<br/> |
| <!--DelRow-->[getKeyEventPolicies](arkts-mdm-systemmanager-getkeyeventpolicies-f.md#getKeyEventPolicies-1) | ��ȡ�����¼��������ԡ�<br/> |
| <!--DelRow-->[getNTPServer](arkts-mdm-systemmanager-getntpserver-f.md#getNTPServer-1) | ��ȡNTPʱ���������Ϣ��<br/> |
| <!--DelRow-->[getOtaUpdatePolicy](arkts-mdm-systemmanager-getotaupdatepolicy-f.md#getOtaUpdatePolicy-1) | ��ѯ�������ԡ�<br/> |
| <!--DelRow-->[getUpdateAuthData](arkts-mdm-systemmanager-getupdateauthdata-f.md#getUpdateAuthData-1) | ��ȡϵͳ���µļ�Ȩ���ݣ�����У��ϵͳ������Ϣ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getUpdateResult](arkts-mdm-systemmanager-getupdateresult-f.md#getUpdateResult-1) | ��ȡϵͳ���½����ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[isActivationLockDisabled](arkts-mdm-systemmanager-isactivationlockdisabled-f.md#isActivationLockDisabled-1) | ��ȡ�豸����������״̬��<br/> |
| <!--DelRow-->[isOtaUpdateNonceEnable](arkts-mdm-systemmanager-isotaupdatenonceenable-f.md#isOtaUpdateNonceEnable-1) | ��ѯ�Ƿ�ʹ�ܷ��������������Nonce���<br/> |
| <!--DelRow-->[notifyUpdatePackages](arkts-mdm-systemmanager-notifyupdatepackages-f.md#notifyUpdatePackages-1) | ֪ͨϵͳ���°���Ϣ���������������£���Ҫ�ȵ��øýӿ�֪ͨϵͳ���°����ٵ���[systemManager.setOtaUpdatePolicy](arkts-mdm-systemmanager-setotaupdatepolicy-f.md#setOtaUpdatePolicy-1)��������<br/>���ԡ�ʹ��Promise�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; �ýӿڱȽϺ�ʱ�������ô˽ӿں󣬺��������Ӧ�����̵߳�������ͬ���ӿ�ʱ��Ҫ�ȴ��ýӿ��첽���ء�<br/> |
| <!--DelRow-->[removeDisallowedNearLinkProtocols](arkts-mdm-systemmanager-removedisallowednearlinkprotocols-f.md#removeDisallowedNearLinkProtocols-1) | Ϊָ���û��Ƴ����õ�����Э��������<br/> |
| <!--DelRow-->[removeKeyEventPolicies](arkts-mdm-systemmanager-removekeyeventpolicies-f.md#removeKeyEventPolicies-1) | ɾ�������¼��������ԡ�<br/> |
| <!--DelRow-->[setActivationLockDisabled](arkts-mdm-systemmanager-setactivationlockdisabled-f.md#setActivationLockDisabled-1) | ����/�����豸���������豸�����������ú󣬽��޷�ʹ�ò����豸���ܡ��ù���ֻ�������ض��豸&lt;!--RP5--&gt;&lt;!--RP5End--&gt;��<br/> |
| <!--DelRow-->[setAutoUnlockAfterReboot](arkts-mdm-systemmanager-setautounlockafterreboot-f.md#setAutoUnlockAfterReboot-1) | �����豸�����Զ�����������������������豸��Ч��<br/> |
| <!--DelRow-->[setInstallLocalEnterpriseAppEnabled](arkts-mdm-systemmanager-setinstalllocalenterpriseappenabled-f.md#setInstallLocalEnterpriseAppEnabled-1) | �����Ƿ�֧�ֱ��ذ�װ��ҵӦ�á�����Ϊ֧�ְ�װ�󣬾߱����ذ�װ������PC/2in1��ҵ�豸�ɱ���˫��Ӧ�ð�װ������װǩ��֤��ַ�����Ϊenterprise_normal����ҵӦ�á�<br/> |
| <!--DelRow-->[setInstallLocalEnterpriseAppEnabledForAccount](arkts-mdm-systemmanager-setinstalllocalenterpriseappenabledforaccount-f.md#setInstallLocalEnterpriseAppEnabledForAccount-1) | ����ָ���û����Ƿ�֧�ֱ��ذ�װ��ҵӦ�á��ھ߱����ذ�װ������PC/2in1��ҵ�豸���·�֧�ֱ�����ҵӦ�ò��Ժ��û���������������ļ�������ֱ��˫����ҵӦ�ð�װ��������ֱ�Ӱ�װ��ҵӦ�á�<br/><br/>��֧��enterprise_normal��enterprise_mdmǩ�����͵���ҵӦ�á�<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ������������������PC/2in1��ҵ�豸�ڵ�ǰ�û��¼�֧�ֱ��ذ�װ��ҵӦ�ã�<br/>&gt;<br/><br/>&lt;!--RP7--&gt;&lt;!--RP7End--&gt;<br/> |
| <!--DelRow-->[setNTPServer](arkts-mdm-systemmanager-setntpserver-f.md#setNTPServer-1) | ����NTP(Network Time Protocol)ʱ���������<br/> |
| <!--DelRow-->[setOtaUpdateNonceEnable](arkts-mdm-systemmanager-setotaupdatenonceenable-f.md#setOtaUpdateNonceEnable-1) | ʹ�ܷ��������������Nonce���<br/> |
| <!--DelRow-->[setOtaUpdatePolicy](arkts-mdm-systemmanager-setotaupdatepolicy-f.md#setOtaUpdatePolicy-1) | �����������ԡ��������������£���Ҫ�ȵ���[systemManager.notifyUpdatePackages](arkts-mdm-systemmanager-notifyupdatepackages-f.md#notifyUpdatePackages-1)�ӿ�֪ͨϵͳ���°����ٵ��øýӿ���<br/>���������ԡ�<br/> |
| <!--DelRow-->[startCollectLog](arkts-mdm-systemmanager-startcollectlog-f.md#startCollectLog-1) | ��ʼ�ռ��豸�������ɲ��洢��Ӳ�̵�[faultlog](@ohos.faultLogger:FaultLogger.FaultType)��־����֧���ռ�δ�洢��Ӳ�̵�faultlog��־��Ӧ��ҵ����־��ϵͳ������־��<br/><br/>- ���ýӿں�ϵͳ������һ����־�ռ���������������ӿ��������ء�������ܻ���Ϊϵͳ���ܵ�ԭ�����ռ�ʧ�ܡ�<br/>- �������MDMӦ�õ��ã���ͬMDMӦ���ڲ�ͬ�û����ռ�����־�ֿ����棬����Ӱ�졣ͬһʱ��ֻ����һ��MDMӦ��������־�ռ�����������ִ�����ǰ���ñ��ӿڻ᷵�ش�����9201009������ִ����ɺ���������MDMӦ�õ��á�<br/>- ����ִ����ɺ�ͨ��<br/>[EnterpriseAdminExtensionAbility.onLogCollected](arkts-mdm-enterpriseadminextensionability-c.md#onLogCollected-1)<br/>�ص�����֪ͨ��MDMӦ�ã�ϵͳ�����ռ�����־�ļ����ص�MDMӦ��ɳ��·����MDMӦ�ÿ����ڻص������ж�ȡ���ռ�����־��<br/>- �����־�ռ�����ִ�г���5���ӣ�<br/>[EnterpriseAdminExtensionAbility.onLogCollected](arkts-mdm-enterpriseadminextensionability-c.md#onLogCollected-1)<br/>�ص������᷵����־�ռ�����ʧ�ܡ�<br/>- Ӧ��ȡ����־�󣬽������[systemManager.finishLogCollected](arkts-mdm-systemmanager-finishlogcollected-f.md#finishLogCollected-1)ɾ�����ռ�������־��<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[ErrorInfo](arkts-mdm-systemmanager-errorinfo-i.md) | ϵͳ���´�����Ϣ��<br/> |
| <!--DelRow-->[KeyEvent](arkts-mdm-systemmanager-keyevent-i.md) | �����¼���<br/>[EnterpriseAdminExtensionAbility.onKeyEvent](arkts-mdm-enterpriseadminextensionability-c.md#onKeyEvent-1)<br/>�����¼��ص�����ʱ�����ݵ�ǰ�����¼���Ϣ��<br/> |
| <!--DelRow-->[KeyEventPolicy](arkts-mdm-systemmanager-keyeventpolicy-i.md) | �����¼��������ԡ������¼�����ʱ����������Ӧ���·������¼��������Եİ���������δ�·������¼��������Եİ����¼���ϵͳִ��ԭ�ȵ���Ӧ�߼���<br/> |
| <!--DelRow-->[KeyItem](arkts-mdm-systemmanager-keyitem-i.md) | ����������Ϣ����ǰ[KeyCode](arkts-mdm-systemmanager-keycode-e.md#KeyCode)�¼�����ʱ�������ѱ����µİ�����Ϣ��<br/> |
| <!--DelRow-->[NotifyDescription](arkts-mdm-systemmanager-notifydescription-i.md) | ��ҵ�Զ������֪ͨ˵����<br/> |
| <!--DelRow-->[OtaUpdatePolicy](arkts-mdm-systemmanager-otaupdatepolicy-i.md) | �������ԡ�<br/> |
| <!--DelRow-->[Package](arkts-mdm-systemmanager-package-i.md) | ϵͳ���°����顣<br/> |
| <!--DelRow-->[PackageDescription](arkts-mdm-systemmanager-packagedescription-i.md) | ϵͳ���°�������Ϣ��<br/> |
| <!--DelRow-->[SystemUpdateInfo](arkts-mdm-systemmanager-systemupdateinfo-i.md) | �����µ�ϵͳ�汾��Ϣ��<br/> |
| <!--DelRow-->[UpdatePackageInfo](arkts-mdm-systemmanager-updatepackageinfo-i.md) | ϵͳ���°���Ϣ��<br/> |
| <!--DelRow-->[UpdateResult](arkts-mdm-systemmanager-updateresult-i.md) | ϵͳ���½����Ϣ��<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[KeyAction](arkts-mdm-systemmanager-keyaction-e.md) | ����������<br/> |
| <!--DelRow-->[KeyCode](arkts-mdm-systemmanager-keycode-e.md) | �������롣[���Ӱ����¼�����](arkts-mdm-systemmanager-addkeyeventpolicies-f.md#addKeyEventPolicies-1)��[ɾ�������¼�����](arkts-mdm-systemmanager-removekeyeventpolicies-f.md#removeKeyEventPolicies-1)��<br/>[��ȡ�����¼�����](arkts-mdm-systemmanager-getkeyeventpolicies-f.md#getKeyEventPolicies-1)��<br/>[�����¼��ص�](arkts-mdm-enterpriseadminextensionability-c.md#onKeyEvent-1)�ӿ�ͨ����������<br/>ӳ�䵽�豸��Ӧʵ�ʰ�����<br/> |
| <!--DelRow-->[KeyPolicy](arkts-mdm-systemmanager-keypolicy-e.md) | �������ԡ�MDMӦ���·��������Եİ���������ϵͳ�����¼�ƥ����ϵͳ��Ϊ��<br/> |
| <!--DelRow-->[NearLinkProtocol](arkts-mdm-systemmanager-nearlinkprotocol-e.md) | ����Э��ö�١�<br/> |
| <!--DelRow-->[PackageType](arkts-mdm-systemmanager-packagetype-e.md) | ϵͳ���°����͡�<br/> |
| <!--DelRow-->[PolicyType](arkts-mdm-systemmanager-policytype-e.md) | ������������ö�١�<br/> |
| <!--DelRow-->[UpdateStatus](arkts-mdm-systemmanager-updatestatus-e.md) | ϵͳ����״̬��<br/> |

