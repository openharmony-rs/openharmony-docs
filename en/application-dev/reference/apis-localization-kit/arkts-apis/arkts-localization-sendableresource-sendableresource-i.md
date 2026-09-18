# SendableResource

This module provides information related to `SendableResource`, including the application bundle package name, application module name, and resource type. `SendableResource` implements the [ISendable](../../../arkts-utils/arkts-sendable.md#isendable) API and supports cross-thread transmission, enabling access to application resources in multi-thread scenarios.

**Inheritance/Implementation:** SendableResource extends lang.ISendable

**Since:** 12

**System capability:** SystemCapability.Global.ResourceManager

## bundleName

```TypeScript
bundleName: string
```

Application bundle name.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.ResourceManager

## id

```TypeScript
id: number
```

Resource ID. The value ranges are as follows: <br>- Application resource ranges: [0x01000000, 0x06FFFFFF] and [0x08000000, 0xFFFFFFFF], indicating the resource IDs of the application itself. <br>- System resource range: [0x07000000, 0x07FFFFFF], indicating the resource IDs preset by the system.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.ResourceManager

## moduleName

```TypeScript
moduleName: string
```

Application module name.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.ResourceManager

## params

```TypeScript
params?: collections.Array <string | number>
```

Resource parameters, including the resource name (string type), replacement values for formatting APIs (string or number in the order of placeholders), and plural quantifier (number type, indicating the quantity). The replacement value of the formatting API is used for parameter substitution during string formatting, while the quantifier of the plural API is used to select the plural form in multilingual environments.

**Type:** [collections.Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)&lt;string &#124; number&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.ResourceManager

## type

```TypeScript
type?: number
```

Resource type. The options are as follows: <br>- 10001: color <br>- 10002: float <br>- 10003: string <br>- 10004: plural <br>- 10005: boolean <br>- 10006: intarray <br>- 10007: integer <br>- 10008: pattern <br>- 10009: strarray <br>- 20000: media <br>- 30000: rawfile <br>- 40000: symbol

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Global.ResourceManager
