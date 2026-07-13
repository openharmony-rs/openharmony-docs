# SystemAdaptiveOptions

系统自适应调节参数，系统会默认开启根据芯片算力进行自适应效果调节的能力。

**起始版本：** 19

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## disableSystemAdaptation

```TypeScript
disableSystemAdaptation?: boolean
```

系统自适应调节参数，推荐不携带该参数。该参数只影响低算力设备，低算力设备的定义由设备厂商决定。在低芯片算力的设备上，会根据算力和负载等条件，自动决策是否使用低算力的近似效果替代原有效果，比如模糊效果会结合接口中携带的模糊相关参数值
及其他低算力处理逻辑，进行自适应效果降级处理。如果想关闭该功能，可以将该标志置为true。

默认值：false

**类型：** boolean

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本19开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

