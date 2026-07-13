# IconCommonOptions

IconCommonOptions定义图标的共通属性。

> **说明：**
>
> 仅在图片格式为SVG时，fillColor和activatedFillColor属性才生效。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## activatedFillColor

```TypeScript
activatedFillColor?: ResourceColor
```

操作块激活时图标填充颜色。

默认值：$r('sys.color.chip_active_icon_color')

值为undefined时，按默认值处理。

**类型：** ResourceColor

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fillColor

```TypeScript
fillColor?: ResourceColor
```

图标填充颜色。

默认值：$r('sys.color.chip_usually_icon_color')

值为undefined时，按默认值处理。

**类型：** ResourceColor

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeOptions
```

图标大小，不支持百分比。

默认值：

- 当ChipOptions.size为ChipSize.SMALL时，默认值为：{width: $r('sys.float.chip_small_icon_size'), height: $r('
sys.float.chip_small_icon_size')}
- 当ChipOptions.size为ChipSize.NORMAL时，默认值为：{width: $r('sys.float.chip_normal_icon_size'), height: $r('
sys.float.chip_normal_icon_size')}

单位：vp

值为undefined时，按默认值处理。

**类型：** SizeOptions

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: ResourceStr
```

图标图片或图片地址引用。

**类型：** ResourceStr

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

