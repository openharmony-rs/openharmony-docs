# PasswordPolicy

设备锁屏口令策略。

**起始版本：** 12

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## additionalDescription

```TypeScript
additionalDescription?: string
```

口令复杂度描述文本，例如：密码中必须包含字母、数字、特殊字符，至少8个字符，最多30个字符。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## complexityRegex

```TypeScript
complexityRegex?: string
```

口令复杂度正则表达式。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## validityPeriod

```TypeScript
validityPeriod?: number
```

密码有效期（单位：毫秒）。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

