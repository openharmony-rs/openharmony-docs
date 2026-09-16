# @ComponentActive

```TypeScript
export declare const ComponentActive: MethodDecorator
```

自定义组件由非激活状态转变为激活状态后，调用@ComponentActive装饰的函数。在组件回收复用场景下，当缓存的组件被重新复用（即从复用池重新添加到节点树）时，组件由非激活状态转为激活状态，触发此回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
