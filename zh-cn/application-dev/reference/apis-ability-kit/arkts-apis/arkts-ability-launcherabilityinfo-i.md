# LauncherAbilityInfo

桌面应用的Ability信息，可以通过
[getLauncherAbilityInfoSync](arkts-ability-getlauncherabilityinfosync-f.md#getlauncherabilityinfosync-1)
<!--Del-->或者
[getLauncherAbilityInfo](./../@ohos.bundle.launcherBundleManager:launcherBundleManager.getLauncherAbilityInfo(bundleName: string, userId: int, callback: AsyncCallback<Array<LauncherAbilityInfo>>))
<!--DelEnd-->获取。

**起始版本：** 18

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## applicationInfo

```TypeScript
readonly applicationInfo: ApplicationInfo
```

launcher ability的应用程序配置信息。

**类型：** ApplicationInfo

**起始版本：** 18

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## elementName

```TypeScript
readonly elementName: ElementName
```

launcher ability的ElementName信息。

**类型：** ElementName

**起始版本：** 18

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## iconId

```TypeScript
readonly iconId: number
```

launcher ability的图标的资源ID值。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## installTime

```TypeScript
readonly installTime: number
```

launcher ability的安装时间戳，单位毫秒。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## labelId

```TypeScript
readonly labelId: number
```

launcher ability的名称的资源ID值。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## userId

```TypeScript
readonly userId: number
```

launcher ability的用户ID。

**类型：** number

**起始版本：** 18

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

