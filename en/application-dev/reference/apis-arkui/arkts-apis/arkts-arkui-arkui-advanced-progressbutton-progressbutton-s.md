# ProgressButton

```TypeScript
export declare struct ProgressButton
```

The **ProgressButton** component is a text-based download button with a progress indicator that shows the download progress.

> **NOTE:** 
> 
> - This component can be used only in the stage model.
> 
> - If the **ProgressButton** component has [universal attributes](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) and [universal events](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) configured, the compiler toolchain automatically generates an additional \_\_Common\_\_ node and mounts the universal attributes and universal events on this node rather than the **ProgressButton** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **ProgressButton** component.

The [universal events](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md) are not supported.

**Since:** 10

**Decorator:** @Component

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ProgressButton } from '@kit.ArkUI';
```

## clickCallback

```TypeScript
clickCallback: () => void
```

Callback invoked when the button is clicked.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## colorOptions

```TypeScript
colorOptions?: ProgressButtonColorOptions
```

Color options of the button. This parameter is used to customize the color of each part of the button (progress indicator, stroke, text, and background). This parameter is passed in when a custom color is required. If it is not passed, the default color scheme is used.

**Type:** [ProgressButtonColorOptions](arkts-arkui-arkui-advanced-progressbutton-progressbuttoncoloroptions-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content: ResourceStr
```

Button text.

The default value is an empty string.

Note: The text is truncated with an ellipsis (...) if it exceeds the maximum display width of the component. The Resource type is supported since API version 20.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enable

```TypeScript
enable: boolean
```

Whether the button can be clicked.

**true**: The button can be clicked.

**false**: The button cannot be clicked.

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## progress

```TypeScript
progress: number
```

Current download progress.

The value ranges from 0 to 100. Values less than 0 are adjusted to **0**, and values greater than 100 are capped at **100**.

Default value: **0**.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## progressButtonRadius

```TypeScript
progressButtonRadius?: LengthMetrics
```

Corner radius of the button. It cannot be set in percentage.

Value range: [0, height/2]

Default value: height/2

If the value is less than 0, the value **0** is used. If the value is invalid, the default value is used. If the input parameter is **undefined**, the default value is used. When using LengthMetrics.vp, you are advised to provide a specific numeric value. Passing **null** or **undefined** will result in an exception.

**Type:** LengthMetrics

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## progressButtonWidth

```TypeScript
progressButtonWidth?: Length
```

Button width, in vp.

The value must be greater than or equal to 44 vp.

The default value is **44vp**. If the provided value is not of the Resource type and is either less than the default value or invalid, the system will automatically use the default value. If the provided value is of the Resource type but is less than the default value, the system will automatically use the default value. If the provided value is invalid, the button width will be 100% of the container width.

**Type:** [Length](arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
