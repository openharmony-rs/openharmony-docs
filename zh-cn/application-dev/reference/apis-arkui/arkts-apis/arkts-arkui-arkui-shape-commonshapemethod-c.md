# CommonShapeMethod

提供形状的偏移、填充和位置设置等通用方法的基类。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## fill

```TypeScript
fill(color: ResourceColor): T
```

设置形状的填充颜色。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [ResourceColor](arkts-arkui-resourcecolor-t.md) | 是 | 形状的填充区域的透明度，黑色表示完全透明，白色表示完全不透明。在maskShape场景下，填充颜色决定了遮罩的透明度效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前对象，用于链式调用。 |

## offset

```TypeScript
offset(offset: Position): T
```

设置相对于组件布局位置的坐标偏移。

> **说明：** 
> 
> - offset()设置相对偏移，position()设置绝对位置，两者定位机制不同。
> 
> - 建议根据场景选择使用其中一种定位方式，避免同时设置导致定位结果难以预测。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | Position | 是 | 相对于组件布局位置的坐标偏移。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前对象，用于链式调用。 |

## position

```TypeScript
position(position: Position): T
```

设置形状的绝对位置。与offset（相对偏移）不同，position设置的是绝对坐标；需要精确定位形状时使用position，需要在现有布局位置上微调时使用offset。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | Position | 是 | 形状的位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前对象，用于链式调用。 |
