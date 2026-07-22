# Refresh属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件：

**继承/实现关系：** RefreshAttribute extends [CommonMethod<RefreshAttribute>](CommonMethod<RefreshAttribute>)

**起始版本：** 8

<!--Device-unnamed-declare class RefreshAttribute extends CommonMethod<RefreshAttribute>--><!--Device-unnamed-declare class RefreshAttribute extends CommonMethod<RefreshAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxPullDownDistance

```TypeScript
maxPullDownDistance(distance: Optional<number>)
```

设置最大下拉距离。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-RefreshAttribute-maxPullDownDistance(distance: Optional<number>): RefreshAttribute--><!--Device-RefreshAttribute-maxPullDownDistance(distance: Optional<number>): RefreshAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| distance | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 最大下拉距离。最大下拉距离的最小值为0，小于0按0处理。当该值小于刷新的下拉偏移量refreshOffset时，Refresh下拉离手不会触发刷新。<br/>undefined和null按没有设置此属性处理。<br/>默认值：undefined<br/>单位：vp |

## maxPullDownDistance

```TypeScript
maxPullDownDistance(distance: number | Resource | undefined)
```

设置最大下拉距离，支持Resource资源类型。

未通过该接口设置时，设置最大下拉距离为undefined。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RefreshAttribute-maxPullDownDistance(distance: number | Resource | undefined): RefreshAttribute--><!--Device-RefreshAttribute-maxPullDownDistance(distance: number | Resource | undefined): RefreshAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| distance | number \| Resource \| undefined | 是 | 最大下拉距离。<br/>默认值：undefined<br/>单位：vp<br/>取值范围：[0, +∞)，值小于0时按0处理。当该值小于刷新的下拉偏移量[refreshOffset](RefreshAttribute#refreshOffset(value: number))时，Refresh下拉离手不会触发刷新。<br/>undefined和null按没有设置此属性处理，即没有最大下拉距离限制。 |

## onOffsetChange

```TypeScript
onOffsetChange(callback: Callback<number>)
```

下拉距离发生变化时触发回调。
> **说明：**  
>  
> 从API version 20开始，该接口支持在[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier)中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RefreshAttribute-onOffsetChange(callback: Callback<number>): RefreshAttribute--><!--Device-RefreshAttribute-onOffsetChange(callback: Callback<number>): RefreshAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 回调函数，用于监听下拉距离的变化。当下拉距离发生变化时触发，回调参数为当前的下拉距离。<br/>单位：vp |

## onRefreshing

```TypeScript
onRefreshing(callback: () => void)
```

进入刷新状态时触发回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RefreshAttribute-onRefreshing(callback: () => void): RefreshAttribute--><!--Device-RefreshAttribute-onRefreshing(callback: () => void): RefreshAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | () =&gt; void | 是 | 进入刷新状态时触发的回调。 |

## onStateChange

```TypeScript
onStateChange(callback: (state: RefreshStatus) => void)
```

当前刷新状态变更时，触发回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RefreshAttribute-onStateChange(callback: (state: RefreshStatus) => void): RefreshAttribute--><!--Device-RefreshAttribute-onStateChange(callback: (state: RefreshStatus) => void): RefreshAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (state: RefreshStatus) =&gt; void | 是 |  |

## pullDownRatio

```TypeScript
pullDownRatio(ratio: Optional<number>)
```

设置下拉跟手系数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RefreshAttribute-pullDownRatio(ratio: Optional<number>): RefreshAttribute--><!--Device-RefreshAttribute-pullDownRatio(ratio: Optional<number>): RefreshAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ratio | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 下拉跟手系数。数值越大，跟随手势下拉的反应越灵敏。0表示不跟随手势下拉，1表示等比例跟随手势下拉。<br/>没有设置或设置为undefined时，默认使用动态下拉跟手系数，下拉距离越大，跟手系数越小。<br/>有效值为0-1之间的值，小于0的值会被视为0，大于1的值会被视为1。 |

## pullToRefresh

```TypeScript
pullToRefresh(value: boolean)
```

设置当下拉距离超过[refreshOffset](RefreshAttribute#refreshOffset(value: number))时是否能触发刷新。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RefreshAttribute-pullToRefresh(value: boolean): RefreshAttribute--><!--Device-RefreshAttribute-pullToRefresh(value: boolean): RefreshAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 当下拉距离超过[refreshOffset](RefreshAttribute#refreshOffset(value: number))时是否能触发刷新。true表示能触发刷新，false表示不能触发刷新。<br/>默认值：true |

## pullUpToCancelRefresh

```TypeScript
pullUpToCancelRefresh(enabled: boolean | undefined)
```

设置上划是否取消刷新。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RefreshAttribute-pullUpToCancelRefresh(enabled: boolean | undefined): RefreshAttribute--><!--Device-RefreshAttribute-pullUpToCancelRefresh(enabled: boolean | undefined): RefreshAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean \| undefined | 是 | 设置上划是否取消刷新。<br/>true表示取消刷新；false表示不取消刷新。<br/>值为undefined时，上划取消刷新。 |

## refreshOffset

```TypeScript
refreshOffset(value: number)
```

设置触发刷新的下拉偏移量，当下拉距离小于该属性设置值时离手不会触发刷新。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RefreshAttribute-refreshOffset(value: number): RefreshAttribute--><!--Device-RefreshAttribute-refreshOffset(value: number): RefreshAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 下拉偏移量，单位vp。<br/>默认值：未设置[promptText](../../../reference/apis-arkui/arkui-ts/ts-container-refresh.md#refreshoptions对象说明)参数时为64vp，设置了[promptText](../../../reference/apis-arkui/arkui-ts/ts-container-refresh.md#refreshoptions对象说明)参数时为96vp。 <br/>如果取值为0或负数的时候此接口采用默认值。 |

## refreshOffset

```TypeScript
refreshOffset(value: number | Resource)
```

设置触发刷新的下拉偏移量，当下拉距离小于该属性设置值时离手不会触发刷新，支持Resource资源类型。

未通过该接口设置时，当未设置[promptText](../../../reference/apis-arkui/arkui-ts/ts-container-refresh.md#refreshoptions对象说明)参数时，默认偏移量为64vp；设置了[promptText](../../../reference/apis-arkui/arkui-ts/ts-container-refresh.md#refreshoptions对象说明)参数时，默认偏移量为96vp。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RefreshAttribute-refreshOffset(value: number | Resource): RefreshAttribute--><!--Device-RefreshAttribute-refreshOffset(value: number | Resource): RefreshAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| Resource | 是 | 下拉偏移量。<br/>单位：vp<br/>取值范围：(0, +∞)。值为0或负数时，按默认值处理。 |

