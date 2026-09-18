# LazyForEachCustomComponentFreezeMode

Enumerates the freeze modes for cached custom nodes that have been removed from the component tree in LazyForEach.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AUTO

```TypeScript
AUTO = 0
```

Follow the enableCustomComponentFreeze field in Metadata to determine whether freezing takes effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DISABLED

```TypeScript
DISABLED = 1
```

Freezing is disabled for cached custom nodes removed from the component tree.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ENABLED

```TypeScript
ENABLED = 2
```

Freezing is enabled for cached custom nodes removed from the component tree. State updates of cached custom components will be frozen.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
