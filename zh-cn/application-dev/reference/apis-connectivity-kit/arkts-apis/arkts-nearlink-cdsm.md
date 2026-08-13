# @ohos.nearlink.cdsm

提供与星闪CDSM（合作设备集合管理）相关的方法。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace cdsm--><!--Device-unnamed-declare namespace cdsm-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createCdsmClient](arkts-connectivity-cdsm-createcdsmclient-f.md#createCdsmClient) | 创建CDSM客户端实例。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CdsmClient](arkts-connectivity-cdsm-cdsmclient-i.md) | 管理CDSM客户端实例。在调用任何CDSM客户端方法之前， 您必须使用[createCdsmClient](arkts-connectivity-cdsm-createcdsmclient-f.md#createCdsmClient)来创建CDSM客户端实例。 |
| [CdsmInfo](arkts-connectivity-cdsm-cdsminfo-i.md) | 描述合作设备集信息。 |
| [CdsmMemberInfo](arkts-connectivity-cdsm-cdsmmemberinfo-i.md) | 描述合作设备集的成员信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CdsmConnectionState](arkts-connectivity-cdsm-cdsmconnectionstate-e.md) | 成员连接状态的枚举。 |

