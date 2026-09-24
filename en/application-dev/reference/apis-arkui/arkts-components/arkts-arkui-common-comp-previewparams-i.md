# PreviewParams

```TypeScript
interface PreviewParams
```

Implements a configuration object for @Preview parameters. Defines preview device attributes such as device type and screen state.

> **NOTE:** 
> 
> In PreviewParams, only input parameters that match the defined parameter types are supported. Otherwise,
> all @Preview parameters are set to default values.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## colorMode

```TypeScript
colorMode?: string
```

Light or dark mode to display. The value can be light or dark. The default value is dark for TV devices and light for other devices. Wearable devices support only dark.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## deviceType

```TypeScript
deviceType?: string
```

Device type on which the component preview is rendered. The default value is Phone. For details about the device type enums, see [deviceTypes tag](../../../quick-start/module-configuration-file.md#devicetypes).

**Type:** string

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dpi

```TypeScript
dpi?: number
```

Screen DPI of the preview device. The default value is 480. The value is an integer within [120, 640].

**Type:** number

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: number
```

Height of the preview device, in px. The default value is 2340px. The value is an integer within [20, 3000].

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## locale

```TypeScript
locale?: string
```

Language and region of the preview device, for example, zh_CN and en_US. The default value is zh_CN.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## orientation

```TypeScript
orientation?: string
```

Screen orientation of the preview device. Options: **portrait** (default), **landscape**.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## roundScreen

```TypeScript
roundScreen?: boolean
```

Whether the preview screen is circular. Default value: **false**. **true**: circular. **false**: non-circular.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: string
```

Title of the component preview. The default value is the custom component name. Only English letters and digits are supported. Chinese characters and special characters are not supported.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: number
```

Width of the preview device, in px. The default value is 1080px. The value is an integer within [20, 3000].

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
