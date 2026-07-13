# CloseOptions

CloseOptions用于定义Chip组件默认的关闭图标功能属性，包括无障碍功能属性，其中accessibilityText默认为"删除"。

继承于[AccessibilityOptions](arkts-arkui-accessibilityoptions-i.md)。

**继承/实现关系：** CloseOptions extends [AccessibilityOptions](arkts-arkui-accessibilityoptions-i.md)

**起始版本：** 14

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: Dimension
```

设置Chip组件默认关闭图标的大小，不支持百分比。

默认值：

size为ChipSize.SMALL时，`默认值：$r('sys.float.chip_small_font_size')`

其他情况默认值：`$r('sys.float.chip_normal_font_size')`

值为undefined时，按默认值处理。

**类型：** Dimension

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

