# BrightnessParam（系统接口）

材质提亮参数的详细说明。

**起始版本：** 22

<!--Device-uiEffect-interface BrightnessParam--><!--Device-uiEffect-interface BrightnessParam-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## cubicCoeff

```TypeScript
cubicCoeff : number
```

灰度调整三阶系数。取值范围[-1, 1]，小于-1时取值为-1，大于1时取值为1，值越大，灰度调整效果越强。

**类型：** number

**起始版本：** 22

<!--Device-BrightnessParam-cubicCoeff : double--><!--Device-BrightnessParam-cubicCoeff : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## fraction

```TypeScript
fraction : number
```

提亮效果混合比例。取值范围[0, 1]，小于0时取值为0，大于1时取值为1，值越大，提亮效果越弱。

**类型：** number

**起始版本：** 22

<!--Device-BrightnessParam-fraction : double--><!--Device-BrightnessParam-fraction : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## lightUpDegree

```TypeScript
lightUpDegree : number
```

灰度调整比例。取值范围[-1, 1]，小于-1时取值为-1，大于1时取值为1，值越大，灰度调整效果越强。

**类型：** number

**起始版本：** 22

<!--Device-BrightnessParam-lightUpDegree : double--><!--Device-BrightnessParam-lightUpDegree : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## negRgb

```TypeScript
negRgb : [number, number, number]
```

基于基准饱和度的负向调整系数。取值范围[-1, 1]，小于-1时取值为-1，大于1时取值为1，值越大饱和度越低。

**类型：** [number, number, number]

**起始版本：** 22

<!--Device-BrightnessParam-negRgb : [double, double, double]--><!--Device-BrightnessParam-negRgb : [double, double, double]-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## posRgb

```TypeScript
posRgb : [number, number, number]
```

基于基准饱和度的正向调整系数。取值范围[-1, 1]，小于-1时取值为-1，大于1时取值为1，值越大饱和度越高。

**类型：** [number, number, number]

**起始版本：** 22

<!--Device-BrightnessParam-posRgb : [double, double, double]--><!--Device-BrightnessParam-posRgb : [double, double, double]-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## quadCoeff

```TypeScript
quadCoeff : number
```

灰度调整二阶系数。取值范围[-1, 1]，小于-1时取值为-1，大于1时取值为1，值越大，灰度调整效果越强。

**类型：** number

**起始版本：** 22

<!--Device-BrightnessParam-quadCoeff : double--><!--Device-BrightnessParam-quadCoeff : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## rate

```TypeScript
rate : number
```

灰度调整线性系数。取值范围[-1, 1]，小于-1时取值为-1，大于1时取值为1，值越大，灰度调整效果越强。

**类型：** number

**起始版本：** 22

<!--Device-BrightnessParam-rate : double--><!--Device-BrightnessParam-rate : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## saturation

```TypeScript
saturation : number
```

提亮基准饱和度。取值范围[0, 1]，小于0时取值为0，大于1时取值为1，值越大基准饱和度越高。

**类型：** number

**起始版本：** 22

<!--Device-BrightnessParam-saturation : double--><!--Device-BrightnessParam-saturation : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

