# PolicyChangedEvent

策略变更事件。 该接口目前在 [onAdminPolicyChanged](../../apis-na/arkts-apis/arkts-na-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onAdminPolicyChanged) 接口中作为回调入参使用。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-common-export interface PolicyChangedEvent--><!--Device-common-export interface PolicyChangedEvent-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## bundleName

```TypeScript
bundleName: string
```

应用包名。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PolicyChangedEvent-bundleName: string--><!--Device-PolicyChangedEvent-bundleName: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## functionName

```TypeScript
functionName: string
```

接口名称。例如调用[setPasswordPolicy](arkts-mdm-securitymanager-setpasswordpolicy-f.md#setPasswordPolicy)接口时，该字段返回值为 setPasswordPolicy。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PolicyChangedEvent-functionName: string--><!--Device-PolicyChangedEvent-functionName: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## parameters

```TypeScript
parameters: string
```

调用接口时传入的参数值（不包含admin参数），JSON格式字符串。例如调用 [setPasswordPolicy](arkts-mdm-securitymanager-setpasswordpolicy-f.md#setPasswordPolicy)接口，该字段返回值为{"policy": {"complexityRegex":"^(?=.*[a-zA-Z])(?=.*\\d).{8},\$","validityPeriod":1808309786000,"additionalDescription":"至少8个字 符，且包含数字和字母。"}}。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PolicyChangedEvent-parameters: string--><!--Device-PolicyChangedEvent-parameters: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## time

```TypeScript
time: number
```

调用接口的时间戳，单位：ms。

**类型：** number

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PolicyChangedEvent-time: number--><!--Device-PolicyChangedEvent-time: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

