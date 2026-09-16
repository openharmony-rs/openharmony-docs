# @ComponentV2

```TypeScript
declare const ComponentV2: ClassDecorator & ((options: ComponentOptions) => ClassDecorator)
```

@ComponentV2主要配合状态管理V2使用，相比[\@Component](../../../ui/state-management/arkts-create-custom-components.md#component)，@ComponentV2支持对象的深度观测和深度监听，装饰器易用性高、拓展性强，适用于需要深度观测嵌套对象状态的场景。除非特别说明，@ComponentV2装饰的自定义组件将与@Component装饰的自定义组件保持相同的行为。

开发指南参考：[\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2)。

> **说明：** 
> 
> - 从API版本26.0.0开始，\@ComponentV2的[ComponentOptions](arkts-arkui-componentoptions-i.md)参数支持可选属性`reusePool`和`poolAccepts`，用于配置全局复用池，开发指南参考：[全局复用：集中化的组件回收与复用](../../../ui/state-management/arkts-global-reuse-pool.md)。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
