# @ObjectLink

```TypeScript
declare const ObjectLink: PropertyDecorator
```

@ObjectLink用于状态管理V1中，接收\@Observed装饰的类的实例，并与父组件中的数据源建立双向数据绑定，适用于在子组件中独立观察并监听嵌套类属性并触发UI刷新的场景。

开发指南参考：[\@Observed装饰器和\@ObjectLink装饰器：嵌套类对象属性变化](../../../ui/state-management/arkts-observed-and-objectlink.md)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
