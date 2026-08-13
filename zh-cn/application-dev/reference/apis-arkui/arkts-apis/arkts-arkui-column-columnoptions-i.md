# ColumnOptions

设置Column组件的子组件间距属性。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface ColumnOptions--><!--Device-unnamed-export interface ColumnOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: string | double
```

纵向布局元素垂直方向间距。&lt;br&gt; space为负数或者 [justifyContent](../../../reference/apis-arkui/arkui-ts/ts-container-column.md#justifycontent8) 设置为FlexAlign.SpaceBetween、FlexAlign.SpaceAround、FlexAlign.SpaceEvenly时，space不生效。&lt;br&gt; 默认值：0&lt;br&gt; 非法值：按默认值处理。&lt;br&gt; 单位：vp&lt;br&gt; **说明：**&lt;br&gt; space取值是大于等于0的数字，或者可以转换为数字的字符串。

**类型：** string \| double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ColumnOptions-space?: string | double--><!--Device-ColumnOptions-space?: string | double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

