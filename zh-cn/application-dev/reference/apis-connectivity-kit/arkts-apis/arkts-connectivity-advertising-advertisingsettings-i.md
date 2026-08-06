# AdvertisingSettings

广播设置。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-advertising-interface AdvertisingSettings--><!--Device-advertising-interface AdvertisingSettings-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## interval

```TypeScript
interval?: int
```

广播时间间隔，单位为slot。 最小的slot数是160，对应的时间是160*0.125=20ms。 最大slot数为16777215，对应的时间为2097151.875 ms。 如果不设置“interval”，则默认值为5000，对应的时间为625 ms。 单位为： 时隙，取值应为[160,16777215]内的整数，每个时隙为125微秒，。 默认值： 5000。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AdvertisingSettings-interval?: int--><!--Device-AdvertisingSettings-interval?: int-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## isConnectable

```TypeScript
isConnectable?: boolean
```

广播是否可连接。 如果不设置“isConnectable”，则默认值为true。 默认值： 默认值：true。

**类型：** boolean

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AdvertisingSettings-isConnectable?: boolean--><!--Device-AdvertisingSettings-isConnectable?: boolean-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## power

```TypeScript
power?: TxPowerMode
```

广播功率模式。 如果不设置“power”，则默认值为“ADV\_TX\_POWER\_LOW”。 默认值： ADV\_TX\_POWER\_LOW。

**类型：** TxPowerMode

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AdvertisingSettings-power?: TxPowerMode--><!--Device-AdvertisingSettings-power?: TxPowerMode-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

