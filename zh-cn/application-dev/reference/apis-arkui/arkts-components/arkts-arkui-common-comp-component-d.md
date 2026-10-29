# @Component

```TypeScript
declare const Component: ClassDecorator & ((options: ComponentOptions) => ClassDecorator)
```

\@Component装饰器能装饰struct关键字声明的结构体。struct被\@Component装饰后具备组件化的能力，可实现UI的封装与复用，适用于构建可复用的自定义组件、拆分复杂界面等场景。使用时需要实现build方法描述UI，一个struct只能被一个\@Component装饰。

开发指南参考：[创建自定义组件](../../../ui/state-management/arkts-create-custom-components.md)。

> **说明：** 
> 
> - 从API version 11开始，\@Component可以接受一个可选的[ComponentOptions](arkts-arkui-common-comp-componentoptions-i.md)类型参数。
> 
> - 从API版本26.0.0开始，ComponentOptions中可以接受可选参数`reusePool`和`poolAccepts`，用于配置全局复用池，开发指南参考：[全局复用：集中化的组件回收与复用](../../../ui/state-management/arkts-global-reuse-pool.md)。

options：\@Component装饰器选项，用于配置组件冻结和全局复用。可通过freezeWhenInactive控制组件冻结（适用于页面路由、TabContent、LazyForEach、Navigation等组件非激活时冻结UI刷新以减少不必要刷新、优化性能的场景），通过reusePool和poolAccepts配置全局复用池（适用于多个父组件共用同类可复用组件、通过if等切换时需跨父组件复用已回收实例的场景），具体属性详见ComponentOptions。缺省时关闭组件冻结和全局复用功能。ClassDecorator：类装饰器，开发者无需关注该返回值。

**起始版本：** 7

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare const Component: ClassDecorator & ((options: ComponentOptions) => ClassDecorator)--><!--Device-unnamed-declare const Component: ClassDecorator & ((options: ComponentOptions) => ClassDecorator)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
