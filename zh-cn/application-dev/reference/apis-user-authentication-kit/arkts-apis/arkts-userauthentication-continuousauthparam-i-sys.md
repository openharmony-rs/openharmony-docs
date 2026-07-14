# ContinuousAuthParam（系统接口）

持续认证参数。用于配置订阅持续认证状态时的相关参数，如指定订阅的目标模板。

**起始版本：** 23

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

## templateId

```TypeScript
templateId?: Uint8Array
```

模板ID。用于指定订阅的目标模板。若不指定此参数，默认订阅当前用户下全部模板的持续认证状态。指定具体模板ID时，仅订阅该模板的认证状态变化。

**类型：** Uint8Array

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**系统接口：** 此接口为系统接口。

