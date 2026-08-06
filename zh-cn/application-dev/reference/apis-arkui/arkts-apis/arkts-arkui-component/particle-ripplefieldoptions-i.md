# RippleFieldOptions

用于描述粒子波动场信息的参数。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

<!--Device-unnamed-export declare interface RippleFieldOptions--><!--Device-unnamed-export declare interface RippleFieldOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## amplitude

```TypeScript
amplitude?: double
```

The amplitude of the ripple field. The greater the amplitude, the stronger the force of the ripple field. Range of values:[0, +∞)

**类型：** double

**默认值：** 0

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RippleFieldOptions-amplitude?: double--><!--Device-RippleFieldOptions-amplitude?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attenuation

```TypeScript
attenuation?: double
```

The attenuation coefficient of the ripple field. The larger the attenuation coefficient, the faster the wave attenuates over time. Range of values:[0,1]

**类型：** double

**默认值：** 0

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RippleFieldOptions-attenuation?: double--><!--Device-RippleFieldOptions-attenuation?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## center

```TypeScript
center?: PositionT<double>
```

The central point where the ripple field generates force. The top-left corner of the component is the origin of coordinates. The coordinate unit is vp.

**类型：** PositionT&lt;double&gt;

**默认值：** {x:0,y:0}

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RippleFieldOptions-center?: PositionT<double>--><!--Device-RippleFieldOptions-center?: PositionT<double>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## region

```TypeScript
region?: FieldRegion
```

The region influenced by the ripple field.

**类型：** FieldRegion

**默认值：** {shape:DisturbanceFieldShape.RECT,position:{x:0,y:0},size:{width:0,height:0}}

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RippleFieldOptions-region?: FieldRegion--><!--Device-RippleFieldOptions-region?: FieldRegion-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## waveSpeed

```TypeScript
waveSpeed?: double
```

Wave speed. The greater the wave speed, the faster the wave changes over time, and the more pronounced the wave motion. Range of values:[0, +∞)

**类型：** double

**默认值：** 0

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RippleFieldOptions-waveSpeed?: double--><!--Device-RippleFieldOptions-waveSpeed?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## wavelength

```TypeScript
wavelength?: double
```

Wavelength, which is the distance over which a wave cycle changes. The larger the wavelength, the slower the wave changes with distance, and the less pronounced the wave fluctiations. Range of values:[0, +∞)

**类型：** double

**默认值：** 0

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RippleFieldOptions-wavelength?: double--><!--Device-RippleFieldOptions-wavelength?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

