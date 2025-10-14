# UI组件适配（动效与视效）

以下接口在ArkTS-Dyn中已废弃，在ArkTS-Sta中需使用替代接口来实现能力。

## 动效类接口

### create
ArkTS-Dyn接口声明：[static create(options: AnimatorOptions): AnimatorResult](../reference/apis-arkui/js-apis-animator.md#createdeprecated)

替代的ArkTS-Sta接口声明：[createAnimator(options: AnimatorOptions): AnimatorResult](../reference/apis-arkui/js-apis-arkui-UIContext.md#createanimator)



ArkTS-Dyn示例：

```ts
Animator.create({duration: 1500, easing: "friction", delay: 0, fill: "forwards", direction: "normal", iterations: 3, begin: 200.0, end: 400.0})
```

ArkTS-Sta示例：

```ts
this.getUIContext().createAnimator({duration: 1500, easing: "friction", delay: 0, fill: "forwards", direction: "normal", iterations: 3, begin: 200.0, end: 400.0})
```


### createAnimator
ArkTS-Dyn接口声明：[static createAnimator(options: AnimatorOptions): AnimatorResult](../reference/apis-arkui/js-apis-animator.md#createanimatordeprecated)

替代的ArkTS-Sta接口声明：[createAnimator(options: AnimatorOptions): AnimatorResult](../reference/apis-arkui/js-apis-arkui-UIContext.md#createanimator)



ArkTS-Dyn示例：

```ts
Animator.createAnimator({duration: 1500, easing: "friction", delay: 0, fill: "forwards", direction: "normal", iterations: 3, begin: 200.0, end: 400.0})
```

ArkTS-Sta示例：

```ts
this.getUIContext().createAnimator({duration: 1500, easing: "friction", delay: 0, fill: "forwards", direction: "normal", iterations: 3, begin: 200.0, end: 400.0})
```


### animateTo
ArkTS-Dyn接口声明：[animateTo(value: AnimateParam, event: () => void): void](../reference/apis-arkui/arkui-ts/ts-explicit-animation.md#animatetodeprecated)

替代的ArkTS-Sta接口声明：[animateTo(value: AnimateParam, event: () => void): void](../reference/apis-arkui/js-apis-arkui-UIContext.md#animateto)



ArkTS-Dyn示例：

```ts
animateTo({ duration: 0 }, ()=>{})
```

ArkTS-Sta示例：

```ts
this.getUIContext().animateTo({ duration: 0 }, ()=>{})
```

### update
ArkTS-Dyn接口声明：[update(options: AnimatorOptions): void](../reference/apis-arkui/js-apis-animator.md#updatedeprecated)

替代的ArkTS-Sta接口声明：[reset(options: AnimatorOptions): void](../reference/apis-arkui/js-apis-animator.md#reset9)



ArkTS-Dyn示例：

```ts
let animatorResult: AnimatorResult = Animator.createAnimator({duration: 1500, easing: "friction", delay: 0, fill: "forwards", direction: "normal", iterations: 3, begin: 200.0, end: 400.0})
animatorResult.update({duration: 500, easing: "friction", delay: 1, fill: "forwards", direction: "normal", iterations: 3, begin: 200.0, end: 400.0})
```

ArkTS-Sta示例：

```ts
let animatorResult: AnimatorResult = this.getUIContext().createAnimator({duration: 1500, easing: "friction", delay: 0, fill: "forwards", direction: "normal", iterations: 3, begin: 200.0, end: 400.0})
animatorResult.reset({duration: 500, easing: "friction", delay: 1, fill: "forwards", direction: "normal", iterations: 3, begin: 200.0, end: 400.0})
```


### onrepeat
ArkTS-Dyn接口声明：[onrepeat: () => void](../reference/apis-arkui/js-apis-animator.md#onrepeatdeprecated)

替代的ArkTS-Sta接口声明：[onRepeat: () => void](../reference/apis-arkui/js-apis-animator.md#onrepeat12)



ArkTS-Dyn示例：

```ts
let animatorResult: AnimatorResult = Animator.createAnimator({duration: 1500, easing: "friction", delay: 0, fill: "forwards", direction: "normal", iterations: 3, begin: 200.0, end: 400.0})
animatorResult.onrepeat = ()=>{
    console.log("onrepeat");
}
```

ArkTS-Sta示例：

```ts
let animatorResult: AnimatorResult = this.getUIContext().createAnimator({duration: 1500, easing: "friction", delay: 0, fill: "forwards", direction: "normal", iterations: 3, begin: 200.0, end: 400.0})
animatorResult.onRepeat = ()=>{
    console.log("onRepeat");
}
```


### oncancel
ArkTS-Dyn接口声明：[oncancel: () => void](../reference/apis-arkui/js-apis-animator.md#oncanceldeprecated)

替代的ArkTS-Sta接口声明：[onCancel: () => void](../reference/apis-arkui/js-apis-animator.md#oncancel12)



ArkTS-Dyn示例：

```ts
let animatorResult: AnimatorResult = Animator.createAnimator({duration: 1500, easing: "friction", delay: 0, fill: "forwards", direction: "normal", iterations: 3, begin: 200.0, end: 400.0})
animatorResult.oncancel = ()=>{
    console.log("oncancel");
}
```

ArkTS-Sta示例：

```ts
let animatorResult: AnimatorResult = this.getUIContext().createAnimator({duration: 1500, easing: "friction", delay: 0, fill: "forwards", direction: "normal", iterations: 3, begin: 200.0, end: 400.0})
animatorResult.onCancel = ()=>{
    console.log("onCancel");
}
```


### onfinish
ArkTS-Dyn接口声明：[onfinish: () => void](../reference/apis-arkui/js-apis-animator.md#onfinishdeprecated)

替代的ArkTS-Sta接口声明：[onFinish: () => void](../reference/apis-arkui/js-apis-animator.md#onfinish12)



ArkTS-Dyn示例：

```ts
let animatorResult: AnimatorResult = Animator.createAnimator({duration: 1500, easing: "friction", delay: 0, fill: "forwards", direction: "normal", iterations: 3, begin: 200.0, end: 400.0})
animatorResult.onfinish = ()=>{
    console.log("onfinish");
}
```

ArkTS-Sta示例：

```ts
let animatorResult: AnimatorResult = this.getUIContext().createAnimator({duration: 1500, easing: "friction", delay: 0, fill: "forwards", direction: "normal", iterations: 3, begin: 200.0, end: 400.0})
animatorResult.onFinish = ()=>{
    console.log("onFinish");
}
```


### onframe
ArkTS-Dyn接口声明：[onframe: (progress: number) => void](../reference/apis-arkui/js-apis-animator.md#onframedeprecated)

替代的ArkTS-Sta接口声明：[onFrame: (progress: number) => void](../reference/apis-arkui/js-apis-animator.md#onframe12)



ArkTS-Dyn示例：

```ts
let animatorResult: AnimatorResult = Animator.createAnimator({duration: 1500, easing: "friction", delay: 0, fill: "forwards", direction: "normal", iterations: 3, begin: 200.0, end: 400.0})
animatorResult.onframe = (progress: number)=>{
    console.log("onframe");
}
```

ArkTS-Sta示例：

```ts
let animatorResult: AnimatorResult = this.getUIContext().createAnimator({duration: 1500, easing: "friction", delay: 0, fill: "forwards", direction: "normal", iterations: 3, begin: 200.0, end: 400.0})
animatorResult.onFrame = (progress: number)=>{
    console.log("onFrame");
}
```

### cubicBezier
ArkTS-Dyn接口声明：[cubicBezier(x1: number, y1: number, x2: number, y2: number): string](../reference/apis-arkui/js-apis-curve.md#curvescubicbezierdeprecated)

替代的ArkTS-Sta接口声明：[cubicBezierCurve(x1: number, y1: number, x2: number, y2: number): ICurve](../reference/apis-arkui/js-apis-curve.md#curvescubicbeziercurve9)



ArkTS-Dyn示例：

```ts
let a: string = curves.cubicBezier(0.42, 0.0, 0.58, 1.0)
```

ArkTS-Sta示例：

```ts
let a: ICurve = curves.cubicBezierCurve(0.42, 0.0, 0.58, 1.0)
```


### steps
ArkTS-Dyn接口声明：[steps(count: number, end: boolean): string](../reference/apis-arkui/js-apis-curve.md#curvesstepsdeprecated)

替代的ArkTS-Sta接口声明：[stepsCurve(count: number, end: boolean): ICurve](../reference/apis-arkui/js-apis-curve.md#curvesstepscurve9)



ArkTS-Dyn示例：

```ts
let a: string = curves.steps(1, false)
```

ArkTS-Sta示例：

```ts
let a: ICurve = curves.stepsCurve(1, false)
```


### spring
ArkTS-Dyn接口声明：[spring(velocity: number, mass: number, stiffness: number, damping: number): string](../reference/apis-arkui/js-apis-curve.md#curvesspringdeprecated)

替代的ArkTS-Sta接口声明：[springCurve(velocity: number, mass: number, stiffness: number, damping: number): ICurve](../reference/apis-arkui/js-apis-curve.md#curvesspringcurve9)



ArkTS-Dyn示例：

```ts
let a: string = curves.spring(1, 1, 1, 1)
```

ArkTS-Sta示例：

```ts
let a: ICurve = curves.springCurve(1, 1, 1, 1)
```


### init
ArkTS-Dyn接口声明：[init(curve?: Curve): string](../reference/apis-arkui/js-apis-curve.md#curvesinitdeprecated)

替代的ArkTS-Sta接口声明： [initCurve(curve?: Curve): ICurve](../reference/apis-arkui/js-apis-curve.md#curvesinitcurve9)



ArkTS-Dyn示例：

```ts
let a: string = curves.init(Curve.EaseIn)
```

ArkTS-Sta示例：

```ts
let a: ICurve = curves.initCurve(Curve.EaseIn)
```

### TransitionOptions
ArkTS-Dyn接口声明：[interface TransitionOptions](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md#transitionoptionsdeprecated)

替代的ArkTS-Sta接口声明：[class TransitionEffect<Type extends keyof TransitionEffects = keyof TransitionEffects, Effect extends TransitionEffects[Type] = TransitionEffects[Type]>](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md#transitioneffect10对象说明)



ArkTS-Dyn示例：

```ts
transition({opacity: 0})
```

ArkTS-Sta示例：

```ts
transition(TransitionEffect.opacity(0))
```


### opacity
ArkTS-Dyn接口声明：[opacity?: number](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md#transitionoptionsdeprecated)

替代的ArkTS-Sta接口声明：[static opacity(alpha: number): TransitionEffect<"opacity">](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md#transitioneffect10对象说明)



ArkTS-Dyn示例：

```ts
transition({opacity: 0})
```

ArkTS-Sta示例：

```ts
transition(TransitionEffect.opacity(0))
```


### rotate
ArkTS-Dyn接口声明：[rotate?: RotateOptions](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md#transitionoptionsdeprecated)

替代的ArkTS-Sta接口声明：[static rotate(options: RotateOptions): TransitionEffect<"rotate">](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md#transitioneffect10对象说明)



ArkTS-Dyn示例：

```ts
transition({rotate: {x: 1, y: 1} as RotateOptions})
```

ArkTS-Sta示例：

```ts
transition(TransitionEffect.rotate({x: 1, y: 1} as RotateOptions))
```


### scale
ArkTS-Dyn接口声明：[scale?: ScaleOptions](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md#transitionoptionsdeprecated)

替代的ArkTS-Sta接口声明：[static scale(options: ScaleOptions): TransitionEffect<"scale">](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md#transitioneffect10对象说明)



ArkTS-Dyn示例：

```ts
transition({scale: {x: 1, y: 1} as ScaleOptions})
```

ArkTS-Sta示例：

```ts
transition(TransitionEffect.scale({x: 1, y: 1} as ScaleOptions))
```


### translate
ArkTS-Dyn接口声明：[translate?: TranslateOptions](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md#transitionoptionsdeprecated)

替代的ArkTS-Sta接口声明：[static translate(options: TranslateOptions): TransitionEffect<"translate">](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md#transitioneffect10对象说明)



ArkTS-Dyn示例：

```ts
transition({translate: {x: 1, y: 1} as TranslateOptions})
```

ArkTS-Sta示例：

```ts
transition(TransitionEffect.translate({x: 1, y: 1} as TranslateOptions))
```


### type
ArkTS-Dyn接口声明：[type?: TransitionType](../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#transitiontype)

替代的ArkTS-Sta接口声明：[static asymmetric(appear: TransitionEffect, disappear: TransitionEffect): TransitionEffect<"asymmetric">](../reference/apis-arkui/arkui-ts/ts-transition-animation-component.md#transitioneffect10对象说明)



ArkTS-Dyn示例：

```ts
transition({type: TransitionType.Insert, opacity: 0})
```

ArkTS-Sta示例：

```ts
transition(TransitionEffect.asymmetric(TransitionEffect.opacity(0), TransitionEffect.IDENTITY))
```

## 视效类接口

### clip
ArkTS-Dyn接口声明：[clip(value: boolean | CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute): T](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sharp-clipping.md#clipdeprecated)

替代的ArkTS-Sta接口声明：[clipShape(value: CircleShape | EllipseShape | PathShape | RectShape): T](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sharp-clipping.md#clipshape12)



ArkTS-Dyn示例：

```ts
Text().clip(new Rect({width: 100, height: 100}))
```

ArkTS-Sta示例：

```ts
Text().clipShape(new Rect({width: 100, height: 100}))
```


### mask
ArkTS-Dyn接口声明：[mask(value: CircleAttribute | EllipseAttribute | PathAttribute | RectAttribute | ProgressMask): T](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sharp-clipping.md#maskdeprecated)

替代的ArkTS-Sta接口声明：[maskShape(value: CircleShape | EllipseShape | PathShape | RectShape): T](../reference/apis-arkui/arkui-ts/ts-universal-attributes-sharp-clipping.md#maskshape12)



ArkTS-Dyn示例：

```ts
Text().mask(new Rect({width: 100, height: 100}))
```

ArkTS-Sta示例：

```ts
Text().maskShape(new Rect({width: 100, height: 100}))
```


### matrix4

### invert

ArkTS-Dyn接口声明：[invert(): Matrix4Transit](../reference/apis-arkui/js-apis-matrix4.md#matrix4invertdeprecated)

替代的ArkTS-Sta接口声明：[invert(): Matrix4Transit](../reference/apis-arkui/js-apis-matrix4.md#invert)



ArkTS-Dyn示例：

```ts
let m = matrix4.invert()
```

ArkTS-Sta示例：

```ts
let m = matrix4.identity().invert()
```


### scale

ArkTS-Dyn接口声明：[scale(options: ScaleOption): Matrix4Transit](../reference/apis-arkui/js-apis-matrix4.md#matrix4scaledeprecated)

替代的ArkTS-Sta接口声明：[scale(options: ScaleOption): Matrix4Transit](../reference/apis-arkui/js-apis-matrix4.md#scale)



ArkTS-Dyn示例：

```ts
let m = matrix4.scale({x: 1, y: 1})
```

ArkTS-Sta示例：

```ts
let m = matrix4.identity().scale({x: 1, y: 1})
```


### rotate

ArkTS-Dyn接口声明：[rotate(options: RotateOption): Matrix4Transit](../reference/apis-arkui/js-apis-matrix4.md#matrix4rotatedeprecated)

替代的ArkTS-Sta接口声明：[rotate(options: RotateOption): Matrix4Transit](../reference/apis-arkui/js-apis-matrix4.md#scale)



ArkTS-Dyn示例：

```ts
let m = matrix4.rotate({x: 1, y: 1})
```

ArkTS-Sta示例：

```ts
let m = matrix4.identity().rotate({x: 1, y: 1})
```


### translate

ArkTS-Dyn接口声明：[translate(options: TranslateOption): Matrix4Transit](../reference/apis-arkui/js-apis-matrix4.md#matrix4translatedeprecated)

替代的ArkTS-Sta接口声明：[translate(options: TranslateOption): Matrix4Transit](../reference/apis-arkui/js-apis-matrix4.md#translate)



ArkTS-Dyn示例：

```ts
let m = matrix4.translate({x: 1, y: 1})
```

ArkTS-Sta示例：

```ts
let m = matrix4.identity().translate({x: 1, y: 1})
```


### transformPoint

ArkTS-Dyn接口声明：[transformPoint(options: [number, number]): [number, number]](../reference/apis-arkui/js-apis-matrix4.md#matrix4transformpointdeprecated)

替代的ArkTS-Sta接口声明：[transformPoint(options: [number, number]): [number, number]](../reference/apis-arkui/js-apis-matrix4.md#transformpoint)



ArkTS-Dyn示例：

```ts
let m = matrix4.transformPoint([1, 1])
```

ArkTS-Sta示例：

```ts
let m = matrix4.identity().transformPoint([1, 1])
```


### combine

ArkTS-Dyn接口声明：[combine(options: Matrix4Transit): Matrix4Transit](../reference/apis-arkui/js-apis-matrix4.md#matrix4combinedeprecated)

替代的ArkTS-Sta接口声明：[combine(options: Matrix4Transit): Matrix4Transit](../reference/apis-arkui/js-apis-matrix4.md#combine)



ArkTS-Dyn示例：

```ts
let m = matrix4.combine(matrix4.scale({x: 1, y: 1}))
```

ArkTS-Sta示例：

```ts
let m = matrix4.identity().combine(matrix4.identity().scale({x: 1, y: 1}))
```


### copy
ArkTS-Dyn接口声明：[copy(): Matrix4Transit](../reference/apis-arkui/js-apis-matrix4.md#matrix4copydeprecated)

替代的ArkTS-Sta接口声明：[copy(): Matrix4Transit](../reference/apis-arkui/js-apis-matrix4.md#copy)



ArkTS-Dyn示例：

```ts
let m = matrix4.copy()
```

ArkTS-Sta示例：

```ts
let m = matrix4.identity().copy()
```