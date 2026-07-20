# Divider属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。

**继承/实现关系：** DividerAttribute extends [CommonMethod<DividerAttribute>](CommonMethod<DividerAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class DividerAttribute extends CommonMethod<DividerAttribute>--><!--Device-unnamed-declare class DividerAttribute extends CommonMethod<DividerAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="color"></a>
## color

```TypeScript
color(value: ResourceColor)
```

设置分割线的颜色，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-DividerAttribute-color(value: ResourceColor): DividerAttribute--><!--Device-DividerAttribute-color(value: ResourceColor): DividerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 分割线颜色。<br/>默认值：'#33182431' <br />非法值：按默认值处理。 <br/>支持通过[WithTheme](../arkts-apis/arkts-with_theme.md)设置通用分割线颜色。 |

<a id="linecap"></a>
## lineCap

```TypeScript
lineCap(value: LineCapStyle)
```

设置分割线的端点样式，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-DividerAttribute-lineCap(value: LineCapStyle): DividerAttribute--><!--Device-DividerAttribute-lineCap(value: LineCapStyle): DividerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LineCapStyle](../arkts-apis/arkts-arkui-linecapstyle-e.md) | 是 | 分割线的端点样式。<br/>默认值：LineCapStyle.Butt <br />非法值：按默认值处理。 |

<a id="strokewidth"></a>
## strokeWidth

```TypeScript
strokeWidth(value: number | string)
```

设置分割线的宽度，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

> **说明：**  
>  
> - 分割线的宽度不支持百分比设置。  
>  
> - 使用水平分割线时，strokeWidth控制高度，优先级低于通用属性[height](arkts-arkui-commonmethod-c.md#height-1)；使用垂直分割线时，strokeWidth控制宽度，优  
> 先级低于通用属性[width](arkts-arkui-commonmethod-c.md#width-1)。  
>  
> - 超过通用属性设置大小时，按照通用属性进行裁切。  
>  
> - 如果设备硬件存在1像素取整后分割线不显示问题，建议使用2像素。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-DividerAttribute-strokeWidth(value: number | string): DividerAttribute--><!--Device-DividerAttribute-strokeWidth(value: number | string): DividerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 | 分割线宽度。<br/>默认值：1px <br />非法值：按默认值处理。 <br/>单位：vp |

<a id="vertical"></a>
## vertical

```TypeScript
vertical(value: boolean)
```

设置分割线的方向，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-DividerAttribute-vertical(value: boolean): DividerAttribute--><!--Device-DividerAttribute-vertical(value: boolean): DividerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 使用水平分割线还是垂直分割线。<br/>false：水平分割线；true：垂直分割线。<br/>默认值：false <br />非法值：按默认值处理。 |

