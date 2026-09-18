# GestureMode

Defines the recognition mode of a gesture group.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Sequence

```TypeScript
Sequence
```

Sequential recognition. Gestures are recognized in the registration sequence until all gestures are recognized successfully. If any gesture in the sequence fails recognition, subsequent gestures will not be recognized.

Only the last gesture in a sequentially recognized gesture group can trigger **onActionEnd**.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Parallel

```TypeScript
Parallel
```

Parallel recognition. Registered gestures are recognized concurrently until all gestures are recognized. The recognition result of each gesture does not affect each other.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Exclusive

```TypeScript
Exclusive
```

Exclusive recognition. All registered gestures are processed simultaneously. Once any gesture is recognized successfully, the recognition process ends, and all other gestures are deemed unrecognized.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
