# @ComponentInactive

```TypeScript
export declare const ComponentInactive: MethodDecorator
```

自定义组件由激活状态转变为非激活状态后，调用@ComponentInactive装饰的函数。在组件回收复用场景下，当组件被回收到复用池时，组件由激活状态转为非激活状态，触发此回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
