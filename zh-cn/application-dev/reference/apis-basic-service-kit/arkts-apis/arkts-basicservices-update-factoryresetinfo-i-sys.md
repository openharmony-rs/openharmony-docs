# FactoryResetInfo（系统接口）

恢复出厂设置信息。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-update-export interface FactoryResetInfo--><!--Device-update-export interface FactoryResetInfo-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## duration

```TypeScript
duration: int
```

恢复出厂设置所需持续时间。单位为min。取值范围[0, 86400]。超出范围时抛出异常。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FactoryResetInfo-duration: int--><!--Device-FactoryResetInfo-duration: int-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

