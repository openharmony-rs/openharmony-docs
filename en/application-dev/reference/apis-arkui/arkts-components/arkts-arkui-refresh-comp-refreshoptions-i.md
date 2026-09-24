# RefreshOptions

```TypeScript
interface RefreshOptions
```

Defines the options of the **Refresh** component.

> **Supplementary Notes**
> 
> - If neither **builder** nor **refreshingContent** is set, the pull-down displacement effect is implemented by adjusting the [translate](arkts-arkui-common-comp-commonmethod-c.md#translate) attribute of the child component.During the pull-down process, the [onAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onareachange) event of the child component is not triggered, and any changes made to the [translate](arkts-arkui-common-comp-commonmethod-c.md#translate) attribute of the child component do not take effect.
> 
> - When **builder** or **refreshingContent** is set, the pull-down displacement effect is implemented by adjusting the position of the child component relative to the **Refresh** component. During the pull-down process, the [onAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onareachange) event of the child component can be triggered. However, if the [position](arkts-arkui-common-comp-commonmethod-c.md#position) attribute is set for the child component, the position of the child component relative to the **Refresh** component is fixed, preventing the child component from moving down with the pull gesture.
> 
> - If the width and height of a custom component set by **builder** are not specified, its dimensions will adapt to the child components. If the width is specified but the height is not, the height of the component is automatically adjusted according to the pull-down distance. If a custom component set by **refreshingContent** does not have a specified height, its height will also adapt to the pull-down distance. In such cases, as the pull-down distance increases, the height of the custom component will increase accordingly. When the custom component's height is set to a fixed value or reaches its maximum height limit, further increases in the pull-down distance will cause the spacing between the custom component and the top boundary of the **Refresh** component to widen.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder?: CustomBuilder
```

Custom content in the refreshing area. NOTE In API version 10 and earlier versions, there is a height limit of 64 vp on custom components. This restriction is removed since API version 11. When a custom component is set with a fixed height, it will be displayed below the refreshing area at that fixed height; when the custom component does not have a height set, its height will adapt to the height of the refreshing area, which may result in the height of the custom component changing to 0 along with the refreshing area. To maintain the intended layout, configure a minimum height constraint for a custom component, which ensures that the component's height does not fall below a certain threshold. For details about how to apply this constraint, see [Example 3](../../../reference/apis-arkui/arkui-ts/ts-container-refresh.md#example-3-customizing-the-refreshing-area-content-with-builder). Since API version 12, use **refreshingContent** instead of **builder** for customizing the content of the refreshing area, to avoid animation interruptions caused by the destruction and re-creation of the custom component during the refreshing process.

**Type:** [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## friction

```TypeScript
friction?: number | string
```

Coefficient of friction, which indicates the component's sensitivity to the pull-down gesture. The value ranges from 0 to 100. Default value: 62

- 0 indicates that the component is not sensitive to the pull-down gesture.  
- 100 indicates that the component is highly sensitive to the pull-down gesture.  
- A larger value indicates a more sensitive response of the component to the pull-down gesture.

**Type:** number &#124; string

**Since:** 8

**Deprecated since:** 11

**Substitutes:** [pullDownRatio](arkts-arkui-refresh-comp-attribute.md#pulldownratio)

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number | string
```

Distance from the pull-down starting point to the top of the component. Default value: **16**. Unit: vp. If the type is string, the pixel unit must be explicitly specified, for example, **'10px'**; if the unit is not specified, for example, **'10'**, the default unit vp is used. Note: This API is supported since API version 8 and deprecated since API version 11. No substitute is provided. NOTE The value range of **offset** is [0vp, 64vp]. If the value is greater than 64 vp, the value 64 vp will be used. The value cannot be a percentage or a negative number.

**Type:** number &#124; string

**Since:** 8

**Deprecated since:** 11

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## promptText

```TypeScript
promptText?: ResourceStr
```

Custom text displayed at the bottom of the refreshing area. NOTE When setting the text, follow the constraints on the **Text** components. If you are using **builder** or **refreshingContent** to customize the content displayed in the refreshing area, the text set with **promptText** will not be displayed. When **promptText** is set and effective, the refreshOffset attribute defaults to 96 vp. The maximum font scale factor for the custom text, as specified by maxFontScale, is 2.

**Type:** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## refreshing

```TypeScript
refreshing: boolean
```

Whether the component is being refreshed. The value **true** means that the component is being refreshed, and **false** means the opposite. Default value: **false** This parameter supports two-way binding through $$.

**Type:** boolean

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## refreshingContent

```TypeScript
refreshingContent?: ComponentContent
```

Custom content in the refreshing area. NOTE If this parameter and the **builder** parameter are set at the same time, the **builder** parameter does not take effect. When a custom component is set with a fixed height, it will be displayed below the refreshing area at that fixed height; when the custom component does not have a height set, its height will adapt to the height of the refreshing area, which may result in the height of the custom component changing to 0 along with the refreshing area. To maintain the intended layout, configure a minimum height constraint for a custom component, which ensures that the component's height does not fall below a certain threshold. For details about how to apply this constraint, see [Example 4](../../../reference/apis-arkui/arkui-ts/ts-container-refresh.md#example-4-customizing-the-refreshing-area-content-with-refreshingcontent).

**Type:** ComponentContent

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
