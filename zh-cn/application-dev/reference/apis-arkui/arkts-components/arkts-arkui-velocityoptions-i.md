# VelocityOptions

粒子速度配置。

> **说明：**  
>  
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

<!--Device-unnamed-declare interface VelocityOptions--><!--Device-unnamed-declare interface VelocityOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle: ParticleTuple<number, number>
```

表示速度的方向（单位为角度）。以元素几何中心为坐标原点，水平方向为X轴，正数表示顺时针方向旋转角度。

默认值：[0.0,0.0]

**类型：** ParticleTuple&lt;number, number&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VelocityOptions-angle: ParticleTuple<number, number>--><!--Device-VelocityOptions-angle: ParticleTuple<number, number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## speed

```TypeScript
speed: ParticleTuple<number, number>
```

表示速度大小。

默认值：[0.0,0.0]

**类型：** ParticleTuple&lt;number, number&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-VelocityOptions-speed: ParticleTuple<number, number>--><!--Device-VelocityOptions-speed: ParticleTuple<number, number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

