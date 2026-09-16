# ShortcutWant

快捷方式内定义的目标[wants](../../../quick-start/module-configuration-file.md#wants标签)信息集合。

**起始版本：** 20

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

## action

```TypeScript
action?: string
```

拉起快捷方式时要执行的操作，与[Want](arkts-ability-app-ability-want-want-c.md#action)的**action**字段一致。在隐式Want模式下与**uri**或**parameters**配合使用，指定要执行的操作。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## flags

```TypeScript
flags?: number
```

拉起快捷方式时Want对象的处理方式，取值为枚举类型[Flags](arkts-ability-wantconstant-flags-e.md)，与[Want](arkts-ability-app-ability-want-want-c.md#flags)的**flags**字段一致。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。

## uri

```TypeScript
uri?: string
```

拉起快捷方式时要匹配的URI，与[Want](arkts-ability-app-ability-want-want-c.md#uri)的**uri**字段一致。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Launcher

**系统接口：** 此接口为系统接口。
