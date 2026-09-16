# @Param

```TypeScript
declare const Param: PropertyDecorator
```

@Param在状态管理V2中用于接收外部输入，实现父子组件之间的单向数据同步。适用于父组件需要向子组件单向传递状态数据的场景，能够简化组件间通信，保证数据流向清晰。@Param装饰的变量不允许在组件内部直接修改，如需子组件向父组件同步数据，请配合@Event使用。

开发指南参考：[

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
