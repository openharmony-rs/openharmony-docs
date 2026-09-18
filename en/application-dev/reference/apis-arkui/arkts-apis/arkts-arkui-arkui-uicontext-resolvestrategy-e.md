# ResolveStrategy

Enumerates resolution strategies for **UIContext** objects.

**Since:** 22

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CALLING_SCOPE

```TypeScript
CALLING_SCOPE = 0
```

Obtain the UIContext of the current calling scope.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## LAST_FOCUS

```TypeScript
LAST_FOCUS = 1
```

Obtain the UIContext of the instance that most recently switched to the focused state.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MAX_INSTANCE_ID

```TypeScript
MAX_INSTANCE_ID = 2
```

Obtain the UIContext of the instance with the largest instance ID.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## UNIQUE

```TypeScript
UNIQUE = 3
```

Obtain the UIContext of the unique UI instance (when only one UI instance exists).

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## LAST_FOREGROUND

```TypeScript
LAST_FOREGROUND = 4
```

Obtain the UIContext of the instance that most recently switched to the foreground.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## UNDEFINED

```TypeScript
UNDEFINED = 5
```

Obtain a UIContext with an ambiguous calling scope.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
