# @ohos.enterprise.applicationManager

��ģ���ṩӦ�ù�����������������Ӧ�����н�ֹ��������ȡӦ�����н�ֹ�������Ƴ�Ӧ�����н�ֹ�����ȡ�

> **˵����**
>
> ��ģ��ӿڽ�����Stageģ����ʹ�á�
>
> ��ģ��ӿڽ����豸����Ӧ�ÿ��ţ��ҵ��ýӿ�ǰ�輤���豸����Ӧ�ã�������ο�[MDM Kit����ָ��](../../../../mdm/mdm-kit-guide.md)��
> [applicationManager.isAppKioskAllowed](arkts-mdm-applicationmanager-isappkioskallowed-f.md#isAppKioskAllowed-1)���⣬�ýӿڶ�����Ӧ�ÿ��š�

**起始版本：** 10

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addAllowedDistributeAbilityConnBundles](arkts-mdm-applicationmanager-addalloweddistributeabilityconnbundles-f.md#addAllowedDistributeAbilityConnBundles-1) | Ϊָ���û���������ʹ�÷ֲ�ʽ������Ӧ�������������е�Ӧ����ָ���û��¿���ʹ��ָ���ķֲ�ʽ������<br/><br/>��ǰ֧�ֵķֲ�ʽ�����У�[Эͬ����](arkts-mdm-applicationmanager-servicetype-e.md#ServiceType)��<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; 1.���Ҫ��������ʹ��Эͬ�����Ӧ���������ڵ��ñ��ӿ�ǰ�����Ѿ�ͨ��<br/>&gt; [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md#setDisallowedPolicyForAccount-1)<br/>&gt; �ӿڽ������������豸�������ݵ��豸�䵥�������ݵ�������������׳�������9201043��<br/><br/>&gt; 2.���������豸�������ݵ��豸�䵥�������ݵ��������������ʱ��ͨ�����ӿ����õ�����ʹ��Эͬ�����Ӧ�������ᱻͬ�������<br/> |
| [addAllowedNotificationBundles](arkts-mdm-applicationmanager-addallowednotificationbundles-f.md#addAllowedNotificationBundles-1) | ������������֪ͨ��Ӧ������������֪ͨ�������󣬲��ڴ������ڵ�Ӧ���޷�����֪ͨ��<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; 1.���Kioskģʽ��֪ͨ����������ͬʱ���ã���ô����Kioskģʽ��Ӧ����֪ͨ�������е�Ӧ�ö����Է���֪ͨ��<br/><br/>&gt; 2.���Ѿ�ͨ��<br/>&gt; [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md#setDisallowedPolicy-1)<br/>&gt; �����˽����豸֪ͨ����ʱ����ͨ�����ӿ�����֪ͨ�����������׳�������9200010��<br/><br/>&gt; 3.֪ͨ��������ϵͳ������Ч��ϵͳ����ʼ�տ��Է���֪ͨ��ϵͳӦ����֪ͨ�������ܿء�<br/><br/>&gt; 4.֧�ֿ��û����ã����ú���û�������Ч��<br/> |
| [addAllowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md#addAllowedRunningBundles-1) | ����Ӧ����Ӧ��������������������������������Ӧ��������ָ���û������У���������������Ӧ�ò�������ָ���û������С�<br/><br/>&gt; **˵����**<br/>&gt;<br/> |
| [addAutoStartApps](arkts-mdm-applicationmanager-addautostartapps-f.md#addAutoStartApps-1) | Ϊ��ǰ�û����ӿ���������Ӧ��������ͨ�����ӿ�������������������Ӧ�ã���ֹ�û����豸���ֶ�ȡ��Ӧ��������&lt;!--RP4--&gt;&lt;!--RP4End--&gt;������ͨ��<br/>[removeAutoStartApps](applicationManager.removeAutoStartApps(admin: Want, autoStartApps: Array&lt;Want&gt;))�ӿڽ�Ӧ�ô���<br/>�����������Ƴ���<br/> |
| [addAutoStartApps](arkts-mdm-applicationmanager-addautostartapps-f.md#addAutoStartApps-2) | Ϊָ���û����ӿ���������Ӧ���������������Ƿ��ֹ���û��ֶ�ȡ��Ӧ��������&lt;!--RP4--&gt;&lt;!--RP4End--&gt;��<br/><br/>ͨ�����ӿڡ�[addAutoStartApps](applicationManager.addAutoStartApps(admin: Want, autoStartApps: Array&lt;Want&gt;))�ӿھ������ӿ�<br/>��������Ӧ�������������ӿڵ����ÿ�ͬʱ��Ч��ͬһ�û��£�����������Ӧ���������֧�ְ���10��Ӧ�á����磺����ǰ����������3��Ӧ�ã�����໹��ͨ�����ӿ�Ϊ��ǰ�û�����7��Ӧ�á�<br/> |
| <!--DelRow-->[addDisallowedRunningBundles](arkts-mdm-applicationmanager-adddisallowedrunningbundles-f-sys.md#addDisallowedRunningBundles-1) | ����Ӧ����Ӧ�����н�ֹ��������������ֹ������Ӧ�ò������ڵ�ǰ�û������У����ڽ�ֹ�����е�Ӧ���������С�ʹ��callback�첽�ص�����API version 21��ʼ�����Ӧ��������������<br/>[addallowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md#addAllowedRunningBundles-1)�ǿ�<br/>���Ͳ�����ͨ�����ӿ�����Ӧ�����н�ֹ����������ᱨ9200010��ͻ�����롣<br/> |
| <!--DelRow-->[addDisallowedRunningBundles](arkts-mdm-applicationmanager-adddisallowedrunningbundles-f-sys.md#addDisallowedRunningBundles-2) | ����Ӧ����Ӧ�����н�ֹ��������������ֹ������Ӧ�ò�������ָ���û���ͨ��userIdָ���������У����ڽ�ֹ�����е�Ӧ���������С�ʹ��callback�첽�ص�����API version 21��ʼ�����Ӧ��������������<br/>[addallowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md#addAllowedRunningBundles-1)�ǿ�<br/>���Ͳ�����ͨ�����ӿ�����Ӧ�����н�ֹ����������ᱨ9200010��ͻ�����롣<br/> |
| <!--DelRow-->[addDisallowedRunningBundles](arkts-mdm-applicationmanager-adddisallowedrunningbundles-f-sys.md#addDisallowedRunningBundles-3) | ����Ӧ����Ӧ�����н�ֹ��������������ֹ������Ӧ�ò������ڵ�ǰ/ָ���û������С�ʹ��Promise�첽�ص�����API version 21��ʼ�����Ӧ��������������<br/>[addallowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md#addAllowedRunningBundles-1)�ǿ�<br/>���Ͳ�����ͨ�����ӿ�����Ӧ�����н�ֹ����������ᱨ9200010��ͻ�����롣<br/> |
| [addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md#addDisallowedRunningBundlesSync-1) | ����Ӧ����Ӧ�����н�ֹ��������������ֹ������Ӧ�ò������ڵ�ǰ/ָ���û������С���API version 21��ʼ�����Ӧ��������������<br/>[addallowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md#addAllowedRunningBundles-1)�ǿգ��Ͳ�����ͨ�����ӿ�����Ӧ�����н�ֹ����������ᱨ9200010��ͻ����<br/>�롣<br/> |
| [addDockApp](arkts-mdm-applicationmanager-adddockapp-f.md#addDockApp-1) | ����λ����������Ӧ�õ�PC/2in1�豸�ĵײ�����������Ӻ��û�����ͨ������������Ӧ��ͼ��ֱ������Ӧ�ã�Ӧ��ͼ��ΪӦ������������ʾ��Ĭ��ͼ�ꡣ<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; 1.��λ��0��1���Ѵ��ڡ�Ӧ�����ġ����������ġ����������λ������Ӧ�û᷵�ش�����9201019������λ��Ϊ����Ӧ�ã�����������ӡ�<br/>&gt;<br/>&gt; 2.����Ӧ�ò���ͨ�����ӿ����ӵ����������Ӧ�����ġ������������ġ������ļ���������������վ����<br/>&gt;<br/>&gt; 3.��֧�����Ӿ���Ӧ�ó�����ڣ�����ͼ�꣩��Ӧ�ã���ͼ���Ӧ�ò�֧�����ӡ�<br/>&gt;<br/>&gt; 4.��֧�����õ�ǰ�û��µĿ������ÿ���û��Ŀ������������100��Ӧ�á�<br/>&gt;<br/>&gt; 5.������Ӧ�õ�λ�ò�����Ӧ��ʱ����Ӧ�ý�ֱ��ռ�ø�λ�ã�ԭӦ�ü�����Ӧ���������˳��һλ��<br/>&gt;<br/>&gt; 6.������index�����������indexֵ���ڿ������ǰӦ������������Ӧ��Ĭ��׷�ӵ������ĩβ��<br/>&gt;<br/>&gt; 7.ͨ�����ӿ�����Ӧ�õ���������û������ֶ��Ƴ������Ӧ�õ�λ�á�<br/> |
| [addFreezeExemptedApps](arkts-mdm-applicationmanager-addfreezeexemptedapps-f.md#addFreezeExemptedApps-1) | Ϊָ���û����Ӻ�̨������Ӧ�����������ɶ��Ѱ�װӦ�����øò��ԣ��ò���������ʧЧ���������б��д���δ��װӦ�ã��򷵻�9200012�����롣�����ò��Ժ���������Ӧ�ñ�ж�أ���ж�ص�Ӧ�ý����������Ƴ����������Ѵ����������е�Ӧ�ã�����<br/>�ɹ����������ò��������в����ظ����Ӹ�Ӧ�á�<br/><br/>�����������Ŀ��Ӧ�õĹ���������Դ������Ӳ����Դ�����͸߹��ĹܿصȲ�����<br/> |
| [addHideLauncherIcon](arkts-mdm-applicationmanager-addhidelaunchericon-f.md#addHideLauncherIcon-1) | ������������Ӧ��ͼ��������<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; 1�����ӿڽ�֧�����ص�ǰ�û�������Ӧ��ͼ�꣬��֧������Ӧ�ÿ�Ƭ��<br/>&gt;<br/>&gt; 2����������ص�Ӧ����Ӧ�÷�������ͬ������Ӧ�÷�����<br/>&gt;<br/>&gt; 3�����ܰ���������Ӧ�ö����ӵ����������У���������Ӧ�ö�����ʾ�������ϡ�<br/> |
| [addKeepAliveApps](arkts-mdm-applicationmanager-addkeepaliveapps-f.md#addKeepAliveApps-1) | ���ӱ���Ӧ�����������Ӻ��Զ�����Ӧ�ý��̡��ڿ�����Ӧ�ñ�ɱ������ϵͳ��������Ӧ�ý��̡�&lt;!--RP7--&gt;&lt;!--RP7End--&gt;<br/><br/>ͨ�����ӿ�����������������Ӧ�ã���ֹ�û����豸���ֶ�ȡ������&lt;!--RP6--&gt;&lt;!--RP6End--&gt;������ͨ��<br/>[removeKeepAliveApps](arkts-mdm-applicationmanager-removekeepaliveapps-f.md#removeKeepAliveApps-1)�ӿڽ�Ӧ�ôӱ����������Ƴ���<br/><br/>�����Ӧ��������Ӧ�ý�ֹ��������[addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md#addDisallowedRunningBundlesSync-1)���Ͳ��ܽ�Ӧ����<br/>��������Ӧ������������ᱨ9200010��ͻ�����롣<br/><br/>�����Ҫ��Phone/Tablet�豸ʹ�����ƹ��ܣ����Ե���[addUserNonStopApps](arkts-mdm-applicationmanager-addusernonstopapps-f.md#addUserNonStopApps-1)����<br/>[addFreezeExemptedApps](arkts-mdm-applicationmanager-addfreezeexemptedapps-f.md#addFreezeExemptedApps-1)�ӿڣ����幦����ο�����ĵ���<br/> |
| [addKeepAliveApps](arkts-mdm-applicationmanager-addkeepaliveapps-f.md#addKeepAliveApps-2) | ���ӱ���Ӧ���������������Ƿ��ֹ�û��ֶ�ȡ��������Ӻ��Զ�����Ӧ�ý��̡��ڿ�����Ӧ�ñ�ɱ������ϵͳ��������Ӧ�ý��̡�<br/><br/>ͨ�����ӿڡ�<br/>[addKeepAliveApps](applicationManager.addKeepAliveApps(admin: Want, bundleNames: Array&lt;string&gt;, accountId: number))<br/>�ӿھ������ӱ���Ӧ�������������ӿڵ����ÿ�ͬʱ��Ч��ͬһ�û��£�����Ӧ���������֧�ְ���5��Ӧ�á����磺����ǰ����������3��Ӧ�ã�����໹��ͨ�����ӿ�Ϊ��ǰ�û�����2��Ӧ�á�<br/><br/>���ͨ��[addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md#addDisallowedRunningBundlesSync-1)�ӿڽ�Ӧ��������Ӧ�ý�ֹ�����������Ͳ���<br/>��Ӧ������������Ӧ������������ᱨ9200010��ͻ�����롣<br/><br/>�����Ҫ��Phone/Tablet�豸ʹ�����ƹ��ܣ����Ե���[addUserNonStopApps](arkts-mdm-applicationmanager-addusernonstopapps-f.md#addUserNonStopApps-1)����<br/>[addFreezeExemptedApps](arkts-mdm-applicationmanager-addfreezeexemptedapps-f.md#addFreezeExemptedApps-1)�ӿڣ����幦����ο�����ĵ���<br/> |
| [addUserNonStopApps](arkts-mdm-applicationmanager-addusernonstopapps-f.md#addUserNonStopApps-1) | Ϊָ���û����Ӳ��ɹ�ͣӦ�����������ɶ��Ѱ�װӦ�����øò��ԡ��������б��д���δ��װӦ�ã��򷵻�9200012�����롣�����ò��Ժ���������Ӧ�ñ�ж�أ���ж�ص�Ӧ�ý����������Ƴ����������Ѵ����������е�Ӧ�ã����سɹ����������ò�����<br/>���в����ظ����Ӹ�Ӧ�á�<br/><br/>���ɹ�ͣӦ����Phone��Tablet�豸��Ч�����û����������������ϻ��ر�Ӧ�ã�������-Ӧ�ú�Ԫ�����е��Ӧ�����ƽ�������ҳ���ҳ���е�ǿ��ֹͣ��ť�ʻ�ɫ�����ã�ҳ���е�ͣ�ð�ť������Ч��<br/><br/>���ɹ�ͣӦ����PC/2in1�豸��Ч�����û�������-Ӧ�ú�Ԫ�����е��Ӧ�����ƽ�������ҳ���ҳ���е�ǿ��ֹͣ��ť�ʻ�ɫ�����ã�ҳ���е�ͣ�ð�ť������Ч��<br/> |
| [clearUpApplicationData](arkts-mdm-applicationmanager-clearupapplicationdata-f.md#clearUpApplicationData-1) | ���Ӧ�ò������������ݡ�<br/> |
| [getAllowedDistributeAbilityConnBundles](arkts-mdm-applicationmanager-getalloweddistributeabilityconnbundles-f.md#getAllowedDistributeAbilityConnBundles-1) | ��ȡָ���û�������ʹ��ָ�����͵ķֲ�ʽ������Ӧ��������<br/> |
| [getAllowedKioskApps](arkts-mdm-applicationmanager-getallowedkioskapps-f.md#getAllowedKioskApps-1) | ��ȡ������Kioskģʽ�����е�Ӧ�á�<br/> |
| [getAllowedNotificationBundles](arkts-mdm-applicationmanager-getallowednotificationbundles-f.md#getAllowedNotificationBundles-1) | ��ȡ��������֪ͨ��Ӧ��������<br/> |
| [getAllowedRunningBundles](arkts-mdm-applicationmanager-getallowedrunningbundles-f.md#getAllowedRunningBundles-1) | ��ȡָ���û��µ�Ӧ����������������<br/> |
| [getApplicationWindowStates](arkts-mdm-applicationmanager-getapplicationwindowstates-f.md#getApplicationWindowStates-1) | ��ѯӦ�ô���״̬<br/> |
| [getAutoStartApps](arkts-mdm-applicationmanager-getautostartapps-f.md#getAutoStartApps-1) | ��ѯ��ǰ�û�����������Ӧ��������<br/> |
| [getAutoStartApps](arkts-mdm-applicationmanager-getautostartapps-f.md#getAutoStartApps-2) | ��ѯָ���û��µĿ���������Ӧ��������<br/> |
| <!--DelRow-->[getDisallowedRunningBundles](arkts-mdm-applicationmanager-getdisallowedrunningbundles-f-sys.md#getDisallowedRunningBundles-1) | ��ȡ��ǰ�û��µ�Ӧ�����н�ֹ������ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getDisallowedRunningBundles](arkts-mdm-applicationmanager-getdisallowedrunningbundles-f-sys.md#getDisallowedRunningBundles-2) | ��ȡָ���û���ͨ��userIdָ�����µ�Ӧ�����н�ֹ������ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getDisallowedRunningBundles](arkts-mdm-applicationmanager-getdisallowedrunningbundles-f-sys.md#getDisallowedRunningBundles-3) | ��ȡ��ǰ/ָ���û��µ�Ӧ�����н�ֹ������ʹ��Promise�첽�ص���<br/> |
| [getDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-getdisallowedrunningbundlessync-f.md#getDisallowedRunningBundlesSync-1) | ��ȡ��ǰ/ָ���û��µ�Ӧ�����н�ֹ������<br/> |
| [getDockApps](arkts-mdm-applicationmanager-getdockapps-f.md#getDockApps-1) | ��ȡ��ǰ�������Ӧ����Ϣ���б���<br/> |
| [getFreezeExemptedApps](arkts-mdm-applicationmanager-getfreezeexemptedapps-f.md#getFreezeExemptedApps-1) | ��ȡ��ǰ�豸�������û���̨������Ӧ��������<br/> |
| [getHideLauncherIcon](arkts-mdm-applicationmanager-gethidelaunchericon-f.md#getHideLauncherIcon-1) | ��ѯ��ǰ�û�����������Ӧ��ͼ��������<br/> |
| [getKeepAliveApps](arkts-mdm-applicationmanager-getkeepaliveapps-f.md#getKeepAliveApps-1) | ��ȡ����Ӧ�ð�����<br/> |
| [getUserNonStopApps](arkts-mdm-applicationmanager-getusernonstopapps-f.md#getUserNonStopApps-1) | ��ȡ��ǰ�豸�������û����ɹ�ͣӦ��������<br/> |
| [isAbilityDisabled](arkts-mdm-applicationmanager-isabilitydisabled-f.md#isAbilityDisabled-1) | ��ȡָ��Ӧ�ã�ϵͳӦ�ú�����Ӧ�þ�֧�֣���Ability����Ƿ񱻽��á�<br/> |
| [isAppKioskAllowed](arkts-mdm-applicationmanager-isappkioskallowed-f.md#isAppKioskAllowed-1) | ��ѯĳӦ���Ƿ�������Kioskģʽ�����С�<br/> |
| [isModifyAutoStartAppsDisallowed](arkts-mdm-applicationmanager-ismodifyautostartappsdisallowed-f.md#isModifyAutoStartAppsDisallowed-1) | ��ѯָ���û��Ƿ��ֹȡ��Ӧ����������<br/> |
| [isModifyKeepAliveAppsDisallowed](arkts-mdm-applicationmanager-ismodifykeepaliveappsdisallowed-f.md#isModifyKeepAliveAppsDisallowed-1) | ��ѯӦ���Ƿ��ֹȡ�����<br/> |
| [publishFormToDesktop](arkts-mdm-applicationmanager-publishformtodesktop-f.md#publishFormToDesktop-1) | ��Ƭ����<br/> |
| [queryBundleStatsInfos](arkts-mdm-applicationmanager-querybundlestatsinfos-f.md#queryBundleStatsInfos-1) | ��ѯָ���û��˻��ڸ���ʱ����ڣ���Ӧ����ǰ̨���е��ۼ�ʱ��ͳ����Ϣ����ѯ����С�������죬����ʱ��Ҫ������ʼʱ�䣨startTime��������ʱ�䣨endTime���Լ�Ŀ���û��˻�ID��accountId�����������startTime<br/>��endTimeΪ���뼶ʱ�����֧�ֵ��÷������Զ���ֵ��startTimeĬ��ȡ�����00:00:00.000��endTimeĬ��ȡ�����24:00:00.000����������㣩����������ӿڷ���BundleStatsInfo���飬<br/>ÿ��Ԫ�ذ���һ��Ӧ�õİ��������������ֵ�����Ӧʱ����ڵ�ǰ̨ʹ��ʱ�������뼶ʱ���������startTimeΪ0�����ʾ���豸�״ο�����ʱ�俪ʼ��ѯ������ʼʱ�����ڽ���ʱ�䣬�ӿڽ����ش�����9200012��<br/> |
| [queryTrafficStats](arkts-mdm-applicationmanager-querytrafficstats-f.md#queryTrafficStats-1) | ��ѯ��ǰ�û���ָ��Ӧ�����ض�ʱ�����ʹ�����������ʹ��Promise�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ������������ͣ�networkInfo.type����֧�ַ������磨connection.NetBearType.BEARER_CELLULAR����Wi-Fi���磨<br/>&gt; connection.NetBearType.BEARER_WIFI��������������ֵ���ӿڻ᷵�ش�����9200012��<br/>&gt;<br/>&gt; �������ʼʱ�䣨networkInfo.startTime��������ʱ�䣨networkInfo.endTime��Ϊ�뼶ʱ��������������ʼʱ�䡢����ʱ��Ϊ����������ʼʱ����ڽ���ʱ�䣬�ӿڻ᷵�ش�����9200012��<br/>&gt;<br/>&gt; ������û�ID��accountId���ǵ�ǰ�û�ʱ���ӿڻ᷵�ش�����9200012��<br/>&gt;<br/>&gt; �����ѯ��ʱ����������ʱ��-��ʼʱ�䣩��СΪ1�죬���Ϊ30�졣ʱ����̫С����ѯ������ܲ�׼ȷ��ʱ����̫�󣬲�ѯ��ʱ��ܳ���<br/> |
| [removeAllowedDistributeAbilityConnBundles](arkts-mdm-applicationmanager-removealloweddistributeabilityconnbundles-f.md#removeAllowedDistributeAbilityConnBundles-1) | Ϊָ���û��Ƴ�����ʹ�÷ֲ�ʽ������Ӧ���������Ƴ����������л���ʣ���Ӧ�ã���������е�Ӧ����ָ���û��¿���ʹ��ָ�����͵ķֲ�ʽ���������������ѱ���գ���ʣ���Ӧ�ã�������Ӧ����ָ���û��¶�������ʹ��ָ�����͵ķֲ�ʽ������<br/> |
| [removeAllowedNotificationBundles](arkts-mdm-applicationmanager-removeallowednotificationbundles-f.md#removeAllowedNotificationBundles-1) | ����������֪ͨ��Ӧ���������Ƴ�Ӧ�á�<br/> |
| [removeAllowedRunningBundles](arkts-mdm-applicationmanager-removeallowedrunningbundles-f.md#removeAllowedRunningBundles-1) | ��Ӧ�ô�ָ���û��µ�Ӧ�����������������Ƴ���<br/> |
| [removeAutoStartApps](arkts-mdm-applicationmanager-removeautostartapps-f.md#removeAutoStartApps-1) | Ϊ��ǰ�û�ɾ������������Ӧ��������<br/> |
| [removeAutoStartApps](arkts-mdm-applicationmanager-removeautostartapps-f.md#removeAutoStartApps-2) | ɾ��ָ���û��Ŀ���������Ӧ�������е�ָ��Ӧ�á�<br/> |
| <!--DelRow-->[removeDisallowedRunningBundles](arkts-mdm-applicationmanager-removedisallowedrunningbundles-f-sys.md#removeDisallowedRunningBundles-1) | �Ƴ���Ӧ�����н�ֹ�����е�Ӧ�ã��ڽ�ֹ�������ڵ�����£���Ӧ�����н�ֹ�����е�Ӧ�ò������ڵ�ǰ�û������С�ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[removeDisallowedRunningBundles](arkts-mdm-applicationmanager-removedisallowedrunningbundles-f-sys.md#removeDisallowedRunningBundles-2) | �Ƴ���Ӧ�����н�ֹ�����е�Ӧ�ã��ڽ�ֹ�������ڵ�����£���Ӧ�����н�ֹ�����е�Ӧ�ò�������ָ���û���ͨ��userIdָ���������С�ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[removeDisallowedRunningBundles](arkts-mdm-applicationmanager-removedisallowedrunningbundles-f-sys.md#removeDisallowedRunningBundles-3) | �Ƴ���ǰ/ָ���û���Ӧ�����н�ֹ�����е�Ӧ�ã�ʹ��Promise�첽�ص���<br/> |
| [removeDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-removedisallowedrunningbundlessync-f.md#removeDisallowedRunningBundlesSync-1) | ��Ӧ�ôӵ�ǰ/ָ���û��µ�Ӧ�����н�ֹ�������Ƴ���<br/> |
| [removeDockApp](arkts-mdm-applicationmanager-removedockapp-f.md#removeDockApp-1) | �ӿ�������Ƴ�Ӧ�á�<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ����Ӧ�ò���ͨ�����ӿڴӿ�������Ƴ�����Ӧ�����ġ������������ġ������ļ���������������վ�������򱨴�9201018�����롣<br/><br/>&gt; **˵��**<br/>&gt; ����Ӧ�ò���ͨ�����ӿڴӿ�������Ƴ�����Ӧ�����ġ������������ġ������ļ���������������վ�������򱨴�9201018�����롣<br/> |
| [removeFreezeExemptedApps](arkts-mdm-applicationmanager-removefreezeexemptedapps-f.md#removeFreezeExemptedApps-1) | Ϊָ���û�ɾ����̨������Ӧ��������ִ��ɾ������ʱ���������б��а���δ��װӦ�ã�ɾ���������ܳɹ�ִ�У��Ѱ�װ��Ӧ�ý���ɾ����δ��װ��Ӧ�ò�Ӱ��ɾ��������<br/> |
| [removeHideLauncherIcon](arkts-mdm-applicationmanager-removehidelaunchericon-f.md#removeHideLauncherIcon-1) | ȡ����������Ӧ��ͼ��������<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ȡ�����ص�Ӧ�û�������2����ʼ�ҿ�λ��ʾ�������2~18���޿�λ�����ڵ�1���ҿ�λ�������1���޿�λ�����ڵ�2����1��Ӧ�õ�λ�ô���С�ļ��з���Ӧ�á�<br/> |
| [removeKeepAliveApps](arkts-mdm-applicationmanager-removekeepaliveapps-f.md#removeKeepAliveApps-1) | �Ƴ�����Ӧ�������е�ָ��Ӧ�á�<br/> |
| [removeUserNonStopApps](arkts-mdm-applicationmanager-removeusernonstopapps-f.md#removeUserNonStopApps-1) | Ϊָ���û�ɾ�����ɹ�ͣӦ��������ִ��ɾ������ʱ���������б��а���δ��װӦ�ã�ɾ���������ܳɹ�ִ�У��Ѱ�װ��Ӧ�ý���ɾ����δ��װ��Ӧ�ò�Ӱ��ɾ��������<br/> |
| [setAbilityDisabled](arkts-mdm-applicationmanager-setabilitydisabled-f.md#setAbilityDisabled-1) | �����Ƿ����ָ��Ӧ�ã�ϵͳӦ�ú�����Ӧ�þ�֧�֣���Ability�������ǰ��֧��UIAbility���ͣ����ú��޷������Ability������û����档<br/> |
| [setAllowedKioskApps](arkts-mdm-applicationmanager-setallowedkioskapps-f.md#setAllowedKioskApps-1) | ����������Kioskģʽ�����е�Ӧ�á�<br/><br/>KioskģʽΪϵͳ�����ṩ��һ��Ӧ������ģʽ����ģʽ�»Ὣ�豸�����ڵ���Ӧ�û���һ��Ӧ�����У�ͬʱ������״̬��״̬�������Ʋ����͹ؼ����ܽ��п��ƣ���ֹ�û����豸����������Ӧ�û�ִ������������<br/> |
| [setKioskFeatures](arkts-mdm-applicationmanager-setkioskfeatures-f.md#setKioskFeatures-1) | ����Kioskģʽ��������ͨ�����ӿڿ��Կ�����Kioskģʽ���ܷ����֪ͨ���ġ��������ġ�<br/><br/>��API version 24��ʼ������֧�������Ƿ������ײ��ϻ�����������������󻬻��һ���ͣչʾ���DOCK����<br/><br/>�ڷ�Kioskģʽ�£����ӿڿ����������ã����ǲ�����Ч������Kioskģʽ��Ż���Ч��<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BundleStatsInfo](arkts-mdm-applicationmanager-bundlestatsinfo-i.md) | Ӧ�ð�ͳ����Ϣ��<br/> |
| [DockInfo](arkts-mdm-applicationmanager-dockinfo-i.md) | ������е�Ӧ����Ϣ��<br/> |
| [WindowStateInfo](arkts-mdm-applicationmanager-windowstateinfo-i.md) | ����״̬��Ϣ<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [KioskFeature](arkts-mdm-applicationmanager-kioskfeature-e.md) | Kioskģʽ��������<br/> |
| [ServiceType](arkts-mdm-applicationmanager-servicetype-e.md) | �ֲ�ʽ�������͡�<br/> |
| [WindowState](arkts-mdm-applicationmanager-windowstate-e.md) | ����״̬<br/> |

