# DeviceResponse

```TypeScript
export interface DeviceResponse
```

Defines the device profile information.

**Since:** 3

**Deprecated since:** 6

<!--Device-unnamed-export interface DeviceResponse--><!--Device-unnamed-export interface DeviceResponse-End-->

**System capability:** SystemCapability.Startup.SystemInfo.Lite

## Modules to Import

```TypeScript
import { Device, DeviceResponse, GetDeviceOptions } from '@kit.BasicServicesKit';
```

## apiVersion

```TypeScript
apiVersion: number
```

API version.

**Type:** number

**Since:** 4

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DeviceResponse-apiVersion: number--><!--Device-DeviceResponse-apiVersion: number-End-->

**System capability:** SystemCapability.Startup.SystemInfo.Lite

## brand

```TypeScript
brand: string
```

Brand.

**Type:** string

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DeviceResponse-brand: string--><!--Device-DeviceResponse-brand: string-End-->

**System capability:** SystemCapability.Startup.SystemInfo.Lite

## deviceType

```TypeScript
deviceType: string
```

Device type. The options are as follows: **phone**, **tablet**, **tv**, and **wearable**.

**Type:** string

**Since:** 4

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DeviceResponse-deviceType: string--><!--Device-DeviceResponse-deviceType: string-End-->

**System capability:** SystemCapability.Startup.SystemInfo.Lite

## language

```TypeScript
language: string
```

System language.

**Type:** string

**Since:** 4

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DeviceResponse-language: string--><!--Device-DeviceResponse-language: string-End-->

**System capability:** SystemCapability.Startup.SystemInfo.Lite

## manufacturer

```TypeScript
manufacturer: string
```

Manufacturer.

**Type:** string

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DeviceResponse-manufacturer: string--><!--Device-DeviceResponse-manufacturer: string-End-->

**System capability:** SystemCapability.Startup.SystemInfo.Lite

## model

```TypeScript
model: string
```

Model.

**Type:** string

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DeviceResponse-model: string--><!--Device-DeviceResponse-model: string-End-->

**System capability:** SystemCapability.Startup.SystemInfo.Lite

## product

```TypeScript
product: string
```

Product code.

**Type:** string

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DeviceResponse-product: string--><!--Device-DeviceResponse-product: string-End-->

**System capability:** SystemCapability.Startup.SystemInfo.Lite

## region

```TypeScript
region: string
```

System region.

**Type:** string

**Since:** 4

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DeviceResponse-region: string--><!--Device-DeviceResponse-region: string-End-->

**System capability:** SystemCapability.Startup.SystemInfo.Lite

## screenDensity

```TypeScript
screenDensity: number
```

Screen pixel density, which indicates the number of pixels per inch on the screen, in dots per inch (DPI). The screen pixel density varies depending on the device.

**Type:** number

**Since:** 4

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DeviceResponse-screenDensity: number--><!--Device-DeviceResponse-screenDensity: number-End-->

**System capability:** SystemCapability.Startup.SystemInfo.Lite

## screenShape

```TypeScript
screenShape: 'rect' | 'circle'
```

Screen shape. The options are as follows:  
- **rect**: rectangular screen  
- **circle**: round screen

**Type:** 'rect' &#124; 'circle'

**Since:** 4

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DeviceResponse-screenShape: 'rect' | 'circle'--><!--Device-DeviceResponse-screenShape: 'rect' | 'circle'-End-->

**System capability:** SystemCapability.Startup.SystemInfo.Lite

## sdkMinorApiVersion

```TypeScript
sdkMinorApiVersion?: number
```

SDK minor API version. Since API version 26.0.0, the API version is in the format of **apiVersion.sdkMinorApiVersion.sdkPatchApiVersion**. If the value fails to be obtained, **-1** is returned, which does not affect the overall return status of the **getInfo** API.

**Model constraint:** This API can be used only in the FA model. **Since version**: 26.0.0 Example: 0

**Type:** number

**Since:** 26.0.0

**Deprecated since:** 26.0.0

**Model restriction:** This API can be used only in the FA model.

<!--Device-DeviceResponse-sdkMinorApiVersion?: number--><!--Device-DeviceResponse-sdkMinorApiVersion?: number-End-->

**System capability:** SystemCapability.Startup.SystemInfo.Lite

## sdkPatchApiVersion

```TypeScript
sdkPatchApiVersion?: number
```

SDK patch API version. Since API version 26.0.0, the API version is in the format of **apiVersion.sdkMinorApiVersion.sdkPatchApiVersion**. If the value fails to be obtained, **-1** is returned, which does not affect the overall return status of the **getInfo** API.

**Model constraint:** This API can be used only in the FA model. **Since version**: 26.0.0 Example: 0

**Type:** number

**Since:** 26.0.0

**Deprecated since:** 26.0.0

**Model restriction:** This API can be used only in the FA model.

<!--Device-DeviceResponse-sdkPatchApiVersion?: number--><!--Device-DeviceResponse-sdkPatchApiVersion?: number-End-->

**System capability:** SystemCapability.Startup.SystemInfo.Lite

## windowHeight

```TypeScript
windowHeight: number
```

Available window height, in px. The available window size varies on different devices.

**Type:** number

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DeviceResponse-windowHeight: number--><!--Device-DeviceResponse-windowHeight: number-End-->

**System capability:** SystemCapability.Startup.SystemInfo.Lite

## windowWidth

```TypeScript
windowWidth: number
```

Available window width, in px. The available window size varies on different devices.

**Type:** number

**Since:** 3

**Deprecated since:** 6

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-DeviceResponse-windowWidth: number--><!--Device-DeviceResponse-windowWidth: number-End-->

**System capability:** SystemCapability.Startup.SystemInfo.Lite
