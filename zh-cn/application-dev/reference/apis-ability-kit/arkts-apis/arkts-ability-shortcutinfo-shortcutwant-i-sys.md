# ShortcutWant（系统接口）

快捷方式内定义的目标[wants](../../../quick-start/module-configuration-file.md#wants标签)信息集合。

**起始版本：** 20

<!--Device-unnamed-export interface ShortcutWant--><!--Device-unnamed-export interface ShortcutWant-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## parameters

```TypeScript
parameters?: Array<ParameterItem>
```

拉起快捷方式时的自定义数据，仅支持配置字符串类型的数据。其中键值均最大支持1024长度的字符串。

**类型：** Array&lt;ParameterItem&gt;

**起始版本：** 20

<!--Device-ShortcutWant-parameters?: Array<ParameterItem>--><!--Device-ShortcutWant-parameters?: Array<ParameterItem>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## targetAbility

```TypeScript
targetAbility: string
```

快捷方式的目标组件名。

**类型：** string

**起始版本：** 20

<!--Device-ShortcutWant-targetAbility: string--><!--Device-ShortcutWant-targetAbility: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## targetBundle

```TypeScript
targetBundle: string
```

快捷方式的目标包名。

**类型：** string

**起始版本：** 20

<!--Device-ShortcutWant-targetBundle: string--><!--Device-ShortcutWant-targetBundle: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## targetModule

```TypeScript
targetModule?: string
```

快捷方式的目标模块名。

**类型：** string

**起始版本：** 20

<!--Device-ShortcutWant-targetModule?: string--><!--Device-ShortcutWant-targetModule?: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

