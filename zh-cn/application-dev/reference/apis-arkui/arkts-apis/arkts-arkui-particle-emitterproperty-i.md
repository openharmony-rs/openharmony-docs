# EmitterProperty

设置发射器属性。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface EmitterProperty--><!--Device-unnamed-export interface EmitterProperty-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## annulusRegion

```TypeScript
annulusRegion?: ParticleAnnulusRegion
```

环形发射器参数。需要对应index的发射器形状为环形才生效。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 20开始，该接口支持在原子化服务中使用。

**类型：** [ParticleAnnulusRegion](arkts-arkui-particle-particleannulusregion-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EmitterProperty-annulusRegion?: ParticleAnnulusRegion--><!--Device-EmitterProperty-annulusRegion?: ParticleAnnulusRegion-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## emitRate

```TypeScript
emitRate?: int
```

发射器发射速率，即每秒发射粒子的数量。 未传入时保持其当前的发射速率， 传入值小于0时取默认值5。emitRate值超过5000时会极大影响性能，建议设置参数小于5000。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EmitterProperty-emitRate?: int--><!--Device-EmitterProperty-emitRate?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: int
```

索引，取整，按初始化参数中发射器的数组索引指定对应的发射器。异常默认值为0。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EmitterProperty-index: int--><!--Device-EmitterProperty-index: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: PositionT<double>
```

发射器位置的数组，只支持number类型。 未传入时保持其当前的发射器位置。需传入两个有效参数，若其中一个为异常值，则position不生效。 x、y的取值范围：(-∞, +∞)。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [PositionT](arkts-arkui-positiont-t.md)&lt;double&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EmitterProperty-position?: PositionT<double>--><!--Device-EmitterProperty-position?: PositionT<double>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeT<double>
```

发射窗口的大小，只支持number类型。 未传入时保持其当前发射窗口大小。需传入两个有效参数且都大于0，若其中一个为异常值，则size不生效。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在原子化服务中使用。

**类型：** [SizeT](arkts-arkui-graphics-sizet-i.md)&lt;double&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-EmitterProperty-size?: SizeT<double>--><!--Device-EmitterProperty-size?: SizeT<double>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

