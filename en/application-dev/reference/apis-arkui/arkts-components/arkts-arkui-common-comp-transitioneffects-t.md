# TransitionEffects

```TypeScript
declare type TransitionEffects = {
  identity: undefined;
  opacity: number;
  slideSwitch: undefined;
  move: TransitionEdge;
  translate: TranslateOptions;
  rotate: RotateOptions;
  scale: ScaleOptions;
  asymmetric: {
    appear: TransitionEffect;
    disappear: TransitionEffect;
  };
}
```

Defines all transition effects.

**Type:** {
  identity: undefined;
  opacity: number;
  slideSwitch: undefined;
  move: TransitionEdge;
  translate: TranslateOptions;
  rotate: RotateOptions;
  scale: ScaleOptions;
  asymmetric: {
    appear: TransitionEffect;
    disappear: TransitionEffect;
  };
}

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-unnamed-declare type TransitionEffects = {  identity: undefined;  opacity: number;  slideSwitch: undefined;  move: TransitionEdge;  translate: TranslateOptions;  rotate: RotateOptions;  scale: ScaleOptions;  asymmetric: {    appear: TransitionEffect;    disappear: TransitionEffect;  };}--><!--Device-unnamed-declare type TransitionEffects = {  identity: undefined;  opacity: number;  slideSwitch: undefined;  move: TransitionEdge;  translate: TranslateOptions;  rotate: RotateOptions;  scale: ScaleOptions;  asymmetric: {    appear: TransitionEffect;    disappear: TransitionEffect;  };}-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
