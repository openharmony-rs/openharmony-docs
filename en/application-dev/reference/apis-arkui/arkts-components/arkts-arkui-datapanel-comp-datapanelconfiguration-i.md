# DataPanelConfiguration

```TypeScript
declare interface DataPanelConfiguration extends CommonConfiguration<DataPanelConfiguration>
```

You need a custom class to implement the **ContentModifier** API. It inherits from [CommonConfiguration](arkts-arkui-common-comp-commonconfiguration-i.md).

**Inheritance/Implementation:** DataPanelConfiguration extends CommonConfiguration<DataPanelConfiguration>

**Since:** 12

<!--Device-unnamed-declare interface DataPanelConfiguration extends CommonConfiguration<DataPanelConfiguration>--><!--Device-unnamed-declare interface DataPanelConfiguration extends CommonConfiguration<DataPanelConfiguration>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxValue

```TypeScript
maxValue: number
```

Maximum value displayed in the data panel.

Default value: **100**

**Note:** 

If the value is less than or equal to 0, **maxValue** is set to the sum of all items in the **values** array, and the values are displayed proportionally.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DataPanelConfiguration-maxValue: number--><!--Device-DataPanelConfiguration-maxValue: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## values

```TypeScript
values: number[]
```

Current values of the data panel.

The array length range is [0, 9].

**Note:** 

If the array length is greater than 9, only the first nine items are used.

**Type:** number[]

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DataPanelConfiguration-values: number[]--><!--Device-DataPanelConfiguration-values: number[]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
