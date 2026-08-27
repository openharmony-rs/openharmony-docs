# @ohos.telephony.data(蜂窝数据)

蜂窝数据提供了移动数据管理能力，包括获取默认移动数据的SIM卡、获取蜂窝数据业务的上下行数据流状态、蜂窝数据业务链路连接状态，以及检查蜂窝数据业务和漫游是否启用等。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CellularData

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getActiveApnName(蜂窝数据)](arkts-telephony-data-getactiveapnname-f.md) | 异步获取默认移动数据SIM卡对应的处于激活状态的数据业务APN（access point name，接入点名称）name信息，若不处于激活状态，返回为空字符串。 |
| [getCellularDataFlowType(蜂窝数据)](arkts-telephony-data-getcellulardataflowtype-f.md) | 获取蜂窝网络的数据流类型（对应信号栏旁边的上下行箭头），使用callback方式作为异步方法。 |
| [getCellularDataFlowType(蜂窝数据)](arkts-telephony-data-getcellulardataflowtype-f.md) | 获取蜂窝网络的数据流类型（对应信号栏旁边的上下行箭头），使用Promise方式作为异步方法。 |
| [getCellularDataState(蜂窝数据)](arkts-telephony-data-getcellulardatastate-f.md) | 获取蜂窝数据业务的连接状态，使用callback方式作为异步方法。 |
| [getCellularDataState(蜂窝数据)](arkts-telephony-data-getcellulardatastate-f.md) | 获取蜂窝数据业务的连接状态，使用Promise方式作为异步方法。 |
| [getDefaultCellularDataSimId(蜂窝数据)](arkts-telephony-data-getdefaultcellulardatasimid-f.md) | 获取默认移动数据的SIM卡ID。 |
| [getDefaultCellularDataSlotId(蜂窝数据)](arkts-telephony-data-getdefaultcellulardataslotid-f.md) | 获取默认移动数据的SIM卡，使用callback方式作为异步方法。 |
| [getDefaultCellularDataSlotId(蜂窝数据)](arkts-telephony-data-getdefaultcellulardataslotid-f.md) | 获取默认移动数据的SIM卡，使用Promise方式作为异步方法。 |
| [getDefaultCellularDataSlotIdSync(蜂窝数据)](arkts-telephony-data-getdefaultcellulardataslotidsync-f.md) | 获取默认移动数据的SIM卡。 |
| [isCellularDataEnabled(蜂窝数据)](arkts-telephony-data-iscellulardataenabled-f.md) | 检查蜂窝数据业务是否启用，使用callback方式作为异步方法。 |
| [isCellularDataEnabled(蜂窝数据)](arkts-telephony-data-iscellulardataenabled-f.md) | 检查蜂窝数据业务是否启用，使用Promise方式作为异步方法。 |
| [isCellularDataEnabledSync(蜂窝数据)](arkts-telephony-data-iscellulardataenabledsync-f.md) | 检查蜂窝数据业务是否启用，调用此API返回结果。 |
| [isCellularDataRoamingEnabled(蜂窝数据)](arkts-telephony-data-iscellulardataroamingenabled-f.md) | 检查蜂窝数据业务是否启用漫游，使用callback方式作为异步方法。 |
| [isCellularDataRoamingEnabled(蜂窝数据)](arkts-telephony-data-iscellulardataroamingenabled-f.md) | 检查蜂窝数据业务是否启用漫游，使用Promise方式作为异步方法。 |
| [isCellularDataRoamingEnabledSync(蜂窝数据)](arkts-telephony-data-iscellulardataroamingenabledsync-f.md) | 检查蜂窝数据业务是否启用漫游，调用此API返回结果。 |
| [queryAllApns(蜂窝数据)](arkts-telephony-data-queryallapns-f.md) | 异步获取默认移动数据的SIM卡的APN（access point name，接入点名称）信息。 |
| [queryApnIds(蜂窝数据)](arkts-telephony-data-queryapnids-f.md) | 异步获取传入的ApnInfo对应的ApnId信息。 |
| [setPreferredApn(蜂窝数据)](arkts-telephony-data-setpreferredapn-f.md) | 异步设置apnId对应的APN为首选APN。 |
| [showSystemApnSettings(蜂窝数据)](arkts-telephony-data-showsystemapnsettings-f.md) | 打开当前默认移动数据卡对应的APN配置界面。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [disableCellularData(蜂窝数据)](arkts-telephony-data-disablecellulardata-f-sys.md) | 禁用蜂窝数据服务，使用callback方式作为异步方法。 |
| [disableCellularData(蜂窝数据)](arkts-telephony-data-disablecellulardata-f-sys.md) | 禁用蜂窝数据服务，使用Promise方式作为异步方法。 |
| [disableCellularDataRoaming(蜂窝数据)](arkts-telephony-data-disablecellulardataroaming-f-sys.md) | 禁用蜂窝数据漫游，使用callback方式作为异步方法。 |
| [disableCellularDataRoaming(蜂窝数据)](arkts-telephony-data-disablecellulardataroaming-f-sys.md) | 禁用蜂窝数据漫游，使用Promise方式作为异步方法。 |
| [enableCellularData(蜂窝数据)](arkts-telephony-data-enablecellulardata-f-sys.md) | 启用蜂窝数据服务，使用callback方式作为异步方法。 |
| [enableCellularData(蜂窝数据)](arkts-telephony-data-enablecellulardata-f-sys.md) | 启用蜂窝数据服务，使用Promise方式作为异步方法。 |
| [enableCellularDataRoaming(蜂窝数据)](arkts-telephony-data-enablecellulardataroaming-f-sys.md) | 启用蜂窝数据漫游，使用callback方式作为异步方法。 |
| [enableCellularDataRoaming(蜂窝数据)](arkts-telephony-data-enablecellulardataroaming-f-sys.md) | 启用蜂窝数据漫游，使用Promise方式作为异步方法。 |
| [setDefaultCellularDataSlotId(蜂窝数据)](arkts-telephony-data-setdefaultcellulardataslotid-f-sys.md) | 设置默认移动数据的SIM卡，使用callback方式作为异步方法。 |
| [setDefaultCellularDataSlotId(蜂窝数据)](arkts-telephony-data-setdefaultcellulardataslotid-f-sys.md) | 设置默认移动数据的SIM卡，使用Promise方式作为异步方法。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [ApnInfo(蜂窝数据)](arkts-telephony-data-apninfo-i.md) | APN信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DataConnectState(蜂窝数据)](arkts-telephony-data-dataconnectstate-e.md) | 描述蜂窝数据链路连接状态。 |
| [DataFlowType(蜂窝数据)](arkts-telephony-data-dataflowtype-e.md) | 描述蜂窝数据流类型。 |
