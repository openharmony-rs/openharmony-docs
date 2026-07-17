# FeatureForAccount

可为指定用户设置禁用/启用的特性的枚举。

**起始版本：** 26.0.0

<!--Device-restrictions-enum FeatureForAccount--><!--Device-restrictions-enum FeatureForAccount-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## MULTI_WINDOW

```TypeScript
MULTI_WINDOW = 0
```

系统多窗口。当前仅支持手机、平板设备使用，禁用后无法使用系统多窗口功能（分屏、一键分屏、智慧多窗、悬浮窗口）。若系统多窗口功能已开启，本次使用不受影响，但关闭后将无法再次使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForAccount-MULTI_WINDOW = 0--><!--Device-FeatureForAccount-MULTI_WINDOW = 0-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## DISTRIBUTED_TRANSMISSION

```TypeScript
DISTRIBUTED_TRANSMISSION = 1
```

[分布式管理服务](../../../../distributedservice/distributedservice-kit-intro.md#运作机制)。禁用后无法使用设备分布式管理服务中的发现、认证、查询、监听等功能。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForAccount-DISTRIBUTED_TRANSMISSION = 1--><!--Device-FeatureForAccount-DISTRIBUTED_TRANSMISSION = 1-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## SUPER_HUB

```TypeScript
SUPER_HUB = 2
```

中转站。当前仅支持手机、平板设备使用，禁用后无法使用中转站功能。若中转站已开启，本次使用不受影响，但关闭后将无法再次使用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FeatureForAccount-SUPER_HUB = 2--><!--Device-FeatureForAccount-SUPER_HUB = 2-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

