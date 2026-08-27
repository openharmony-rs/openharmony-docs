# RowOptionsV2

设置Row组件的子组件间距属性。间距类型SpaceType支持number、string或Resource类型。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## space

```TypeScript
space?: SpaceType
```

横向布局元素间距。取值范围：大于等于0。从API version 9开始，justifyContent设置为FlexAlign.SpaceBetween、FlexAlign.SpaceAround、FlexAlign.SpaceEvenly时space参数不生效。默认值：0单位：vp非法值：按默认值处理。  
**说明：**space取值是大于等于0的数字，或者可以转换为非负数字的字符串，或者可以转换为数字的Resource类型数据。负数作为非法值将被当作默认值0处理。

**类型：** [SpaceType](arkts-arkui-spacetype-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
