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
| [createCdsmClient(星闪合作设备集合管理能力)](arkts-connectivity-cdsm-createcdsmclient-f.md) | 创建CDSM客户端实例。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CdsmClient(星闪合作设备集合管理能力)](arkts-connectivity-cdsm-cdsmclient-i.md) | CDSM客户端类，提供了获取远端设备的合作设备集合信息等操作方法。  - 使用该类的方法前，需通过[cdsm.createCdsmClient](arkts-connectivity-cdsm-createcdsmclient-f.md)方法构造该类的实例。  适用于需要获知一组星闪设备（合作设备集合）的成员组成及连接状态变化并据此进行业务联动的场景。例如，手机与耳机配对后，手机可通过CDSM查询左右耳机信息并感知其连接状态变化。同一应用针对同一远端设备创建一个 [CdsmClient](arkts-connectivity-cdsm-cdsmclient-i.md) 实例即可，重复创建会增加不必要的资源开销。 |
| [CdsmInfo(星闪合作设备集合管理能力)](arkts-connectivity-cdsm-cdsminfo-i.md) | 表示合作设备集合信息。 |
| [CdsmMemberInfo(星闪合作设备集合管理能力)](arkts-connectivity-cdsm-cdsmmemberinfo-i.md) | 表示合作设备集合的成员信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CdsmConnectionState(星闪合作设备集合管理能力)](arkts-connectivity-cdsm-cdsmconnectionstate-e.md) | 表示合作设备集合中成员设备的连接状态，为枚举值。 |
