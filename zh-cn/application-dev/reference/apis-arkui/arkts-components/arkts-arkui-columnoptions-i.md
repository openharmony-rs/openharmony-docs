# ColumnOptions

设置Column组件的子组件间距属性。
> **说明：**  
>  
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

<!--Device-unnamed-interface ColumnOptions--><!--Device-unnamed-interface ColumnOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: string | number
```

纵向布局元素垂直方向间距。

space为负数或者[justifyContent](ColumnAttribute#justifyContent)设置为FlexAlign.SpaceBetween、FlexAlign.SpaceAround、FlexAlign.SpaceEvenly时，space不生效。

默认值：0

非法值：按默认值处理。

单位：vp

**说明：**

space取值是大于等于0的数字，或者可以转换为数字的字符串。

**类型：** string \| number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ColumnOptions-space?: string | number--><!--Device-ColumnOptions-space?: string | number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

