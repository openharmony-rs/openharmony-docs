# LazyGridLayoutAttribute

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件：

**继承/实现关系：** LazyGridLayoutAttribute extends [CommonMethod<T>]

**起始版本：** 19

<!--Device-unnamed-declare class LazyGridLayoutAttribute<T> extends CommonMethod<T>--><!--Device-unnamed-declare class LazyGridLayoutAttribute<T> extends CommonMethod<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## columnsGap

```TypeScript
columnsGap(value: LengthMetrics): T
```

设置列与列的间距。默认值为0vp，设置为小于0的值时，按默认值显示。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-LazyGridLayoutAttribute-columnsGap(value: LengthMetrics): T--><!--Device-LazyGridLayoutAttribute-columnsGap(value: LengthMetrics): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md) | 是 | 列与列的间距。<br/>取值范围：[0, +∞)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## footer

```TypeScript
footer(builder: CustomBuilder | undefined): T
```

设置LazyVGridLayout的尾部组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyGridLayoutAttribute-footer(builder: CustomBuilder | undefined): T--><!--Device-LazyGridLayoutAttribute-footer(builder: CustomBuilder | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | CustomBuilder \| undefined | 是 | 尾部组件构建函数。<br>传入undefined时移除尾部组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## header

```TypeScript
header(builder: CustomBuilder | undefined): T
```

设置LazyVGridLayout的头部组件。

> **说明：**  
>  
> 头部组件位于容器顶部区域，通常用于展示标题、分组说明或其他固定在内容前方的元素。  
>  
> 当本组件随滚动容器滚动至可视区域内，且通过[sticky](#sticky)设置了header吸顶模式时，header会吸附在滚动容器可视区域顶部。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyGridLayoutAttribute-header(builder: CustomBuilder | undefined): T--><!--Device-LazyGridLayoutAttribute-header(builder: CustomBuilder | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | CustomBuilder \| undefined | 是 | 头部组件构造函数。<br/>方法入参为undefined时，当前LazyVGridLayout不设置头部组件，如果已有头部组件，也会被移除。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## onVisibleIndexesChange

```TypeScript
onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T
```

设置onVisibleIndexesChange回调函数。当LazyVGridLayout可视区域内子组件的索引值发生变化时触发回调，返回可视区域内子组件的起始索引值和结束索引值。

> **说明：**  
>  
> 当父组件设置主轴方向尺寸时，LazyVGridLayout按照父组件可视区域进行懒加载。此时onVisibleIndexesChange回调中start返回当前可视区域起始位置子组件的索引值，end返回当前可视区域结束位置子组件的  
> 索引值。  
>  
> 当父组件未设置主轴方向尺寸时，LazyVGridLayout会被内容撑开，导致所有子组件都会被加载布局。此时onVisibleIndexesChange回调中start返回0，end返回数据源最后一个子组件的索引值。  
>  
> 此处的父组件指最靠近当前组件的上层滚动组件，其他文档下的具体含义请参考对应内容。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyGridLayoutAttribute-onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T--><!--Device-LazyGridLayoutAttribute-onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | OnVisibleIndexesChangeCallback \| undefined | 是 | onVisibleIndexesChange事件的回调函数。传入undefined时取消监听。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## rowsGap

```TypeScript
rowsGap(value: LengthMetrics): T
```

设置行与行的间距。默认值为0vp，设置为小于0的值时，按默认值显示。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-LazyGridLayoutAttribute-rowsGap(value: LengthMetrics): T--><!--Device-LazyGridLayoutAttribute-rowsGap(value: LengthMetrics): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md) | 是 | <br>行与行的间距。<br/>取值范围：[0, +∞)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## sticky

```TypeScript
sticky(sticky: StickyStyle | undefined): T
```

设置[header](#header)和[footer](#footer)的吸附效果。当本组件随滚动容器滚动至可视区域内，且通过sticky设置header吸顶或footer吸底时，header会吸附在滚动容器可视区域顶部，footer会吸附在滚动容器可视区域底部。

> **说明：**  
>  
> 由于浮点数计算精度，设置sticky后，在滚动过程中小概率产生缝隙，可以通过[pixelRound](arkts-arkui-common-commonmethod-c.md#pixelround-1)指定当前组件向下像素取整解决该问题。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyGridLayoutAttribute-sticky(sticky: StickyStyle | undefined): T--><!--Device-LazyGridLayoutAttribute-sticky(sticky: StickyStyle | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sticky | StickyStyle \| undefined | 是 | 头部组件和尾部组件的吸附模式。sticky属性可以设置为StickyStyle.Header或StickyStyle.Footer，也可以设置为StickyStyle.BOTH，以同时支持头部组件吸顶和尾部组件吸底。<br/>方法入参为undefined时，恢复为默认值StickyStyle.None。<br/>未通过该接口设置时，默认头部组件不吸顶、尾部组件不吸底。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

