# Rating

The **Rating** component provides a rating bar.

> **NOTE**

> - If the parent node of the **Rating** component has fixed dimensions, you must also specify the width and height > for the **Rating** component, or set its parent node's clip > attribute to **true**.

## Child Components

Not supported

## Sequential Keyboard Navigation Specifications

| Key | Description |  
|------------|-----------------------------|  
| Tab | Switch the focus between components. |
| Left and right arrow keys | Increase or decrease the rating on preview at the specified step, without changing the actual rating.|
| Home | Move the focus to the first star, without changing the actual rating. |
| End | Move the focus to the last star, without changing the actual rating. |
| Space/Enter | Submit the rating result based on the current rating. |

## Rating

```TypeScript
Rating(options?: RatingOptions)
```

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RatingOptions](arkts-arkui-ratingoptions-i.md) | No | Rating bar options.<br> The default values of the parameters in **RatingOptions** apply if this parameter is not set. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [RatingConfiguration](arkts-arkui-ratingconfiguration-i.md) | You need a custom class to implement the **ContentModifier** API. Inherits from [CommonConfiguration](arkts-arkui-commonconfiguration-i.md). |
| [RatingOptions](arkts-arkui-ratingoptions-i.md) | Provides configuration options for the **Rating** component. |
| [StarStyleOptions](arkts-arkui-starstyleoptions-i.md) | Provides style settings for the selected, unselected, and partially selected stars in the **Rating** component. |

### Types

| Name | Description |
| --- | --- |
| [OnRatingChangeCallback](arkts-arkui-onratingchangecallback-t.md) | Defines the callback triggered when the rating value changes. |

## Examples

```TypeScript
### Example 1: Setting the Default Rating Style

This example shows how to create a Rating component with the default star style.


```

```TypeScript
### Example 2: Implementing a Custom Rating Bar

This example implements a custom rating bar, where each circle represents 0.5 points. When ratingIndicator is set to true, the rating bar is used as an indicator and the rating cannot be changed. ratingStars sets the total number of stars, and ratingStepSize sets the increment step.


```

```TypeScript
### Example 3: Setting the Rating Style Through Resource Configuration

This example demonstrates how to set starStyle through resource configuration to customize the star image link. This method is recommended for setting the style since API version 20.


```

```TypeScript
### Example 4: Customizing the Rating Style

This example shows how to customize the star images by configuring starStyle.

> Note
> 
> The resources used in this example are not located in the src > main > resource directory. Starting from DevEco Studio 6.0.0 Beta2, the resources that are located outside the resources directory are not packaged by default when a project or module is created. To package these resources, go to buildOptions > resOptions > copyCodeResource in the module's build-profile.json5 file, and set enable to true. For details, see the description of [resOptions](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348).
```
