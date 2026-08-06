# ShortcutWant

快捷方式内定义的目标\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_信息集合。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export interface ShortcutWant--><!--Device-unnamed-export interface ShortcutWant-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## parameters

```TypeScript
parameters?: Array<ParameterItem>
```

拉起快捷方式时的自定义数据，仅支持配置字符串类型的数据。其中键值均最大支持1024长度的字符串。

**类型：** Array&lt;ParameterItem&gt;

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-ShortcutWant-parameters?: Array<ParameterItem>--><!--Device-ShortcutWant-parameters?: Array<ParameterItem>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## targetAbility

```TypeScript
targetAbility: string
```

快捷方式的目标组件名。

**类型：** string

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ShortcutWant-targetAbility: string--><!--Device-ShortcutWant-targetAbility: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## targetBundle

```TypeScript
targetBundle: string
```

快捷方式的目标包名。

**类型：** string

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ShortcutWant-targetBundle: string--><!--Device-ShortcutWant-targetBundle: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## targetModule

```TypeScript
targetModule?: string
```

快捷方式的目标模块名。

**类型：** string

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-ShortcutWant-targetModule?: string--><!--Device-ShortcutWant-targetModule?: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

