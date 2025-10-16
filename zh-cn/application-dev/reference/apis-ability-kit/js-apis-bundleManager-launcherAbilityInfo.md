# LauncherAbilityInfo

桌面应用的Ability信息，可以通过[getLauncherAbilityInfoSync](js-apis-launcherBundleManager.md#launcherbundlemanagergetlauncherabilityinfosync18)<!--Del-->或者[getLauncherAbilityInfo](js-apis-launcherBundleManager-sys.md#launcherbundlemanagergetlauncherabilityinfo9)<!--DelEnd-->获取。

> **说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> 本模块首批接口从API version 18开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { launcherBundleManager } from '@kit.AbilityKit';
```

## LauncherAbilityInfo

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 20

| 名称            | 类型                                                        | 只读 | 可选 | 说明                                 |
| --------------- | ----------------------------------------------------------- | ---- | ---- | ------------------------------------ |
| applicationInfo | [ApplicationInfo](js-apis-bundleManager-applicationInfo.md) | 是   | 否   | launcher ability的应用程序的配置信息。 |
| elementName     | [ElementName](js-apis-bundleManager-elementName.md)         | 是   | 否   | launcher ability的ElementName信息。    |
| labelId         | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 否   | launcher ability的标签ID。             |
| iconId          | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 否   | launcher ability的图标ID。             |
| userId          | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 否   | launcher ability的用户ID。             |
| installTime     | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 否   | launcher ability的安装时间戳，单位毫秒。 |