# Divider属性/事件

除支持通用属性外，还支持以下属性：支持通用事件。

**继承/实现关系：** DividerAttribute extends CommonMethod<DividerAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## color

```TypeScript
color(value: ResourceColor)
```

设置分割线的颜色，支持attributeModifier动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 分割线颜色。默认值：'#33182431' 非法值：按默认值处理。 支持通过 WithTheme设置通用分割线颜色。 |

## lineCap

```TypeScript
lineCap(value: LineCapStyle)
```

设置分割线的端点样式，支持attributeModifier动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LineCapStyle](../arkts-apis/arkts-arkui-linecapstyle-e.md) | 是 | 分割线的端点样式。默认值：LineCapStyle.Butt 非法值：按默认值处理。 |

## strokeWidth

```TypeScript
strokeWidth(value: number | string)
```

设置分割线的宽度，支持attributeModifier动态设置属性方法。

> **说明：**
> 
> - 分割线的宽度不支持百分比设置。
> 
> - 使用水平分割线时，strokeWidth控制高度，优先级低于通用属性height；使用垂直分割线时，strokeWidth控制宽度，优
> 先级低于通用属性width。
> 
> - 超过通用属性设置大小时，按照通用属性进行裁切。
> 
> - 如果设备硬件存在1像素取整后分割线不显示问题，建议使用2像素。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 | 分割线宽度。默认值：1px 非法值：按默认值处理。 单位：vp |

## vertical

```TypeScript
vertical(value: boolean)
```

设置分割线的方向，支持attributeModifier动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 使用水平分割线还是垂直分割线。false：水平分割线；true：垂直分割线。默认值：false 非法值：按默认值处理。 |
