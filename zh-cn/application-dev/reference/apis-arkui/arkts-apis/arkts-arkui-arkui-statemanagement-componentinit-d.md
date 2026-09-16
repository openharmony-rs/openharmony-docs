# @ComponentInit

```TypeScript
export declare const ComponentInit: MethodDecorator
```

\@ComponentInit装饰的函数在自定义组件初始化即将完成时执行，先于\@ComponentAppear触发。开发者可以在此时注册生命周期监听器和修改状态变量。与\@ComponentAppear的区别在于：\@ComponentInit侧重于初始化阶段的准备操作（如注册监听），\@ComponentAppear侧重于组件即将展现前的状态变更，两者配合使用可分别承担初始化与显现前的职责。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
