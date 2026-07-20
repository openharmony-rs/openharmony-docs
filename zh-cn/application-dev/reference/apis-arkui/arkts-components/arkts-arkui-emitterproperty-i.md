# EmitterProperty

设置发射器属性。

**起始版本：** 12

<!--Device-unnamed-interface EmitterProperty--><!--Device-unnamed-interface EmitterProperty-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## annulusRegion

```TypeScript
annulusRegion?: ParticleAnnulusRegion
```

环形发射器参数。需要对应index的发射器形状为环形才生效。

**类型：** ParticleAnnulusRegion

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-EmitterProperty-annulusRegion?: ParticleAnnulusRegion--><!--Device-EmitterProperty-annulusRegion?: ParticleAnnulusRegion-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## emitRate

```TypeScript
emitRate?: number
```

发射器发射速率，即每秒发射粒子的数量。

未传入时保持其当前的发射速率， 传入值小于0时取默认值5。emitRate值超过5000时会极大影响性能，建议设置参数小于5000。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-EmitterProperty-emitRate?: number--><!--Device-EmitterProperty-emitRate?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index : number
```

索引，取整，按初始化参数中发射器的数组索引指定对应的发射器。异常默认值为0。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-EmitterProperty-index : number--><!--Device-EmitterProperty-index : number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: PositionT<number>
```

发射器位置的数组，只支持number类型。

未传入时保持其当前的发射器位置。需传入两个有效参数，若其中一个为异常值，则position不生效。

x、y的取值范围：(-∞, +∞)。

**类型：** PositionT&lt;number&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-EmitterProperty-position?: PositionT<number>--><!--Device-EmitterProperty-position?: PositionT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: SizeT<number>
```

发射窗口的大小，只支持number类型。

未传入时保持其当前发射窗口大小。需传入两个有效参数且都大于0，若其中一个为异常值，则size不生效。

**类型：** SizeT&lt;number&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-EmitterProperty-size?: SizeT<number>--><!--Device-EmitterProperty-size?: SizeT<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

