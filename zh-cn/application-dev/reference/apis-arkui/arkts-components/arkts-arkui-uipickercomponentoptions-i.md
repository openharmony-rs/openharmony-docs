# UIPickerComponentOptions

UIPickerComponent容器的参数说明。

**起始版本：** 22

<!--Device-unnamed-declare interface UIPickerComponentOptions--><!--Device-unnamed-declare interface UIPickerComponentOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## selectedIndex

```TypeScript
selectedIndex?: number
```

选中项的索引值，用于指定初始选中的选项。 > 取值范围：[0, 子组件的个数-1]内的整数。不在取值范围内时，使用默认值；设置小数时，使用向下取整后的整数。 > 默认值：0。当需要组件初始显示特定选项时传入此参数。 > **说明：** > > 统计子组件的个数时，不包含Row容器内的子组件，Row容器及其子组件共同视为1个子组件。

**类型：** number

**默认值：** 0

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIPickerComponentOptions-selectedIndex?: number--><!--Device-UIPickerComponentOptions-selectedIndex?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

