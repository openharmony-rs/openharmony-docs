# @ohos.enterprise.locationManager

本模块提供设备位置服务策略管理的能力，包括设置和查询位置服务开关策略等。 **使用场景**： 适用于企业设备管理场景，管理员可通过此模块统一管控设备位置服务策略。 > **说明：** > > 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../mdm/mdm-kit-guide.md)。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace locationManager--><!--Device-unnamed-declare namespace locationManager-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getLocationPolicy](arkts-mdm-locationmanager-getlocationpolicy-f.md#getLocationPolicy) | 查询位置服务管理策略。可在企业设备管理应用中检查当前设备的位置服务策略状态，用于策略合规性验证或策略调整前的状态确认。适用于确认当前策略配置、设备管理应用启动时读取策略状态、排查位置服务问题时检查策略等场景。 |
| [getLocationPolicy](arkts-mdm-locationmanager-getlocationpolicy-f.md#getLocationPolicy) | 查询位置服务管理策略。可在企业设备管理应用中检查当前设备的位置服务策略状态，用于策略合规性验证或策略调整前的状态确认。适用于确认当前策略配置、设备管理应用启动时读取策略状态、排查位置服务问题时检查策略等场景。 |
| [setLocationPolicy](arkts-mdm-locationmanager-setlocationpolicy-f.md#setLocationPolicy) | 设置位置服务管理策略。可用于企业管控场景，如：在涉密区域禁用位置服务以保护信息安全，或在物流配送应用中强制开启位置服务以追踪设备位置。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LocationPolicy](arkts-mdm-locationmanager-locationpolicy-e.md) | 位置服务策略值。 |

