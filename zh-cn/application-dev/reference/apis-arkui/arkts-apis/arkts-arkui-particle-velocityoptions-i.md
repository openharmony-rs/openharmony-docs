# VelocityOptions

粒子速度配置。 > **说明：** > > 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface VelocityOptions--><!--Device-unnamed-export declare interface VelocityOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle: ParticleTuple<double, double>
```

表示速度的方向（单位为角度）。以元素几何中心为坐标原点，水平方向为X轴，正数表示顺时针方向旋转角度。 默认值：{range:[0.0,0.0]} **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [ParticleTuple](arkts-arkui-particletuple-t.md)&lt;double, double&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VelocityOptions-angle: ParticleTuple<double, double>--><!--Device-VelocityOptions-angle: ParticleTuple<double, double>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## speed

```TypeScript
speed: ParticleTuple<double, double>
```

表示速度大小。 默认值：{range:[0.0,0.0]} **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** [ParticleTuple](arkts-arkui-particletuple-t.md)&lt;double, double&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VelocityOptions-speed: ParticleTuple<double, double>--><!--Device-VelocityOptions-speed: ParticleTuple<double, double>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

