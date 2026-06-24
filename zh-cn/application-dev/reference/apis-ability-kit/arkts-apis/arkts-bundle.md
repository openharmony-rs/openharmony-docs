# @ohos.bundle

��ģ���ṩӦ����Ϣ��ѯ������֧��[����Ϣ](arkts-ability-bundleinfo-depr-i.md#BundleInfo)��[Ӧ����Ϣ](arkts-ability-applicationinfo-depr-i.md#ApplicationInfo)��
[Ability�����Ϣ](arkts-ability-abilityinfo-depr-i.md#AbilityInfo)����Ϣ�Ĳ�ѯ���Լ�Ӧ�ý���״̬�Ĳ�ѯ�����õȡ�

> **˵����**
>
> ��API version 9��ʼ����ģ�鲻��ά��������ʹ��[@ohos.bundle.bundleManager](arkts-bundle-bundlemanager.md#bundleManager)�����

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [bundleManager:bundleManager](arkts-bundle-bundlemanager.md#bundleManager)

**系统能力：** SystemCapability.BundleManager.BundleFramework

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[cleanBundleCacheFiles](arkts-ability-bundle-cleanbundlecachefiles-f-sys.md#cleanBundleCacheFiles-1) | ���ָ��Ӧ�ó���Ļ������ݣ�ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[cleanBundleCacheFiles](arkts-ability-bundle-cleanbundlecachefiles-f-sys.md#cleanBundleCacheFiles-2) | ���ָ��Ӧ�ó���Ļ������ݣ�ʹ��Promise�첽�ص���<br/> |
| [getAbilityIcon](arkts-ability-bundle-getabilityicon-f.md#getAbilityIcon-1) | ͨ��bundleName��abilityName��ȡ��ӦIcon��[PixelMap](@ohos.multimedia.image:image)��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�<br/> |
| [getAbilityIcon](arkts-ability-bundle-getabilityicon-f.md#getAbilityIcon-2) | ͨ��bundleName��abilityName��ȡ��ӦIcon��[PixelMap](@ohos.multimedia.image:image)��ʹ��Promise�첽�ص���<br/><br/>��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�<br/> |
| [getAbilityInfo](arkts-ability-bundle-getabilityinfo-f.md#getAbilityInfo-1) | ͨ��Bundle���ƺ��������ȡAbility�����Ϣ��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�<br/> |
| [getAbilityInfo](arkts-ability-bundle-getabilityinfo-f.md#getAbilityInfo-2) | ͨ��Bundle���ƺ��������ȡAbility�����Ϣ��ʹ��Promise��ʽ�첽�ص���<br/><br/>��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�<br/> |
| [getAbilityLabel](arkts-ability-bundle-getabilitylabel-f.md#getAbilityLabel-1) | ͨ��Bundle���ƺ�Ability�������ȡӦ�����ƣ�ʹ��callback�첽�ص���<br/><br/>��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�<br/> |
| [getAbilityLabel](arkts-ability-bundle-getabilitylabel-f.md#getAbilityLabel-2) | ͨ��Bundle���ƺ�ability���ƻ�ȡӦ�����ƣ�ʹ��Promise�첽�ص���<br/><br/>��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�<br/> |
| [getAllApplicationInfo](arkts-ability-bundle-getallapplicationinfo-f.md#getAllApplicationInfo-1) | ��ȡָ���û��������Ѱ�װ��Ӧ����Ϣ��ʹ��callback�첽�ص���<br/> |
| [getAllApplicationInfo](arkts-ability-bundle-getallapplicationinfo-f.md#getAllApplicationInfo-2) | ��ȡ���÷������û����Ѱ�װ��Ӧ����Ϣ��ʹ��callback�첽�ص���<br/> |
| [getAllApplicationInfo](arkts-ability-bundle-getallapplicationinfo-f.md#getAllApplicationInfo-3) | ��ȡָ���û��������Ѱ�װ��Ӧ����Ϣ��ʹ��promise�첽�ص���<br/> |
| [getAllBundleInfo](arkts-ability-bundle-getallbundleinfo-f.md#getAllBundleInfo-1) | ��ȡϵͳ��ָ���û������е�BundleInfo��ʹ��callback�첽�ص���<br/> |
| [getAllBundleInfo](arkts-ability-bundle-getallbundleinfo-f.md#getAllBundleInfo-2) | ��ȡ��ǰ�û����е�BundleInfo��ʹ��callback�첽�ص���<br/> |
| [getAllBundleInfo](arkts-ability-bundle-getallbundleinfo-f.md#getAllBundleInfo-3) | ��ȡָ���û����е�BundleInfo��ʹ��Promise��ʽ�첽�ص���<br/> |
| [getApplicationInfo](arkts-ability-bundle-getapplicationinfo-f.md#getApplicationInfo-1) | ���ݸ�����Bundle���ƻ�ȡָ���û��µ�ApplicationInfo��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�<br/> |
| [getApplicationInfo](arkts-ability-bundle-getapplicationinfo-f.md#getApplicationInfo-2) | ���ݸ�����Bundle���ƻ�ȡApplicationInfo��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�<br/> |
| [getApplicationInfo](arkts-ability-bundle-getapplicationinfo-f.md#getApplicationInfo-3) | ���ݸ�����Bundle���ƻ�ȡApplicationInfo��ʹ��Promise�첽�ص���<br/><br/>��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�<br/> |
| [getBundleArchiveInfo](arkts-ability-bundle-getbundlearchiveinfo-f.md#getBundleArchiveInfo-1) | ��ȡ�й�HAP�а�����Ӧ�ó��������Ϣ��ʹ��callback�첽�ص���<br/> |
| [getBundleArchiveInfo](arkts-ability-bundle-getbundlearchiveinfo-f.md#getBundleArchiveInfo-2) | ��ȡ�й�HAP�а�����Ӧ�ó��������Ϣ��ʹ��Promise�첽�ص���<br/> |
| [getBundleInfo](arkts-ability-bundle-getbundleinfo-f.md#getBundleInfo-1) | ���ݸ�����Bundle���ƻ�ȡBundleInfo��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�<br/> |
| [getBundleInfo](arkts-ability-bundle-getbundleinfo-f.md#getBundleInfo-2) | ���ݸ�����Bundle���ƻ�ȡBundleInfo��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�<br/> |
| [getBundleInfo](arkts-ability-bundle-getbundleinfo-f.md#getBundleInfo-3) | ���ݸ�����Bundle���ƻ�ȡBundleInfo��ʹ��Promise�첽�ص���<br/><br/>��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getBundleInstaller](arkts-ability-bundle-getbundleinstaller-f-sys.md#getBundleInstaller-1) | ��ȡ���ڰ�װ���Ľӿڣ�ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getBundleInstaller](arkts-ability-bundle-getbundleinstaller-f-sys.md#getBundleInstaller-2) | ��ȡ���ڰ�װ���Ľӿڣ�ʹ��Promise�첽�ص������ذ�װ�ӿڶ���<br/> |
| [getLaunchWantForBundle](arkts-ability-bundle-getlaunchwantforbundle-f.md#getLaunchWantForBundle-1) | ��ѯ����ָ��Ӧ�õ�want����ʹ��callback�첽�ص���<br/> |
| [getLaunchWantForBundle](arkts-ability-bundle-getlaunchwantforbundle-f.md#getLaunchWantForBundle-2) | ��ѯ����ָ��Ӧ�õ�want����ʹ��Promise�첽�ص���<br/> |
| [getNameForUid](arkts-ability-bundle-getnameforuid-f.md#getNameForUid-1) | <br/> |
| [getNameForUid](arkts-ability-bundle-getnameforuid-f.md#getNameForUid-2) | ͨ��uid��ȡ��Ӧ��Bundle���ƣ�ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getPermissionDef](arkts-ability-bundle-getpermissiondef-f-sys.md#getPermissionDef-1) | ��Ȩ�����ƻ�ȡȨ�޵���ϸ��Ϣ��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getPermissionDef](arkts-ability-bundle-getpermissiondef-f-sys.md#getPermissionDef-2) | ��Ȩ�����ƻ�ȡȨ�޵���ϸ��Ϣ��ʹ��promise�첽�ص���<br/> |
| [isAbilityEnabled](arkts-ability-bundle-isabilityenabled-f.md#isAbilityEnabled-1) | ���ݸ�����AbilityInfo��ѯability�Ƿ��Ѿ����ã�ʹ��callback�첽�ص���<br/> |
| [isAbilityEnabled](arkts-ability-bundle-isabilityenabled-f.md#isAbilityEnabled-2) | ���ݸ�����AbilityInfo��ѯability�Ƿ��Ѿ����ã�ʹ��Promise�첽�ص���<br/> |
| [isApplicationEnabled](arkts-ability-bundle-isapplicationenabled-f.md#isApplicationEnabled-1) | ���ݸ�����bundleName��ѯָ��Ӧ�ó����Ƿ��Ѿ����ã�ʹ��callback�첽�ص���<br/> |
| [isApplicationEnabled](arkts-ability-bundle-isapplicationenabled-f.md#isApplicationEnabled-2) | ���ݸ�����bundleName��ѯָ��Ӧ�ó����Ƿ��Ѿ����ã�ʹ��Promise�첽�ص���<br/> |
| [queryAbilityByWant](arkts-ability-bundle-queryabilitybywant-f.md#queryAbilityByWant-1) | ���ݸ�������ͼ��ȡָ���û���Ability��Ϣ��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�<br/> |
| [queryAbilityByWant](arkts-ability-bundle-queryabilitybywant-f.md#queryAbilityByWant-2) | ���ݸ�������ͼ��ȡAbility��Ϣ��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�<br/> |
| [queryAbilityByWant](arkts-ability-bundle-queryabilitybywant-f.md#queryAbilityByWant-3) | ���ݸ�������ͼ��ȡAbility�����Ϣ��ʹ��Promise�첽�ص���<br/><br/>��ȡ���÷��Լ�����Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[setAbilityEnabled](arkts-ability-bundle-setabilityenabled-f-sys.md#setAbilityEnabled-1) | �����Ƿ�����ָ����Ability�����ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[setAbilityEnabled](arkts-ability-bundle-setabilityenabled-f-sys.md#setAbilityEnabled-2) | �����Ƿ�����ָ����Ability�����ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[setApplicationEnabled](arkts-ability-bundle-setapplicationenabled-f-sys.md#setApplicationEnabled-1) | �����Ƿ�����ָ����Ӧ�ó���ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[setApplicationEnabled](arkts-ability-bundle-setapplicationenabled-f-sys.md#setApplicationEnabled-2) | �����Ƿ�����ָ����Ӧ�ó���ʹ��Promise�첽�ص���<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [BundleOptions](arkts-ability-bundle-bundleoptions-i.md) | &gt; **˵����**<br/>&gt;<br/>&gt; ��API version 7��ʼ֧�֣���API version 9��ʼ��������������ӿڡ�<br/><br/>��ѯѡ�����userId��<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AbilitySubType](arkts-ability-bundle-abilitysubtype-e.md) | &gt; **˵����**<br/>&gt;<br/>&gt; ��API version 7��ʼ֧�֣���API version 9��ʼ��������������ӿڡ�<br/><br/>Ability����������͡�<br/> |
| [AbilityType](arkts-ability-bundle-abilitytype-e.md) | &gt; **˵����**<br/>&gt;<br/>&gt; ��API version 7��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [bundleManager.AbilityType](arkts-ability-bundlemanager-abilitytype-e.md#AbilityType)�����<br/><br/>Ability������͡�<br/> |
| [BundleFlag](arkts-ability-bundle-bundleflag-e.md) | &gt; **˵����**<br/>&gt;<br/>&gt; ��API version 7��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [bundleManager.BundleFlag](arkts-ability-bundlemanager-bundleflag-e.md#BundleFlag)�����<br/><br/>����Ϣ��־��ָʾ��Ҫ��ȡ�İ���Ϣ�����ݡ�<br/><br/>���ӿ����־��ƥ��ʱ���ñ�־�ᱻ���ԣ������ȡapplicationʱʹ��GET_ABILITY_INFO_WITH_PERMISSION�Խ���������Ӱ�졣<br/><br/>��־���Ե���ʹ�ã�����ʹ��GET_APPLICATION_INFO_WITH_PERMISSION + GET_APPLICATION_INFO_WITH_DISABLE����ʹ���ͬʱ����Ӧ��Ȩ����Ϣ�ͱ����õ�Ӧ����Ϣ��<br/> |
| [ColorMode](arkts-ability-bundle-colormode-e.md) | &gt; **˵����**<br/>&gt;<br/>&gt; ��API version 7��ʼ֧�֣���API version 9��ʼ��������������ӿڡ�<br/><br/>Ӧ�á���Ƭ�ȵ���ɫģʽ��<br/> |
| [DisplayOrientation](arkts-ability-bundle-displayorientation-e.md) | &gt; **˵����**<br/>&gt;<br/>&gt; ��API version 7��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [bundleManager.DisplayOrientation](arkts-ability-bundlemanager-displayorientation-e.md#DisplayOrientation)�����<br/><br/>��Ļ��ʾ����<br/> |
| [GrantStatus](arkts-ability-bundle-grantstatus-e.md) | &gt; **˵����**<br/>&gt;<br/>&gt; ��API version 7��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [bundleManager.PermissionGrantState](arkts-ability-bundlemanager-permissiongrantstate-e.md#PermissionGrantState)�����<br/><br/>Ȩ������״̬��<br/> |
| [InstallErrorCode](arkts-ability-bundle-installerrorcode-e.md) | &gt; **˵����**<br/>&gt;<br/>&gt; ��API version 7��ʼ֧�֣���API version 9��ʼ����������ʹ��[��������ϵͳͨ�ô�����](../../../../reference/apis-ability-kit/errorcode-bundle.md)<br/>&gt; �����<br/> |
| [LaunchMode](arkts-ability-bundle-launchmode-e.md) | &gt; **˵����**<br/>&gt;<br/>&gt; ��API version 7��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [bundleManager.LaunchType](arkts-ability-bundlemanager-launchtype-e.md#LaunchType)�����<br/><br/>Ability���������ģʽ��<br/> |

