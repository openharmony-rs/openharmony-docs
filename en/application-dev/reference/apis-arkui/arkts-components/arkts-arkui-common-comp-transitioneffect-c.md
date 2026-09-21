# TransitionEffect

```TypeScript
declare class TransitionEffect<
  Type extends keyof TransitionEffects = keyof TransitionEffects,
  Effect extends TransitionEffects[Type] = TransitionEffects[Type]
>
```

Defines the transition effect by using the provided APIs, as listed below.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## animation

```TypeScript
animation(value: AnimateParam): TransitionEffect
```

Animation settings.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [AnimateParam](arkts-arkui-common-comp-animateparam-i.md) | Yes | Animation parameters.<br>The **onFinish** callback in **AnimateParam** does not work here.<br>If **combine** is used for combining transition effects, the animation settings of a transition effect are applicable to the one following it. |

**Return value:**

| Type | Description |
| --- | --- |
| [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md) | Current animation effect. |

## asymmetric

```TypeScript
static asymmetric(
    appear: TransitionEffect,
    disappear: TransitionEffect
  ): TransitionEffect<"asymmetric">
```

Sets the asymmetric transition effect.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appear | [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md) | Yes | Transition effect for appearance.<br>If the **asymmetric** function is not used for **TransitionEffect**, the transition effect takes effect for both appearance and disappearance of the component. |
| disappear | [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md) | Yes | Transition effect for disappearance.<br>If the **asymmetric** function is not used for **TransitionEffect**, the transition effect takes effect for both appearance and disappearance of the component. |

**Return value:**

| Type | Description |
| --- | --- |
| [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md)&lt;"asymmetric"&gt; | Asymmetric transition effect for the current animation. |

## combine

```TypeScript
combine(transitionEffect: TransitionEffect): TransitionEffect
```

Combination of transition effects.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transitionEffect | [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md) | Yes | Combined transition effect. |

**Return value:**

| Type | Description |
| --- | --- |
| [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md) | Combined transition effect. |

## constructor

```TypeScript
constructor(type: Type, effect: Effect)
```

Constructs a **TransitionEffect** object.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [Type](../arkts-apis/arkts-arkui-arkui-statemanagement-type-d.md) | Yes | Transition type. |
| effect | [Effect](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-sceneresources-effect-i.md) | Yes | Transition parameter. |

## move

```TypeScript
static move(edge: TransitionEdge): TransitionEffect<"move">
```

Sets the slide-in and slide-out effects for component transitions from the screen edges.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| edge | [TransitionEdge](arkts-arkui-common-comp-transitionedge-e.md) | Yes | The slide-in and slide-out effects for component transitions from the screen edges. This is essentially a translation effect, specifying the start point of insertion and the end point of deletion. |

**Return value:**

| Type | Description |
| --- | --- |
| [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md)&lt;"move"&gt; | Current animation's slide-in and slide-out effects from the screen edges. |

## opacity

```TypeScript
static opacity(alpha: number): TransitionEffect<"opacity">
```

Sets the opacity for component transition.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| alpha | number | Yes | Opacity of the component during transition, which is the value of the start point of insertion and the end point of deletion.<br>Value range: [0, 1].<br>**NOTE:** <br>If the value specified is less than 0, the value **0** is used. If the value specified is greater than 1, the value **1** is used. |

**Return value:**

| Type | Description |
| --- | --- |
| [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md)&lt;"opacity"&gt; | Opacity of component transition. |

## rotate

```TypeScript
static rotate(options: RotateOptions): TransitionEffect<"rotate">
```

Sets the rotation effect for component transitions.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RotateOptions](arkts-arkui-common-comp-rotateoptions-i.md) | Yes | Rotation effect for component transitions, specifying the start point of insertion and the end point of deletion.<br>- **x**: X-component of the rotation vector.<br>- **y**: Y- component of the rotation vector.<br>- **z**: Z-component of the rotation vector.<br>- **centerX** and **centerY**: rotation center point. The default values are both **"50%"**, indicating the center point of the page.<br>- If the center point is (0, 0), it refers to the upper left corner of the component.<br>- **centerZ**: z-axis anchor point, that is, the z-component of the 3D rotation center point. The default value is **0**.<br>- **perspective**: viewing distance. It is not supported for use in transition animations. |

**Return value:**

| Type | Description |
| --- | --- |
| [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md)&lt;"rotate"&gt; | Rotation effect for the current animation. |

## scale

```TypeScript
static scale(options: ScaleOptions): TransitionEffect<"scale">
```

Sets the scaling effect for component transitions.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ScaleOptions](arkts-arkui-common-comp-scaleoptions-i.md) | Yes | Scaling effect for component transitions, specifying the start point of insertion and the end point of deletion. The scale value set here is multiplied by the component's **scale** attribute. For example, if the component's scale is 0.8 and the transition scale is set to 0.5, the component entry animation starts from a scale of 0.4.<br>- **x**: scale factor along the x-axis.<br>- **y**: scale factor along the y-axis.<br>-z: currently invalid in two-dimensional display.<br>- **centerX** and **centerY**: scale center point. The default values are both **"50%"**, indicating the center point of the page.<br>- If the center point is (0, 0), it refers to the upper left corner of the component.<br>**NOTE:** <br>If **centerX** or **centerY** is set to an invalid string (for example, **"illegalString"**), the default value **"0"** is used. |

**Return value:**

| Type | Description |
| --- | --- |
| [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md)&lt;"scale"&gt; | Scaling effect for component transitions. |

## translate

```TypeScript
static translate(options: TranslateOptions): TransitionEffect<"translate">
```

Sets the translation effect for component transitions.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TranslateOptions](arkts-arkui-common-comp-translateoptions-i.md) | Yes | Translation effect for component transitions, specifying the start point of insertion and the end point of deletion.<br>-**x**: distance to translate along the x-axis.<br>-**y**: distance to translate along the y-axis.<br>-**z**: distance to translate along the z-axis. |

**Return value:**

| Type | Description |
| --- | --- |
| [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md)&lt;"translate"&gt; | Translation effect for the current animation. |

## IDENTITY

```TypeScript
static readonly IDENTITY: TransitionEffect<"identity">
```

Disables the transition effect.

**Type:** [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md)&lt;"identity"&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## OPACITY

```TypeScript
static readonly OPACITY: TransitionEffect<"opacity">
```

Applies a transition effect with the opacity changing from 0 to 1 when the component appears and from 1 to 0 when the component disappears. This is equivalent to **TransitionEffect.opacity(0)**.

**Type:** [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md)&lt;"opacity"&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SLIDE

```TypeScript
static readonly SLIDE: TransitionEffect<
    "asymmetric",
    {
      appear: TransitionEffect<"move", TransitionEdge>;
      disappear: TransitionEffect<"move", TransitionEdge>;
    }
  >
```

Applies a transition effect of sliding in from the start edge when the component appears and sliding out from the end edge when the component disappears. This means sliding in from the left edge and sliding out from the right edge for left-to-right scripts, and sliding in from the right edge and sliding out from the left edge for right-to- left scripts. This is equivalent to **TransitionEffect.asymmetric(TransitionEffect.move(TransitionEdge.START), TransitionEffect.move(TransitionEdge.END))**.

**Type:** [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md)&lt;"asymmetric", {       appear: TransitionEffect&lt;"move", [TransitionEdge](arkts-arkui-common-comp-transitionedge-e.md)&gt;;       disappear: TransitionEffect&lt;"move", TransitionEdge&gt;;     }&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SLIDE_SWITCH

```TypeScript
static readonly SLIDE_SWITCH: TransitionEffect<"slideSwitch">
```

Applies a transition effect of sliding in from the right with first scaling down and then scaling up when the component appears and sliding out from the left with first scaling down and then scaling up when the component disappears. This transition effect comes with its own animation parameters, which can also be overridden. The default animation duration is 600 milliseconds, with a specified animation curve of cubicBezierCurve(0.24, 0.0, 0.50, 1.0) and a minimum scale factor of 0.8.

**Type:** [TransitionEffect](arkts-arkui-common-comp-transitioneffect-c.md)&lt;"slideSwitch"&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
