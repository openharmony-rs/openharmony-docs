# NavDestinationActiveReason

```TypeScript
declare enum NavDestinationActiveReason
```

Enumerates reasons for the activation state changes of the **NavDestination** component.

**Since:** 17

<!--Device-unnamed-declare enum NavDestinationActiveReason--><!--Device-unnamed-declare enum NavDestinationActiveReason-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## APP_STATE

```TypeScript
APP_STATE = 5
```

Activation state changes due to switching between foreground and background states of the application.

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

<!--Device-NavDestinationActiveReason-APP_STATE = 5--><!--Device-NavDestinationActiveReason-APP_STATE = 5-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CONTENT_COVER

```TypeScript
CONTENT_COVER = 1
```

Activation state changes due to the opening or closing of a modal page.

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

<!--Device-NavDestinationActiveReason-CONTENT_COVER = 1--><!--Device-NavDestinationActiveReason-CONTENT_COVER = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DIALOG

```TypeScript
DIALOG = 3
```

Activation state changes due to the opening or closing of a custom dialog box.

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

<!--Device-NavDestinationActiveReason-DIALOG = 3--><!--Device-NavDestinationActiveReason-DIALOG = 3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## OVERLAY

```TypeScript
OVERLAY = 4
```

Activation state changes due to the opening or closing of an overlay using **OverlayManager**.

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

<!--Device-NavDestinationActiveReason-OVERLAY = 4--><!--Device-NavDestinationActiveReason-OVERLAY = 4-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SHEET

```TypeScript
SHEET = 2
```

Activation state changes due to the opening or closing of a sheet.

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

<!--Device-NavDestinationActiveReason-SHEET = 2--><!--Device-NavDestinationActiveReason-SHEET = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TRANSITION

```TypeScript
TRANSITION = 0
```

Activation state changes due to page navigation.

**Since:** 17

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 17.

<!--Device-NavDestinationActiveReason-TRANSITION = 0--><!--Device-NavDestinationActiveReason-TRANSITION = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
