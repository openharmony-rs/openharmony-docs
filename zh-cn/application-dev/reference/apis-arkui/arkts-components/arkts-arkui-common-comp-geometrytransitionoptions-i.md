# GeometryTransitionOptions

```TypeScript
declare interface GeometryTransitionOptions
```

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## follow

```TypeScript
follow?: boolean
```

仅用于if范式下标记始终在组件树上的组件是否跟随共享元素转场。if范式是指在build()方法中使用if条件语句控制组件显隐的声明式UI开发模式。true表示跟随共享元素转场，false表示不跟随共享元素转场。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
