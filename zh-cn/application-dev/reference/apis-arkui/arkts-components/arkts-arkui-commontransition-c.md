# CommonTransition

页面转场通用动效。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

转场通用动效的构造函数。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## opacity

```TypeScript
opacity(value: number): T
```

设置入场的起点透明度值或者退场的终点透明度值。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 设置入场的起点透明度值或者退场的终点透明度值。<br/>取值范围：[0, 1] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

## scale

```TypeScript
scale(value: ScaleOptions): T
```

设置页面转场时的缩放效果。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ScaleOptions | 是 | 设置页面转场时的缩放效果，为入场时起点和退场时终点的值。<br/>- x：横向放大倍数（或缩小比例）。<br/>- y：纵向放大倍数（或缩小比例）。<br/>- z：竖向放大倍数（或缩小比例）。<br/>- centerX、centerY缩放中心点。centerX和centerY默认值是"50%"，即默认以页面的中心点为旋转中心点。<br/>- 中心点为(0, 0)代表页面的左上角。<br>**起始版本：** 18 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

## slide

```TypeScript
slide(value: SlideEffect): T
```

设置页面转场时的滑入滑出效果。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | SlideEffect | 是 | 页面转场时的滑入滑出效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

## translate

```TypeScript
translate(value: TranslateOptions): T
```

设置页面转场时的平移效果。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | TranslateOptions | 是 | 设置页面转场时的平移效果，为入场时起点和退场时终点的值，和slide同时设置时默认生效slide。<br/>- x：横向的平移距离。<br/>- y：纵向的平移距离。<br/>- z：竖向的平移距离。<br>**起始版本：** 18 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前组件。 |

