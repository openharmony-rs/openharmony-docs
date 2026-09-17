# Resource

This module provides resource-related information, including the application package name, application module name, and resource ID.

**Since:** 9

**System capability:** SystemCapability.Global.ResourceManager

## bundleName

```TypeScript
bundleName: string
```

Application bundle name.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

## id

```TypeScript
id: number
```

Resource ID. The value ranges are as follows: <br>- Application resource ranges: [0x01000000, 0x06FFFFFF] and [0x08000000, 0xFFFFFFFF], indicating the resource IDs of the application itself. <br>- System resource range: [0x07000000, 0x07FFFFFF], indicating the resource IDs preset by the system.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

## moduleName

```TypeScript
moduleName: string
```

Application module name.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

## params

```TypeScript
params?: any[]
```

Resource parameters, including the resource name (string type), replacement values for formatting APIs (string or number types in the order of placeholders), and plural quantifier (number type, indicating the quantity). The replacement value of the formatting API is used for parameter substitution during string formatting, while the quantifier of the plural API is used to select the plural form in multilingual environments.

**Type:** any[]

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

## type

```TypeScript
type?: number
```

Resource type. The options are as follows: <br>- 10001: color <br>- 10002: float <br>- 10003: string <br>- 10004: plural <br>- 10005: boolean <br>- 10006: intarray <br>- 10007: integer <br>- 10008: pattern <br>- 10009: strarray <br>- 20000: media <br>- 30000: rawfile <br>- 40000: symbol

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager
