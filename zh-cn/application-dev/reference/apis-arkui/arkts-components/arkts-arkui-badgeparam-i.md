# BadgeParam

包含用于创建Badge组件的基础参数。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## position

```TypeScript
position?: BadgePosition | Position
```

设置标记显示位置。默认值：BadgePosition.RightTop  
**说明：**Position作为入参，不支持设置百分比；设置为非法值时，按(0,0)处理，(0,0)为组件左上角位置。BadgePosition作为入参时，会跟随Direction属性控制镜像显示。

**类型：** [BadgePosition](arkts-arkui-badgeposition-e.md) \| Position

**默认值：** BadgePosition.RightTop

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style: BadgeStyle
```

Badge组件可设置样式，支持设置文本颜色、大小、标记颜色和标记大小。

**类型：** [BadgeStyle](arkts-arkui-badgestyle-i.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
