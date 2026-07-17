# HeatDistortionEffectParam（系统接口）

热浪扭曲效果的参数。

**起始版本：** 26.0.0

<!--Device-uiEffect-interface HeatDistortionEffectParam--><!--Device-uiEffect-interface HeatDistortionEffectParam-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## intensity

```TypeScript
intensity: number
```

热浪扭曲的强度。取值范围[0, 1]，超出边界会在实现时自动截断。0表示无扭曲，1表示最大扭曲程度。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeatDistortionEffectParam-intensity: double--><!--Device-HeatDistortionEffectParam-intensity: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## noiseScale

```TypeScript
noiseScale: number
```

热浪扭曲的噪声缩放，控制噪声纹理的细度。取值范围[0.1, 5.0]，超出边界会在实现时自动截断。值越大，噪声纹理越细腻。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeatDistortionEffectParam-noiseScale: double--><!--Device-HeatDistortionEffectParam-noiseScale: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## progress

```TypeScript
progress: number
```

热浪扭曲的动画进度。取值范围[0, 1]，超出边界会在实现时自动截断。0对应动画开始，1对应动画结束。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeatDistortionEffectParam-progress: double--><!--Device-HeatDistortionEffectParam-progress: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## riseWeight

```TypeScript
riseWeight: number
```

热浪扭曲的上升权重，控制气泡的上升速度。取值范围[0, 1]，超出边界会在实现时自动截断。值越大，向上运动越明显。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeatDistortionEffectParam-riseWeight: double--><!--Device-HeatDistortionEffectParam-riseWeight: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

