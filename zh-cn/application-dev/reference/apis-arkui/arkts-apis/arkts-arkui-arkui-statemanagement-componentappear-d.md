# @ComponentAppear

```TypeScript
export declare const ComponentAppear: MethodDecorator
```

与aboutToAppear相似，\@ComponentAppear装饰的函数在创建自定义组件的新实例后，在其build()函数执行前调用，不同的是，\@ComponentAppear装饰的函数仅在自定义组件处于[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).INIT状态才会触发。允许在\@ComponentAppear装饰的函数中改变状态变量，更改将在后续执行build()函数中生效。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
