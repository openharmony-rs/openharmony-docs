# @ComponentBuilt

```TypeScript
export declare const ComponentBuilt: MethodDecorator
```

\@ComponentBuilt装饰的函数在自定义组件的build()函数首次执行后调用，即从CustomComponentLifecycleState.APPEARED到CustomComponentLifecycleState.BUILT的阶段触发。开发者可以在此阶段实现埋点数据上报等不影响实际UI的功能。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
