# LaunchMode

Enumerates the operation modes for the routing stack.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## STANDARD

```TypeScript
STANDARD = 0
```

Default routing stack operation mode.

In this mode, push operations add the specified **NavDestination** page to the stack; replace operations replace the current top **NavDestination** page.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MOVE_TO_TOP_SINGLETON

```TypeScript
MOVE_TO_TOP_SINGLETON = 1
```

This mode searches from the bottom to the top of the routing stack. If a **NavDestination** page with the specified name exists, it moves that page to the top of the stack (for a replace operation, it replaces the last top **NavDestination** page with the specified one); otherwise, it behaves like **STANDARD**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## POP_TO_SINGLETON

```TypeScript
POP_TO_SINGLETON = 2
```

This mode searches from the bottom to the top of the routing stack. If a **NavDestination** page with the specified name exists, it removes all **NavDestination** pages above it(for a replace operation, it replaces the last top **NavDestination** page with the specified one); otherwise, it behaves like **STANDARD**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NEW_INSTANCE

```TypeScript
NEW_INSTANCE = 3
```

This mode creates an instance of **NavDestination**. Compared with **STANDARD**, this mode does not reuse the instance with the same name in the stack. When this mode is specified, the newly created page will execute the push animation effect by default.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
