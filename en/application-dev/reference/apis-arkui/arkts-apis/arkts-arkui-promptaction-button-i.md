# Button

Describes the menu item button in the action menu.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## color

```TypeScript
color: string | Resource
```

Text color of the button.

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## primary

```TypeScript
primary?: boolean
```

Whether the button responds to the **Enter** key by default when the dialog box has focus and the **Tab** key is not pressed for sequential focus navigation. If there are multiple buttons, set this parameter to **true** for only one button. Otherwise, no button will respond. Multiple dialog boxes can automatically gain focus and respond to user interactions in a sequential manner. **true**: The button responds to the **Enter** key by default. **false**: The button does not respond to the **Enter** key by default.<br>Default value: **false**.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text: string | Resource
```

Button text.

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
