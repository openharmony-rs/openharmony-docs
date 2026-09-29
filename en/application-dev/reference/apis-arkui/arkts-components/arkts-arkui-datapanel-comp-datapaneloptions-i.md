# DataPanelOptions

```TypeScript
declare interface DataPanelOptions
```

Defines data panel configuration options.

**Since:** 7

<!--Device-unnamed-declare interface DataPanelOptions--><!--Device-unnamed-declare interface DataPanelOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## max

```TypeScript
max?: number
```

- When set to a value greater than 0, this parameter indicates the maximum value in the **values** list.  
- When set to a value equal to or smaller than 0, this parameter indicates the sum of values in the **values**  
list, and the values are displayed proportionally.

Default Value: **100**

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-DataPanelOptions-max?: number--><!--Device-DataPanelOptions-max?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: DataPanelType
```

Type of the data panel (dynamic modification is not supported).

The value options are as follows: **DataPanelType.Line** (linear data panel, suitable for displaying comparisons of multiple data segments in limited space) and **DataPanelType.Circle** (circle data panel, suitable for intuitively displaying data proportion relationships).

If not passed, the default value is **DataPanelType.Circle**.

**Type:** [DataPanelType](arkts-arkui-datapanel-comp-datapaneltype-e.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-DataPanelOptions-type?: DataPanelType--><!--Device-DataPanelOptions-type?: DataPanelType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## values

```TypeScript
values: number[]
```

Data value list. The array length range is [0, 9]. If more than nine values are set, only the first nine ones are used. A value less than 0 evaluates to the value **0**.

**Type:** number[]

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-DataPanelOptions-values: number[]--><!--Device-DataPanelOptions-values: number[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
