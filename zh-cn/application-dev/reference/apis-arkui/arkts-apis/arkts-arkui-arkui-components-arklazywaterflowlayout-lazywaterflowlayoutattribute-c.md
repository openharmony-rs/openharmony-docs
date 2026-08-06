# LazyWaterFlowLayoutAttribute

定义懒加载瀑布流布局属性。

**继承/实现关系：** LazyWaterFlowLayoutAttribute extends [CommonMethod<T>](CommonMethod<T>)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

<!--Device-unnamed-export declare class LazyWaterFlowLayoutAttribute<T> extends CommonMethod<T>--><!--Device-unnamed-export declare class LazyWaterFlowLayoutAttribute<T> extends CommonMethod<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## columnsGap

```TypeScript
columnsGap(value: LengthMetrics | undefined): T
```

列之间的间距。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyWaterFlowLayoutAttribute-columnsGap(value: LengthMetrics | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-columnsGap(value: LengthMetrics | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 列之间的间距。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：LengthMetrics.vp(0) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## footer

```TypeScript
footer(builder: CustomBuilder | undefined): T
```

设置懒加载瀑布流布局的footer。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyWaterFlowLayoutAttribute-footer(builder: CustomBuilder | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-footer(builder: CustomBuilder | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | footer生成器函数\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_传递undefined将删除footer。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## header

```TypeScript
header(builder: CustomBuilder | undefined): T
```

设置懒加载瀑布流布局的header。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyWaterFlowLayoutAttribute-header(builder: CustomBuilder | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-header(builder: CustomBuilder | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | header生成器函数\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_传递undefined将删除header。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## onVisibleIndexesChange

```TypeScript
onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T
```

当组件中显示的第一个或最后一个项目更改时调用。 它在组件初始化时会触发一次。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyWaterFlowLayoutAttribute-onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 回调函数，当可见区域中子组件的索引发生变化时触发。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_传递undefined将取消注册回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## rowsGap

```TypeScript
rowsGap(value: LengthMetrics | undefined): T
```

行之间的间距。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyWaterFlowLayoutAttribute-rowsGap(value: LengthMetrics | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-rowsGap(value: LengthMetrics | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 行之间的间距。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：LengthMetrics.vp(0) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## sticky

```TypeScript
sticky(sticky: StickyStyle | undefined): T
```

设置header和footer的吸顶吸底样式。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyWaterFlowLayoutAttribute-sticky(sticky: StickyStyle | undefined): T--><!--Device-LazyWaterFlowLayoutAttribute-sticky(sticky: StickyStyle | undefined): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sticky | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | header和footer的吸顶吸底样式 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

