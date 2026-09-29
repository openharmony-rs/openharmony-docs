# EnvPropsOptions

```TypeScript
declare interface EnvPropsOptions
```

Defines a key-value pair object used to specify environment variable names and their default values, passed as a parameter to [envProps](arkts-arkui-environment-c.md#envprops).

**Since:** 10

<!--Device-unnamed-declare interface EnvPropsOptions--><!--Device-unnamed-declare interface EnvPropsOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## defaultValue

```TypeScript
defaultValue: number | string | boolean
```

Default value used if the value of the specified environment variable key is not found in AppStorage.

**Type:** number &#124; string &#124; boolean

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-EnvPropsOptions-defaultValue: number | string | boolean--><!--Device-EnvPropsOptions-defaultValue: number | string | boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key: string
```

Environment variable name. For details about the value range, see [Built-in Environment Variables](arkts-arkui-environment-c.md#built-in-environment-variables).

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-EnvPropsOptions-key: string--><!--Device-EnvPropsOptions-key: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
