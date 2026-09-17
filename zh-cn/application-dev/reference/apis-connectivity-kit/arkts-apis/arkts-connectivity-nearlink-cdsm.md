# @ohos.nearlink.cdsm(星闪合作设备集合管理能力)

本模块提供了星闪合作设备集合管理（Coordinated Devices Set Management，CDSM）的能力，包括查询和订阅星闪合作设备集合信息的功能。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

## 导入模块

```TypeScript
import { cdsm } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createCdsmClient](arkts-connectivity-cdsm-createcdsmclient-f.md) | 创建CDSM客户端实例。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CdsmClient](arkts-connectivity-cdsm-cdsmclient-i.md) | CDSM客户端类，提供了获取远端设备的合作设备集合信息等操作方法。 |
| [CdsmInfo](arkts-connectivity-cdsm-cdsminfo-i.md) | 表示合作设备集合信息。 |
| [CdsmMemberInfo](arkts-connectivity-cdsm-cdsmmemberinfo-i.md) | 表示合作设备集合的成员信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CdsmConnectionState](arkts-connectivity-cdsm-cdsmconnectionstate-e.md) | 表示合作设备集合中成员设备的连接状态，为枚举值。 |
