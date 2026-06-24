# @ohos.bundle.launcherBundleManager

��ģ��֧��launcherӦ�ã�������ͼ���Ӧ�ã�����Ĳ�ѯ������֧��
[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)��Ϣ�Ĳ�ѯ��

**起始版本：** 18

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[getAllLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getalllauncherabilityinfo-f-sys.md#getAllLauncherAbilityInfo-1) | ��ѯָ���û�������Ӧ�õ�[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)��ʹ��callback�첽�ص���<br/> |
| <!--DelRow-->[getAllLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getalllauncherabilityinfo-f-sys.md#getAllLauncherAbilityInfo-2) | ��ѯָ���û�������Ӧ�õ�[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[getLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getlauncherabilityinfo-f-sys.md#getLauncherAbilityInfo-1) | ��ѯָ��bundleName���û���[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)��ʹ��callback�첽<br/>�ص���<br/> |
| <!--DelRow-->[getLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getlauncherabilityinfo-f-sys.md#getLauncherAbilityInfo-2) | ��ѯָ��bundleName���û���[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)��ʹ��Promise�첽��<br/>����<br/> |
| [getLauncherAbilityInfoSync](arkts-ability-launcherbundlemanager-getlauncherabilityinfosync-f.md#getLauncherAbilityInfoSync-1) | ��ѯָ��bundleName���û���[LauncherAbilityInfo](arkts-ability-launcherabilityinfo-i.md#LauncherAbilityInfo)��<br/> |
| <!--DelRow-->[getShortcutInfo](arkts-ability-launcherbundlemanager-getshortcutinfo-f-sys.md#getShortcutInfo-1) | ��ѯ��ǰ�û���ָ��Ӧ�õĿ�ݷ�ʽ��Ϣ[ShortcutInfo](arkts-ability-shortcutinfo-i.md#ShortcutInfo)��ֻ֧�ֲ�ѯ��Ӧ�õ�ShortcutInfo����ѯ����Ӧ����ʹ��<br/>[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md#getShortcutInfoByAppIndex-1)��ʹ��callback�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getShortcutInfo](arkts-ability-launcherbundlemanager-getshortcutinfo-f-sys.md#getShortcutInfo-2) | ��ѯ��ǰ�û���ָ��Ӧ�õĿ�ݷ�ʽ��Ϣ[ShortcutInfo](arkts-ability-shortcutinfo-i.md#ShortcutInfo)��ֻ֧�ֲ�ѯ��Ӧ�õ�ShortcutInfo����ѯ����Ӧ����ʹ��<br/>[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md#getShortcutInfoByAppIndex-1)��ʹ��Promise�첽�ص���<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md#getShortcutInfoByAppIndex-1) | ��ѯ��ǰ�û���ָ������Ӧ�õĿ�ݷ�ʽ��Ϣ[ShortcutInfo](arkts-ability-shortcutinfo-i.md#ShortcutInfo)��<br/><br/>���÷���ȡ�Լ�����Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getShortcutInfoSync](arkts-ability-launcherbundlemanager-getshortcutinfosync-f-sys.md#getShortcutInfoSync-1) | ��ѯ��ǰ�û���ָ��Ӧ�õĿ�ݷ�ʽ��Ϣ[ShortcutInfo](arkts-ability-shortcutinfo-i.md#ShortcutInfo)��ֻ֧�ֲ�ѯ��Ӧ�õ�ShortcutInfo����ѯ����Ӧ����ʹ��<br/>[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md#getShortcutInfoByAppIndex-1)��<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[getShortcutInfoSync](arkts-ability-launcherbundlemanager-getshortcutinfosync-f-sys.md#getShortcutInfoSync-2) | ��ѯָ���û���ָ��Ӧ�õĿ�ݷ�ʽ��Ϣ[ShortcutInfo](arkts-ability-shortcutinfo-i.md#ShortcutInfo)��ֻ֧�ֲ�ѯ��Ӧ�õ�ShortcutInfo����ѯ����Ӧ����ʹ��<br/>[getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md#getShortcutInfoByAppIndex-1)��<br/><br/>��ȡ���÷���������Ϣʱ����ҪȨ�ޡ�<br/> |
| <!--DelRow-->[startShortcut](arkts-ability-launcherbundlemanager-startshortcut-f-sys.md#startShortcut-1) | ����ָ��[ShortcutInfo](arkts-ability-shortcutinfo-i.md#ShortcutInfo)�е�ability��ʹ��Promise�첽�ص���<br/> |
| <!--DelRow-->[startShortcutWithReason](arkts-ability-launcherbundlemanager-startshortcutwithreason-f-sys.md#startShortcutWithReason-1) | ����ָ���Ŀ�ݷ�ʽ��Ϣ�������Ӧ��Ability����Я����ݷ�ʽ������ԭ��ʹ��Promise�첽�ص���<br/><br/>�����𷽿���ͨ��[LaunchParam](arkts-ability-abilityconstant-launchparam-i.md#LaunchParam)��launchReasonMessage�ֶλ�ȡ��<br/>����ԭ�򣬲���������ԭ�����ҵ���߼�������<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [LauncherAbilityInfo](arkts-ability-launcherbundlemanager-launcherabilityinfo-t.md) | LauncherAbilityInfo��Ϣ��<br/> |
| <!--DelRow-->[ParameterItem](arkts-ability-launcherbundlemanager-parameteritem-t-sys.md) | ��ݷ�ʽ������Ϣ�е��Զ������ݡ�<br/> |
| <!--DelRow-->[ShortcutInfo](arkts-ability-launcherbundlemanager-shortcutinfo-t-sys.md) | Ӧ��[module.json5�����ļ�](../../../../quick-start/module-configuration-file.md#shortcuts��ǩ)�ж���Ŀ�ݷ�ʽ��Ϣ��<br/> |
| <!--DelRow-->[ShortcutWant](arkts-ability-launcherbundlemanager-shortcutwant-t-sys.md) | ��ݷ�ʽ�ڶ����Ŀ��[wants](../../../../quick-start/module-configuration-file.md#wants��ǩ)��Ϣ���ϡ�<br/> |

