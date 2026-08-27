# ListDividerOptions

用于设置List或ListItemGroup组件的分割线样式。

> **说明：**
> 
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## color

```TypeScript
color?: ResourceColor
```

分割线颜色。默认值：0x08000000

**类型：** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**默认值：** 0x08000000 [since 18]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## endMargin

```TypeScript
endMargin?: Length
```

分割线与列表侧边结束端的距离。默认值：0单位：vp  
**说明：**设置为负数或者百分比时，按默认值处理。endMargin + startMargin 超过列宽度后startMargin和endMargin均会被置0。

**类型：** [Length](../arkts-apis/arkts-arkui-length-t.md)

**默认值：** 0vp [since 18]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## startMargin

```TypeScript
startMargin?: Length
```

分割线与列表侧边起始端的距离。默认值：0单位：vp  
**说明：**设置为负数或者百分比时，按默认值处理。endMargin + startMargin 超过列宽度后startMargin和endMargin均会被置0。

**类型：** [Length](../arkts-apis/arkts-arkui-length-t.md)

**默认值：** 0vp [since 18]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth: Length
```

分割线的线宽。单位：vp  
**说明：**设置为负数，百分比，或者大于等于List内容区长度时，按0处理。

**类型：** [Length](../arkts-apis/arkts-arkui-length-t.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
