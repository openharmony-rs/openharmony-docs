# LiquidMaterialEffectParam（系统接口）

材质的各项参数及其用途的详细说明。

**起始版本：** 22

<!--Device-uiEffect-interface LiquidMaterialEffectParam--><!--Device-uiEffect-interface LiquidMaterialEffectParam-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## distortFactor

```TypeScript
distortFactor : number
```

扰动效果系数。值大于等于0，值小于0时表示无扰动效果。

**类型：** number

**起始版本：** 22

<!--Device-LiquidMaterialEffectParam-distortFactor : double--><!--Device-LiquidMaterialEffectParam-distortFactor : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## distortProgress

```TypeScript
distortProgress : number
```

扰动效果进度。取值范围[0, 1]，小于0时取值为0，大于1时取值为1。0表示开始扰动，1表示结束扰动。

**类型：** number

**起始版本：** 22

<!--Device-LiquidMaterialEffectParam-distortProgress : double--><!--Device-LiquidMaterialEffectParam-distortProgress : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## enable

```TypeScript
enable : boolean
```

是否开启材质效果。 true表示开启材质效果，false表示关闭材质效果。

**类型：** boolean

**起始版本：** 22

<!--Device-LiquidMaterialEffectParam-enable : boolean--><!--Device-LiquidMaterialEffectParam-enable : boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## materialFactor

```TypeScript
materialFactor : number
```

材质系数。取值范围[0, 1]，小于0时取值为0，大于1时取值为1。值为0表示无材质效果，使用叠加颜色填充，值越大材质效果越明显。

**类型：** number

**起始版本：** 22

<!--Device-LiquidMaterialEffectParam-materialFactor : double--><!--Device-LiquidMaterialEffectParam-materialFactor : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## reflectionFactor

```TypeScript
reflectionFactor : number
```

反射系数。取值范围[0, 10]，小于0时取值为0，大于10时取值为10。值为0表示无反射效果，值越大反射强度越高。

**类型：** number

**起始版本：** 22

<!--Device-LiquidMaterialEffectParam-reflectionFactor : double--><!--Device-LiquidMaterialEffectParam-reflectionFactor : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## refractionFactor

```TypeScript
refractionFactor : number
```

折射效果系数。取值范围[0, 10]，小于0时取值为0，大于10时取值为10。值为0表示无折射效果，值越大折射强度越高。

**类型：** number

**起始版本：** 22

<!--Device-LiquidMaterialEffectParam-refractionFactor : double--><!--Device-LiquidMaterialEffectParam-refractionFactor : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## ripplePosition

```TypeScript
ripplePosition?: Array<[number, number]>
```

水波效果作用的位置。数组中每个位置包含x和y两个维度，最多支持10个位置坐标传入。传入超出10个位置坐标则整体无效。

**类型：** Array<[number, number]>

**起始版本：** 22

<!--Device-LiquidMaterialEffectParam-ripplePosition?: Array<[double, double]>--><!--Device-LiquidMaterialEffectParam-ripplePosition?: Array<[double, double]>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## rippleProgress

```TypeScript
rippleProgress : number
```

水波效果进度。值大于等于0，值小于0时表示无水波效果。

**类型：** number

**起始版本：** 22

<!--Device-LiquidMaterialEffectParam-rippleProgress : double--><!--Device-LiquidMaterialEffectParam-rippleProgress : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## tintColor

```TypeScript
tintColor : [number, number, number, number]
```

材质叠加的颜色，四个变量分别对应RGBA。取值范围[0, 1]，小于0时取值为0，大于1时取值为1。

**类型：** [number, number, number, number]

**起始版本：** 22

<!--Device-LiquidMaterialEffectParam-tintColor : [double, double, double, double]--><!--Device-LiquidMaterialEffectParam-tintColor : [double, double, double, double]-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

