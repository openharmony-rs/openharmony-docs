# @ComponentRecycle

```TypeScript
export declare const ComponentRecycle: MethodDecorator
```

当组件被回收后，先执行应用程序中定义的资源释放等回收操作，完成回收后调用\@ComponentRecycle装饰的函数，即从CustomComponentLifecycleState.BUILT到CustomComponentLifecycleState.RECYCLED阶段触发。随后该组件被冻结，以避免该组件处于复用池时进行UI更新。最后，回收会递归遍历所有子组件，对每个完成回收的子组件调用子组件中\@ComponentRecycle装饰的函数。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
