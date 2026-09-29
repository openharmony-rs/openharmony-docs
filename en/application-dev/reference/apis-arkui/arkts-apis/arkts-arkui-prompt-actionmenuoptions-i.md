# ActionMenuOptions

```TypeScript
interface ActionMenuOptions
```

Describes the options for showing the action menu.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [ActionMenuOptions](arkts-arkui-promptaction-actionmenuoptions-i.md)

<!--Device-prompt-interface ActionMenuOptions--><!--Device-prompt-interface ActionMenuOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { prompt } from '@kit.ArkUI';
```

## buttons

```TypeScript
buttons: [Button, Button?, Button?, Button?, Button?, Button?]
```

Array of menu item buttons. The array structure is **{text:'button', color: '#666666'}**. Up to six buttons are supported. If there are more than six buttons, extra buttons will not be displayed.

**Type:** [Button, Button?, Button?, Button?, Button?, Button?]

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [buttons](arkts-arkui-promptaction-actionmenuoptions-i.md#buttons)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ActionMenuOptions-buttons: [Button, Button?, Button?, Button?, Button?, Button?]--><!--Device-ActionMenuOptions-buttons: [Button, Button?, Button?, Button?, Button?, Button?]-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: string
```

Title of the menu.

**Type:** string

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [title](arkts-arkui-promptaction-actionmenuoptions-i.md#title)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ActionMenuOptions-title?: string--><!--Device-ActionMenuOptions-title?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
