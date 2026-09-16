# @Component

```TypeScript
declare const Component: ClassDecorator & ((options: ComponentOptions) => ClassDecorator)
```

\@Component装饰器能装饰struct关键字声明的结构体。struct被\@Component装饰后具备组件化的能力，可实现UI的封装与复用，适用于构建可复用的自定义组件、拆分复杂界面等场景。使用时需要实现build方法描述UI，一个struct只能被一个\@Component装饰。

开发指南参考：[创建自定义组件](../../../ui/state-management/arkts-create-custom-components.md)。

> **说明：** 
> 
> - 从API version 11开始，\@Component可以接受一个可选的[ComponentOptions](arkts-arkui-componentoptions-i.md)类型参数。
> 
> - 从API版本26.0.0开始，ComponentOptions中可以接受可选参数`reusePool`和`poolAccepts`，用于配置全局复用池，开发指南参考：[全局复用：集中化的组件回收与复用](../../../ui/state-management/arkts-global-reuse-pool.md)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
