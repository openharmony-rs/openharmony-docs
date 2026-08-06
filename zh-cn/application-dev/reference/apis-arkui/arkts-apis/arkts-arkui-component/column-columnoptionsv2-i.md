# ColumnOptionsV2

设置Column组件的子组件间距属性。间距类型SpaceType支持number、string或Resource类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface ColumnOptionsV2--><!--Device-unnamed-export interface ColumnOptionsV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: SpaceType
```

纵向布局元素垂直方向间距。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_ space为负数或者justifyContent设置为FlexAlign.SpaceBetween、FlexAlign.SpaceAround、 FlexAlign.SpaceEvenly时，space不生效。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_ 默认值：0\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ 单位：vp\_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_ 非法值：按默认值处理。\_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_ **说明：**\_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_ space取值是大于等于0的数字，或者可以转换为数字的字符串， 或者可以转换为数字的Resource类型数据。

**类型：** SpaceType

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColumnOptionsV2-space?: SpaceType--><!--Device-ColumnOptionsV2-space?: SpaceType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

