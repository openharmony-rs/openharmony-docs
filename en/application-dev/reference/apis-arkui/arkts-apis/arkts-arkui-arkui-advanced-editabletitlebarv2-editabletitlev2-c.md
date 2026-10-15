# EditableTitleV2

```TypeScript
export declare class EditableTitleV2
```

Defines the title configuration class, which is decorated with **@ObservedV2** and supports state observation.

**Since:** 26.0.0

**Decorator:** @ObservedV2

<!--Device-unnamed-export declare class EditableTitleV2--><!--Device-unnamed-export declare class EditableTitleV2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { EditableLeftIconTypeV2, EditableTitleBarV2, EditableLeftIconV2, EditableLeftIconV2Options, EditableTitleV2, EditableTitleV2Options, EditableTitleBarItemV2, EditableTitleBarItemV2Options, EditableTitleBarMenuItemV2, EditableTitleBarMenuItemV2Options, EditableSaveButtonV2, EditableSaveButtonV2Options, EditableTitleBarStyleV2, EditableTitleBarStyleV2Options } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: EditableTitleV2Options)
```

A constructor used to create an **EditableTitleV2** instance.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleV2-constructor(options?: EditableTitleV2Options)--><!--Device-EditableTitleV2-constructor(options?: EditableTitleV2Options)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [EditableTitleV2Options](arkts-arkui-arkui-advanced-editabletitlebarv2-editabletitlev2options-i.md) | No | Title configuration options.<br>Default value: undefined. If this parameter is not passed, the default value of each attribute is used. |

## mainTitle

```TypeScript
public mainTitle: ResourceStr
```

Main title content.

Default value: **''**, indicating that the title content is empty.

**Decorator:** @Trace

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Default:** ''

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleV2-public mainTitle: ResourceStr--><!--Device-EditableTitleV2-public mainTitle: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## subTitle

```TypeScript
public subTitle?: ResourceStr
```

Subtitle content. Pass this parameter when supplementary information needs to be displayed below the title.

Default value: **undefined**, indicating that the subtitle is not displayed.

**Decorator:** @Trace

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Decorator:** @Trace

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleV2-public subTitle?: ResourceStr--><!--Device-EditableTitleV2-public subTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
