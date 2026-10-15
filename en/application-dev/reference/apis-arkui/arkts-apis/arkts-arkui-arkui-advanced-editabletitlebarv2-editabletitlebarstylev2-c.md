# EditableTitleBarStyleV2

```TypeScript
export declare class EditableTitleBarStyleV2
```

Defines the title bar style configuration class, which is decorated with **@ObservedV2** and supports state observation.

**Since:** 26.0.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class EditableTitleBarStyleV2--><!--Device-unnamed-export declare class EditableTitleBarStyleV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { EditableLeftIconTypeV2, EditableTitleBarV2, EditableLeftIconV2, EditableLeftIconV2Options, EditableTitleV2, EditableTitleV2Options, EditableTitleBarItemV2, EditableTitleBarItemV2Options, EditableTitleBarMenuItemV2, EditableTitleBarMenuItemV2Options, EditableSaveButtonV2, EditableSaveButtonV2Options, EditableTitleBarStyleV2, EditableTitleBarStyleV2Options } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: EditableTitleBarStyleV2Options)
```

A constructor used to create an **EditableTitleBarStyleV2** instance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarStyleV2-constructor(options?: EditableTitleBarStyleV2Options)--><!--Device-EditableTitleBarStyleV2-constructor(options?: EditableTitleBarStyleV2Options)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [EditableTitleBarStyleV2Options](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlebarstylev2options-i.md) | No | Options for the title bar style.<br>Default value: **undefined**, which means the default configuration is used when this parameter is not passed. |

## backgroundBlurStyle

```TypeScript
public backgroundBlurStyle?: BlurStyle
```

Background blur style of the title bar.

Default value: **BlurStyle.NONE**, indicating no blur effect.

**Decorator:** @Trace

**Type:** [BlurStyle](../arkts-components/arkts-arkui-common-comp-blurstyle-e.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarStyleV2-public backgroundBlurStyle?: BlurStyle--><!--Device-EditableTitleBarStyleV2-public backgroundBlurStyle?: BlurStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
public backgroundColor?: ResourceColor
```

Background color of the title bar.

Default value: **'#00000000'**, indicating a transparent background.

**Decorator:** @Trace

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarStyleV2-public backgroundColor?: ResourceColor--><!--Device-EditableTitleBarStyleV2-public backgroundColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentMargin

```TypeScript
public contentMargin?: LocalizedMargin
```

Outer margin of the title bar. Negative values are not supported. If a negative value is set, it does not take effect.

Default value:

**{

start: LengthMetrics.resource($r('sys.float.margin_left')),

end: LengthMetrics.resource($r('sys.float.margin_right'))

}**.

**Decorator:** @Trace

**Type:** [LocalizedMargin](arkts-arkui-localizedmargin-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarStyleV2-public contentMargin?: LocalizedMargin--><!--Device-EditableTitleBarStyleV2-public contentMargin?: LocalizedMargin-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## safeAreaEdges

```TypeScript
public safeAreaEdges?: Array<SafeAreaEdge>
```

Edges of the expanded safe area.

Default value: **[SafeAreaEdge.TOP]**.

**Decorator:** @Trace

**Type:** Array&lt;[SafeAreaEdge](../arkts-components/arkts-arkui-common-comp-safeareaedge-e.md)&gt;

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarStyleV2-public safeAreaEdges?: Array<SafeAreaEdge>--><!--Device-EditableTitleBarStyleV2-public safeAreaEdges?: Array<SafeAreaEdge>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## safeAreaTypes

```TypeScript
public safeAreaTypes?: Array<SafeAreaType>
```

Types of the expanded safe area.

Default value: **[SafeAreaType.SYSTEM]**.

**Decorator:** @Trace

**Type:** Array&lt;[SafeAreaType](../arkts-components/arkts-arkui-common-comp-safeareatype-e.md)&gt;

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarStyleV2-public safeAreaTypes?: Array<SafeAreaType>--><!--Device-EditableTitleBarStyleV2-public safeAreaTypes?: Array<SafeAreaType>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
