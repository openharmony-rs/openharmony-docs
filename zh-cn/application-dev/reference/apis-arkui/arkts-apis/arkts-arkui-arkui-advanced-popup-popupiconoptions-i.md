# PopupIconOptions

PopupIconOptions定义图标的属性。

**起始版本：** 11

<!--Device-unnamed-export interface PopupIconOptions--><!--Device-unnamed-export interface PopupIconOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Popup, PopupOptions, PopupButtonOptions, PopupIconOptions, PopupTextOptions } from '@kit.ArkUI';
```

## borderRadius

```TypeScript
borderRadius?: Length | BorderRadiuses
```

设置图标圆角。

默认值：`$r('sys.float.ohos_id_corner_radius_default_s')`

**类型：** Length | BorderRadiuses

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupIconOptions-borderRadius?: Length | BorderRadiuses--><!--Device-PopupIconOptions-borderRadius?: Length | BorderRadiuses-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fillColor

```TypeScript
fillColor?: ResourceColor
```

设置图标填充颜色。仅针对svg图源生效。

默认不改变图标颜色。

**类型：** ResourceColor

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupIconOptions-fillColor?: ResourceColor--><!--Device-PopupIconOptions-fillColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Dimension
```

设置图标高度。

默认值：32VP

**类型：** Dimension

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupIconOptions-height?: Dimension--><!--Device-PopupIconOptions-height?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## image

```TypeScript
image: ResourceStr
```

设置图标内容。

**类型：** ResourceStr

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupIconOptions-image: ResourceStr--><!--Device-PopupIconOptions-image: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

设置图标宽度。

默认值：32VP

**类型：** Dimension

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupIconOptions-width?: Dimension--><!--Device-PopupIconOptions-width?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

