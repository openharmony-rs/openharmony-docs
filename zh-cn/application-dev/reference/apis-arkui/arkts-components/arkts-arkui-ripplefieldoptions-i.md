# RippleFieldOptions

用于描述粒子波动场信息的参数。

**起始版本：** 22

<!--Device-unnamed-declare interface RippleFieldOptions--><!--Device-unnamed-declare interface RippleFieldOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## amplitude

```TypeScript
amplitude?: number
```

The amplitude of the ripple field. The greater the amplitude, the stronger the force of the ripple field.Range of values:[0, +∞)

**类型：** number

**默认值：** 0

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-RippleFieldOptions-amplitude?: number--><!--Device-RippleFieldOptions-amplitude?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attenuation

```TypeScript
attenuation?: number
```

The attenuation coefficient of the ripple field. The larger the attenuation coefficient, the faster the wave attenuates over time. Range of values:[0,1]

**类型：** number

**默认值：** 0

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-RippleFieldOptions-attenuation?: number--><!--Device-RippleFieldOptions-attenuation?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## center

```TypeScript
center?: PositionT<number>
```

The central point where the ripple field generates force. The top-left corner of the component is the origin of coordinates. The coordinate unit is vp.

**类型：** PositionT&lt;number&gt;

**默认值：** {x:0,y:0}

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-RippleFieldOptions-center?: PositionT<number>--><!--Device-RippleFieldOptions-center?: PositionT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## region

```TypeScript
region?: FieldRegion
```

The region influenced by the ripple field.

**类型：** FieldRegion

**默认值：** {shape:DisturbanceFieldShape.RECT,position:{x:0,y:0},size:{width:0,height:0}}

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-RippleFieldOptions-region?: FieldRegion--><!--Device-RippleFieldOptions-region?: FieldRegion-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## waveSpeed

```TypeScript
waveSpeed?: number
```

Wave speed. The greater the wave speed, the faster the wave changes over time, and the more pronounced the wave motion. Range of values:[0, +∞)

**类型：** number

**默认值：** 0

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-RippleFieldOptions-waveSpeed?: number--><!--Device-RippleFieldOptions-waveSpeed?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## wavelength

```TypeScript
wavelength?: number
```

Wavelength, which is the distance over which a wave cycle changes. The larger the wavelength, the slower the wave changes with distance, and the less pronounced the wave fluctiations.Range of values:[0, +∞)

**类型：** number

**默认值：** 0

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-RippleFieldOptions-wavelength?: number--><!--Device-RippleFieldOptions-wavelength?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

