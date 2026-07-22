# ShapeClip

用于设置图形裁剪。

**起始版本：** 12

<!--Device-unnamed-export declare class ShapeClip--><!--Device-unnamed-export declare class ShapeClip-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

ShapeMask的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShapeClip-constructor()--><!--Device-ShapeClip-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setCircleShape

```TypeScript
setCircleShape(circle: Circle): void
```

用于裁剪圆形。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShapeClip-setCircleShape(circle: Circle): void--><!--Device-ShapeClip-setCircleShape(circle: Circle): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| circle | [Circle](arkts-arkui-graphics-circle-i.md) | 是 | 圆形的形状。 |

## setCommandPath

```TypeScript
setCommandPath(path: CommandPath): void
```

用于设置路径绘制指令。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShapeClip-setCommandPath(path: CommandPath): void--><!--Device-ShapeClip-setCommandPath(path: CommandPath): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | [CommandPath](arkts-arkui-graphics-commandpath-i.md) | 是 | 路径绘制指令。 |

## setOvalShape

```TypeScript
setOvalShape(oval: Rect): void
```

用于裁剪椭圆形。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShapeClip-setOvalShape(oval: Rect): void--><!--Device-ShapeClip-setOvalShape(oval: Rect): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oval | [Rect](../../apis-test-kit/arkts-apis/arkts-test-uitest-rect-i.md) | 是 | 椭圆形的形状。 |

## setRectShape

```TypeScript
setRectShape(rect: Rect): void
```

用于裁剪矩形。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShapeClip-setRectShape(rect: Rect): void--><!--Device-ShapeClip-setRectShape(rect: Rect): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | [Rect](../../apis-test-kit/arkts-apis/arkts-test-uitest-rect-i.md) | 是 | 矩形的形状。 |

## setRoundRectShape

```TypeScript
setRoundRectShape(roundRect: RoundRect): void
```

用于裁剪圆角矩形。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ShapeClip-setRoundRectShape(roundRect: RoundRect): void--><!--Device-ShapeClip-setRoundRectShape(roundRect: RoundRect): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| roundRect | [RoundRect](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-drawing-roundrect-c.md) | 是 | 圆角矩形的形状。 |

