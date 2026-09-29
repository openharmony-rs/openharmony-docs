# PageNodeInfo

```TypeScript
export default interface PageNodeInfo
```

PageNodeInfo defines the page node information used for auto-fill.

**Since:** 26.0.0

<!--Device-unnamed-export default interface PageNodeInfo--><!--Device-unnamed-export default interface PageNodeInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## autoFillType

```TypeScript
autoFillType: AutoFillType
```

The auto fill type of page node.

**Type:** [AutoFillType](arkts-ability-autofilltype-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-PageNodeInfo-autoFillType: AutoFillType--><!--Device-PageNodeInfo-autoFillType: AutoFillType-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## id

```TypeScript
id: number
```

The id of page node. The value should be an integer

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-PageNodeInfo-id: int--><!--Device-PageNodeInfo-id: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## isFocus

```TypeScript
isFocus: boolean
```

Is the page node in the focus. The value **true** means the current node is focused; The value **false** means the current node is not focused.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PageNodeInfo-isFocus: boolean--><!--Device-PageNodeInfo-isFocus: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## placeholder

```TypeScript
placeholder?: string
```

The placeholder of page node.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-PageNodeInfo-placeholder?: string--><!--Device-PageNodeInfo-placeholder?: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## rect

```TypeScript
rect: AutoFillRect
```

The rect of page node.

**Type:** [AutoFillRect](arkts-ability-autofillrect-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PageNodeInfo-rect: AutoFillRect--><!--Device-PageNodeInfo-rect: AutoFillRect-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

## value

```TypeScript
value: string
```

The value of page node.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-PageNodeInfo-value: string--><!--Device-PageNodeInfo-value: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore
