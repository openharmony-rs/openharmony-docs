# ShortcutInfo

快捷方式的配置信息。

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## appIndex

```TypeScript
appIndex: number
```

快捷方式所属应用的分身索引。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## bundleName

```TypeScript
bundleName: string
```

快捷方式所属应用的包名。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## hostAbility

```TypeScript
hostAbility?: string
```

快捷方式的宿主组件名, 即承载此快捷方式的组件名。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## icon

```TypeScript
icon?: string
```

快捷方式的图标，取值为资源文件的索引。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## iconId

```TypeScript
iconId?: number
```

快捷方式图标的资源ID。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## id

```TypeScript
id: string
```

快捷方式的ID。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## label

```TypeScript
label?: string
```

快捷方式的标签信息，即快捷方式对外显示的文字描述信息。可以是描述性内容，也可以是标识label的资源索引。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## labelId

```TypeScript
labelId?: number
```

快捷方式标签信息为资源索引时的资源ID。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## moduleName

```TypeScript
moduleName?: string
```

快捷方式的模块名。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## sourceType

```TypeScript
sourceType: number
```

快捷方式来源类型。0表示自定义快捷方式，1表示静态快捷方式，2表示动态快捷方式。从API version 23开始，支持动态快捷方式。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## visible

```TypeScript
visible?: boolean
```

快捷方式是否显示。true：快捷方式显示；false：快捷方式不显示。默认值为true。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## wants

```TypeScript
wants?: Array<ShortcutWant>
```

快捷方式内定义的目标wants信息集合。

**类型：** Array&lt;[ShortcutWant](arkts-ability-shortcutinfo-shortcutwant-i.md)&gt;

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher
