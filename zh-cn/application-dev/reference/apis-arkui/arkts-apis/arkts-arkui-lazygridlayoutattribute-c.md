# LazyGridLayoutAttribute

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)外，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)外，还支持以下事件：

**继承/实现关系：** LazyGridLayoutAttribute extends [CommonMethod<T>](CommonMethod<T>)

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## columnsGap

```TypeScript
columnsGap(value: LengthMetrics): T
```

设置列与列的间距。设置为小于0的值时，按默认值显示。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | LengthMetrics | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full<br/>@stagemodelonly<br/>@crossplatform<br/>@atomicservice |

## footer

```TypeScript
footer(builder: CustomBuilder | undefined): T
```

设置LazyVGridLayout的尾部组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | CustomBuilder \| undefined | 是 | 尾部组件构建函数。<br/><br/>传入undefined时移除尾部组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full<br/>@stagemodelonly<br/>@crossplatform<br/>@atomicservice |

## header

```TypeScript
header(builder: CustomBuilder | undefined): T
```

设置LazyVGridLayout的头部组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | CustomBuilder \| undefined | 是 | 头部组件构建函数。<br/><br/>传入undefined时移除头部组件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full<br/>@stagemodelonly<br/>@crossplatform<br/>@atomicservice |

## onVisibleIndexesChange

```TypeScript
onVisibleIndexesChange(callback: OnVisibleIndexesChangeCallback | undefined): T
```

设置onVisibleIndexesChange回调函数。当LazyVGridLayout可视区域内子组件的索引值发生变化时触发回调，返回可视区域内子组件的起始索引值和结束索引值。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | OnVisibleIndexesChangeCallback \| undefined | 是 | onVisibleIndexesChange事件的回调函数。<br/>传入undefined时取消监听。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full<br/>@stagemodelonly<br/>@crossplatform<br/>@atomicservice |

## rowsGap

```TypeScript
rowsGap(value: LengthMetrics): T
```

设置行与行的间距。设置为小于0的值时，按默认值显示。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | LengthMetrics | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full<br/>@stagemodelonly<br/>@crossplatform<br/>@atomicservice |

## sticky

```TypeScript
sticky(sticky: StickyStyle | undefined): T
```

设置头部和尾部组件的吸顶吸底样式。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sticky | StickyStyle \| undefined | 是 | 头部和尾部组件的吸顶吸底样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | @syscap SystemCapability.ArkUI.ArkUI.Full<br/>@stagemodelonly<br/>@crossplatform<br/>@atomicservice |

