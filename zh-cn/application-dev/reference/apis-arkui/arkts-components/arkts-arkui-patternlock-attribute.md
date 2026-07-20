# PatternLock属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性。

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件。

**继承/实现关系：** PatternLockAttribute extends [CommonMethod<PatternLockAttribute>](CommonMethod<PatternLockAttribute>)

**起始版本：** 9

<!--Device-unnamed-declare class PatternLockAttribute extends CommonMethod<PatternLockAttribute>--><!--Device-unnamed-declare class PatternLockAttribute extends CommonMethod<PatternLockAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="activatecirclestyle"></a>
## activateCircleStyle

```TypeScript
activateCircleStyle(options: Optional<CircleStyleOptions>)
```

设置宫格圆点在“激活”状态下的背景圆环样式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PatternLockAttribute-activateCircleStyle(options: Optional<CircleStyleOptions>): PatternLockAttribute--><!--Device-PatternLockAttribute-activateCircleStyle(options: Optional<CircleStyleOptions>): PatternLockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-optional-t.md)&lt;CircleStyleOptions&gt; | 是 | 宫格圆点在“激活”状态的背景圆环样式。 |

<a id="activecolor"></a>
## activeColor

```TypeScript
activeColor(value: ResourceColor)
```

设置宫格圆点在“激活”状态的填充颜色，“激活”状态为手指经过圆点但还未选中的状态。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PatternLockAttribute-activeColor(value: ResourceColor): PatternLockAttribute--><!--Device-PatternLockAttribute-activeColor(value: ResourceColor): PatternLockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 宫格圆点在“激活”状态的填充颜色。<br/>默认值：'#ff182431' |

<a id="autoreset"></a>
## autoReset

```TypeScript
autoReset(value: boolean)
```

设置在完成密码输入后再次在组件区域按下时是否重置组件状态。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PatternLockAttribute-autoReset(value: boolean): PatternLockAttribute--><!--Device-PatternLockAttribute-autoReset(value: boolean): PatternLockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 在完成密码输入后再次在组件区域按下时是否重置组件状态。<br/>true：完成密码输入后再次在组件区域按下时重置组件状态（即清除之前输入的密码）；false：完成密码输入后再次在组件区域按下时不重置组件状态。<br/>默认值：true |

<a id="backgroundcolor"></a>
## backgroundColor

```TypeScript
backgroundColor(value: ResourceColor)
```

设置背景颜色。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PatternLockAttribute-backgroundColor(value: ResourceColor): PatternLockAttribute--><!--Device-PatternLockAttribute-backgroundColor(value: ResourceColor): PatternLockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 背景颜色。 |

<a id="circleradius"></a>
## circleRadius

```TypeScript
circleRadius(value: Length)
```

设置宫格中圆点的半径。设置为0或负数时，取默认值。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PatternLockAttribute-circleRadius(value: Length): PatternLockAttribute--><!--Device-PatternLockAttribute-circleRadius(value: Length): PatternLockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 宫格中圆点的半径。<br/>默认值：6vp<br/>取值范围：(0, sideLength/11]。设置小于等于0的值时，按默认值处理；超过最大值时，按最大值处理。 |

<a id="ondotconnect"></a>
## onDotConnect

```TypeScript
onDotConnect(callback: import('../api/@ohos.base').Callback<number>)
```

密码输入选中宫格圆点时触发该回调。

回调参数为选中宫格圆点顺序的数字，数字为选中宫格圆点的索引值（第一行圆点从左往右依次为0、1、2，第二行圆点从左往右依次为3、4、5，第三行圆点从左往右依次为6、7、8）。

> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PatternLockAttribute-onDotConnect(callback: import('../api/@ohos.base').Callback<number>): PatternLockAttribute--><!--Device-PatternLockAttribute-onDotConnect(callback: import('../api/@ohos.base').Callback<number>): PatternLockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | import('../api/@ohos.base').Callback&lt;number&gt; | 是 | 密码输入选中宫格圆点时触发该回调。 |

<a id="onpatterncomplete"></a>
## onPatternComplete

```TypeScript
onPatternComplete(callback: (input: Array<number>) => void)
```

密码输入结束时触发该回调。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PatternLockAttribute-onPatternComplete(callback: (input: Array<number>) => void): PatternLockAttribute--><!--Device-PatternLockAttribute-onPatternComplete(callback: (input: Array<number>) => void): PatternLockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (input: Array&lt;number&gt;) =&gt; void | 是 | 与选中宫格圆点顺序一致的数字数组，每个数字表示选中宫格圆点的索引值（第一行圆点从左往右依次为0、1、2，第二行圆点从左往右依次为3、4、5，第三行圆点从左往右依次为6、7、8）。 |

<a id="pathcolor"></a>
## pathColor

```TypeScript
pathColor(value: ResourceColor)
```

设置连线的颜色。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PatternLockAttribute-pathColor(value: ResourceColor): PatternLockAttribute--><!--Device-PatternLockAttribute-pathColor(value: ResourceColor): PatternLockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 连线的颜色。<br/>默认值：'#33182431' |

<a id="pathstrokewidth"></a>
## pathStrokeWidth

```TypeScript
pathStrokeWidth(value: number | string)
```

设置连线的宽度。设置为0或负数时连线不显示。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PatternLockAttribute-pathStrokeWidth(value: number | string): PatternLockAttribute--><!--Device-PatternLockAttribute-pathStrokeWidth(value: number | string): PatternLockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string | 是 | 连线的宽度。<br/>默认值：12vp<br/>取值范围：(0, sideLength/3]，设置为0或负数时连线不显示，超过最大值按最大值处理。 |

<a id="regularcolor"></a>
## regularColor

```TypeScript
regularColor(value: ResourceColor)
```

设置宫格圆点在“未选中”状态的填充颜色。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PatternLockAttribute-regularColor(value: ResourceColor): PatternLockAttribute--><!--Device-PatternLockAttribute-regularColor(value: ResourceColor): PatternLockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 宫格圆点在“未选中”状态的填充颜色。<br/>默认值：'#ff182431' |

<a id="selectedcolor"></a>
## selectedColor

```TypeScript
selectedColor(value: ResourceColor)
```

设置宫格圆点在“选中”状态的填充颜色。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PatternLockAttribute-selectedColor(value: ResourceColor): PatternLockAttribute--><!--Device-PatternLockAttribute-selectedColor(value: ResourceColor): PatternLockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 宫格圆点在“选中”状态的填充颜色。<br/>默认值：'#ff182431' |

<a id="sidelength"></a>
## sideLength

```TypeScript
sideLength(value: Length)
```

设置组件的宽度和高度（宽高相同）。当设置为0或负数时，组件不显示。

> **说明：**  
>  
> PatternLock组件设置了通用属性宽高比[aspectRatio](arkts-arkui-commonmethod-c.md#aspectratio-1)，且不等于1时（组件尺寸被设定为长方形），九宫格依然绘制为正方形（超出组件范围）。

**起始版本：** 9

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PatternLockAttribute-sideLength(value: Length): PatternLockAttribute--><!--Device-PatternLockAttribute-sideLength(value: Length): PatternLockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 组件的宽度和高度。默认值：288vp |

<a id="skipunselectedpoint"></a>
## skipUnselectedPoint

```TypeScript
skipUnselectedPoint(skipped: boolean)
```

设置未选中的宫格圆点在密码路径经过时是否自动选中。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-PatternLockAttribute-skipUnselectedPoint(skipped: boolean): PatternLockAttribute--><!--Device-PatternLockAttribute-skipUnselectedPoint(skipped: boolean): PatternLockAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| skipped | boolean | 是 | 未选中的宫格圆点在密码路径经过时是否自动选中。<br/>true：跳过选中密码路径经过的宫格圆点；false：自动选中密码路径经过的宫格圆点。默认值：false。 |

