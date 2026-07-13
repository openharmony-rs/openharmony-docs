# MutableBinding

可变数据绑定的泛型类，允许对绑定值进行读写操作，提供完整的get和set访问器。

**起始版本：** 20

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
set value(newValue: T)
```

提供set访问器，用于设置当前绑定值的值。构造MutableBinding类实例时必须提供set访问器，否则触发set访问器会造成运行时错误。

**类型：** T

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

