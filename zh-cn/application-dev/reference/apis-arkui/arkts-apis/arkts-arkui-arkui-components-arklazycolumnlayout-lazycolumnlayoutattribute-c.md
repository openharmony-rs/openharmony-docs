# LazyColumnLayoutAttribute

定义懒加载列布局属性。

**继承/实现关系：** LazyColumnLayoutAttribute extends CommonMethod<LazyColumnLayoutAttribute>

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class LazyColumnLayoutAttribute--><!--Device-unnamed-export declare class LazyColumnLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems(value: HorizontalAlign | undefined): LazyColumnLayoutAttribute
```

设置行内容的水平对齐方式。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyColumnLayoutAttribute-alignItems(value: HorizontalAlign | undefined): LazyColumnLayoutAttribute--><!--Device-LazyColumnLayoutAttribute-alignItems(value: HorizontalAlign | undefined): LazyColumnLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [HorizontalAlign](../../apis-na/arkts-apis/arkts-na-enums-horizontalalign-e.md) \| undefined | 是 | 行内容的水平对齐。 &lt;br&gt;默认值为HorizontalAlign.Center。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LazyColumnLayoutAttribute](arkts-arkui-arkui-components-arklazycolumnlayout-lazycolumnlayoutattribute-c.md) |  |

## footer

```TypeScript
footer(builder: CustomBuilder | undefined): LazyColumnLayoutAttribute
```

设置懒加载列布局的footer。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyColumnLayoutAttribute-footer(builder: CustomBuilder | undefined): LazyColumnLayoutAttribute--><!--Device-LazyColumnLayoutAttribute-footer(builder: CustomBuilder | undefined): LazyColumnLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | CustomBuilder \| undefined | 是 | footer生成器函数 &lt;br&gt;传入undefined移除footer。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LazyColumnLayoutAttribute](arkts-arkui-arkui-components-arklazycolumnlayout-lazycolumnlayoutattribute-c.md) |  |

## header

```TypeScript
header(builder: CustomBuilder | undefined): LazyColumnLayoutAttribute
```

设置懒加载列布局的header。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyColumnLayoutAttribute-header(builder: CustomBuilder | undefined): LazyColumnLayoutAttribute--><!--Device-LazyColumnLayoutAttribute-header(builder: CustomBuilder | undefined): LazyColumnLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | CustomBuilder \| undefined | 是 | header生成器函数 &lt;br&gt;传递undefined将移除header。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LazyColumnLayoutAttribute](arkts-arkui-arkui-components-arklazycolumnlayout-lazycolumnlayoutattribute-c.md) |  |

## onVisibleIndexesChange

```TypeScript
onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): LazyColumnLayoutAttribute
```

当子组件在可见区域的索引发生变化时触发。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyColumnLayoutAttribute-onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): LazyColumnLayoutAttribute--><!--Device-LazyColumnLayoutAttribute-onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): LazyColumnLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnVisibleIndexesChangeCallback](../../apis-na/arkts-apis/arkts-na-onvisibleindexeschangecallback-t.md) \| undefined | 是 | 回调函数，当可见区域中子组件的索引发生变化时触发。 &lt;br&gt;传递undefined将取消注册回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LazyColumnLayoutAttribute](arkts-arkui-arkui-components-arklazycolumnlayout-lazycolumnlayoutattribute-c.md) |  |

## space

```TypeScript
space(space: LengthMetrics | undefined): LazyColumnLayoutAttribute
```

行之间的间距。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyColumnLayoutAttribute-space(space: LengthMetrics | undefined): LazyColumnLayoutAttribute--><!--Device-LazyColumnLayoutAttribute-space(space: LengthMetrics | undefined): LazyColumnLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| space | [LengthMetrics](../../apis-na/arkts-apis/arkts-na-graphics-lengthmetrics-c.md) \| undefined | 是 | 行之间的间距。 &lt;br&gt;默认值为0。&lt;br&gt;范围：[0, +∞)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LazyColumnLayoutAttribute](arkts-arkui-arkui-components-arklazycolumnlayout-lazycolumnlayoutattribute-c.md) |  |

## sticky

```TypeScript
sticky(sticky: StickyStyle | undefined): LazyColumnLayoutAttribute
```

设置header和footer吸顶吸底样式。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-LazyColumnLayoutAttribute-sticky(sticky: StickyStyle | undefined): LazyColumnLayoutAttribute--><!--Device-LazyColumnLayoutAttribute-sticky(sticky: StickyStyle | undefined): LazyColumnLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sticky | [StickyStyle](../../apis-na/arkts-apis/arkts-na-list-stickystyle-e.md) \| undefined | 是 | header和footer吸顶吸底样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LazyColumnLayoutAttribute](arkts-arkui-arkui-components-arklazycolumnlayout-lazycolumnlayoutattribute-c.md) |  |

