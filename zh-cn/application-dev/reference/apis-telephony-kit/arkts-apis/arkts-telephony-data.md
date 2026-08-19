# @ohos.telephony.data

蜂窝数据提供了移动数据管理能力，包括获取默认移动数据的SIM卡、获取蜂窝数据业务的上下行数据流状态、蜂窝数据业务链路连接状态，以及检查蜂窝数据业务和漫游是否启用等。

**起始版本：** 23

<!--Device-unnamed-declare namespace data--><!--Device-unnamed-declare namespace data-End-->

**系统能力：** SystemCapability.Telephony.CellularData

## 导入模块

```TypeScript
import { data } from '@kit.TelephonyKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getActiveApnName](arkts-telephony-data-getactiveapnname-f.md) | 异步获取默认移动数据SIM卡对应的处于激活状态的数据业务APN（access point name，接入点名称）name信息，若不处于激活状态，返回为空字符串。 |
| [getCellularDataFlowType](arkts-telephony-data-getcellulardataflowtype-f.md) | 获取蜂窝网络的数据流类型（对应信号栏旁边的上下行箭头），使用callback方式作为异步方法。 |
| [getCellularDataFlowType](arkts-telephony-data-getcellulardataflowtype-f.md) | 获取蜂窝网络的数据流类型（对应信号栏旁边的上下行箭头），使用Promise方式作为异步方法。 |
| [getCellularDataState](arkts-telephony-data-getcellulardatastate-f.md) | 获取蜂窝数据业务的连接状态，使用callback方式作为异步方法。 |
| [getCellularDataState](arkts-telephony-data-getcellulardatastate-f.md) | 获取蜂窝数据业务的连接状态，使用Promise方式作为异步方法。 |
| [getDefaultCellularDataSimId](arkts-telephony-data-getdefaultcellulardatasimid-f.md) | 获取默认移动数据的SIM卡ID。 |
| [getDefaultCellularDataSlotId](arkts-telephony-data-getdefaultcellulardataslotid-f.md) | 获取默认移动数据的SIM卡，使用callback方式作为异步方法。 |
| [getDefaultCellularDataSlotId](arkts-telephony-data-getdefaultcellulardataslotid-f.md) | 获取默认移动数据的SIM卡，使用Promise方式作为异步方法。 |
| [getDefaultCellularDataSlotIdSync](arkts-telephony-data-getdefaultcellulardataslotidsync-f.md) | 获取默认移动数据的SIM卡。 |
| [isCellularDataEnabled](arkts-telephony-data-iscellulardataenabled-f.md) | 检查蜂窝数据业务是否启用，使用callback方式作为异步方法。 |
| [isCellularDataEnabled](arkts-telephony-data-iscellulardataenabled-f.md) | 检查蜂窝数据业务是否启用，使用Promise方式作为异步方法。 |
| [isCellularDataEnabledSync](arkts-telephony-data-iscellulardataenabledsync-f.md) | 检查蜂窝数据业务是否启用，调用此API返回结果。 |
| [isCellularDataRoamingEnabled](arkts-telephony-data-iscellulardataroamingenabled-f.md) | 检查蜂窝数据业务是否启用漫游，使用callback方式作为异步方法。 |
| [isCellularDataRoamingEnabled](arkts-telephony-data-iscellulardataroamingenabled-f.md) | 检查蜂窝数据业务是否启用漫游，使用Promise方式作为异步方法。 |
| [isCellularDataRoamingEnabledSync](arkts-telephony-data-iscellulardataroamingenabledsync-f.md) | 检查蜂窝数据业务是否启用漫游，调用此API返回结果。 |
| [queryAllApns](arkts-telephony-data-queryallapns-f.md) | 异步获取默认移动数据的SIM卡的APN（access point name，接入点名称）信息。 |
| [queryApnIds](arkts-telephony-data-queryapnids-f.md) | 异步获取传入的ApnInfo对应的ApnId信息。 |
| [setPreferredApn](arkts-telephony-data-setpreferredapn-f.md) | 异步设置apnId对应的APN为首选APN。 > 注意: > > 如果传入的apnId为无效的apnId，切回运营商默认配置的优选Apn。 |
| [showSystemApnSettings](arkts-telephony-data-showsystemapnsettings-f.md) | 打开当前默认移动数据卡对应的APN配置界面。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [disableCellularData](arkts-telephony-data-disablecellulardata-f-sys.md) | 禁用蜂窝数据服务，使用callback方式作为异步方法。 |
| [disableCellularData](arkts-telephony-data-disablecellulardata-f-sys.md) | 禁用蜂窝数据服务，使用Promise方式作为异步方法。 |
| [disableCellularDataRoaming](arkts-telephony-data-disablecellulardataroaming-f-sys.md) | 禁用蜂窝数据漫游，使用callback方式作为异步方法。 |
| [disableCellularDataRoaming](arkts-telephony-data-disablecellulardataroaming-f-sys.md) | 禁用蜂窝数据漫游，使用Promise方式作为异步方法。 |
| [enableCellularData](arkts-telephony-data-enablecellulardata-f-sys.md) | 启用蜂窝数据服务，使用callback方式作为异步方法。 |
| [enableCellularData](arkts-telephony-data-enablecellulardata-f-sys.md) | 启用蜂窝数据服务，使用Promise方式作为异步方法。 |
| [enableCellularDataRoaming](arkts-telephony-data-enablecellulardataroaming-f-sys.md) | 启用蜂窝数据漫游，使用callback方式作为异步方法。 |
| [enableCellularDataRoaming](arkts-telephony-data-enablecellulardataroaming-f-sys.md) | 启用蜂窝数据漫游，使用Promise方式作为异步方法。 |
| [setDefaultCellularDataSlotId](arkts-telephony-data-setdefaultcellulardataslotid-f-sys.md) | 设置默认移动数据的SIM卡，使用callback方式作为异步方法。 |
| [setDefaultCellularDataSlotId](arkts-telephony-data-setdefaultcellulardataslotid-f-sys.md) | 设置默认移动数据的SIM卡，使用Promise方式作为异步方法。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [ApnInfo](arkts-telephony-data-apninfo-i.md) | APN信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DataConnectState](arkts-telephony-data-dataconnectstate-e.md) | 描述蜂窝数据链路连接状态。 |
| [DataFlowType](arkts-telephony-data-dataflowtype-e.md) | 描述蜂窝数据流类型。 |

