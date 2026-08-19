# GuideLinePosition

guideLine位置参数，用于定义guideLine的位置。

**起始版本：** 12

<!--Device-unnamed-declare interface GuideLinePosition--><!--Device-unnamed-declare interface GuideLinePosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## end

```TypeScript
end? : Dimension
```

guideLine距离容器右侧或者底部的距离。单位：vp。与start二选一，若同时声明则仅start生效。若容器的width被声明为"auto"，则Axis.Vertical类型的guideLine不支持使用end方式声明；若容 器的height被声明为"auto"，则Axis.Horizontal类型的guideLine不支持使用end方式声明。

**类型：** Dimension

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GuideLinePosition-end? : Dimension--><!--Device-GuideLinePosition-end? : Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start? : Dimension
```

guideLine距离容器左侧或者顶部的距离。单位：vp。 默认值：0。与end二选一，若同时声明则仅start生效。若容器的width被声明为"auto"，则Axis.Vertical类型的guideLine只能使用start方式声明（不允许使用百分比）；若容器的height被声明为" auto"，则Axis.Horizontal类型的guideLine只能使用start方式声明（不允许使用百分比）。

**类型：** Dimension

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-GuideLinePosition-start? : Dimension--><!--Device-GuideLinePosition-start? : Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

