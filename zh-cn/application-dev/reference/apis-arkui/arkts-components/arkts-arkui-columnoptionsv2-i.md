# ColumnOptionsV2

设置Column组件的子组件间距属性。间距类型SpaceType支持number、string或Resource类型。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-unnamed-interface ColumnOptionsV2--><!--Device-unnamed-interface ColumnOptionsV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: SpaceType
```

设置纵向布局元素垂直方向间距。 space为负数或者justifyContent设置为FlexAlign.SpaceBetween、FlexAlign.SpaceAround、 FlexAlign.SpaceEvenly时，space不生效。 取值范围：[0, +∞) 默认值：0 单位：vp 非法值：按默认值处理。 **说明：** space取值是大于等于0的数字，或者可以转换为非负数字的字符串，或者可以转换为数字的Resource类型数据。

**类型：** [SpaceType](arkts-arkui-spacetype-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-ColumnOptionsV2-space?: SpaceType--><!--Device-ColumnOptionsV2-space?: SpaceType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

