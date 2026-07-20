# NestedScrollInfo

嵌套可滚动容器组件信息

**起始版本：** 14

<!--Device-unnamed-declare interface NestedScrollInfo--><!--Device-unnamed-declare interface NestedScrollInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## child

```TypeScript
child: Scroller
```

可滚动容器组件的控制器，child对应的组件需要是parent对应组件的子组件，且组件间存在嵌套滚动关系。

**类型：** Scroller

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-NestedScrollInfo-child: Scroller--><!--Device-NestedScrollInfo-child: Scroller-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## parent

```TypeScript
parent: Scroller
```

可滚动容器组件的控制器。

**类型：** Scroller

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-NestedScrollInfo-parent: Scroller--><!--Device-NestedScrollInfo-parent: Scroller-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

