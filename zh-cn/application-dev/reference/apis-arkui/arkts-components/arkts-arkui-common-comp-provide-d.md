# @Provide

```TypeScript
declare const Provide: PropertyDecorator & ((value: string | ProvideOptions) => PropertyDecorator)
```

\@Provide和[@Consume](arkts-arkui-common-comp-consume-d.md#consume)配套使用，用于[状态管理V1](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，实现跨组件层级的双向同步，适用于需要跨越多层组件传递状态、避免逐层传递的场景，能够解决组件层级较深时状态传递繁琐的问题。\@Provide装饰的变量作为数据源，通过别名或变量名与\@Consume装饰的变量建立双向绑定关系。当\@Provide或\@Consume装饰的变量发生变化时，变化会自动同步到对方。

开发指南参考：[@Provide装饰器和@Consume装饰器：与后代组件双向同步](../../../ui/state-management/arkts-provide-and-consume.md)。

value：用于设置别名或允许重写的别名。<br>类型为string时，将直接作为别名，后代组件可通过该别名访问数据。<br>类型为ProvideOptions时，若设置了allowOverride，allowOverride的值将作为别名且该别名允许重写；若未设置allowOverride，则别名为变量名，不允许重写。<br>value缺省时别名为变量名，不允许重写。若此时定义同名\@Provide，运行时会报错。PropertyDecorator：属性装饰器，开发者无需关注该返回值。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare const Provide: PropertyDecorator & ((value: string | ProvideOptions) => PropertyDecorator)--><!--Device-unnamed-declare const Provide: PropertyDecorator & ((value: string | ProvideOptions) => PropertyDecorator)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
