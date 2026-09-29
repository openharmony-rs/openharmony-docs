# @ohos.measure(Text Measurement)

This module provides APIs for calculating text width and height, and supports configuring various text attributes (
 such as the font size, style, weight, and line height). It is applicable to scenarios where the text size needs to be
 obtained before component construction, such as adaptive layout, text clipping, and dynamic UI size adjustment,
 helping you achieve more precise layout calculation and performance optimization.

> **NOTE**
 >
 > - This module cannot be used in the file declaration of the [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md). In
 > other words, the APIs of this module can be used only after a component instance is created; they cannot be called
 > in the lifecycle of the UIAbility.
 >
 > - To perform more complex text measurements, you are advised to use the measurement APIs under
 > [Paragraph](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-paragraph-c.md).
 >
 > - When calling the text measurement APIs, you are advised not to use
 > [ApplicationContext.setFontSizeScale](../../apis-ability-kit/arkts-apis/arkts-ability-applicationcontext-c.md#setfontsizescale)
 > to set the application font size scale at the same time. To ensure timing consistency, you are advised to listen
 > for font size scale changes on your own to guarantee the accuracy of measurement results.
 >
 > - For measuring text after truncation, direct use of the string length for truncation may lead to inaccuracies,
 > because certain Unicode characters (for example, emojis) have code points with a length greater than 1. As such,
 > you are advised to perform iterative processing based on Unicode code points during truncation.



## Modules to Import

```TypeScript
import { MeasureText, MeasureOptions } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [MeasureText](arkts-arkui-measure-measuretext-c.md) | Defines the Measure interface. |

### Interfaces

| Name | Description |
| --- | --- |
| [MeasureOptions](arkts-arkui-measure-measureoptions-i.md) | Provides attributes of the measured text. |
