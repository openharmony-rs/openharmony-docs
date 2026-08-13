# ShortcutInfo（系统接口）

快捷方式的配置信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface ShortcutInfo--><!--Device-unnamed-export interface ShortcutInfo-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## appIndex

```TypeScript
appIndex: int
```

快捷方式所属应用的分身索引。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortcutInfo-appIndex: int--><!--Device-ShortcutInfo-appIndex: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

快捷方式所属应用的包名。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortcutInfo-bundleName: string--><!--Device-ShortcutInfo-bundleName: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## hostAbility

```TypeScript
hostAbility?: string
```

快捷方式的宿主组件名, 即承载此快捷方式的组件名。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortcutInfo-hostAbility?: string--><!--Device-ShortcutInfo-hostAbility?: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## icon

```TypeScript
icon?: string
```

快捷方式的图标，取值为资源文件的索引。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortcutInfo-icon?: string--><!--Device-ShortcutInfo-icon?: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## iconId

```TypeScript
iconId?: long
```

快捷方式图标的资源ID。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortcutInfo-iconId?: long--><!--Device-ShortcutInfo-iconId?: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## id

```TypeScript
id: string
```

快捷方式的ID。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortcutInfo-id: string--><!--Device-ShortcutInfo-id: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## label

```TypeScript
label?: string
```

快捷方式的标签信息，即快捷方式对外显示的文字描述信息。可以是描述性内容，也可以是标识label的资源索引。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortcutInfo-label?: string--><!--Device-ShortcutInfo-label?: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## labelId

```TypeScript
labelId?: long
```

快捷方式标签信息为资源索引时的资源ID。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortcutInfo-labelId?: long--><!--Device-ShortcutInfo-labelId?: long-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## moduleName

```TypeScript
moduleName?: string
```

快捷方式的模块名。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortcutInfo-moduleName?: string--><!--Device-ShortcutInfo-moduleName?: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## sourceType

```TypeScript
sourceType: int
```

快捷方式来源类型。0表示自定义快捷方式，1表示静态快捷方式，2表示动态快捷方式。从API version 23开始，支持动态快捷方式。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortcutInfo-sourceType: int--><!--Device-ShortcutInfo-sourceType: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## wants

```TypeScript
wants?: Array<ShortcutWant>
```

快捷方式内定义的目标wants信息集合。

**类型：** Array&lt;[ShortcutWant](arkts-ability-shortcutinfo-shortcutwant-i-sys.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortcutInfo-wants?: Array<ShortcutWant>--><!--Device-ShortcutInfo-wants?: Array<ShortcutWant>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

