# EditableTitleV2Options

```TypeScript
export declare interface EditableTitleV2Options
```

Defines the title configuration options.

**Since:** 26.0.0

<!--Device-unnamed-export declare interface EditableTitleV2Options--><!--Device-unnamed-export declare interface EditableTitleV2Options-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { EditableLeftIconTypeV2, EditableTitleBarV2, EditableLeftIconV2, EditableLeftIconV2Options, EditableTitleV2, EditableTitleV2Options, EditableTitleBarItemV2, EditableTitleBarItemV2Options, EditableTitleBarMenuItemV2, EditableTitleBarMenuItemV2Options, EditableSaveButtonV2, EditableSaveButtonV2Options, EditableTitleBarStyleV2, EditableTitleBarStyleV2Options } from '@kit.ArkUI';
```

## mainTitle

```TypeScript
mainTitle?: ResourceStr
```

Primary title content.

Default value: **''**, which means the title content is empty.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleV2Options-mainTitle?: ResourceStr--><!--Device-EditableTitleV2Options-mainTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## subTitle

```TypeScript
subTitle?: ResourceStr
```

Subtitle content. Pass this parameter when supplementary information needs to be displayed below the title.

Default value: **undefined**, which means no subtitle is displayed.

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EditableTitleV2Options-subTitle?: ResourceStr--><!--Device-EditableTitleV2Options-subTitle?: ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
