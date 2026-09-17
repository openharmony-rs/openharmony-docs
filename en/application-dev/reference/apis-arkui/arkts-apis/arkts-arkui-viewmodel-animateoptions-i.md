# AnimateOptions

AnimateOptions

@interface AnimateOptions

**Since:** 4

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay: number
```

Delay for the animation start. The default value indicates no delay. The default value is 0.

**Type:** number

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction: "normal" | "reverse" | "alternate" | "alternate-reverse"
```

The animation playback mode. The default value is "normal".

**Type:** "normal" &#124; "reverse" &#124; "alternate" &#124; "alternate-reverse"

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration: number
```

Duration of the animation, in milliseconds. The default value is 0.

**Type:** number

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## easing

```TypeScript
easing: string
```

Time curve of the animation. For details about the supported types. linear The animation speed keeps unchanged. ease The animation starts and ends at a low speed, cubic-bezier(0.25, 0.1, 0.25, 1.0). ease-in The animation starts at a low speed, cubic-bezier(0.42, 0.0, 1.0, 1.0). ease-out The animation ends at a low speed, cubic-bezier(0.0, 0.0, 0.58, 1.0). ease-in-out The animation starts and ends at a low speed, cubic-bezier(0.42, 0.0, 0.58, 1.0). fast-out-slow-in Standard curve, cubic-bezier(0.4, 0.0, 0.2, 1.0). linear-out-slow-in Deceleration curve, cubic-bezier(0.0, 0.0, 0.2, 1.0). fast-out-linear-in Acceleration curve, cubic-bezier(0.4, 0.0, 1.0, 1.0). friction Damping curve, cubic-bezier(0.2, 0.0, 0.2, 1.0). extreme-deceleration Extreme deceleration curve, cubic-bezier(0.0, 0.0, 0.0, 1.0). sharp Sharp curve, cubic-bezier(0.33, 0.0, 0.67, 1.0). rhythm Rhythm curve, cubic-bezier(0.7, 0.0, 0.2, 1.0). smooth Smooth curve, cubic-bezier(0.4, 0.0, 0.4, 1.0). cubic-bezier(x1, y1, x2, y2) You can customize an animation speed curve in the cubic-bezier() function. The x and y values of each input parameter must be between 0 and 1. Step curve. The number must be set and only an integer is supported, step-position is optional. It can be set to start or end. The default value is end. The default value is ease.

**Type:** string

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fill

```TypeScript
fill: "none" | "forwards" | "backwards" | "both"
```

Whether to resume to the initial state after the animation is executed. none: The initial state is restored after the animation is executed. forwards: The state at the end of the animation (defined in the last key frame) is retained after the animation is executed.

**Type:** "none" &#124; "forwards" &#124; "backwards" &#124; "both"

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## iterations

```TypeScript
iterations: number | string
```

Number of times the animation will be played. number indicates a fixed number of playback operations, and Infinity indicates an unlimited number of playback operations. The default value is 1.

**Type:** number &#124; string

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
