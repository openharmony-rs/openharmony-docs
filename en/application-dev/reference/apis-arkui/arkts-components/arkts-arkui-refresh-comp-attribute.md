# Refresh properties/events

```TypeScript
declare class RefreshAttribute extends CommonMethod<RefreshAttribute>
```

In addition to the universal attributes, the following attributes are supported.

In addition to the universal events, the following events are supported.

**Inheritance/Implementation:** RefreshAttribute extends CommonMethod<RefreshAttribute>

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxPullDownDistance

```TypeScript
maxPullDownDistance(distance: Optional<number>)
```

Sets the maximum pull-down distance.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| distance | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Maximum pull-down distance. The minimum value for the maximum pull-down distance is 0. Values less than 0 are treated as **0**. If this value is less than the refresh offset (**refreshOffset**), the refresh action will not be triggered when the pull-down gesture is released.<br>If set to **undefined** or **null**, this parameter is considered not set.<br>Default value: **undefined**.<br>Unit: vp |

<a id="maxpulldowndistance-1"></a>

## maxPullDownDistance

```TypeScript
maxPullDownDistance(distance: number | Resource | undefined)
```

Sets the maximum pull-down distance. The resource type is supported.

If this API is not set, the maximum pull-down distance is **undefined**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| distance | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; undefined | Yes | Maximum pull-down distance.<br>Default value: **undefined**.<br>Unit: vp<br>Value range: [0, +∞). If the value is less than 0, **0** is used. If this value is less than the [refreshOffset](../../../reference/apis-arkui/arkui-ts/ts-container-refresh.md#refreshoffset12), the refresh action will not be triggered when the pull-down gesture is released. <br>If this parameter is set to **undefined** or **null**, it is considered that this attribute is not set, meaning there is no limit on the maximum pull-down distance. |

## onOffsetChange

```TypeScript
onOffsetChange(callback: Callback<number>)
```

Called when the pull-down distance changes.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;number&gt; | Yes | Callback used to listen for the pull-down distance changes. It is triggered when the pull-down distance changes and returns the current pull-down distance.<br>Unit: vp |

## onRefreshing

```TypeScript
onRefreshing(callback: () => void)
```

Called when the component starts refreshing.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | () =&gt; void | Yes | Callback triggered when the component enters the refresh state. |

## onStateChange

```TypeScript
onStateChange(callback: (state: RefreshStatus) => void)
```

Called when the refresh status changes.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (state: RefreshStatus) =&gt; void | Yes |  |

## pullDownRatio

```TypeScript
pullDownRatio(ratio: Optional<number>)
```

Sets the pull-down ratio.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ratio | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Pull-down ratio. A larger value indicates higher responsiveness to the pull- down gesture. The value **0** indicates that the pull-down does not follow the gesture, and **1** indicates that the pull-down follows the gesture proportionally.<br>If this parameter is not set or is set to **undefined**, a dynamic pull-down ratio is used. That is, the larger the pull-down distance, the smaller the ratio.<br>The value ranges from 0 to 1. A value less than 0 is handled as **0**, and a value greater than 1 is handled as **1**. |

## pullToRefresh

```TypeScript
pullToRefresh(value: boolean)
```

Sets whether to initiate a refresh when the pull-down distance exceeds the value of [refreshOffset](#refreshoffset).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to initiate a refresh when the pull-down distance exceeds the value of [refreshOffset](#refreshoffset). The value **true** means to initiate a refresh, and **false** means the opposite.<br>Default value: **true** |

## pullUpToCancelRefresh

```TypeScript
pullUpToCancelRefresh(enabled: boolean | undefined)
```

Sets whether to enable the pull-up-to-cancel gesture for refreshing operations.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean &#124; undefined | Yes | Whether to enable the pull-up-to-cancel gesture for refreshing operations.<br>**true**: Enable the pull-up-to-cancel gesture. **false**: Disable the pull-up-to-cancel gesture.<br> **undefined**: Enable the pull-up-to-cancel gesture. |

## refreshOffset

```TypeScript
refreshOffset(value: number)
```

Sets the minimum pull-down offset required to trigger a refresh. If the distance pulled down is less than the value specified by this attribute, releasing the gesture does not trigger a refresh.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Pull-down offset, in vp.<br>Default value: 96 vp when [promptText](arkts-arkui-refresh-comp-refreshoptions-i.md) is set and 64 vp when [promptText](arkts-arkui-refresh-comp-refreshoptions-i.md) is not set.<br>If the value specified is 0 or less than 0, the default value is used. |

<a id="refreshoffset-1"></a>

## refreshOffset

```TypeScript
refreshOffset(value: number | Resource)
```

Sets the pull-down offset that triggers the refresh. When the pull-down distance is less than the value of this attribute, releasing the pull-down gesture does not trigger the refresh. The resource type is supported.

If this API and [promptText](arkts-arkui-refresh-comp-refreshoptions-i.md) are not set, the default offset is 64 vp. If [promptText](arkts-arkui-refresh-comp-refreshoptions-i.md) is set, the default offset is 96 vp.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Pull-down offset.<br>Unit: vp<br>Value range: (0, +∞). If the value is 0 or a negative number, the default value will be used. |
