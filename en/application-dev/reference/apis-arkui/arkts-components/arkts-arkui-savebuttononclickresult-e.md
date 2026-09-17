# SaveButtonOnClickResult

Enumerates the authorization results after the **SaveButton** component is tapped.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SUCCESS

```TypeScript
SUCCESS = 0
```

Authorization is successful.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TEMPORARY_AUTHORIZATION_FAILED

```TypeScript
TEMPORARY_AUTHORIZATION_FAILED = 1
```

Authorization fails.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CANCELED_BY_USER

```TypeScript
CANCELED_BY_USER = 2
```

Authorization is canceled by the user through a dialog box after the **SaveButton** component is clicked. This value is returned in the callback result only when [userCancelEvent](arkts-arkui-savebutton-comp-attribute.md#usercancelevent) is triggered with its parameter set to **true**.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
