# innerBundleManager

本模块提供launcher应用使用的接口。

> **说明：**
>
> 本模块从API version 9开始不再支持。建议使用[launcherBundleManager](arkts-bundle-launcherbundlemanager.md)
> 及[bundleMonitor](arkts-bundle-bundlemonitor.md)替代。
>
> 本模块为系统接口。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [launcherBundleManager:launcherBundleManager](arkts-bundle-launcherbundlemanager.md)

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getLauncherAbilityInfos](arkts-ability-getlauncherabilityinfos-f-sys.md#getlauncherabilityinfos-1) | 根据给定的Bundle名称获取LauncherAbilityInfos，使用callback异步回调。@link @ohos.bundle.launcherBundleManager:launcherBundleManager.getLauncherAbilityInfo(bundleName: string, userId: int, callback: AsyncCallback&lt;Array&lt;LauncherAbilityInfo&gt;&gt;)}&gt; 替代。 |
| [getLauncherAbilityInfos](arkts-ability-getlauncherabilityinfos-f-sys.md#getlauncherabilityinfos-2) | 根据给定的Bundle名称获取LauncherAbilityInfos，使用Promise异步回调。@link @ohos.bundle.launcherBundleManager:launcherBundleManager.getLauncherAbilityInfo(bundleName: string, userId: int, callback: AsyncCallback&lt;Array&lt;LauncherAbilityInfo&gt;&gt;)}&gt; 替代。 |
| [on](arkts-ability-on-f-sys.md#on-1) | 注册Callback。@link @ohos.bundle.bundleMonitor:bundleMonitor.on(type: BundleChangedEvent, callback: Callback&lt;BundleChangedInfo&gt;)}&gt; 替代。 |
| [on](arkts-ability-on-f-sys.md#on-2) | 注册Callback。@link @ohos.bundle.bundleMonitor:bundleMonitor.on(type: BundleChangedEvent, callback: Callback&lt;BundleChangedInfo&gt;)}&gt; 替代。 |
| [off](arkts-ability-off-f-sys.md#off-1) | 取消注册Callback。@link @ohos.bundle.bundleMonitor:bundleMonitor.off(type: BundleChangedEvent, callback?: Callback&lt;BundleChangedInfo&gt;)}&gt; 替代。 |
| [off](arkts-ability-off-f-sys.md#off-2) | 取消注册Callback。@link @ohos.bundle.bundleMonitor:bundleMonitor.off(type: BundleChangedEvent, callback?: Callback&lt;BundleChangedInfo&gt;)}&gt; 替代。 |
| [getAllLauncherAbilityInfos](arkts-ability-getalllauncherabilityinfos-f-sys.md#getalllauncherabilityinfos-1) | 获取所有的LauncherAbilityInfos，使用callback异步回调。@link @ohos.bundle.launcherBundleManager:launcherBundleManager.getAllLauncherAbilityInfo(userId: int, callback: AsyncCallback&lt;Array&lt;LauncherAbilityInfo&gt;&gt;)}&gt; 替代。 |
| [getAllLauncherAbilityInfos](arkts-ability-getalllauncherabilityinfos-f-sys.md#getalllauncherabilityinfos-2) | 获取LauncherAbilityInfos，使用Promise异步回调。@link @ohos.bundle.launcherBundleManager:launcherBundleManager.getAllLauncherAbilityInfo(userId: int, callback: AsyncCallback&lt;Array&lt;LauncherAbilityInfo&gt;&gt;)}&gt; 替代。 |
| [getShortcutInfos](arkts-ability-getshortcutinfos-f-sys.md#getshortcutinfos-1) | 根据给定的Bundle名称获取快捷方式信息，使用callback异步回调。@link @ohos.bundle.launcherBundleManager:launcherBundleManager.getShortcutInfo(bundleName :string, callback: AsyncCallback&lt;Array&lt;ShortcutInfo&gt;&gt;)}&gt; 替代。 |
| [getShortcutInfos](arkts-ability-getshortcutinfos-f-sys.md#getshortcutinfos-2) | 根据给定的Bundle名称获取快捷方式信息，使用Promise异步回调。@link @ohos.bundle.launcherBundleManager:launcherBundleManager.getShortcutInfo(bundleName :string, callback: AsyncCallback&lt;Array&lt;ShortcutInfo&gt;&gt;)}&gt; 替代。 |
<!--DelEnd-->

