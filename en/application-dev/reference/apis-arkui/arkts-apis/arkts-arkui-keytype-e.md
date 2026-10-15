# KeyType

```TypeScript
declare enum KeyType
```

Sets the status type of a button operation.

**Since:** 7

<!--Device-unnamed-declare enum KeyType--><!--Device-unnamed-declare enum KeyType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CANCEL

```TypeScript
CANCEL = 3
```

The key event is canceled. In the [global monitoring of basic input events](../../../reference/apis-arkui/arkui-ts/ts-inputeventmonitor.md), blocking the **Up** event propagation automatically dispatches a **CANCEL** event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-KeyType-CANCEL = 3--><!--Device-KeyType-CANCEL = 3-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Down

```TypeScript
Down
```

The key is pressed.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-KeyType-Down--><!--Device-KeyType-Down-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Up

```TypeScript
Up
```

The key is released.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-KeyType-Up--><!--Device-KeyType-Up-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
