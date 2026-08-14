# LiquidMaterialEffectParam（系统接口）

材质效果参数，用于控制材质的折射、反射、扰动和叠加颜色等显示属性。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-uiEffect-interface LiquidMaterialEffectParam--><!--Device-uiEffect-interface LiquidMaterialEffectParam-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## distortFactor

```TypeScript
distortFactor : double
```

扰动效果系数。值大于等于0，值小于0时表示无扰动效果。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-LiquidMaterialEffectParam-distortFactor : double--><!--Device-LiquidMaterialEffectParam-distortFactor : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## distortProgress

```TypeScript
distortProgress : double
```

扰动效果进度。取值范围为[0, 1]，小于0时取值为0，大于1时取值为1。0表示开始扰动，1表示结束扰动。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-LiquidMaterialEffectParam-distortProgress : double--><!--Device-LiquidMaterialEffectParam-distortProgress : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## enable

```TypeScript
enable : boolean
```

是否开启材质效果。true表示开启，false表示关闭。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-LiquidMaterialEffectParam-enable : boolean--><!--Device-LiquidMaterialEffectParam-enable : boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## materialFactor

```TypeScript
materialFactor : double
```

材质系数。取值范围为[0, 1]，小于0时取值为0，大于1时取值为1。值为0表示无材质效果，使用叠加颜色填充，值越大材质效果越明显。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-LiquidMaterialEffectParam-materialFactor : double--><!--Device-LiquidMaterialEffectParam-materialFactor : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## reflectionFactor

```TypeScript
reflectionFactor : double
```

反射系数。取值范围为[0, 10]，小于0时取值为0，大于10时取值为10。值为0表示无反射效果，值越大反射强度越高。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-LiquidMaterialEffectParam-reflectionFactor : double--><!--Device-LiquidMaterialEffectParam-reflectionFactor : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## refractionFactor

```TypeScript
refractionFactor : double
```

折射效果系数。取值范围为[0, 10]，小于0时取值为0，大于10时取值为10。值为0表示无折射效果，值越大折射强度越高。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-LiquidMaterialEffectParam-refractionFactor : double--><!--Device-LiquidMaterialEffectParam-refractionFactor : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## ripplePosition

```TypeScript
ripplePosition?: Array<[double, double]>
```

水波效果作用的位置。当需要在多个指定位置同时触发水波效果时传入此参数。不传入时默认无水波位置， 水波效果不生效。数组中每个位置包含x和y两个维度，坐标为归一化坐标，[0, 0]表示左上角， [1, 1]表示右下角。最多支持10个位置坐标，超出则整体无效。

**类型：** Array&lt;[double, double]&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-LiquidMaterialEffectParam-ripplePosition?: Array<[double, double]>--><!--Device-LiquidMaterialEffectParam-ripplePosition?: Array<[double, double]>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## rippleProgress

```TypeScript
rippleProgress : double
```

水波效果进度。值大于等于0，值小于0时表示无水波效果。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-LiquidMaterialEffectParam-rippleProgress : double--><!--Device-LiquidMaterialEffectParam-rippleProgress : double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## tintColor

```TypeScript
tintColor : [double, double, double, double]
```

材质叠加的颜色，四个变量分别对应RGBA。取值范围为[0, 1]，小于0时取值为0，大于1时取值为1。

**类型：** [double, double, double, double]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-LiquidMaterialEffectParam-tintColor : [double, double, double, double]--><!--Device-LiquidMaterialEffectParam-tintColor : [double, double, double, double]-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

