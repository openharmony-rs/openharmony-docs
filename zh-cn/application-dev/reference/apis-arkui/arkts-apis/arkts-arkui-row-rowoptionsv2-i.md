# RowOptionsV2

设置Row组件的子组件间距属性。 间距类型SpaceType支持number、string或Resource类型。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface RowOptionsV2--><!--Device-unnamed-export interface RowOptionsV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: SpaceType
```

横向布局元素间距。 space为负数或者justifyContent设置为FlexAlign.SpaceBetween、 FlexAlign.SpaceAround、FlexAlign.SpaceEvenly时不生效。 默认值：0 单位：vp 非法值：按默认值处理。

**类型：** [SpaceType](../arkts-components/arkts-arkui-spacetype-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RowOptionsV2-space?: SpaceType--><!--Device-RowOptionsV2-space?: SpaceType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

