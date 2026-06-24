# @ohos.enterprise.bundleManager

��ģ���ṩ�������������������Ӱ���װ������������ȡ����װ�����������Ƴ�����װ���������ȡ�

> **˵����**
>
> ��ģ��ӿڽ�����Stageģ����ʹ�á�
>
> ��ģ��ӿڽ����豸����Ӧ�ÿ��ţ��ҵ��ýӿ�ǰ�輤���豸����Ӧ�ã�������ο�[MDM Kit����ָ��](../../../../mdm/mdm-kit-guide.md)��

**起始版本：** 10

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[addAllowedInstallBundles](arkts-mdm-bundlemanager-addallowedinstallbundles-f-sys.md#addAllowedInstallBundles-1) | ����Ӧ������ǰ�û���Ӧ�ó������װ��������������������������Ӧ�������ڵ�ǰ�û��°�װ������������װ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[addAllowedInstallBundles](arkts-mdm-bundlemanager-addallowedinstallbundles-f-sys.md#addAllowedInstallBundles-2) | ����Ӧ����Ӧ�ó������װ��������������������������Ӧ��������ָ���û���ͨ��userIdָ�����°�װ������������װ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[addAllowedInstallBundles](arkts-mdm-bundlemanager-addallowedinstallbundles-f-sys.md#addAllowedInstallBundles-3) | ����Ӧ����Ӧ�ó������װ��������������������������Ӧ�������ڵ�ǰ/ָ���û��°�װ������������װ��ʹ��Promise�첽�ص���<br/> |
| [addAllowedInstallBundlesSync](arkts-mdm-bundlemanager-addallowedinstallbundlessync-f.md#addAllowedInstallBundlesSync-1) | ����Ӧ����Ӧ�ó������װ��������������������������Ӧ�������ڵ�ǰ/ָ���û��°�װ����������������Ӧ�ò�������װ��ϵͳӦ��ж�غ����°�װ�����ܵ��ӿ����ƣ�����ͨӦ����ж�غ����°�װʱ������ܵ��ӿ����ơ�<br/> |
| <!--DelRow-->[addDisallowedInstallBundles](arkts-mdm-bundlemanager-adddisallowedinstallbundles-f-sys.md#addDisallowedInstallBundles-1) | ����Ӧ����Ӧ�ó������װ��ֹ��������������ֹ������Ӧ�ò������ڵ�ǰ�û��°�װ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[addDisallowedInstallBundles](arkts-mdm-bundlemanager-adddisallowedinstallbundles-f-sys.md#addDisallowedInstallBundles-2) | ����Ӧ����Ӧ�ó������װ��ֹ��������������ֹ������Ӧ�ò�������ָ���û���ͨ��userIdָ�����°�װ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[addDisallowedInstallBundles](arkts-mdm-bundlemanager-adddisallowedinstallbundles-f-sys.md#addDisallowedInstallBundles-3) | ����Ӧ����Ӧ�ó������װ��ֹ��������������ֹ������Ӧ�ò������ڵ�ǰ/ָ���û��°�װ��ʹ��Promise�첽�ص���<br/> |
| [addDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-adddisallowedinstallbundlessync-f.md#addDisallowedInstallBundlesSync-1) | ����Ӧ����Ӧ�ó������װ��ֹ��������������ֹ������Ӧ�ò������ڵ�ǰ/ָ���û��°�װ��ϵͳӦ��ж�غ����°�װ�����ܵ��ӿ����ƣ�����ͨӦ����ж�غ����°�װʱ������ܵ��ӿ����ơ�<br/> |
| <!--DelRow-->[addDisallowedUninstallBundles](arkts-mdm-bundlemanager-adddisalloweduninstallbundles-f-sys.md#addDisallowedUninstallBundles-1) | ����Ӧ����Ӧ�ó����ж�ؽ�ֹ��������������ֹ������Ӧ�ò������ڵ�ǰ�û���ж�أ�ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[addDisallowedUninstallBundles](arkts-mdm-bundlemanager-adddisalloweduninstallbundles-f-sys.md#addDisallowedUninstallBundles-2) | ����Ӧ����Ӧ�ó����ж�ؽ�ֹ��������������ֹ������Ӧ�ò�������ָ���û���ͨ��userIdָ������ж�ء�ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[addDisallowedUninstallBundles](arkts-mdm-bundlemanager-adddisalloweduninstallbundles-f-sys.md#addDisallowedUninstallBundles-3) | ����Ӧ����Ӧ�ó����ж�ؽ�ֹ��������������ֹ������Ӧ�ò������ڵ�ǰ/ָ���û���ж�ء�ʹ��Promise�첽�ص���<br/> |
| [addDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-adddisalloweduninstallbundlessync-f.md#addDisallowedUninstallBundlesSync-1) | ����Ӧ������ж�ؽ�ֹ��������������ֹ������Ӧ�ò������ڵ�ǰ/ָ���û���ж�ء�<br/> |
| [addInstallationAllowedAppDistributionTypes](arkts-mdm-bundlemanager-addinstallationallowedappdistributiontypes-f.md#addInstallationAllowedAppDistributionTypes-1) | ���ӿɰ�װӦ�õķַ����͡����ӳɹ��󣬵�ǰ�豸���԰�װ��Ӧ�ַ����͵�Ӧ�ã����޷���װ[AppDistributionType](arkts-mdm-bundlemanager-appdistributiontype-e.md#AppDistributionType)��δ���ӵķַ����͵�Ӧ<br/>�á�<br/><br/>Ӧ�ó���ǩ��֤��ķַ�������ϸ������μ�[ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md#ApplicationInfo)��appDistributionType���ԡ�<br/> |
| <!--DelRow-->[getAllowedInstallBundles](arkts-mdm-bundlemanager-getallowedinstallbundles-f-sys.md#getAllowedInstallBundles-1) | ��ȡ��ǰ�û��µ�Ӧ�ó������װ����������ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getAllowedInstallBundles](arkts-mdm-bundlemanager-getallowedinstallbundles-f-sys.md#getAllowedInstallBundles-2) | ��ȡָ���û���ͨ��userIdָ�����µ�Ӧ�ó������װ����������ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getAllowedInstallBundles](arkts-mdm-bundlemanager-getallowedinstallbundles-f-sys.md#getAllowedInstallBundles-3) | ��ȡ��ǰ/ָ���û��µ�Ӧ�ó������װ����������ʹ��Promise�첽�ص���<br/> |
| [getAllowedInstallBundlesSync](arkts-mdm-bundlemanager-getallowedinstallbundlessync-f.md#getAllowedInstallBundlesSync-1) | ��ȡ��ǰ/ָ���û��µ�Ӧ�ó������װ����������<br/> |
| <!--DelRow-->[getDisallowedInstallBundles](arkts-mdm-bundlemanager-getdisallowedinstallbundles-f-sys.md#getDisallowedInstallBundles-1) | ��ȡ��ǰ�û��µ�Ӧ�ó������װ��ֹ������ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getDisallowedInstallBundles](arkts-mdm-bundlemanager-getdisallowedinstallbundles-f-sys.md#getDisallowedInstallBundles-2) | ��ȡָ���û���ͨ��userIdָ�����µ�Ӧ�ó������װ��ֹ������ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getDisallowedInstallBundles](arkts-mdm-bundlemanager-getdisallowedinstallbundles-f-sys.md#getDisallowedInstallBundles-3) | ��ȡ��ǰ/ָ���û��µ�Ӧ�ó������װ��ֹ������ʹ��Promise�첽�ص���<br/> |
| [getDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-getdisallowedinstallbundlessync-f.md#getDisallowedInstallBundlesSync-1) | ��ȡ��ǰ/ָ���û��µ�Ӧ�ó������װ��ֹ������<br/> |
| <!--DelRow-->[getDisallowedUninstallBundles](arkts-mdm-bundlemanager-getdisalloweduninstallbundles-f-sys.md#getDisallowedUninstallBundles-1) | ��ȡ��ǰ�û��µ�Ӧ�ó����ж�ؽ�ֹ������ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getDisallowedUninstallBundles](arkts-mdm-bundlemanager-getdisalloweduninstallbundles-f-sys.md#getDisallowedUninstallBundles-2) | ��ȡָ���û���ͨ��userIdָ�����µ�Ӧ�ó����ж�ؽ�ֹ������ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getDisallowedUninstallBundles](arkts-mdm-bundlemanager-getdisalloweduninstallbundles-f-sys.md#getDisallowedUninstallBundles-3) | ��ȡ��ǰ/ָ���û���Ӧ�ó����ж�ؽ�ֹ�����ӿڣ�ʹ��Promise�첽�ص���<br/> |
| [getDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-getdisalloweduninstallbundlessync-f.md#getDisallowedUninstallBundlesSync-1) | ��ȡ��ǰ/ָ���û��°�ж�ؽ�ֹ������<br/> |
| [getInstallationAllowedAppDistributionTypes](arkts-mdm-bundlemanager-getinstallationallowedappdistributiontypes-f.md#getInstallationAllowedAppDistributionTypes-1) | ��ȡ�ɰ�װ��Ӧ�ó���ǩ��֤��ķַ����͡�<br/> |
| [getInstalledBundleList](arkts-mdm-bundlemanager-getinstalledbundlelist-f.md#getInstalledBundleList-1) | ��ȡ�豸ָ���û����Ѱ�װӦ���б���ʹ��Promise�첽�ص���<br/> |
| [getInstalledBundleList](arkts-mdm-bundlemanager-getinstalledbundlelist-f.md#getInstalledBundleList-2) | ���ݸ�����bundleInfoGetFlag��ȡ�豸ָ���û����Ѱ�װӦ���б���ʹ��Promise�첽�ص���<br/> |
| [getInstalledBundleStorageStats](arkts-mdm-bundlemanager-getinstalledbundlestoragestats-f.md#getInstalledBundleStorageStats-1) | ��ȡ�豸ָ���û����Ѱ�װӦ�õĴ洢ռ����Ϣ��ʹ��Promise�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; 1.���ܻ�ȡ�Ѱ�װӦ�õĴ洢ռ����Ϣ��<br/>&gt;<br/>&gt; 2.bundleNames����Ϊempty��ȫ������δ��װ��Ӧ�ð��������׳�9200012�����롣<br/>&gt;<br/>&gt; 3.bundleNames�������ݵİ�������Ӧ���Ѱ�װ������Ӧ��δ��װʱ���ӿڷ����������Ѱ�װ��Ӧ�÷���ʵ�ʵĴ洢ռ����Ϣ��δ��װ��Ӧ�ô洢ռ����ϢΪ0��<br/>&gt;<br/>&gt; 4.�ýӿ�֧�ֿ��û���ѯ�����������100�û��£���ѯ101�û��µ�ĳЩӦ�õĴ洢ռ����Ϣ��<br/> |
| <!--DelRow-->[install](arkts-mdm-bundlemanager-install-f-sys.md#install-1) | ��װָ��·���µ�Ӧ�ð���ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[install](arkts-mdm-bundlemanager-install-f-sys.md#install-2) | ��װָ��·���µ�ָ����װ������Ӧ�ð���ʹ��callback�첽�ص���<br/> |
| [install](arkts-mdm-bundlemanager-install-f.md#install-3) | ��װָ��·���µ�Ӧ�ð���ʹ��Promise�첽�ص���&lt;/br&gt;�˽ӿ�ֻ�ܰ�װ�ַ�����Ϊenterprise_mdm��MDMӦ�ã���enterprise_normal����ͨ��ҵӦ�ã����͵�Ӧ�ã�����ͨ��<br/>[getBundleInfoForSelf](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1)�ӿڲ�ѯӦ��<br/>������[BundleInfo](../../apis-ability-kit/arkts-apis/arkts-ability-bundleinfo-i.md#BundleInfo)������BundleInfo.appInfo.appDistributionTypeΪӦ�õķַ����͡�<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; �ýӿڱȽϺ�ʱ�������ô˽ӿں󣬺��������Ӧ�����̵߳�������ͬ���ӿ�ʱ��Ҫ�ȴ��ýӿ��첽���ء�<br/> |
| [installForResult](arkts-mdm-bundlemanager-installforresult-f.md#installForResult-1) | ��װӦ��<br/> |
| [installMarketApps](arkts-mdm-bundlemanager-installmarketapps-f.md#installMarketApps-1) | ���ز���װӦ���г�Ӧ�á�<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ���ӿڵ��óɹ����������������Ӧ���������񣬴��������Ӧ���г���������������һ�¡����ذ�װ�����󣬰�װ�����ͨ���ص�<br/>&gt; [EnterpriseAdminExtensionAbility.onMarketAppInstallResult]{@link<br/><br/>&gt; **˵��**<br/>&gt;<br/>���ӿڵ��óɹ����������������Ӧ���������񣬴��������Ӧ���г���������������һ�¡����ذ�װ�����󣬰�װ�����ͨ���ص�[EnterpriseAdminExtensionAbility.onMarketAppInstallResult<br/>](|
| <!--DelRow-->[removeAllowedInstallBundles](arkts-mdm-bundlemanager-removeallowedinstallbundles-f-sys.md#removeAllowedInstallBundles-1) | �Ƴ���ǰ�û���Ӧ�ó������װ���������е�ָ��Ӧ�á���װ������������ʱ���������������е�Ӧ�ò������ڵ�ǰ�û��°�װ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[removeAllowedInstallBundles](arkts-mdm-bundlemanager-removeallowedinstallbundles-f-sys.md#removeAllowedInstallBundles-2) | �Ƴ���Ӧ�ó������װ���������е�Ӧ�ã��������������ڵ�����£��������������е�Ӧ�ò�������ָ���û���ͨ��userIdָ�����°�װ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[removeAllowedInstallBundles](arkts-mdm-bundlemanager-removeallowedinstallbundles-f-sys.md#removeAllowedInstallBundles-3) | �Ƴ���Ӧ�ó������װ���������е�Ӧ�ã��������������ڵ�����£��������������е�Ӧ�ò������ڵ�ǰ/ָ���û��°�װ��ʹ��Promise�첽�ص���<br/> |
| [removeAllowedInstallBundlesSync](arkts-mdm-bundlemanager-removeallowedinstallbundlessync-f.md#removeAllowedInstallBundlesSync-1) | ��Ӧ�ó������װ�����������Ƴ�Ӧ�ã��������������ڵ�����£�����Ӧ�ó������װ���������е�Ӧ�ò������ڵ�ǰ/ָ���û��°�װ��<br/> |
| <!--DelRow-->[removeDisallowedInstallBundles](arkts-mdm-bundlemanager-removedisallowedinstallbundles-f-sys.md#removeDisallowedInstallBundles-1) | �Ƴ���Ӧ�ó������װ��ֹ�����е�Ӧ�ã��ڽ�ֹ�������ڵ�����£��ڽ�ֹ�����е�Ӧ�ò������ڵ�ǰ�û��°�װ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[removeDisallowedInstallBundles](arkts-mdm-bundlemanager-removedisallowedinstallbundles-f-sys.md#removeDisallowedInstallBundles-2) | �Ƴ���Ӧ�ó������װ��ֹ�����е�Ӧ�ã��ڽ�ֹ�������ڵ�����£��ڽ�ֹ�����е�Ӧ�ò�������ָ���û���ͨ��userIdָ�����°�װ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[removeDisallowedInstallBundles](arkts-mdm-bundlemanager-removedisallowedinstallbundles-f-sys.md#removeDisallowedInstallBundles-3) | �Ƴ���Ӧ�ó������װ��ֹ�����е�Ӧ�ã��ڽ�ֹ�������ڵ�����£��ڽ�ֹ�����е�Ӧ�ò������ڵ�ǰ/ָ���û��°�װ��ʹ��Promise�첽�ص���<br/> |
| [removeDisallowedInstallBundlesSync](arkts-mdm-bundlemanager-removedisallowedinstallbundlessync-f.md#removeDisallowedInstallBundlesSync-1) | ��Ӧ�ó������װ��ֹ�������Ƴ�Ӧ�ã��ڽ�ֹ�������ڵ�����£���Ӧ�ó������װ��ֹ�����е�Ӧ�ò������ڵ�ǰ/ָ���û��°�װ��<br/> |
| <!--DelRow-->[removeDisallowedUninstallBundles](arkts-mdm-bundlemanager-removedisalloweduninstallbundles-f-sys.md#removeDisallowedUninstallBundles-1) | �Ƴ���Ӧ�ó����ж�ؽ�ֹ�����е�Ӧ�ã��ڽ�ֹ�������ڵ�����£��ڽ�ֹ�����е�Ӧ�ò������ڵ�ǰ�û���ж�أ�ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[removeDisallowedUninstallBundles](arkts-mdm-bundlemanager-removedisalloweduninstallbundles-f-sys.md#removeDisallowedUninstallBundles-2) | �Ƴ���Ӧ�ó����ж�ؽ�ֹ�����е�Ӧ�ã��ڽ�ֹ�������ڵ�����£��ڽ�ֹ�����е�Ӧ�ò�������ָ���û���ͨ��userIdָ������ж�ء�ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[removeDisallowedUninstallBundles](arkts-mdm-bundlemanager-removedisalloweduninstallbundles-f-sys.md#removeDisallowedUninstallBundles-3) | �Ƴ���Ӧ�ó����ж�ؽ�ֹ�����е�Ӧ�á��ڽ�ֹ�������ڵ�����£��ڽ�ֹ�����е�Ӧ�ò������ڵ�ǰ/ָ���û���ж�ء�ʹ��Promise�첽�ص���<br/> |
| [removeDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-removedisalloweduninstallbundlessync-f.md#removeDisallowedUninstallBundlesSync-1) | �ڰ�ж�ؽ�ֹ�������Ƴ�Ӧ�á��ڽ�ֹ�������ڵ�����£��ڰ�ж�ؽ�ֹ�����е�Ӧ�ò������ڵ�ǰ/ָ���û���ж�ء�<br/> |
| [removeInstallationAllowedAppDistributionTypes](arkts-mdm-bundlemanager-removeinstallationallowedappdistributiontypes-f.md#removeInstallationAllowedAppDistributionTypes-1) | �Ƴ�Ӧ�õķַ����͡���ֻ�Ƴ��������в��ֵķַ����ͣ���ǰ�豸���԰�װ������ʣ�µķַ����͵�Ӧ�ã����޷���װ<br/>[AppDistributionType]{@link bundleManager.AppDistributionType)��δ���ӵķַ����͵�Ӧ�á�<br/><br/>Ӧ�ó���ǩ��֤��ķַ�������ϸ������μ�[ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md#ApplicationInfo)��appDistributionType���ԡ�<br/> |
| <!--DelRow-->[uninstall](arkts-mdm-bundlemanager-uninstall-f-sys.md#uninstall-1) | ж�ص�ǰ�û��µ�ָ��Ӧ�ó�������Ҳ�����Ӧ�ó�������ݡ�ʹ��callback�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��Ӧ��Ϊ����ж�ص�Ԥ��Ӧ�û���ͨ��<br/>&gt; [addDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-adddisalloweduninstallbundlessync-f.md#addDisallowedUninstallBundlesSync-1)<br/>&gt; �ӿ������˲�����ж��ʱ�����ô˽ӿ�ж��Ӧ�û᷵��401�����롣<br/> |
| <!--DelRow-->[uninstall](arkts-mdm-bundlemanager-uninstall-f-sys.md#uninstall-2) | ж��ָ���û��£��ɲ���userIdָ������ָ��Ӧ�ó�������Ҳ�����Ӧ�ó�������ݡ�ʹ��callback�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��Ӧ��Ϊ����ж�ص�Ԥ��Ӧ�û���ͨ��<br/>&gt; [addDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-adddisalloweduninstallbundlessync-f.md#addDisallowedUninstallBundlesSync-1)<br/>&gt; �ӿ������˲�����ж��ʱ�����ô˽ӿ�ж��Ӧ�û᷵��401�����롣<br/> |
| <!--DelRow-->[uninstall](arkts-mdm-bundlemanager-uninstall-f-sys.md#uninstall-3) | ж�ص�ǰ�û��µ�ָ��Ӧ�ó������ѡ���Ƿ���Ӧ�ó�������ݣ���isKeepDataָ������ʹ��callback�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��Ӧ��Ϊ����ж�ص�Ԥ��Ӧ�û���ͨ��<br/>&gt; [addDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-adddisalloweduninstallbundlessync-f.md#addDisallowedUninstallBundlesSync-1)<br/>&gt; �ӿ������˲�����ж��ʱ�����ô˽ӿ�ж��Ӧ�û᷵��401�����롣<br/> |
| <!--DelRow-->[uninstall](arkts-mdm-bundlemanager-uninstall-f-sys.md#uninstall-4) | ж��ָ���û��£��ɲ���userIdָ������ָ��Ӧ�ó�����ӿڣ�ѡ���Ƿ���Ӧ�ó�������ݣ���isKeepDataָ������ʹ��callback�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��Ӧ��Ϊ����ж�ص�Ԥ��Ӧ�û���ͨ��<br/>&gt; [addDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-adddisalloweduninstallbundlessync-f.md#addDisallowedUninstallBundlesSync-1)<br/>&gt; �ӿ������˲�����ж��ʱ�����ô˽ӿ�ж��Ӧ�û᷵��401�����롣<br/> |
| [uninstall](arkts-mdm-bundlemanager-uninstall-f.md#uninstall-5) | ж�ص�ǰ/ָ���û��µ�ָ�����ӿڣ�ѡ���Ƿ��������ݣ���isKeepDataָ������ʹ��Promise�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��Ӧ��Ϊ����ж�ص�Ԥ��Ӧ�û���ͨ��<br/>&gt; [addDisallowedUninstallBundlesSync](arkts-mdm-bundlemanager-adddisalloweduninstallbundlessync-f.md#addDisallowedUninstallBundlesSync-1)<br/>&gt; �ӿ������˲�����ж��ʱ�����ô˽ӿ�ж��Ӧ�û᷵��401�����롣<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ApplicationInfo](arkts-mdm-bundlemanager-applicationinfo-i.md) | Ӧ�ó�����Ϣ��<br/> |
| [BundleInfo](arkts-mdm-bundlemanager-bundleinfo-i.md) | ����Ӧ�ð���Ϣ��<br/> |
| [BundleStorageStats](arkts-mdm-bundlemanager-bundlestoragestats-i.md) | Ӧ�õĴ洢ռ����Ϣ��<br/> |
| [InstallParam](arkts-mdm-bundlemanager-installparam-i.md) | Ӧ�ð���װ��ָ���Ĳ�����Ϣ��<br/> |
| [Resource](arkts-mdm-bundlemanager-resource-i.md) | ��Դ�����Ϣ������Ӧ�ð�����Ӧ��ģ��������Դid��<br/> |
| [SignatureInfo](arkts-mdm-bundlemanager-signatureinfo-i.md) | ����Ӧ�ð���ǩ����Ϣ��<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AppDistributionType](arkts-mdm-bundlemanager-appdistributiontype-e.md) | Ӧ�ó���ǩ��֤��ķַ����͡���ϸ������μ�[ApplicationInfo](../../apis-ability-kit/arkts-apis/arkts-ability-applicationinfo-i.md#ApplicationInfo)��appDistributionType����<br/>��<br/> |
| [BundleInfoGetFlag](arkts-mdm-bundlemanager-bundleinfogetflag-e.md) | ����Ϣ��ȡ��־��ָʾ��Ҫ��ȡ�İ���Ϣ�����ݡ�<br/> |

