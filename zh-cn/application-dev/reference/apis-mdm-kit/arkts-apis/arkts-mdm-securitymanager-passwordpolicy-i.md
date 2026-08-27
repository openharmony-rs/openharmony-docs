# PasswordPolicy

设备锁屏口令策略。

**起始版本：** 12

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

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

## passwordAlgs

```TypeScript
passwordAlgs?: PasswordAlgs
```

处理口令数据使用的加密算法。设置后，PC/2in1设备上将原始口令处理成口令凭据会使用该参数指定的加密算法，其他设备无效果。

**类型：** [PasswordAlgs](arkts-mdm-securitymanager-passwordalgs-e.md)

**起始版本：** 26.0.0

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
