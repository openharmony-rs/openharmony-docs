# @Consume

```TypeScript
declare const Consume: PropertyDecorator & ((value: string) => PropertyDecorator)
```

[@Provide](arkts-arkui-common-comp-provide-d.md#provide)和\@Consume配套使用，用于[状态管理V1](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，实现跨组件层级的双向同步，适用于需要在多层嵌套组件间共享状态的场景，能够避免逐层传递的繁琐，简化组件间的通信逻辑。\@Consume装饰的变量作为数据消费方，通过别名或变量名与\@Provide装饰的变量建立双向绑定关系。当\@Provide或\@Consume装饰的变量发生变化时，变化会自动同步到对方。匹配规则：优先使用别名匹配，若未设置别名则使用变量名匹配。

开发指南参考：[@Provide装饰器和@Consume装饰器：与后代组件双向同步](../../../ui/state-management/arkts-provide-and-consume.md)。

> **说明：** 
> 
> 从API version 20开始，@Consume装饰的变量支持设置默认值。当查找不到@Provide的匹配结果时，@Consume装饰的变量会使用默认值进行初始化；当查找到@Provide的匹配结果时，
> @Consume装饰的变量会优先使用@Provide匹配结果的值，默认值不生效。
> 
> 从API version 20开始，支持跨BuilderNode配对@Provide/@Consume。在BuilderNode场景下，BuilderNode会在上树前构造节点，
> 所以BuilderNode内部定义的@Consume需要设置默认值，并在BuilderNode上树后，重新获取最近的@Provide数据，与之建立双向同步关系。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
