# @ohos.enterprise.common

本模块提供MDM Kit中常用公共能力的纯类型定义，包含枚举类型和数据结构。本模块仅导出类型声明，不包含具体实现逻辑或可执行代码。

> **说明：**
>
> 本模块接口仅可在Stage模型下使用。

**起始版本：** 22

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ApplicationInstance](arkts-mdm-applicationinstance-i.md) | 应用的实例数据。该接口目前在[addUserNonStopApps](arkts-mdm-addusernonstopapps-f.md#addusernonstopapps-1)、[removeUserNonStopApps](arkts-mdm-removeusernonstopapps-f.md#removeusernonstopapps-1)、[addFreezeExemptedApps](arkts-mdm-addfreezeexemptedapps-f.md#addfreezeexemptedapps-1)、[removeFreezeExemptedApps](arkts-mdm-removefreezeexemptedapps-f.md#removefreezeexemptedapps-1)接口中作为入参使用。 |
| [InstallationResult](arkts-mdm-installationresult-i.md) | 应用安装结果。该对象目前在[EnterpriseAdminExtensionAbility.onMarketAppInstallResult](arkts-mdm-enterpriseadminextensionability-c.md#onmarketappinstallresult-1)作为回调入参使用。 |
| [PolicyChangedEvent](arkts-mdm-policychangedevent-i.md) | 策略变更事件 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ManagedPolicy](arkts-mdm-managedpolicy-e.md) | 企业设备管控策略。 |
| [Result](arkts-mdm-result-e.md) | 应用安装结果码。 |
| [StartupScene](arkts-mdm-startupscene-e.md) | 开机向导完成场景。端侧系统在首次切换子用户完成（仅限PC）、OTA升级完成、首次开机完成开机向导时会通过[onStartupGuideCompleted](arkts-mdm-enterpriseadminextensionability-c.md#onstartupguidecompleted-1)回调接口通知设备管理应用。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [EnterpriseAdminExtensionContext](arkts-mdm-enterpriseadminextensioncontext-t.md) | EnterpriseAdminExtensionContext是[EnterpriseAdminExtensionAbility](arkts-mdm-enterpriseadminextensionability-c.md)的上下文环境，继承自[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。 |

