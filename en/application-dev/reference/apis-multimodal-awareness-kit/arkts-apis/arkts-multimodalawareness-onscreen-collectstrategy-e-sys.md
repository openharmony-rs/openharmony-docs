# CollectStrategy (System API)

```TypeScript
export enum CollectStrategy
```

Defines a page information collection policy.

**Since:** 23

<!--Device-onScreen-export enum CollectStrategy--><!--Device-onScreen-export enum CollectStrategy-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## ALLOW

```TypeScript
ALLOW = 1 << 0
```

Collection is supported.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-CollectStrategy-ALLOW = 1 << 0--><!--Device-CollectStrategy-ALLOW = 1 << 0-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## ALLOW_USER_CHANGE

```TypeScript
ALLOW_USER_CHANGE = 1 << 5
```

Collection policies can be configured.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-CollectStrategy-ALLOW_USER_CHANGE = 1 << 5--><!--Device-CollectStrategy-ALLOW_USER_CHANGE = 1 << 5-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## ANCO_APP

```TypeScript
ANCO_APP = 1 << 4
```

VM application, which is a non-HarmonyOS application.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-CollectStrategy-ANCO_APP = 1 << 4--><!--Device-CollectStrategy-ANCO_APP = 1 << 4-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## BUSINESS_APP

```TypeScript
BUSINESS_APP = 1 << 6
```

Application data can be collected.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-CollectStrategy-BUSINESS_APP = 1 << 6--><!--Device-CollectStrategy-BUSINESS_APP = 1 << 6-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## FLOAT_SCREEN

```TypeScript
FLOAT_SCREEN = 1 << 7
```

Floating window.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-CollectStrategy-FLOAT_SCREEN = 1 << 7--><!--Device-CollectStrategy-FLOAT_SCREEN = 1 << 7-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## LAUNCHER

```TypeScript
LAUNCHER = 1 << 9
```

Desktop application.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-CollectStrategy-LAUNCHER = 1 << 9--><!--Device-CollectStrategy-LAUNCHER = 1 << 9-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## PIP_SCREEN

```TypeScript
PIP_SCREEN = 1 << 8
```

Picture-in-picture mode.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-CollectStrategy-PIP_SCREEN = 1 << 8--><!--Device-CollectStrategy-PIP_SCREEN = 1 << 8-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## PRIVATE_WINDOW

```TypeScript
PRIVATE_WINDOW = 1 << 3
```

Privacy window of the application.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-CollectStrategy-PRIVATE_WINDOW = 1 << 3--><!--Device-CollectStrategy-PRIVATE_WINDOW = 1 << 3-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## SPLIT_SCREEN

```TypeScript
SPLIT_SCREEN = 1 << 1
```

Collection policy of the split-screen window on the application.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-CollectStrategy-SPLIT_SCREEN = 1 << 1--><!--Device-CollectStrategy-SPLIT_SCREEN = 1 << 1-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.

## UNSUPPORTED_APP

```TypeScript
UNSUPPORTED_APP = 1 << 2
```

Automatic collection is not supported.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-CollectStrategy-UNSUPPORTED_APP = 1 << 2--><!--Device-CollectStrategy-UNSUPPORTED_APP = 1 << 2-End-->

**System capability:** SystemCapability.MultimodalAwareness.OnScreenAwareness

**System API:** This is a system API.
