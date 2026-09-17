# SmartGestureShortcutOptions

Smart gesture response behavior configuration object.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action?: GestureShortcut
```

Smart gesture response priority. Currently only **GestureShortcut.PRIMARY** is supported, indicating the component serves as the preferred response target for smart gesture operations such as swiping and clicking.

Default value: **GestureShortcut.PRIMARY**.

**Type:** [GestureShortcut](../arkts-apis/arkts-arkui-gestureshortcut-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enabled

```TypeScript
enabled?: boolean
```

Whether the current component responds to smart gestures.

**true**: The component responds to smart gestures.

**false**: The component does not respond to smart gestures.

Default value: **false**.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectable

```TypeScript
selectable?: boolean
```

Whether to display and retain the selected state after the component is selected by a smart gesture operation.

**true**: Show the selection indicator.

**false**: Do not show the selection indicator.

When **enabled** is **true**, the default value is **true**; when **enabled** is **false**, the default value is **false**.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
