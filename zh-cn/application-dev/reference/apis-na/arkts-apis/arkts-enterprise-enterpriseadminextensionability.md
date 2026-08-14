# @ohos.enterprise.EnterpriseAdminExtensionAbility

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [EnterpriseAdminExtensionAbility](arkts-na-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md) | 本模块提供[企业设备管理扩展能力](../../../mdm/mdm-kit-term.md#enterpriseadminextensionability企业设备管理扩展能力)，是企业设备管理应用的核心组件。 **主要功能**： - 提供设备管理应用的生命周期管理能力（激活、去激活、启动等事件）。 - 提供应用生命周期事件监听能力（安装、卸载、启动、停止、更新）。 - 提供系统账号管理事件监听能力（账号新增、切换、删除）。 - 提供Kiosk模式、按键事件、日志收集、系统更新等系统级事件回调。 - 提供策略变更事件监听能力。 **使用场景**：企业设备管理应用开发、企业应用生命周期管理、设备安全管控、账号管理、设备运维监控等。 设备管理应用需要存在一个EnterpriseAdminExtensionAbility并重写相关接口，以此具备模块提供的各项能力，比如接收由系统发送的该应用被激活或者解除激活的通知。 |

