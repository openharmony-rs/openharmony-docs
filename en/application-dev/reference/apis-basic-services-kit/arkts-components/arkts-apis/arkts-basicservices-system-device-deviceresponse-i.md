# DeviceResponse

```TypeScript
export interface DeviceResponse
```

Defines the device profile information.

**Since:** 3

**Deprecated since:** 6

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

**System capability:** SystemCapability.Startup.SystemInfo.Lite
