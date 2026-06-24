# TransitionHierarchyStrategy（系统接口）

```TypeScript
declare enum TransitionHierarchyStrategy
```

共享元素动画过程中in/out组件层级位置移动策略枚举。

| 名称 | 值 | 说明 |
| ------ | - | ---- |
| NONE | 0 | 无层级提拉，in/out组件保持原来的层级位置，受父组件scale、position影响。 |
| ADAPTIVE | 1 | 有层级提拉，in/out组件中相对低层级的组件被提拉至组件树上in/out组件相对高层级的位置上。

此模式还会导致被提拉的组件与父组件解绑，不受父组件scale、position影响。

例如in组件层级高于out组件，开启层级提拉后会在动画过程中将out组件从自己的父组件处解耦，并提拉至in组件的层级位置处，in组件层级位置不变。|

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

