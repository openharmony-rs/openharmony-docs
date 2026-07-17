# CommonShapeMethod

常见的形状方法。

**起始版本：** 12

<!--Device-unnamed-declare class CommonShapeMethod<T>--><!--Device-unnamed-declare class CommonShapeMethod<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## fill

```TypeScript
fill(color: ResourceColor): T
```

设置形状的填充区域的透明度，黑色表示完全透明，白色表示完全不透明。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-fill(color: ResourceColor): T--><!--Device-CommonShapeMethod-fill(color: ResourceColor): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [ResourceColor](arkts-arkui-resourcecolor-t.md) | 是 | 形状的填充区域的透明度，黑色表示完全透明，白色表示完全不透明。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前对象。 |

## offset

```TypeScript
offset(offset: Position): T
```

设置相对于组件布局位置的坐标偏移。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-offset(offset: Position): T--><!--Device-CommonShapeMethod-offset(offset: Position): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | [Position](arkts-arkui-display-position-i.md) | 是 | 相对于组件布局位置的坐标偏移。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前对象。 |

## position

```TypeScript
position(position: Position): T
```

设置形状的位置。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-CommonShapeMethod-position(position: Position): T--><!--Device-CommonShapeMethod-position(position: Position): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [Position](arkts-arkui-display-position-i.md) | 是 | 设置形状的位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前对象。 |

