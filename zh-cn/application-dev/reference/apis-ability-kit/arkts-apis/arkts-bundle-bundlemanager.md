# @ohos.bundle.bundleManager

��ģ���ṩӦ����Ϣ�Ĳ�ѯ������֧��Ӧ�ð���Ϣ[BundleInfo](bundleManager/BundleInfo)��Ӧ�ó�����Ϣ
[ApplicationInfo](bundleManager/ApplicationInfo)��UIAbility�����Ϣ
[AbilityInfo](bundleManager/AbilityInfo)��ExtensionAbility�����Ϣ
[ExtensionAbilityInfo](bundleManager/ExtensionAbilityInfo:ExtensionAbilityInfo)����Ϣ�Ĳ�ѯ��

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [canOpenLink](arkts-ability-bundlemanager-canopenlink-f.md#canOpenLink-1) | ���ݸ����������ж�Ŀ��Ӧ���Ƿ�ɷ��ʣ������е�scheme��Ҫ��[module.json5�ļ�](../../../../quick-start/module-configuration-file.md)��querySchemes�ֶ�<br/>�����á�<br/> |
| <!--DelRow-->[cleanAllBundleCache](arkts-ability-bundlemanager-cleanallbundlecache-f-sys.md#cleanAllBundleCache-1) | ����ȫ�ֻ��档ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[cleanBundleCacheFiles](arkts-ability-bundlemanager-cleanbundlecachefiles-f-sys.md#cleanBundleCacheFiles-1) | ���ݸ�����bundleName����BundleCache��ʹ��callback�첽�ص���<br/><br/>���÷�����������������ʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[cleanBundleCacheFiles](arkts-ability-bundlemanager-cleanbundlecachefiles-f-sys.md#cleanBundleCacheFiles-2) | ���ݸ�����bundleName����BundleCache��ʹ��Promise�첽�ص���<br/><br/>���÷�����������������ʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[cleanBundleCacheFiles](arkts-ability-bundlemanager-cleanbundlecachefiles-f-sys.md#cleanBundleCacheFiles-3) | ���ݸ�����bundleName��appIndex����BundleCache��ʹ��Promise�첽�ص���<br/><br/>���÷�����������������ʱ����ҪȨ�ޡ�<br/> |
| [cleanBundleCacheFilesForSelf](arkts-ability-bundlemanager-cleanbundlecachefilesforself-f.md#cleanBundleCacheFilesForSelf-1) | ����Ӧ�������Ļ��档ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[deleteAbc](arkts-ability-bundlemanager-deleteabc-f-sys.md#deleteAbc-1) | ���ݸ�����abcPathɾ��.abc�ļ���ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[disableDynamicIcon](arkts-ability-bundlemanager-disabledynamicicon-f-sys.md#disableDynamicIcon-1) | ���ݸ�����bundleName���ö�̬ͼ�ꡣʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[disableDynamicIcon](arkts-ability-bundlemanager-disabledynamicicon-f-sys.md#disableDynamicIcon-2) | ���ݸ�����bundleName��option���ö�̬ͼ�ꡣʹ��Promise�첽�ص���<br/><br/>���õ�ǰ�û��µĶ�̬ͼ����Ϣʱ��Ҫ����Ȩ��ohos.permission.ACCESS_DYNAMIC_ICON��<br/><br/>���������û��µĶ�̬ͼ����Ϣʱ��Ҫ����Ȩ��ohos.permission.ACCESS_DYNAMIC_ICON �� ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS��<br/> |
| <!--DelRow-->[enableDynamicIcon](arkts-ability-bundlemanager-enabledynamicicon-f-sys.md#enableDynamicIcon-1) | ���ݸ�����bundleName��moduleNameʹ�ܶ�̬ͼ�ꡣʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[enableDynamicIcon](arkts-ability-bundlemanager-enabledynamicicon-f-sys.md#enableDynamicIcon-2) | ���ݸ�����bundleName��moduleName��optionʹ�ܶ�̬ͼ�ꡣʹ��Promise�첽�ص���<br/><br/>ʹ�ܵ�ǰ�û��µĶ�̬ͼ����Ϣʱ��Ҫ����Ȩ��ohos.permission.ACCESS_DYNAMIC_ICON��<br/><br/>ʹ�������û��µĶ�̬ͼ����Ϣʱ��Ҫ����Ȩ��ohos.permission.ACCESS_DYNAMIC_ICON �� ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS��<br/> |
| <!--DelRow-->[getAbilityIcon](arkts-ability-bundlemanager-getabilityicon-f-sys.md#getAbilityIcon-1) | ͨ��bundleName��moduleName��abilityName��ȡ��ӦIcon��[PixelMap](@ohos.multimedia.image:image)��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷���Ϣʱ����ҪȨ�ޡ�<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 9��ʼ֧�֣���API version 10��ʼ����������ʹ��<br/>&gt; [getMediaContent](@ohos.resourceManager:resourceManager.ResourceManager.getMediaContent(resId: long, callback: _AsyncCallback&lt;Uint8Array&gt;))<br/>&gt; �����<br/> |
| <!--DelRow-->[getAbilityIcon](arkts-ability-bundlemanager-getabilityicon-f-sys.md#getAbilityIcon-2) | ͨ��bundleName��moduleName��abilityName��ȡ��ӦIcon��[PixelMap](@ohos.multimedia.image:image)��ʹ��Promise�첽�ص���<br/><br/>��ȡ���÷���Ϣʱ����ҪȨ�ޡ�<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 9��ʼ֧�֣���API version 10��ʼ����������ʹ��<br/>&gt; [getMediaContent](@ohos.resourceManager:resourceManager.ResourceManager.getMediaContent(resId: long, callback: _AsyncCallback&lt;Uint8Array&gt;))<br/>&gt; �����<br/> |
| [getAbilityInfo](arkts-ability-bundlemanager-getabilityinfo-f.md#getAbilityInfo-1) | ��ȡָ����Դ��ʶ���������Ϣ��־��Ӧ��Ability��Ϣ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getAbilityLabel](arkts-ability-bundlemanager-getabilitylabel-f-sys.md#getAbilityLabel-1) | ��ȡָ��bundleName��moduleName��abilityName��label��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getAbilityLabel](arkts-ability-bundlemanager-getabilitylabel-f-sys.md#getAbilityLabel-2) | ��ȡָ��bundleName��moduleName��abilityName��label��ʹ��Promise�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getAbilityLabelSync](arkts-ability-bundlemanager-getabilitylabelsync-f-sys.md#getAbilityLabelSync-1) | ��ͬ���ķ�����ȡָ��bundleName��moduleName��abilityName��label��<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getAdditionalInfo](arkts-ability-bundlemanager-getadditionalinfo-f-sys.md#getAdditionalInfo-1) | ��ͬ���ӿڲ�ѯָ��bundleName�Ķ�����Ϣ���÷���ֵ���ڵ���install�ӿ�ʱ�����[InstallParam](arkts-ability-installer-installparam-i-sys.md#InstallParam)�е�<br/>additionalInfo�ֶΡ�<br/> |
| <!--DelRow-->[getAllAppCloneBundleInfo](arkts-ability-bundlemanager-getallappclonebundleinfo-f-sys.md#getAllAppCloneBundleInfo-1) | ����bundleName��[bundleFlags](arkts-ability-bundlemanager-bundleflag-e.md#BundleFlag)�Լ��û�ID��ѯ��Ӧ�úͷ���Ӧ�õ�BundleInfo�б���<br/>ʹ��Promise�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getAllAppProvisionInfo](arkts-ability-bundlemanager-getallappprovisioninfo-f-sys.md#getAllAppProvisionInfo-1) | ����userId��ȡָ���û�������Ӧ�õ�[Provision](bundleManager/AppProvisionInfo)�����ļ���Ϣ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getAllApplicationInfo](arkts-ability-bundlemanager-getallapplicationinfo-f-sys.md#getAllApplicationInfo-1) | ���ݸ�����appFlags��ȡϵͳ�����е�ApplicationInfo��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getAllApplicationInfo](arkts-ability-bundlemanager-getallapplicationinfo-f-sys.md#getAllApplicationInfo-2) | ���ݸ�����appFlags��userId��ȡϵͳ�����е�ApplicationInfo��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getAllApplicationInfo](arkts-ability-bundlemanager-getallapplicationinfo-f-sys.md#getAllApplicationInfo-3) | ���ݸ�����appFlags��userId��ȡϵͳ�����е�ApplicationInfo��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getAllBundleCacheSize](arkts-ability-bundlemanager-getallbundlecachesize-f-sys.md#getAllBundleCacheSize-1) | ��ȡȫ�ֻ����С����λ���ֽڡ�ʹ��Promise�첽�ص���<br/><br/>�г�������ʱ��Ӧ�õĻ��桢������[Ӧ������ָ��](../../../../../device-dev/subsystems/subsys-app-privilege-config-guide.md)�������á�<br/>AllowAppDataNotCleared����Ȩ��Ӧ�õĻ��棬�޷�����ȡ��<br/> |
| <!--DelRow-->[getAllBundleInfo](arkts-ability-bundlemanager-getallbundleinfo-f-sys.md#getAllBundleInfo-1) | ���ݸ�����bundleFlags��ȡϵͳ�����е�BundleInfo��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getAllBundleInfo](arkts-ability-bundlemanager-getallbundleinfo-f-sys.md#getAllBundleInfo-2) | ���ݸ�����bundleFlags��userId��ȡϵͳ�����е�BundleInfo��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getAllBundleInfo](arkts-ability-bundlemanager-getallbundleinfo-f-sys.md#getAllBundleInfo-3) | ���ݸ�����bundleFlags��userId��ȡϵͳ�����е�BundleInfo��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getAllBundleInfoByDeveloperId](arkts-ability-bundlemanager-getallbundleinfobydeveloperid-f-sys.md#getAllBundleInfoByDeveloperId-1) | ���ݸ�����developerId��ȡ��ǰ�û��µİ���Ϣ�б���<br/> |
| <!--DelRow-->[getAllBundleInstallInfo](arkts-ability-bundlemanager-getallbundleinstallinfo-f-sys.md#getAllBundleInstallInfo-1) | ��ȡϵͳ������Ӧ�õ���չ��װ��Ϣ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getAllDynamicIconInfo](arkts-ability-bundlemanager-getalldynamiciconinfo-f-sys.md#getAllDynamicIconInfo-1) | ��ѯָ���û�������Ӧ�ú����з����Ķ�̬ͼ����Ϣ��ʹ��Promise�첽�ص���<br/><br/>��ѯ��ǰ�û�������Ӧ�ú����з����Ķ�̬ͼ����Ϣʱ��Ҫ����Ȩ��ohos.permission.GET_BUNDLE_INFO_PRIVILEGED��<br/><br/>��ѯ�����û����������û�������Ӧ�ú����з����Ķ�̬ͼ����Ϣʱ��Ҫ����Ȩ��ohos.permission.GET_BUNDLE_INFO_PRIVILEGED �� <br/>ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS��<br/> |
| <!--DelRow-->[getAllNewPreinstalledApplicationInfo](arkts-ability-bundlemanager-getallnewpreinstalledapplicationinfo-f-sys.md#getAllNewPreinstalledApplicationInfo-1) | ��ȡ�豸OTA�����ڼ䵱ǰ�û�������������Ԥ��Ӧ����Ϣ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getAllPluginInfo](arkts-ability-bundlemanager-getallplugininfo-f-sys.md#getAllPluginInfo-1) | ���ݸ�����hostBundleName��userId��ȡ���е�PluginBundleInfo��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getAllPreinstalledApplicationInfo](arkts-ability-bundlemanager-getallpreinstalledapplicationinfo-f-sys.md#getAllPreinstalledApplicationInfo-1) | ��ȡ����Ԥ��Ӧ����Ϣ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getAllSharedBundleInfo](arkts-ability-bundlemanager-getallsharedbundleinfo-f-sys.md#getAllSharedBundleInfo-1) | ��ȡ���еĹ�������Ϣ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getAllSharedBundleInfo](arkts-ability-bundlemanager-getallsharedbundleinfo-f-sys.md#getAllSharedBundleInfo-2) | ��ȡ���еĹ�������Ϣ��ʹ��Promise�첽�ص���<br/> |
| [getAlternateIcons](arkts-ability-bundlemanager-getalternateicons-f.md#getAlternateIcons-1) | ��ѯ��ǰӦ����app.json5��[alternateIcons��ǩ](../../../../quick-start/app-configuration-file.md#alternateicons��ǩ)���õı���ͼ����Ϣ��ʹ��<br/>Promise�첽�ص���<br/> |
| <!--DelRow-->[getAppCloneBundleInfo](arkts-ability-bundlemanager-getappclonebundleinfo-f-sys.md#getAppCloneBundleInfo-1) | ����bundleName������������[bundleFlags](arkts-ability-bundlemanager-bundleflag-e.md#BundleFlag)�Լ��û�ID��ѯ��Ӧ�û����Ӧ�õ�<br/>BundleInfo��ʹ��Promise�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| [getAppCloneIdentity](arkts-ability-bundlemanager-getappcloneidentity-f.md#getAppCloneIdentity-1) | ����uid��ѯ����Ӧ�õİ����ͷ���������ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getAppCloneIdentityBySandboxDataDir](arkts-ability-bundlemanager-getappcloneidentitybysandboxdatadir-f-sys.md#getAppCloneIdentityBySandboxDataDir-1) | ����Ӧ�õ�ɳ��Ŀ¼���ƻ�ȡӦ�õ�������Ϣ������Ӧ�ð����ͷ���������Ϣ��<br/> |
| <!--DelRow-->[getAppProvisionInfo](arkts-ability-bundlemanager-getappprovisioninfo-f-sys.md#getAppProvisionInfo-1) | ��ȡָ��bundleName��provision�����ļ���Ϣ��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getAppProvisionInfo](arkts-ability-bundlemanager-getappprovisioninfo-f-sys.md#getAppProvisionInfo-2) | ��ȡָ��bundleName��userId��provision�����ļ���Ϣ��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getAppProvisionInfo](arkts-ability-bundlemanager-getappprovisioninfo-f-sys.md#getAppProvisionInfo-3) | ����bundleName��userId��ȡӦ�õ�provision�����ļ���Ϣ��ʹ��Promise�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getAppProvisionInfoSync](arkts-ability-bundlemanager-getappprovisioninfosync-f-sys.md#getAppProvisionInfoSync-1) | ��ͬ����������bundleName��userId��ȡӦ�õ�provision�����ļ���Ϣ�����ؽ����<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getApplicationInfo](arkts-ability-bundlemanager-getapplicationinfo-f-sys.md#getApplicationInfo-1) | ���ݸ�����bundleName��appFlags��ȡApplicationInfo��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getApplicationInfo](arkts-ability-bundlemanager-getapplicationinfo-f-sys.md#getApplicationInfo-2) | ���ݸ�����bundleName��appFlags��userId��ȡApplicationInfo��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getApplicationInfo](arkts-ability-bundlemanager-getapplicationinfo-f-sys.md#getApplicationInfo-3) | ���ݸ�����bundleName��appFlags��userId��ȡApplicationInfo��ʹ��Promise�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getApplicationInfoSync](arkts-ability-bundlemanager-getapplicationinfosync-f-sys.md#getApplicationInfoSync-1) | ��ͬ���������ݸ�����bundleName��applicationFlags��userId��ȡApplicationInfo��<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getApplicationInfoSync](arkts-ability-bundlemanager-getapplicationinfosync-f-sys.md#getApplicationInfoSync-2) | ��ͬ���������ݸ�����bundleName��applicationFlags��ȡApplicationInfo��<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| [getApplicationLabel](arkts-ability-bundlemanager-getapplicationlabel-f.md#getApplicationLabel-1) | ��ȡָ�������ͷ���������Ӧ�����ơ�ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getBundleArchiveInfo](arkts-ability-bundlemanager-getbundlearchiveinfo-f-sys.md#getBundleArchiveInfo-1) | ���ݸ�����hapFilePath��bundleFlags��ȡBundleInfo��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getBundleArchiveInfo](arkts-ability-bundlemanager-getbundlearchiveinfo-f-sys.md#getBundleArchiveInfo-2) | ���ݸ�����hapFilePath��bundleFlags��ȡBundleInfo��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getBundleArchiveInfoSync](arkts-ability-bundlemanager-getbundlearchiveinfosync-f-sys.md#getBundleArchiveInfoSync-1) | ��ͬ���������ݸ�����hapFilePath��bundleFlags��ȡBundleInfo����<br/> |
| [getBundleInfo](arkts-ability-bundlemanager-getbundleinfo-f.md#getBundleInfo-1) | ���ݸ�����bundleName��bundleFlags��ȡBundleInfo��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| [getBundleInfo](arkts-ability-bundlemanager-getbundleinfo-f.md#getBundleInfo-2) | ���ݸ�����bundleName��bundleFlags��userId��ȡ[BundleInfo](bundleManager/BundleInfo)��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷�������Ϣʱ����ҪȨ�ޡ�<br/> |
| [getBundleInfo](arkts-ability-bundlemanager-getbundleinfo-f.md#getBundleInfo-3) | ���ݸ�����bundleName��bundleFlags��userId��ȡBundleInfo��ʹ��Promise�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-1) | ���ݸ�����bundleFlags��ȡ��ǰӦ�õ�BundleInfo��ʹ��Promise�첽�ص���<br/> |
| [getBundleInfoForSelf](arkts-ability-bundlemanager-getbundleinfoforself-f.md#getBundleInfoForSelf-2) | ���ݸ�����bundleFlags��ȡ��ǰӦ�õ�BundleInfo��ʹ��callback�첽�ص���<br/> |
| [getBundleInfoForSelfSync](arkts-ability-bundlemanager-getbundleinfoforselfsync-f.md#getBundleInfoForSelfSync-1) | ��ͬ���������ݸ�����bundleFlags��ȡ��ǰӦ�õ�BundleInfo��<br/> |
| [getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getBundleInfoSync-1) | ��ͬ���������ݸ�����bundleName��bundleFlags��userId��ȡBundleInfo��<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| [getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getBundleInfoSync-2) | ��ͬ���������ݸ�����bundleName��bundleFlags��ȡ���÷������û��µ�BundleInfo��<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getBundleInstallStatus](arkts-ability-bundlemanager-getbundleinstallstatus-f-sys.md#getBundleInstallStatus-1) | ��ѯ��ǰ�û���ָ��Ӧ�õİ�װ״̬��<br/> |
| [getBundleNameByUid](arkts-ability-bundlemanager-getbundlenamebyuid-f.md#getBundleNameByUid-1) | ���ݸ�����uid��ȡ��ӦӦ�õ�bundleName��ʹ��callback�첽�ص���<br/> |
| [getBundleNameByUid](arkts-ability-bundlemanager-getbundlenamebyuid-f.md#getBundleNameByUid-2) | ���ݸ�����uid��ȡ��ӦӦ�õ�bundleName��ʹ��Promise�첽�ص���<br/> |
| [getBundleNameByUidSync](arkts-ability-bundlemanager-getbundlenamebyuidsync-f.md#getBundleNameByUidSync-1) | ��ͬ���������ݸ�����uid��ȡ��ӦӦ�õ�bundleName��<br/> |
| <!--DelRow-->[getDeveloperIds](arkts-ability-bundlemanager-getdeveloperids-f-sys.md#getDeveloperIds-1) | ���ݸ�����Ӧ��[appDistributionType](arkts-ability-bundlemanager-appdistributiontype-e-sys.md#AppDistributionType)��ȡ��ǰ�û��µ����п�����ID�б���<br/> |
| <!--DelRow-->[getDynamicIcon](arkts-ability-bundlemanager-getdynamicicon-f-sys.md#getDynamicIcon-1) | ���ݸ�����bundleName��ö�̬ͼ���Ӧ��moduleName��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getDynamicIconInfo](arkts-ability-bundlemanager-getdynamiciconinfo-f-sys.md#getDynamicIconInfo-1) | ����ָ����bundleName��ȡ�����û������з����µĶ�̬ͼ����Ϣ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getExtResource](arkts-ability-bundlemanager-getextresource-f-sys.md#getExtResource-1) | ���ݸ�����bundleName�����չ��Դ��Ӧ��moduleNames��ʹ��Promise�첽�ص���<br/> |
| [getInstalledBundleList](arkts-ability-bundlemanager-getinstalledbundlelist-f.md#getInstalledBundleList-1) | ���ݸ�����bundleFlags��ȡϵͳ�����е�BundleInfo��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getJsonProfile](arkts-ability-bundlemanager-getjsonprofile-f-sys.md#getJsonProfile-1) | ��ͬ���ķ������ݸ�����profileType��bundleName��moduleName��ѯ��Ӧ�����ļ���JSON�ַ�����<br/><br/>��ȡ���÷��Լ��������ļ�ʱ����ҪȨ�ޡ�<br/> |
| [getLaunchWant](arkts-ability-bundlemanager-getlaunchwant-f.md#getLaunchWant-1) | ��ȡ��Ӧ��[���UIAbility](../../../../quick-start/application-package-glossary.md#uiability)��Want������<br/> |
| <!--DelRow-->[getLaunchWantForBundle](arkts-ability-bundlemanager-getlaunchwantforbundle-f-sys.md#getLaunchWantForBundle-1) | ���ݸ�����bundleName��userId��ȡ��������Ӧ�ó����Want������ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getLaunchWantForBundle](arkts-ability-bundlemanager-getlaunchwantforbundle-f-sys.md#getLaunchWantForBundle-2) | ���ݸ�����bundleName��ȡ��������Ӧ�ó����Want������ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getLaunchWantForBundle](arkts-ability-bundlemanager-getlaunchwantforbundle-f-sys.md#getLaunchWantForBundle-3) | ���ݸ�����bundleName��userId��ȡ��������Ӧ�ó����Want������ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getLaunchWantForBundleSync](arkts-ability-bundlemanager-getlaunchwantforbundlesync-f-sys.md#getLaunchWantForBundleSync-1) | ���ݸ����İ������û�ID����ȡ��������Ӧ�ó����Want������<br/> |
| <!--DelRow-->[getPermissionDef](arkts-ability-bundlemanager-getpermissiondef-f-sys.md#getPermissionDef-1) | ���ݸ�����permissionName��ȡȨ�޶���ṹ��PermissionDef��Ϣ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getPermissionDef](arkts-ability-bundlemanager-getpermissiondef-f-sys.md#getPermissionDef-2) | ���ݸ�����permissionName��ȡȨ�޶���ṹ��PermissionDef��Ϣ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getPermissionDefSync](arkts-ability-bundlemanager-getpermissiondefsync-f-sys.md#getPermissionDefSync-1) | ��ͬ���������ݸ�����permissionName��ȡȨ�޶���ṹ��PermissionDef��Ϣ��<br/> |
| [getPluginBundlePathForSelf](arkts-ability-bundlemanager-getpluginbundlepathforself-f.md#getPluginBundlePathForSelf-1) | ��ȡָ������ڵ�ǰ[Ӧ��ɳ��](../../../../file-management/app-sandbox-directory.md)�ڵİ�װ·����<br/> |
| [getProfileByAbility](arkts-ability-bundlemanager-getprofilebyability-f.md#getProfileByAbility-1) | ���ݸ�����moduleName��abilityName��metadataName��module.json5��<br/>[abilities��ǩ](../../../../quick-start/module-configuration-file.md#abilities��ǩ)�µ�metadata��ǩ��name����ȡ������Ӧ�����ļ���json��ʽ�ַ���<br/>��ʹ��callback�첽�ص���<br/><br/>&gt; ˵����<br/>&gt; &gt; ��������ļ���Ϣ��������Դ���ø�ʽ���򷵻�ֵ��������Դ���ø�ʽ������ $string:res_id���������߿���ͨ��[��Դ����](../../apis-localization-kit/arkts-apis/arkts-resourcemanager.md#resourceManager)����<br/>&gt; �ؽӿڣ�����ȡ���õ���Դ��<br/> |
| [getProfileByAbility](arkts-ability-bundlemanager-getprofilebyability-f.md#getProfileByAbility-2) | ���ݸ�����moduleName��abilityName��metadataName��module.json5��<br/>[abilities��ǩ](../../../../quick-start/module-configuration-file.md#abilities��ǩ)�µ�metadata��ǩ��name����ȡ������Ӧ�����ļ���json��ʽ�ַ���<br/>��ʹ��Promise�첽�ص���<br/><br/>&gt; ˵����<br/>&gt; &gt; ��������ļ���Ϣ��������Դ���ø�ʽ���򷵻�ֵ��������Դ���ø�ʽ������ $string:res_id���������߿���ͨ��[��Դ����](../../apis-localization-kit/arkts-apis/arkts-resourcemanager.md#resourceManager)����<br/>&gt; �ؽӿڣ�����ȡ���õ���Դ��<br/> |
| [getProfileByAbilitySync](arkts-ability-bundlemanager-getprofilebyabilitysync-f.md#getProfileByAbilitySync-1) | ��ͬ���������ݸ�����moduleName��abilityName��metadataName��module.json5��<br/>[metadata��ǩ](../../../../quick-start/module-configuration-file.md#metadata��ǩ)�µ�name����ȡ������Ӧ�����ļ���json��ʽ�ַ��������ض���Ϊstring��<br/>�顣<br/> |
| [getProfileByExtensionAbility](arkts-ability-bundlemanager-getprofilebyextensionability-f.md#getProfileByExtensionAbility-1) | ���ݸ�����moduleName��extensionAbilityName��metadataName��module.json5��<br/>[metadata��ǩ](../../../../quick-start/module-configuration-file.md#metadata��ǩ)�µ�name����ȡ������Ӧ�����ļ���json��ʽ�ַ�����ʹ��callback�첽<br/>�ص���<br/> |
| [getProfileByExtensionAbility](arkts-ability-bundlemanager-getprofilebyextensionability-f.md#getProfileByExtensionAbility-2) | ���ݸ�����moduleName��extensionAbilityName��metadataName��module.json5��<br/>[metadata��ǩ](../../../../quick-start/module-configuration-file.md#metadata��ǩ)�µ�name����ȡ������Ӧ�����ļ���json��ʽ�ַ�����ʹ��Promise�첽��<br/>����<br/> |
| [getProfileByExtensionAbilitySync](arkts-ability-bundlemanager-getprofilebyextensionabilitysync-f.md#getProfileByExtensionAbilitySync-1) | ��ͬ���������ݸ�����moduleName��extensionAbilityName��metadataName��module.json5��<br/>[metadata��ǩ](../../../../quick-start/module-configuration-file.md#metadata��ǩ)�µ�name����ȡ������Ӧ�����ļ���json��ʽ�ַ��������ض���Ϊstring��<br/>�顣<br/> |
| <!--DelRow-->[getRecoverableApplicationInfo](arkts-ability-bundlemanager-getrecoverableapplicationinfo-f-sys.md#getRecoverableApplicationInfo-1) | ��ȡ���пɻָ���Ԥ��Ӧ����Ϣ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getRecoverableApplicationInfo](arkts-ability-bundlemanager-getrecoverableapplicationinfo-f-sys.md#getRecoverableApplicationInfo-2) | ��ȡ���пɻָ���Ԥ��Ӧ����Ϣ��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getSandboxDataDir](arkts-ability-bundlemanager-getsandboxdatadir-f-sys.md#getSandboxDataDir-1) | ����Ӧ�ð����ͷ���������ȡ��Ӧ��ɳ��Ŀ¼��<br/> |
| <!--DelRow-->[getSharedBundleInfo](arkts-ability-bundlemanager-getsharedbundleinfo-f-sys.md#getSharedBundleInfo-1) | ��ȡָ���Ĺ�������Ϣ��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getSharedBundleInfo](arkts-ability-bundlemanager-getsharedbundleinfo-f-sys.md#getSharedBundleInfo-2) | ��ȡָ���Ĺ�������Ϣ��ʹ��Promise�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| [getSignatureInfo](arkts-ability-bundlemanager-getsignatureinfo-f.md#getSignatureInfo-1) | ���ݸ�����uid��ȡ��ӦӦ�õ�[ǩ����Ϣ](bundleManager/BundleInfo:SignatureInfo)��<br/> |
| <!--DelRow-->[getSpecifiedDistributionType](arkts-ability-bundlemanager-getspecifieddistributiontype-f-sys.md#getSpecifiedDistributionType-1) | ��ͬ���ķ�����ѯָ��bundleName��[HarmonyAppProvision�����ļ�˵��](../../../../security/app-provision-structure.md)���÷���ֵ���ڵ���install�ӿ�ʱ��<br/>���[InstallParam](arkts-ability-installer-installparam-i-sys.md#InstallParam)�е�specifiedDistributionType�ֶΡ�<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[isAbilityEnabled](arkts-ability-bundlemanager-isabilityenabled-f-sys.md#isAbilityEnabled-1) | ��ȡӦ�û�ָ������Ӧ������Ľ��û�ʹ��״̬��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[isAbilityEnabled](arkts-ability-bundlemanager-isabilityenabled-f-sys.md#isAbilityEnabled-2) | ��ȡָ������Ľ��û�ʹ��״̬��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[isAbilityEnabled](arkts-ability-bundlemanager-isabilityenabled-f-sys.md#isAbilityEnabled-3) | ��ȡָ������Ľ��û�ʹ��״̬��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[isAbilityEnabledSync](arkts-ability-bundlemanager-isabilityenabledsync-f-sys.md#isAbilityEnabledSync-1) | ��ͬ��������ȡָ������Ľ��û�ʹ��״̬��<br/> |
| <!--DelRow-->[isApplicationDisableForbidden](arkts-ability-bundlemanager-isapplicationdisableforbidden-f-sys.md#isApplicationDisableForbidden-1) | ��ͬ��������ѯָ���û���ָ��Ӧ�û����Ӧ���Ƿ����ý�ֹͣ�á�<br/> |
| <!--DelRow-->[isApplicationEnabled](arkts-ability-bundlemanager-isapplicationenabled-f-sys.md#isApplicationEnabled-1) | ��ȡָ��Ӧ�û����Ӧ�õĽ��û�ʹ��״̬��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[isApplicationEnabled](arkts-ability-bundlemanager-isapplicationenabled-f-sys.md#isApplicationEnabled-2) | ��ȡָ��Ӧ�õĽ��û�ʹ��״̬��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[isApplicationEnabled](arkts-ability-bundlemanager-isapplicationenabled-f-sys.md#isApplicationEnabled-3) | ��ȡָ��Ӧ�õĽ��û�ʹ��״̬��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[isApplicationEnabledSync](arkts-ability-bundlemanager-isapplicationenabledsync-f-sys.md#isApplicationEnabledSync-1) | ��ͬ��������ȡָ��Ӧ�õĽ��û�ʹ��״̬��<br/> |
| <!--DelRow-->[migrateData](arkts-ability-bundlemanager-migratedata-f-sys.md#migrateData-1) | �����ļ������ļ���Դ·��������Ŀ��·����ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[queryAbilityInfo](arkts-ability-bundlemanager-queryabilityinfo-f-sys.md#queryAbilityInfo-1) | ���ݸ�����want��abilityFlags��ȡһ������AbilityInfo��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[queryAbilityInfo](arkts-ability-bundlemanager-queryabilityinfo-f-sys.md#queryAbilityInfo-2) | ���ݸ�����want��abilityFlags��userId��ȡ���AbilityInfo��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[queryAbilityInfo](arkts-ability-bundlemanager-queryabilityinfo-f-sys.md#queryAbilityInfo-3) | ���ݸ�����want��abilityFlags��userId��ȡһ������AbilityInfo��ʹ��Promise�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[queryAbilityInfo](arkts-ability-bundlemanager-queryabilityinfo-f-sys.md#queryAbilityInfo-4) | ���ݸ�����want�б���abilityFlags��userId��ȡһ������AbilityInfo��ʹ��Promise�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[queryAbilityInfoSync](arkts-ability-bundlemanager-queryabilityinfosync-f-sys.md#queryAbilityInfoSync-1) | ��ͬ���������ݸ�����want��abilityFlags��userId��ȡһ������AbilityInfo��<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[queryExtensionAbilityInfo](arkts-ability-bundlemanager-queryextensionabilityinfo-f-sys.md#queryExtensionAbilityInfo-1) | ���ݸ�����want��extensionAbilityType��extensionAbilityFlags��ȡһ������ExtensionAbilityInfo��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[queryExtensionAbilityInfo](arkts-ability-bundlemanager-queryextensionabilityinfo-f-sys.md#queryExtensionAbilityInfo-2) | ���ݸ�����want��extensionAbilityType��extensionAbilityFlags��userId��ȡһ������ExtensionAbilityInfo��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[queryExtensionAbilityInfo](arkts-ability-bundlemanager-queryextensionabilityinfo-f-sys.md#queryExtensionAbilityInfo-3) | ���ݸ�����want��extensionAbilityType��extensionAbilityFlags��userId��ȡExtensionAbilityInfo��ʹ��Promise�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[queryExtensionAbilityInfoSync](arkts-ability-bundlemanager-queryextensionabilityinfosync-f-sys.md#queryExtensionAbilityInfoSync-1) | ��ͬ���������ݸ�����want��extensionAbilityType��extensionAbilityFlags��userId��ȡExtensionAbilityInfo��<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[queryExtensionAbilityInfoSync](arkts-ability-bundlemanager-queryextensionabilityinfosync-f-sys.md#queryExtensionAbilityInfoSync-2) | ���ݸ�����want��extensionAbilityType��extensionAbilityFlags��userId��ȡExtensionAbilityInfo��ʹ��ͬ����ʽ���ؽ����<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[queryExtensionAbilityInfoSync](arkts-ability-bundlemanager-queryextensionabilityinfosync-f-sys.md#queryExtensionAbilityInfoSync-3) | ���ݸ�����extensionAbilityType��extensionAbilityFlags��userId��ȡExtensionAbilityInfo��<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[recoverBackupBundleData](arkts-ability-bundlemanager-recoverbackupbundledata-f-sys.md#recoverBackupBundleData-1) | �ָ�ָ���û���ָ��Ӧ�û����Ӧ�õı������ݡ�ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[removeBackupBundleData](arkts-ability-bundlemanager-removebackupbundledata-f-sys.md#removeBackupBundleData-1) | ɾ��ָ���û���ָ��Ӧ�û����Ӧ�õı������ݡ�ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[setAbilityEnabled](arkts-ability-bundlemanager-setabilityenabled-f-sys.md#setAbilityEnabled-1) | ����ָ��Ӧ�û����Ӧ������Ľ��û�ʹ��״̬��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[setAbilityEnabled](arkts-ability-bundlemanager-setabilityenabled-f-sys.md#setAbilityEnabled-2) | ����ָ������Ľ��û�ʹ��״̬��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[setAbilityEnabled](arkts-ability-bundlemanager-setabilityenabled-f-sys.md#setAbilityEnabled-3) | ����ָ������Ľ��û�ʹ��״̬��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[setAbilityEnabledSync](arkts-ability-bundlemanager-setabilityenabledsync-f-sys.md#setAbilityEnabledSync-1) | ��ͬ����������ָ������Ľ��û�ʹ��״̬��<br/> |
| <!--DelRow-->[setAbilityFileTypesForSelf](arkts-ability-bundlemanager-setabilityfiletypesforself-f-sys.md#setAbilityFileTypesForSelf-1) | ���õ�ǰӦ��֧�ִ򿪵��ļ����͡�<br/> |
| <!--DelRow-->[setAdditionalInfo](arkts-ability-bundlemanager-setadditionalinfo-f-sys.md#setAdditionalInfo-1) | ����ָ��Ӧ�õĶ�����Ϣ���˽ӿڽ���Ӧ���г����á�<br/> |
| [setAlternateIcon](arkts-ability-bundlemanager-setalternateicon-f.md#setAlternateIcon-1) | ���ݸ����ı���ͼ���������õ��÷������ı���ͼ�ꡣʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[setApplicationEnabled](arkts-ability-bundlemanager-setapplicationenabled-f-sys.md#setApplicationEnabled-1) | ����ָ��Ӧ�û����Ӧ�õĽ��û�ʹ��״̬��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[setApplicationEnabled](arkts-ability-bundlemanager-setapplicationenabled-f-sys.md#setApplicationEnabled-2) | ����Ӧ�ó��������û��ǽ��ã��������ڽ���ʱ�Ƿ�ɱ�����̡�<br/> |
| <!--DelRow-->[setApplicationEnabled](arkts-ability-bundlemanager-setapplicationenabled-f-sys.md#setApplicationEnabled-3) | ����ָ��Ӧ�õĽ��û�ʹ��״̬��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[setApplicationEnabled](arkts-ability-bundlemanager-setapplicationenabled-f-sys.md#setApplicationEnabled-4) | ����ָ��Ӧ�õĽ��û�ʹ��״̬��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[setApplicationEnabledSync](arkts-ability-bundlemanager-setapplicationenabledsync-f-sys.md#setApplicationEnabledSync-1) | ��ͬ����������ָ��Ӧ�õĽ��û�ʹ��״̬��<br/> |
| <!--DelRow-->[setApplicationEnabledSync](arkts-ability-bundlemanager-setapplicationenabledsync-f-sys.md#setApplicationEnabledSync-2) | ����Ӧ�ó��������û��ǽ��ã��������ڽ���ʱ�Ƿ�ɱ�����̡�<br/> |
| <!--DelRow-->[switchUninstallState](arkts-ability-bundlemanager-switchuninstallstate-f-sys.md#switchUninstallState-1) | �л�ָ��Ӧ�õĿ�ж��״̬���˽ӿ���EDMӦ�����عܿػ��Ʋ�����Ӱ�졣<br/> |
| <!--DelRow-->[verifyAbc](arkts-ability-bundlemanager-verifyabc-f-sys.md#verifyAbc-1) | ���ݸ�����abcPaths��deleteOriginalFilesУ��.abc�ļ���ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[verifyAbc](arkts-ability-bundlemanager-verifyabc-f-sys.md#verifyAbc-2) | ���ݸ�����abcPaths��deleteOriginalFilesУ��.abc�ļ���ʹ��Promise�첽�ص���<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[AbilityFlag](arkts-ability-bundlemanager-abilityflag-e-sys.md) | Ability�����Ϣ��־��ָʾ��Ҫ��ȡ��Ability�����Ϣ�����ݡ�<br/> |
| [AbilityType](arkts-ability-bundlemanager-abilitytype-e.md) | ��ʶAbility��������͡�<br/> |
| <!--DelRow-->[AppDistributionType](arkts-ability-bundlemanager-appdistributiontype-e-sys.md) | ��ʶӦ��[HarmonyAppProvision�����ļ�˵��](../../../../security/app-provision-structure.md)��<br/> |
| <!--DelRow-->[ApplicationFlag](arkts-ability-bundlemanager-applicationflag-e-sys.md) | Ӧ����Ϣ��־��ָʾ��Ҫ��ȡ��Ӧ����Ϣ�����ݡ�<br/> |
| <!--DelRow-->[ApplicationInfoFlag](arkts-ability-bundlemanager-applicationinfoflag-e-sys.md) | ��ʶӦ�ú��û�֮��ĸ���״̬���͡�<br/> |
| [BundleFlag](arkts-ability-bundlemanager-bundleflag-e.md) | ����Ϣ��־��ָʾ��Ҫ��ȡ�İ���Ϣ�����ݡ�<br/> |
| <!--DelRow-->[BundleFlag](arkts-ability-bundlemanager-bundleflag-e-sys.md) | ����Ϣ��־��ָʾ��Ҫ��ȡ�İ���Ϣ�����ݡ�<br/> |
| <!--DelRow-->[BundleInstallStatus](arkts-ability-bundlemanager-bundleinstallstatus-e-sys.md) | ��ʶӦ�õİ�װ״̬��<br/> |
| [BundleType](arkts-ability-bundlemanager-bundletype-e.md) | ��ʶӦ�õ����͡�<br/> |
| [CompatiblePolicy](arkts-ability-bundlemanager-compatiblepolicy-e.md) | ��ʶ��̬������İ汾�������͡�<br/> |
| [DisplayOrientation](arkts-ability-bundlemanager-displayorientation-e.md) | ��ʶ��Ability����ʾģʽ����������FAģ�͵�[PageAbility](../../../../application-models/pageability-overview.md)��<br/><br/>&lt;!--Table: 40%; 10%; 50%--&gt;<br/> |
| <!--DelRow-->[ExtensionAbilityFlag](arkts-ability-bundlemanager-extensionabilityflag-e-sys.md) | ��չ�����Ϣ��־��ָʾ��Ҫ��ȡ����չ�����Ϣ�����ݡ�<br/> |
| [ExtensionAbilityType](arkts-ability-bundlemanager-extensionabilitytype-e.md) | ��չ��������͡�<br/><br/>&lt;!--Table: 30%; 10%; 60%--&gt;<br/><br/>&lt;!--RP2--&gt;&lt;!--RP2End--&gt;<br/> |
| [LaunchType](arkts-ability-bundlemanager-launchtype-e.md) | ��ʶ�����[����ģʽ](../../../../application-models/uiability-launch-type.md)��<br/> |
| [ModuleType](arkts-ability-bundlemanager-moduletype-e.md) | ��ʶģ�����͡�<br/> |
| [MultiAppModeType](arkts-ability-bundlemanager-multiappmodetype-e.md) | ��ʶӦ�ö࿪��ģʽ���͡�<br/> |
| [PermissionGrantState](arkts-ability-bundlemanager-permissiongrantstate-e.md) | Ȩ������״̬��<br/> |
| <!--DelRow-->[ProfileType](arkts-ability-bundlemanager-profiletype-e-sys.md) | ��ʶ�����ļ����͡�<br/> |
| [SupportWindowMode](arkts-ability-bundlemanager-supportwindowmode-e.md) | ��ʶ�������֧�ֵĴ���ģʽ��<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AbilityInfo](arkts-ability-bundlemanager-abilityinfo-t.md) | Ability��Ϣ��<br/> |
| [AlternateIconInfo](arkts-ability-bundlemanager-alternateiconinfo-t.md) | Ӧ�ñ���ͼ����Ϣ��<br/> |
| [AppCloneIdentity](arkts-ability-bundlemanager-appcloneidentity-t.md) | ����Ӧ�ð���������Ϣ��<br/> |
| <!--DelRow-->[AppProvisionInfo](arkts-ability-bundlemanager-appprovisioninfo-t-sys.md) | Ӧ��[HarmonyAppProvision�����ļ�](../../../../security/app-provision-structure.md)�е���Ϣ��<br/> |
| [ApplicationInfo](arkts-ability-bundlemanager-applicationinfo-t.md) | Ӧ�ó�����Ϣ��<br/> |
| [BundleInfo](arkts-ability-bundlemanager-bundleinfo-t.md) | Ӧ�ð���Ϣ��<br/> |
| <!--DelRow-->[BundleOptions](arkts-ability-bundlemanager-bundleoptions-t-sys.md) | Ӧ�ð�ѡ��������û��ѯӦ�������Ϣ��<br/> |
| [DataItem](arkts-ability-bundlemanager-dataitem-t.md) | ģ�����õ�·�ɱ��е��Զ������ݡ�<br/> |
| [Dependency](arkts-ability-bundlemanager-dependency-t.md) | ģ���������Ķ�̬��������Ϣ��<br/> |
| <!--DelRow-->[DynamicIconInfo](arkts-ability-bundlemanager-dynamiciconinfo-t-sys.md) | Ӧ�õĶ�̬ͼ����Ϣ��<br/> |
| [ElementName](arkts-ability-bundlemanager-elementname-t.md) | ElementName��Ϣ��<br/> |
| [ExtensionAbilityInfo](arkts-ability-bundlemanager-extensionabilityinfo-t.md) | ExtensionAbility��Ϣ��<br/> |
| [HapModuleInfo](arkts-ability-bundlemanager-hapmoduleinfo-t.md) | ģ����Ϣ��<br/> |
| [Metadata](arkts-ability-bundlemanager-metadata-t.md) | Ԫ������Ϣ��<br/> |
| [ModuleMetadata](arkts-ability-bundlemanager-modulemetadata-t.md) | ģ���Ԫ������Ϣ��<br/> |
| <!--DelRow-->[PermissionDef](arkts-ability-bundlemanager-permissiondef-t-sys.md) | [module.json5�����ļ�](../../../../quick-start/module-configuration-file.md)�ж����Ȩ����ϸ��Ϣ��<br/> |
| <!--DelRow-->[PluginBundleInfo](arkts-ability-bundlemanager-pluginbundleinfo-t-sys.md) | �����Ϣ��<br/> |
| <!--DelRow-->[PluginModuleInfo](arkts-ability-bundlemanager-pluginmoduleinfo-t-sys.md) | �����ģ����Ϣ��<br/> |
| <!--DelRow-->[PreinstalledApplicationInfo](arkts-ability-bundlemanager-preinstalledapplicationinfo-t-sys.md) | Ԥ��Ӧ����Ϣ��<br/> |
| [PreloadItem](arkts-ability-bundlemanager-preloaditem-t.md) | ԭ�ӻ�������ģ���Ԥ����ģ����Ϣ��<br/> |
| <!--DelRow-->[RecoverableApplicationInfo](arkts-ability-bundlemanager-recoverableapplicationinfo-t-sys.md) | Ԥ��Ӧ�ñ�ж�غ���Իָ���Ԥ��Ӧ����Ϣ��<br/> |
| [ReqPermissionDetail](arkts-ability-bundlemanager-reqpermissiondetail-t.md) | Ӧ������ʱ����ϵͳ�����Ȩ�޼��ϵ���ϸ��Ϣ��<br/> |
| [RouterItem](arkts-ability-bundlemanager-routeritem-t.md) | ģ�����õ�·�ɱ���Ϣ��<br/> |
| <!--DelRow-->[SharedBundleInfo](arkts-ability-bundlemanager-sharedbundleinfo-t-sys.md) | ��������Ϣ��<br/> |
| [SignatureInfo](arkts-ability-bundlemanager-signatureinfo-t.md) | Ӧ�ð���ǩ����Ϣ��<br/> |
| [Skill](arkts-ability-bundlemanager-skill-t.md) | skill��Ϣ��<br/> |
| [SkillUrl](arkts-ability-bundlemanager-skillurl-t.md) | SkillUri��Ϣ��<br/> |
| [UsedScene](arkts-ability-bundlemanager-usedscene-t.md) | Ȩ��ʹ�õĳ�����ʱ����<br/> |
| <!--DelRow-->[Validity](arkts-ability-bundlemanager-validity-t-sys.md) | �����ļ��е���Ч�ڡ�<br/> |
| [WindowSize](arkts-ability-bundlemanager-windowsize-t.md) | ���ڳߴ硣<br/> |

