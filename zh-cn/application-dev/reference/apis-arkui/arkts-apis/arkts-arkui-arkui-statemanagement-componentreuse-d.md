# @ComponentReuse

```TypeScript
export declare const ComponentReuse: MethodDecorator
```

当可复用的自定义组件从缓存中重新添加到节点树时调用\@ComponentReuse装饰的函数，即从CustomComponentLifecycleState.RECYCLED到CustomComponentLifecycleState.BUILT阶段触发，以接收组件的构造参数。最后，复用会递归遍历所有子组件，对每个完成复用的子组件，会调用子组件中\@ComponentReuse装饰的函数。

> **说明：** 
> 
> - 在状态管理V1的组件里，\@ComponentReuse装饰的函数允许有一个入参或者无参。入参params建议为Record\&lt;string, Object \| undefined \| null\&gt;类型。
> 
> - 在状态管理V2的组件里，\@ComponentReuse装饰的函数没有入参。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
