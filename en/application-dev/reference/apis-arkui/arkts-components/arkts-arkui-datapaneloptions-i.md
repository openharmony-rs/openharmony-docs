# DataPanelOptions

Defines data panel configuration options.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## max

```TypeScript
max?: number
```

- When set to a value greater than 0, this parameter indicates the maximum value in the **values** list.  
- When set to a value equal to or smaller than 0, this parameter indicates the sum of values in the **values**  
list, and the values are displayed proportionally based on their relative sizes.

Default value: **100**

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: DataPanelType
```

Type of the data panel (dynamic modification is not supported).

Default value: **DataPanelType.Circle**

**Type:** [DataPanelType](arkts-arkui-datapaneltype-e.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## values

```TypeScript
values: number[]
```

Data value list. A maximum of nine values are supported. If more than nine values are set, only the first nine ones are used. A value less than 0 evaluates to the value **0**.

**Type:** number[]

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
