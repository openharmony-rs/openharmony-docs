# PasswordPolicy

设备锁屏口令策略。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-securityManager-export interface PasswordPolicy--><!--Device-securityManager-export interface PasswordPolicy-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## additionalDescription

```TypeScript
additionalDescription?: string
```

口令复杂度描述文本，例如：密码中必须包含字母、数字、特殊字符，至少8个字符，最多30个字符。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PasswordPolicy-additionalDescription?: string--><!--Device-PasswordPolicy-additionalDescription?: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## complexityRegex

```TypeScript
complexityRegex?: string
```

口令复杂度正则表达式。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PasswordPolicy-complexityRegex?: string--><!--Device-PasswordPolicy-complexityRegex?: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## passwordAlgs

```TypeScript
passwordAlgs?: PasswordAlgs
```

处理口令数据使用的加密算法。设置后，PC/2in1设备上将原始口令处理成口令凭据会使用该参数指定的加密算法，其他设备无效果。

**类型：** [PasswordAlgs](arkts-mdm-securitymanager-passwordalgs-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PasswordPolicy-passwordAlgs?: PasswordAlgs--><!--Device-PasswordPolicy-passwordAlgs?: PasswordAlgs-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## validityPeriod

```TypeScript
validityPeriod?: long
```

密码有效期（单位：毫秒）。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PasswordPolicy-validityPeriod?: long--><!--Device-PasswordPolicy-validityPeriod?: long-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

