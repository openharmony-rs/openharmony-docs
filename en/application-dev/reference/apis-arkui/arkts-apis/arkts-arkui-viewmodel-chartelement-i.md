# ChartElement

The &lt;chart&gt; component displays line charts, gauge charts, and bar charts.

@extends Element @interface ChartElement

**Inheritance/Implementation:** ChartElement extends [Element](arkts-arkui-viewmodel-element-i.md)

**Since:** 4

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## append

```TypeScript
append(params: {
    /**
     * Set the data subscript of the line chart to be updated.
     *
     * @type { number }
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @famodelonly
     * @since 4 dynamiconly
     */
    serial: number;
    /**
     * Set the new data.
     *
     * @type { Array<number> }
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @famodelonly
     * @since 4 dynamiconly
     */
    data: Array<number>;
  }): void
```

Data is dynamiconlyally added to an existing data sequence. The target sequence is specified based on serial, which is the subscript of the datasets array and starts from 0. datasets[index].data is not updated. Only line charts support this attribute. The value is incremented by 1 based on the horizontal coordinate and is related to the xAxis min/max setting.

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | {     /**      * Set the data subscript of the line chart to be updated.      *      * @type { number }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @famodelonly      * @since 4 dynamiconly      */     serial: number;     /**      * Set the new data.      *      * @type { Array&lt;number&gt; }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @famodelonly      * @since 4 dynamiconly      */     data: Array&lt;number&gt;;   } | Yes |  |
