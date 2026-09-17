# PanGestureOptions

Defines the PanGesture options.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value?: { fingers?: number; direction?: PanDirection; distance?: number })
```

Creates a pan gesture configuration object. The **PanGestureOptions** API enables dynamic updates to pan gesture properties without requiring state variable modifications that would trigger UI re-renders.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | { fingers?: number; direction?: PanDirection; distance?: number } | No | Pan gesture configuration. <br>**fingers**: minimum number of fingers required. The value ranges from 1 to 10.<br>Default value: **1** <br>**direction**: pan direction. The value supports the AND (&) and OR (&#124;) operations.<br>Default value: **PanDirection.All** <br>**distance**: minimum pan distance to trigger the gesture, in vp.<br>Default value: **8** for the stylus and **5** for other input sources. <br>**NOTE:** <br>If a pan gesture and a [tab](../../apis-avsession-kit/arkts-apis/arkts-avsession-avmusictemplate-customelement-i.md#tabs) swipe occur at the same time, set **distance** to **1** to make the gesture more easily recognizable.<br>If the value specified is less than **0**, the default value is used.<br>To avoid slow response and lagging during scrolling, set a reasonable pan distance.<br>When the scale attribute is applied to the component, the actual pan distance is adjusted based on the **scale** ratio. |

## getDirection

```TypeScript
getDirection(): PanDirection
```

Obtains the pan direction.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [PanDirection](arkts-arkui-pandirection-e.md) | Pan direction. |

## getDistance

```TypeScript
getDistance(): number
```

Obtains the minimum pan distance to trigger the gesture. The unit is vp.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Minimum pan distance to trigger the gesture. |

## setDirection

```TypeScript
setDirection(value: PanDirection)
```

Sets the pan direction.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PanDirection](arkts-arkui-pandirection-e.md) | Yes | Pan direction. The value supports the AND ( & ) and OR (&#124;) operations.<br>Default value: **PanDirection.All** |

## setDistance

```TypeScript
setDistance(value: number)
```

Sets the minimum pan distance to trigger the gesture, in vp. To avoid performance degradation due to excessive response delays or accidental releases, avoid excessively large values. For best practices, see [Reducing the Pan Distance for Gesture Recognition](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-application-latency-optimization-cases#section1116134115286).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Minimum pan distance to trigger the gesture, in vp.<br>Default value: **8** for the stylus and **5** for other input sources.<br>**NOTE:** <br>If a pan gesture and a [tab](../../apis-avsession-kit/arkts-apis/arkts-avsession-avmusictemplate-customelement-i.md#tabs) swipe occur at the same time, set **distance** to **1** to make the gesture more easily recognizable.<br>If the value specified is less than **0**, the default value is used.<br>To avoid slow response and lagging during scrolling, set a reasonable pan distance.<br>When the scale attribute is applied to the component, the actual pan distance is adjusted based on the **scale** ratio. |

## setFingers

```TypeScript
setFingers(value: number)
```

Sets the minimum number of fingers to trigger the gesture.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Minimum number of fingers to trigger a pan gesture. The value ranges from 1 to 10.<br> Default value: **1** |
