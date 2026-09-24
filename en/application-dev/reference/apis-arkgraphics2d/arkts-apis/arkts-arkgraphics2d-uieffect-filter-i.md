# Filter

```TypeScript
interface Filter
```

Filter effect class, used to apply corresponding effects to specified components. Before calling Filter methods, you need to first create a Filter instance through createFilter.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## blur

```TypeScript
blur(blurRadius: number): Filter
```

Adds a blur effect to the component.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blurRadius | number | Yes | Blur radius, in px. The value must be greater than or equal to 0. A larger blur radius results in a stronger blur effect. When the blur radius is 0, there is no blur effect. If a negative number is passed in, it is automatically corrected to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the blur effect attached, supporting chained calls to add other effects. |

**Examples**

```TypeScript
// xxx.ts
import { uiEffect } from '@kit.ArkGraphics2D';

// Create a Filter instance
let filter: uiEffect.Filter = uiEffect.createFilter();
// Set the blur radius to 10px
filter.blur(10);

@Entry
@Component
struct UIEffectFilterExample {
    build() {
        Column({ space: 15 }) {
            Text('UIEffectFilter').fontSize(20).width('75%').fontColor('#DCDCDC')
            Image($r('app.media.foreground'))
                .width(100)
                .height(100)
                .backgroundImage($r('app.media.background'))
                .backgroundImagePosition(Alignment.Center)
                .backgroundImageSize({ width: 90, height: 90 })
                // Apply the Filter effect to the component background
                .backgroundFilter(filter)
        }
        .height('100%')
        .width('100%')
    }
}
```

## hdrBrightnessRatio

```TypeScript
hdrBrightnessRatio(ratio: number): Filter
```

Adds an HDR (High Dynamic Range) brightening effect to the component content. Nesting is not recommended, as forced nesting may cause overexposure.

The brightening effect requires the HDR rendering pipeline to be enabled to take effect. In some scenarios, HDR cannot be enabled even if an attempt is made to trigger the HDR rendering pipeline, for example, when the device hardware specifications do not support HDR.

The maximum supported brightness boost multiple is calculated as the device's current maximum brightness divided by its SDR reference white luminance.

> **NOTE:** 
> 
> Using the HDR brightening effect incurs certain performance and power consumption overhead.
> It is recommended to use it in scenarios where HDR images or videos already exist.

**Since:** 24

**Required permissions:** 
- API version 24 and later: ohos.permission.HDR_BRIGHTNESS
- API versions 20 to 23: N/A

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ratio | number | Yes | Brightening ratio. The value range is [1.0, the maximum brightening ratio supported by the current device]. Values less than 1.0 are treated as 1.0; a value equal to 1.0 means no processing; values greater than 1.0 attempt to trigger the HDR rendering pipeline; values exceeding the maximum ratio are treated as the maximum ratio. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the HDR brightening effect attached, supporting chained calls to add other effects. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 20 - 23 |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 24 and later |

**Examples**

```TypeScript
// Create a Filter instance
let filter: uiEffect.Filter = uiEffect.createFilter();
// Set the HDR brightness ratio to 2.0
filter.hdrBrightnessRatio(2.0);
```
