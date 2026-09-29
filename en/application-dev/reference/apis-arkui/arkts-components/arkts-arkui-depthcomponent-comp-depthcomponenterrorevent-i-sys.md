# DepthComponentErrorEvent (System API)

```TypeScript
declare interface DepthComponentErrorEvent
```

Provides the event information about the background resource load failure.

**Since:** 26.0.0

<!--Device-unnamed-declare interface DepthComponentErrorEvent--><!--Device-unnamed-declare interface DepthComponentErrorEvent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## componentHeight

```TypeScript
componentHeight: number
```

Height of the component, in vp.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DepthComponentErrorEvent-componentHeight: double--><!--Device-DepthComponentErrorEvent-componentHeight: double-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## componentWidth

```TypeScript
componentWidth: number
```

Width of the component, in vp.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DepthComponentErrorEvent-componentWidth: double--><!--Device-DepthComponentErrorEvent-componentWidth: double-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## error

```TypeScript
error?: BusinessError<void>
```

Error information of the load failure.

**Type:** [BusinessError](arkts-arkui-image-comp-businesserror-t.md)&lt;void&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-DepthComponentErrorEvent-error?: BusinessError<void>--><!--Device-DepthComponentErrorEvent-error?: BusinessError<void>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
