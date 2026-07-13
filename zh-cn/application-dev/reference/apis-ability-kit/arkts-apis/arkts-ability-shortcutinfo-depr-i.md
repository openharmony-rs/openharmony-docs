# ShortcutInfo

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃，建议使用[bundleManager-ShortcutInfo](arkts-ability-shortcutinfo-depr-i.md)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [shortcutInfo:ShortcutInfo](arkts-ability-shortcutinfo-depr-i.md)

**系统能力：** SystemCapability.BundleManager.BundleFramework

## bundleName

```TypeScript
readonly bundleName: string
```

包含该快捷方式的Bundle名称。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** bundleName

**系统能力：** SystemCapability.BundleManager.BundleFramework

## disableMessage

```TypeScript
readonly disableMessage: string
```

快捷方式的禁用消息。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework

## hostAbility

```TypeScript
readonly hostAbility: string
```

快捷方式的本地Ability信息。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** hostAbility

**系统能力：** SystemCapability.BundleManager.BundleFramework

## icon

```TypeScript
readonly icon: string
```

快捷方式的图标。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** icon

**系统能力：** SystemCapability.BundleManager.BundleFramework

## iconId

```TypeScript
readonly iconId: number
```

快捷方式的图标ID。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** iconId

**系统能力：** SystemCapability.BundleManager.BundleFramework

## id

```TypeScript
readonly id: string
```

快捷方式所属应用程序的ID。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** id

**系统能力：** SystemCapability.BundleManager.BundleFramework

## isEnabled

```TypeScript
readonly isEnabled?: boolean
```

是否启用快捷方式，取值为true表示启用快捷方式，取值为false表示停用快捷方式。

**类型：** boolean

**默认值：** false

**起始版本：** 7

**废弃版本：** 9

**替代接口：** visible

**系统能力：** SystemCapability.BundleManager.BundleFramework

## isHomeShortcut

```TypeScript
readonly isHomeShortcut?: boolean
```

快捷方式是否为静态，取值为true表示是静态的快捷方式，取值为false表示不是静态的快捷方式。

**类型：** boolean

**默认值：** false

**起始版本：** 7

**废弃版本：** 9

**替代接口：** sourceType

**系统能力：** SystemCapability.BundleManager.BundleFramework

## isStatic

```TypeScript
readonly isStatic?: boolean
```

快捷方式是否为静态，取值为true表示是静态的快捷方式，取值为false表示不是静态的快捷方式。

**类型：** boolean

**默认值：** false

**起始版本：** 7

**废弃版本：** 9

**替代接口：** sourceType

**系统能力：** SystemCapability.BundleManager.BundleFramework

## label

```TypeScript
readonly label: string
```

快捷方式的名称。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** label

**系统能力：** SystemCapability.BundleManager.BundleFramework

## labelId

```TypeScript
readonly labelId: number
```

快捷方式的名称ID。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** labelId

**系统能力：** SystemCapability.BundleManager.BundleFramework

## wants

```TypeScript
readonly wants: Array<ShortcutWant>
```

快捷方式意图列表。

**类型：** Array<ShortcutWant>

**起始版本：** 7

**废弃版本：** 9

**替代接口：** wants

**系统能力：** SystemCapability.BundleManager.BundleFramework

