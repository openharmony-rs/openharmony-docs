# OtaUpdatePolicy

升级策略。

**起始版本：** 12

<!--Device-systemManager-export interface OtaUpdatePolicy--><!--Device-systemManager-export interface OtaUpdatePolicy-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## delayUpdateTime

```TypeScript
delayUpdateTime?: number
```

表示延迟升级时间（单位：小时）。单位为： 小时，取值应为≥0的整数。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OtaUpdatePolicy-delayUpdateTime?: number--><!--Device-OtaUpdatePolicy-delayUpdateTime?: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## disableSystemOtaUpdate

```TypeScript
disableSystemOtaUpdate?: boolean
```

表示是否禁用在公网环境下升级。true表示禁用公网升级，false表示不禁用公网升级。如果作为[systemManager.setOtaUpdatePolicy](arkts-mdm-systemmanager-setotaupdatepolicy-f.md#setotaupdatepolicy)的入参，该字段可缺省，缺省时保持当前配置不变。当前配置可通过[systemManager.getOtaUpdatePolicy](arkts-mdm-systemmanager-getotaupdatepolicy-f.md#getotaupdatepolicy)接口获取。禁用公网升级后，可以采用内网升级。<!--RP4--><!--RP4End-->

**类型：** boolean

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OtaUpdatePolicy-disableSystemOtaUpdate?: boolean--><!--Device-OtaUpdatePolicy-disableSystemOtaUpdate?: boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## installEndTime

```TypeScript
installEndTime?: number
```

表示指定安装窗口结束时间（时间戳）。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OtaUpdatePolicy-installEndTime?: number--><!--Device-OtaUpdatePolicy-installEndTime?: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## installStartTime

```TypeScript
installStartTime?: number
```

表示指定安装窗口起始时间（时间戳）。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OtaUpdatePolicy-installStartTime?: number--><!--Device-OtaUpdatePolicy-installStartTime?: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## latestUpdateTime

```TypeScript
latestUpdateTime?: number
```

表示最晚升级时间（时间戳）。单位为： 秒，取值应为≥0的整数。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OtaUpdatePolicy-latestUpdateTime?: number--><!--Device-OtaUpdatePolicy-latestUpdateTime?: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## policyType

```TypeScript
policyType: PolicyType
```

表示升级策略类型。

**类型：** PolicyType

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OtaUpdatePolicy-policyType: PolicyType--><!--Device-OtaUpdatePolicy-policyType: PolicyType-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## version

```TypeScript
version: string
```

表示待升级软件版本号。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OtaUpdatePolicy-version: string--><!--Device-OtaUpdatePolicy-version: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

