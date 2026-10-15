# EditableTitleBarStyleV2Options

```TypeScript
export declare interface EditableTitleBarStyleV2Options
```

Defines the title bar style configuration options.

**Since:** 26.0.0

<!--Device-unnamed-export declare interface EditableTitleBarStyleV2Options--><!--Device-unnamed-export declare interface EditableTitleBarStyleV2Options-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { EditableLeftIconTypeV2, EditableTitleBarV2, EditableLeftIconV2, EditableLeftIconV2Options, EditableTitleV2, EditableTitleV2Options, EditableTitleBarItemV2, EditableTitleBarItemV2Options, EditableTitleBarMenuItemV2, EditableTitleBarMenuItemV2Options, EditableSaveButtonV2, EditableSaveButtonV2Options, EditableTitleBarStyleV2, EditableTitleBarStyleV2Options } from '@kit.ArkUI';
```

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

Background blur style of the title bar. Pass this parameter when a background blur effect is needed for the title bar. If it is not passed, no blur effect is applied.

Default value: **BlurStyle.NONE**, indicating no blur effect.

**Type:** [BlurStyle](../arkts-components/arkts-arkui-common-comp-blurstyle-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarStyleV2Options-backgroundBlurStyle?: BlurStyle--><!--Device-EditableTitleBarStyleV2Options-backgroundBlurStyle?: BlurStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## backgroundColor

```TypeScript
backgroundColor?: ResourceColor
```

Background color of the title bar.

Default value: **'#00000000'**, indicating a transparent background.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarStyleV2Options-backgroundColor?: ResourceColor--><!--Device-EditableTitleBarStyleV2Options-backgroundColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentMargin

```TypeScript
contentMargin?: LocalizedMargin
```

Outer margin of the title bar. Negative values are not supported (they do not take effect).

Default value:

**{

start: LengthMetrics.resource($r('sys.float.margin_left')),

end: LengthMetrics.resource($r('sys.float.margin_right'))

}**.

**Type:** [LocalizedMargin](arkts-arkui-localizedmargin-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarStyleV2Options-contentMargin?: LocalizedMargin--><!--Device-EditableTitleBarStyleV2Options-contentMargin?: LocalizedMargin-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## safeAreaEdges

```TypeScript
safeAreaEdges?: Array<SafeAreaEdge>
```

Edges of the expanded safe area. Pass this parameter when the safe area expansion direction needs to be customized. If it is not passed, the safe area is expanded upward by default.

Default value: **[SafeAreaEdge.TOP]**

**Type:** Array&lt;[SafeAreaEdge](../arkts-components/arkts-arkui-common-comp-safeareaedge-e.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarStyleV2Options-safeAreaEdges?: Array<SafeAreaEdge>--><!--Device-EditableTitleBarStyleV2Options-safeAreaEdges?: Array<SafeAreaEdge>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## safeAreaTypes

```TypeScript
safeAreaTypes?: Array<SafeAreaType>
```

Types of the expanded safe area. Pass this parameter when the title bar needs to be extended to a specific safe area. If it is not passed, the title bar is extended only to the system safe area.

Default value: **[SafeAreaType.SYSTEM]**

**Type:** Array&lt;[SafeAreaType](../arkts-components/arkts-arkui-common-comp-safeareatype-e.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleBarStyleV2Options-safeAreaTypes?: Array<SafeAreaType>--><!--Device-EditableTitleBarStyleV2Options-safeAreaTypes?: Array<SafeAreaType>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
