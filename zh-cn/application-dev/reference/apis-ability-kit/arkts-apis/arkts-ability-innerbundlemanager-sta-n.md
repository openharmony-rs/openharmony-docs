# innerBundleManager

��ģ���ṩlauncherӦ��ʹ�õĽӿڡ�

> **˵����**
>
> ��ģ���API version 9��ʼ����֧�֡�����ʹ��[launcherBundleManager](arkts-bundle-launcherbundlemanager.md#launcherBundleManager)
> ��[bundleMonitor](arkts-bundle-bundlemonitor.md#bundleMonitor)�����
>
> ��ģ��Ϊϵͳ�ӿڡ�

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [launcherBundleManager:launcherBundleManager](arkts-bundle-launcherbundlemanager.md#launcherBundleManager)

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[getLauncherAbilityInfos](arkts-ability-innerbundlemanager-getlauncherabilityinfos-f-sys.md#getLauncherAbilityInfos-1) | ���ݸ�����Bundle���ƻ�ȡLauncherAbilityInfos��ʹ��callback�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [getLauncherAbilityInfo](@ohos.bundle.launcherBundleManager:launcherBundleManager.getLauncherAbilityInfo(bundleName: string, userId: int, callback: AsyncCallback&lt;Array&lt;LauncherAbilityInfo&gt;&gt;))<br/>&gt; �����<br/> |
| <!--DelRow-->[getLauncherAbilityInfos](arkts-ability-innerbundlemanager-getlauncherabilityinfos-f-sys.md#getLauncherAbilityInfos-2) | ���ݸ�����Bundle���ƻ�ȡLauncherAbilityInfos��ʹ��Promise�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [getLauncherAbilityInfo](@ohos.bundle.launcherBundleManager:launcherBundleManager.getLauncherAbilityInfo(bundleName: string, userId: int, callback: AsyncCallback&lt;Array&lt;LauncherAbilityInfo&gt;&gt;))<br/>&gt; �����<br/> |
| <!--DelRow-->[on](arkts-ability-innerbundlemanager-on-f-sys.md#on-1) | ע��Callback��<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [on](@ohos.bundle.bundleMonitor:bundleMonitor.on(type: BundleChangedEvent, callback: Callback&lt;BundleChangedInfo&gt;))<br/>&gt; �����<br/> |
| <!--DelRow-->[on](arkts-ability-innerbundlemanager-on-f-sys.md#on-2) | ע��Callback��<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [on](@ohos.bundle.bundleMonitor:bundleMonitor.on(type: BundleChangedEvent, callback: Callback&lt;BundleChangedInfo&gt;))<br/>&gt; �����<br/> |
| <!--DelRow-->[off](arkts-ability-innerbundlemanager-off-f-sys.md#off-1) | ȡ��ע��Callback��<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [off](@ohos.bundle.bundleMonitor:bundleMonitor.off(type: BundleChangedEvent, callback?: Callback&lt;BundleChangedInfo&gt;))<br/>&gt; �����<br/> |
| <!--DelRow-->[off](arkts-ability-innerbundlemanager-off-f-sys.md#off-2) | ȡ��ע��Callback��<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [off](@ohos.bundle.bundleMonitor:bundleMonitor.off(type: BundleChangedEvent, callback?: Callback&lt;BundleChangedInfo&gt;))<br/>&gt; �����<br/> |
| <!--DelRow-->[getAllLauncherAbilityInfos](arkts-ability-innerbundlemanager-getalllauncherabilityinfos-f-sys.md#getAllLauncherAbilityInfos-1) | ��ȡ���е�LauncherAbilityInfos��ʹ��callback�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [getAllLauncherAbilityInfo](@ohos.bundle.launcherBundleManager:launcherBundleManager.getAllLauncherAbilityInfo(userId: int, callback: AsyncCallback&lt;Array&lt;LauncherAbilityInfo&gt;&gt;))<br/>&gt; �����<br/> |
| <!--DelRow-->[getAllLauncherAbilityInfos](arkts-ability-innerbundlemanager-getalllauncherabilityinfos-f-sys.md#getAllLauncherAbilityInfos-2) | ��ȡLauncherAbilityInfos��ʹ��Promise�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [getAllLauncherAbilityInfo](@ohos.bundle.launcherBundleManager:launcherBundleManager.getAllLauncherAbilityInfo(userId: int, callback: AsyncCallback&lt;Array&lt;LauncherAbilityInfo&gt;&gt;))<br/>&gt; �����<br/> |
| <!--DelRow-->[getShortcutInfos](arkts-ability-innerbundlemanager-getshortcutinfos-f-sys.md#getShortcutInfos-1) | ���ݸ�����Bundle���ƻ�ȡ��ݷ�ʽ��Ϣ��ʹ��callback�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [getShortcutInfo](@ohos.bundle.launcherBundleManager:launcherBundleManager.getShortcutInfo(bundleName :string, callback: AsyncCallback&lt;Array&lt;ShortcutInfo&gt;&gt;))<br/>&gt; �����<br/> |
| <!--DelRow-->[getShortcutInfos](arkts-ability-innerbundlemanager-getshortcutinfos-f-sys.md#getShortcutInfos-2) | ���ݸ�����Bundle���ƻ�ȡ��ݷ�ʽ��Ϣ��ʹ��Promise�첽�ص���<br/><br/>&gt; **˵����**<br/>&gt;<br/>&gt; ��API version 8��ʼ֧�֣���API version 9��ʼ����������ʹ��<br/>&gt; [getShortcutInfo](@ohos.bundle.launcherBundleManager:launcherBundleManager.getShortcutInfo(bundleName :string, callback: AsyncCallback&lt;Array&lt;ShortcutInfo&gt;&gt;))<br/>&gt; �����<br/> |

