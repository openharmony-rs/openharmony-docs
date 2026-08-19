# AnimatorOptions

定义动画选项。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface AnimatorOptions--><!--Device-unnamed-export interface AnimatorOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { Animator, AnimatorOptions, AnimatorResult, SimpleAnimatorOptions } from '@kit.ArkUI';
```

## begin

```TypeScript
begin: double
```

动画插值起点。 默认值：0

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorOptions-begin: double--><!--Device-AnimatorOptions-begin: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay: int
```

动画延时播放时长，单位毫秒，设置为0时，表示不延时。设置为负数时动画提前播放，如果提前播放的时长大于动画总时长，动画直接过渡到终点。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorOptions-delay: int--><!--Device-AnimatorOptions-delay: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction: "normal" | "reverse" | "alternate" | "alternate-reverse"
```

动画播放模式。

**类型：** "normal" \| "reverse" \| "alternate" \| "alternate-reverse"

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorOptions-direction: "normal" | "reverse" | "alternate" | "alternate-reverse"--><!--Device-AnimatorOptions-direction: "normal" | "reverse" | "alternate" | "alternate-reverse"-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration: int
```

动画播放的时长，单位毫秒。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorOptions-duration: int--><!--Device-AnimatorOptions-duration: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## easing

```TypeScript
easing: string
```

动画插值曲线，非法字符串时取:"ease"。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorOptions-easing: string--><!--Device-AnimatorOptions-easing: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end: double
```

动画插值终点。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorOptions-end: double--><!--Device-AnimatorOptions-end: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fill

```TypeScript
fill: "none" | "forwards" | "backwards" | "both"
```

动画执行后是否恢复到初始状态，动画执行后，动画结束时的状态（在最后一个关键帧中定义）将保留。

**类型：** "none" \| "forwards" \| "backwards" \| "both"

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorOptions-fill: "none" | "forwards" | "backwards" | "both"--><!--Device-AnimatorOptions-fill: "none" | "forwards" | "backwards" | "both"-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iterations

```TypeScript
iterations: int
```

动画播放次数。设置为0时不播放，设置为-1时无限次播放，设置大于0时为播放次数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AnimatorOptions-iterations: int--><!--Device-AnimatorOptions-iterations: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

