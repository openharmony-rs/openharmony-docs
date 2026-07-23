# LazyWaterFlowLayoutAttribute

定义懒加载瀑布流布局属性。

**继承/实现关系：** LazyWaterFlowLayoutAttribute extends [CommonMethod<T>]

**起始版本：** 26.0.0

<!--Device-unnamed-export declare class LazyWaterFlowLayoutAttribute<T> extends CommonMethod<T>--><!--Device-unnamed-export declare class LazyWaterFlowLayoutAttribute<T> extends CommonMethod<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { LazyVWaterFlowLayout, LazyWaterFlowLayoutAttribute, LazyVWaterFlowLayoutAttribute } from '@kit.ArkUI';
```

## columnsGap

```TypeScript
columnsGap(value: LengthMetrics | undefined): T
```

列之间的间距。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyWaterFlowLayoutAttribute-columnsGap(value: LengthMetrics | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-columnsGap(value: LengthMetrics | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) \| undefined | 是 | 列之间的间距。<br>默认值：LengthMetrics.vp(0) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## footer

```TypeScript
footer(builder: CustomBuilder | undefined): T
```

设置懒加载瀑布流布局的footer。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyWaterFlowLayoutAttribute-footer(builder: CustomBuilder | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-footer(builder: CustomBuilder | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) \| undefined | 是 | footer生成器函数<br>传递undefined将删除footer。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## header

```TypeScript
header(builder: CustomBuilder | undefined): T
```

设置懒加载瀑布流布局的header。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyWaterFlowLayoutAttribute-header(builder: CustomBuilder | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-header(builder: CustomBuilder | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) \| undefined | 是 | header生成器函数<br>传递undefined将删除header。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## onVisibleIndexesChange

```TypeScript
onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T
```

当组件中显示的第一个或最后一个项目更改时调用。它在组件初始化时会触发一次。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyWaterFlowLayoutAttribute-onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnVisibleIndexesChangeCallback](../arkts-components/arkts-arkui-onvisibleindexeschangecallback-t.md) \| undefined | 是 | 回调函数，当可见区域中子组件的索引发生变化时触发。<br>传递undefined将取消注册回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## rowsGap

```TypeScript
rowsGap(value: LengthMetrics | undefined): T
```

行之间的间距。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyWaterFlowLayoutAttribute-rowsGap(value: LengthMetrics | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-rowsGap(value: LengthMetrics | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) \| undefined | 是 | 行之间的间距。<br>默认值：LengthMetrics.vp(0) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## sticky

```TypeScript
sticky(sticky: StickyStyle | undefined): T
```

设置header和footer的吸顶吸底样式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyWaterFlowLayoutAttribute-sticky(sticky: StickyStyle | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-sticky(sticky: StickyStyle | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sticky | [StickyStyle](../arkts-components/arkts-arkui-stickystyle-e.md) \| undefined | 是 | header和footer的吸顶吸底样式 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

