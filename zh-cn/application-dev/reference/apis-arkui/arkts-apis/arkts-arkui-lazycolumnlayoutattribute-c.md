# LazyColumnLayoutAttribute

定义懒加载列布局属性。

**继承/实现关系：** LazyColumnLayoutAttribute extends [CommonMethod<LazyColumnLayoutAttribute>](CommonMethod<LazyColumnLayoutAttribute>)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems(value: HorizontalAlign | undefined): LazyColumnLayoutAttribute
```

设置行内容的水平对齐方式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | HorizontalAlign \| undefined | 是 | 行内容的水平对齐。<br>默认值为HorizontalAlign.Center。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LazyColumnLayoutAttribute | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## footer

```TypeScript
footer(builder: CustomBuilder | undefined): LazyColumnLayoutAttribute
```

设置懒加载列布局的footer。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | CustomBuilder \| undefined | 是 | footer生成器函数<br>传入undefined移除footer。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LazyColumnLayoutAttribute | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## header

```TypeScript
header(builder: CustomBuilder | undefined): LazyColumnLayoutAttribute
```

设置懒加载列布局的header。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | CustomBuilder \| undefined | 是 | header生成器函数<br>传递undefined将移除header。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LazyColumnLayoutAttribute | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## onVisibleIndexesChange

```TypeScript
onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): LazyColumnLayoutAttribute
```

当子组件在可见区域的索引发生变化时触发。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | OnVisibleIndexesChangeCallback \| undefined | 是 | 回调函数，当可见区域中子组件的索引发生变化时触发。<br>传递undefined将取消注册回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LazyColumnLayoutAttribute | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## space

```TypeScript
space(space: LengthMetrics | undefined): LazyColumnLayoutAttribute
```

行之间的间距。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| space | LengthMetrics \| undefined | 是 | 行之间的间距。<br>默认值为0。<br>范围：[0, +∞)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LazyColumnLayoutAttribute | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

## sticky

```TypeScript
sticky(sticky: StickyStyle | undefined): LazyColumnLayoutAttribute
```

设置header和footer吸顶吸底样式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sticky | StickyStyle \| undefined | 是 | header和footer吸顶吸底样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LazyColumnLayoutAttribute | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

