# FocusPriority

Sets the focus priority of a component.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AUTO

```TypeScript
AUTO = 0
```

Default priority, that is, the focus priority assigned by default.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PRIOR

```TypeScript
PRIOR = 2000
```

Priority that indicates the component is prioritized in the container. This level is higher than **AUTO**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PREVIOUS

```TypeScript
PREVIOUS = 3000
```

Priority of a previously focused node in the container. This level is higher than **PRIOR**.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
