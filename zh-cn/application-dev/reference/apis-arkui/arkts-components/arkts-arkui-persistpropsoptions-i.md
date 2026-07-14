# PersistPropsOptions

用于指定持久化属性及其默认值的键值对对象，作为[persistProps](arkts-arkui-persistentstorage-c.md#persistprops-1)参数传入。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## defaultValue

```TypeScript
defaultValue: number | string | boolean | Object
```

在PersistentStorage和AppStorage未查询到时，则使用默认值初始化它。从API version 12开始，defaultValue允许为null或undefined。

**类型：** number | string | boolean | Object

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key: string
```

属性名。

**类型：** string

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

