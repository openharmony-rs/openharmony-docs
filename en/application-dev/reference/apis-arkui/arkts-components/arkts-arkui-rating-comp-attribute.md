# Rating properties/events

```TypeScript
declare class RatingAttribute extends CommonMethod<RatingAttribute>
```

In addition to the universal attributes, the following attributes are supported.

**Inheritance/Implementation:** RatingAttribute extends CommonMethod&lt;RatingAttribute&gt;

**Since:** 7

<!--Device-unnamed-declare class RatingAttribute extends CommonMethod<RatingAttribute>--><!--Device-unnamed-declare class RatingAttribute extends CommonMethod<RatingAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

<a id="contentmodifier1"></a>

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<RatingConfiguration>)
```

Creates a content modifier. You need to customize a class to implement the **ContentModifier** API and return **WrappedBuilder** in the **applyContent** API to redefine the rendering logic of the content area of the **Rating** component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RatingAttribute-contentModifier(modifier: ContentModifier<RatingConfiguration>): RatingAttribute--><!--Device-RatingAttribute-contentModifier(modifier: ContentModifier<RatingConfiguration>): RatingAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[RatingConfiguration](arkts-arkui-rating-comp-ratingconfiguration-i.md)&gt; | Yes | Content modifier to apply to the current component.<br>**modifier**: content modifier. You need a custom class to implement the **ContentModifier** API. |

<a id="contentmodifier2"></a>

## contentModifier

```TypeScript
contentModifier(modifier: Optional<ContentModifier<RatingConfiguration>>)
```

Creates a content modifier. Compared with [contentModifier](#contentmodifier1), this API supports the **undefined** type for the **modifier** parameter. If **modifier** is set to **undefined**, no content modifier is used.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-RatingAttribute-contentModifier(modifier: Optional<ContentModifier<RatingConfiguration>>): RatingAttribute--><!--Device-RatingAttribute-contentModifier(modifier: Optional<ContentModifier<RatingConfiguration>>): RatingAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ContentModifier](arkts-arkui-common-comp-contentmodifier-i.md)&lt;[RatingConfiguration](arkts-arkui-rating-comp-ratingconfiguration-i.md)&gt;&gt; | Yes | Content modifier to apply to the current component.<br>**modifier**: content modifier. You need a custom class to implement the **ContentModifier** API. <br>If **modifier** is set to **undefined**, no content modifier is used. |

<a id="onchange1"></a>

## onChange

```TypeScript
onChange(callback: (value: number) => void)
```

Triggered when the rating value changes.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-RatingAttribute-onChange(callback: (value: number) => void): RatingAttribute--><!--Device-RatingAttribute-onChange(callback: (value: number) => void): RatingAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (value: number) =&gt; void | Yes |  |

<a id="onchange2"></a>

## onChange

```TypeScript
onChange(callback: Optional<OnRatingChangeCallback>)
```

Triggered when the rating value changes. Compared with [onChange](#onchange1), this API supports the **undefined** type for the **callback** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RatingAttribute-onChange(callback: Optional<OnRatingChangeCallback>): RatingAttribute--><!--Device-RatingAttribute-onChange(callback: Optional<OnRatingChangeCallback>): RatingAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnRatingChangeCallback](arkts-arkui-rating-comp-onratingchangecallback-t.md)&gt; | Yes | Defines the callback triggered when the rating value changes.<br>If **callback** is set to **undefined**, the callback function is not used. |

<a id="stars1"></a>

## stars

```TypeScript
stars(value: number)
```

Sets the total number of stars. The default value is **5**.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-RatingAttribute-stars(value: number): RatingAttribute--><!--Device-RatingAttribute-stars(value: number): RatingAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Total number of stars.<br>Value range: greater than 0. Values less than or equal to 0 are treated as **5**. |

<a id="stars2"></a>

## stars

```TypeScript
stars(starCount: Optional<number>)
```

Sets the total number of stars. Compared with [stars](#stars1), this API supports the **undefined** type for the **starCount** parameter. If **starCount** is set to **undefined**, the default value **5** is used.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RatingAttribute-stars(starCount: Optional<number>): RatingAttribute--><!--Device-RatingAttribute-stars(starCount: Optional<number>): RatingAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| starCount | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Total number of stars.<br>Value range: greater than 0. If the value is less than or equal to 0 or is **undefined**, the value **5** is displayed. |

<a id="starstyle1"></a>

## starStyle

```TypeScript
starStyle(options: StarStyleOptions)
```

Sets the star style. For details about the supported image types, see [Image](arkts-arkui-image-comp.md).

Local and network images are supported. The PixelMap type is not supported.

By default, the image is loaded in asynchronous mode. Synchronous loading is not supported.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-RatingAttribute-starStyle(options: StarStyleOptions): RatingAttribute--><!--Device-RatingAttribute-starStyle(options: StarStyleOptions): RatingAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [StarStyleOptions](arkts-arkui-rating-comp-starstyleoptions-i.md) | Yes | Star style.<br>**NOTE:** <br>If an incorrect image path is provided for **backgroundUri**, **foregroundUri**, or **secondaryUri**, the previously displayed image will be retained. If the first provided path is incorrect, no image will be displayed. <br>When **backgroundUri** or **foregroundUri** is set to **undefined** or an empty string, the **Rating** component falls back to the default star image. <br>If **secondaryUri** is not set, or is set to **undefined** or an empty string, **backgroundUri** will be used as a fallback. The behavior in this case is the same as when only **foregroundUri** and **backgroundUri** are configured.<br>**Since:** 18 |

<a id="starstyle2"></a>

## starStyle

```TypeScript
starStyle(options: Optional<StarStyleOptions>)
```

Sets the star style. For details about the supported image types, see [Image](arkts-arkui-image-comp.md).

Local and network images are supported. The PixelMap type is not supported.

By default, the image is loaded in asynchronous mode. Synchronous loading is not supported.

Compared with [starStyle](#starstyle1), this API supports the **undefined** type for the **options** parameter.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RatingAttribute-starStyle(options: Optional<StarStyleOptions>): RatingAttribute--><!--Device-RatingAttribute-starStyle(options: Optional<StarStyleOptions>): RatingAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[StarStyleOptions](arkts-arkui-rating-comp-starstyleoptions-i.md)&gt; | Yes | Star style.<br>**NOTE:** <br>If an incorrect image path is provided for **backgroundUri**, **foregroundUri**, or **secondaryUri**, the previously displayed image will be retained. If the first provided path is incorrect, no image will be displayed. <br>When **backgroundUri** or **foregroundUri** is set to **undefined** or an empty string, the **Rating** component falls back to the default star image. <br>If **secondaryUri** is not set, or is set to **undefined** or an empty string, **backgroundUri** will be used as a fallback. The behavior in this case is the same as when only **foregroundUri** and **backgroundUri** are configured. |

<a id="stepsize1"></a>

## stepSize

```TypeScript
stepSize(value: number)
```

Sets the step for rating. Values less than 0.1 are treated as the default value. The default value is **0.5**.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-RatingAttribute-stepSize(value: number): RatingAttribute--><!--Device-RatingAttribute-stepSize(value: number): RatingAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Step for rating.<br>Value range: [0.1, stars] |

<a id="stepsize2"></a>

## stepSize

```TypeScript
stepSize(size: Optional<number>)
```

Sets the step for rating. Values less than 0.1 are treated as the default value. Compared with [stepSize](#stepsize1), this API supports the **undefined** type for the **size** parameter. If **size** is set to **undefined**, the default value **0.5** is used.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-RatingAttribute-stepSize(size: Optional<number>): RatingAttribute--><!--Device-RatingAttribute-stepSize(size: Optional<number>): RatingAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Step for rating.<br>If **size** is set to **undefined**, the default value **0.5** is used. <br>Value range: [0.1, stars] |
