# PageNodeInfo (System API)

```TypeScript
export default interface PageNodeInfo
```

PageNodeInfo defines the page node information used for auto-fill.

**Since:** 26.0.0

<!--Device-unnamed-export default interface PageNodeInfo--><!--Device-unnamed-export default interface PageNodeInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## depth

```TypeScript
depth: number
```

Depth of the page node, in px.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-PageNodeInfo-depth: int--><!--Device-PageNodeInfo-depth: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.

## enableAutoFill

```TypeScript
enableAutoFill: boolean
```

Status of the auto-fill feature. true if enabled, false otherwise.

**Type:** boolean

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-PageNodeInfo-enableAutoFill: boolean--><!--Device-PageNodeInfo-enableAutoFill: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.

## metadata

```TypeScript
metadata?: string
```

Metadata of the page node, used to carry custom attributes or configuration information of the node to help the auto-fill service perform more precise matching and filling. The default value is an empty string.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-PageNodeInfo-metadata?: string--><!--Device-PageNodeInfo-metadata?: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.

## passwordRules

```TypeScript
passwordRules?: string
```

Rule for auto-generating a password, used to specify the format and constraints of the generated password (such as length and character types). It takes effect only when the auto-fill type is password.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-PageNodeInfo-passwordRules?: string--><!--Device-PageNodeInfo-passwordRules?: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.

## tag

```TypeScript
tag: string
```

Tag name of the page node, used to identify the component type of the node.

**Type:** string

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-PageNodeInfo-tag: string--><!--Device-PageNodeInfo-tag: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**System API:** This is a system API.
