# DeviceSecurityLevelPolicy

```TypeScript
export enum DeviceSecurityLevelPolicy
```

DLS策略

**起始版本：** 26.0.1

<!--Device-securityManager-export enum DeviceSecurityLevelPolicy--><!--Device-securityManager-export enum DeviceSecurityLevelPolicy-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## ALLOW_BALANCED

```TypeScript
ALLOW_BALANCED = 1
```

允许切换DSL1

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceSecurityLevelPolicy-ALLOW_BALANCED = 1--><!--Device-DeviceSecurityLevelPolicy-ALLOW_BALANCED = 1-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## ALLOW_FLEXIBLE

```TypeScript
ALLOW_FLEXIBLE = 2
```

允许切换DSL2，禁止切换到DSL1

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceSecurityLevelPolicy-ALLOW_FLEXIBLE = 2--><!--Device-DeviceSecurityLevelPolicy-ALLOW_FLEXIBLE = 2-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## DEFAULT_ENFORCED

```TypeScript
DEFAULT_ENFORCED = 0
```

禁止切换DSL等级

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeviceSecurityLevelPolicy-DEFAULT_ENFORCED = 0--><!--Device-DeviceSecurityLevelPolicy-DEFAULT_ENFORCED = 0-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager
