# GeometryTransitionOptions

**起始版本：** 11

<!--Device-unnamed-declare interface GeometryTransitionOptions--><!--Device-unnamed-declare interface GeometryTransitionOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hierarchyStrategy

```TypeScript
hierarchyStrategy?: TransitionHierarchyStrategy
```

决定共享元素动画过程中in/out组件在组件树上层级位置的移动策略，默认值：TransitionHierarchyStrategy.ADAPTIVE。

实际影响绑定的in/out组件相对其他组件的前后重叠关系，常规情况下慎重修改。

建议在发现共享元素动画过程中出现组件前后重叠关系错误时需要调整再设置此参数。

**系统接口：** 此接口为系统接口。

**类型：** TransitionHierarchyStrategy

**默认值：** TransitionHierarchyStrategy.ADAPTIVE

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12 - 12开始，该接口支持在原子化服务API中使用。

<!--Device-GeometryTransitionOptions-hierarchyStrategy?: TransitionHierarchyStrategy--><!--Device-GeometryTransitionOptions-hierarchyStrategy?: TransitionHierarchyStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

