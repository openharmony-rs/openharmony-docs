# @ComponentDisappear

```TypeScript
export declare const ComponentDisappear: MethodDecorator
```

@ComponentDisappear装饰的函数在自定义组件销毁前执行，即向CustomComponentLifecycleState.DISAPPEARED状态转变时触发。不建议在此函数中改变状态变量，特别是\@Link变量的修改可能会导致应用程序行为不稳定。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
