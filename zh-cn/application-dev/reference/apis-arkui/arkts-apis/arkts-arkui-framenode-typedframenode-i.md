# TypedFrameNode

TypedFrameNode继承自[FrameNode](arkts-arkui-framenode-c.md)，用于声明具体类型的FrameNode，支持Text、Image、Button、Column等多种组件类型，适用于通过代码动态创建具体类型组件节 点的场景。

**继承/实现关系：** TypedFrameNode extends [FrameNode](arkts-arkui-framenode-c.md)

**起始版本：** 12

<!--Device-unnamed-export interface TypedFrameNode--><!--Device-unnamed-export interface TypedFrameNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attribute

```TypeScript
readonly attribute: T
```

该接口用于获取对应组件的属性设置对象，以设置/更新组件的通用、私有属性。

**类型：** T

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TypedFrameNode-readonly attribute: T--><!--Device-TypedFrameNode-readonly attribute: T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## initialize

```TypeScript
initialize: C
```

该接口用于传入对应组件的构造参数，以设置/更新组件的初始值。

**类型：** C

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TypedFrameNode-initialize: C--><!--Device-TypedFrameNode-initialize: C-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

