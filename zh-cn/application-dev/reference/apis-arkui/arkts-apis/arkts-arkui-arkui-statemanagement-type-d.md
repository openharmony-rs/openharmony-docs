# @Type

```TypeScript
export declare const Type: TypeDecorator
```

@Type装饰类属性，用于[状态管理V2](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)，确保序列化类时不丢失属性的复杂类型。在使用[PersistenceV2](arkts-arkui-arkui-statemanagement-persistencev2-c.md)等持久化能力对复杂类对象进行序列化和反序列化时，类的属性类型信息可能会丢失。通过@Type标记属性的原始类型，可确保在序列化过程中正确保留和还原属性的复杂类型信息，适用于需要持久化或序列化复杂对象的场景，例如应用状态持久化存储、跨组件复杂数据传递等。

开发指南参考：[@Type装饰器：标记类属性的类型](../../../ui/state-management/arkts-new-type.md)。

@Type标记属性的原始类型，可确保在序列化过程中正确保留和还原属性的复杂类型信息。

type：标记类属性的原始类型，取值为对应类的构造函数，需与被装饰属性的类型一致。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-unnamed-export declare const Type: TypeDecorator--><!--Device-unnamed-export declare const Type: TypeDecorator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
