# ShapeMask

用于设置图形遮罩。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class ShapeMask--><!--Device-unnamed-export declare class ShapeMask-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

ShapeMask的构造函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeMask-constructor()--><!--Device-ShapeMask-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setCircleShape

```TypeScript
setCircleShape(circle: Circle): void
```

用于设置圆形遮罩。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeMask-setCircleShape(circle: Circle): void--><!--Device-ShapeMask-setCircleShape(circle: Circle): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| circle | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 圆形的形状。 |

## setCommandPath

```TypeScript
setCommandPath(path: CommandPath): void
```

用于设置路径绘制指令。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeMask-setCommandPath(path: CommandPath): void--><!--Device-ShapeMask-setCommandPath(path: CommandPath): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 路径绘制指令。 |

## setOvalShape

```TypeScript
setOvalShape(oval: Rect): void
```

用于设置椭圆形遮罩。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeMask-setOvalShape(oval: Rect): void--><!--Device-ShapeMask-setOvalShape(oval: Rect): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oval | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 椭圆形的形状。 |

## setRectShape

```TypeScript
setRectShape(rect: Rect): void
```

用于设置矩形遮罩。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeMask-setRectShape(rect: Rect): void--><!--Device-ShapeMask-setRectShape(rect: Rect): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 矩形的形状。 |

## setRoundRectShape

```TypeScript
setRoundRectShape(roundRect: RoundRect): void
```

用于设置圆角矩形遮罩。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeMask-setRoundRectShape(roundRect: RoundRect): void--><!--Device-ShapeMask-setRoundRectShape(roundRect: RoundRect): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| roundRect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 圆角矩形的形状。 |

## fillColor

```TypeScript
fillColor: int
```

遮罩的填充颜色，使用ARGB格式。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。 通过fillColor的透明度和亮度生成一个仅含透明度的颜色。亮度越高，颜色越透明。然后，使用[BlendMode.SRC\_IN]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_方式 与RenderNode本身的颜色混合，生成最终颜色。 取值限定为整数。

**类型：** int

**默认值：** 0XFF000000

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeMask-fillColor: int--><!--Device-ShapeMask-fillColor: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeColor

```TypeScript
strokeColor: int
```

遮罩的边框颜色，使用ARGB格式。默认值为\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_。 通过strokeColor的透明度和亮度生成一个仅含透明度的颜色。亮度越高，颜色越透明。然后，使用[BlendMode.SRC\_IN]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 方式与RenderNode本身的颜色混合，生成最终颜色。 取值限定为整数。

**类型：** int

**默认值：** 0XFF000000

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeMask-strokeColor: int--><!--Device-ShapeMask-strokeColor: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth: double
```

遮罩的边框宽度，单位为px。默认值为0。

**类型：** double

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ShapeMask-strokeWidth: double--><!--Device-ShapeMask-strokeWidth: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

