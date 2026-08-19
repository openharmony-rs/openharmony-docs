# @ohos.telephony.observer

本模块提供订阅管理功能，可以订阅/取消订阅的事件包括：网络状态变化、信号状态变化、通话状态变化、蜂窝数据链路连接状态、蜂窝数据业务的上下行数据流状态、SIM状态变化。

**起始版本：** 23

<!--Device-unnamed-declare namespace observer--><!--Device-unnamed-declare namespace observer-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry

## 导入模块

```TypeScript
import { observer } from '@kit.TelephonyKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [offCCallStateChange](arkts-telephony-observer-offccallstatechange-f.md) | 取消三方应用监听运营商通话状态并获取通话号码，使用callback方式作为异步方法。 |
| [offCallStateChange](arkts-telephony-observer-offcallstatechange-f.md) | Cancel callback when the call state is updated. |
| [offCallStateChangeEx](arkts-telephony-observer-offcallstatechangeex-f.md) | Cancel callback when the telCall state is updated. |
| [offCellularDataConnectionStateChange](arkts-telephony-observer-offcellulardataconnectionstatechange-f.md) | Cancel callback when the cellular data link connection state is updated. |
| [offCellularDataFlowChange](arkts-telephony-observer-offcellulardataflowchange-f.md) | Cancel callback when the uplink and downlink data flow state of cellular data services is updated. |
| [offCommunicationStateChange](arkts-telephony-observer-offcommunicationstatechange-f.md) | 取消订阅5A网络状态变化事件，使用callback异步回调。 |
| [offGetSimActiveState](arkts-telephony-observer-offgetsimactivestate-f.md) | 取消SIM卡激活状态变化的监听，使用callback方式作为异步方法。 |
| [offIccAccountInfoChange](arkts-telephony-observer-officcaccountinfochange-f.md) | Cancel to receive an ICC account change. |
| [offNetworkStateChange](arkts-telephony-observer-offnetworkstatechange-f.md) | Cancel callback when the network state is updated. |
| [offSignalInfoChange](arkts-telephony-observer-offsignalinfochange-f.md) | Cancel callback when the signal strength is updated. |
| [offSimStateChange](arkts-telephony-observer-offsimstatechange-f.md) | Cancel callback when the sim state is updated. |
| [off_callStateChange](arkts-telephony-observer-offcallstatechange-f.md) | 取消订阅通话状态变化事件，使用callback方式作为异步方法。 |
| [off_callStateChangeEx](arkts-telephony-observer-offcallstatechangeex-f.md) | 取消订阅通话状态变化拓展事件，使用callback方式作为异步方法。 |
| [off_cellularDataConnectionStateChange](arkts-telephony-observer-offcellulardataconnectionstatechange-f.md) | 移除订阅蜂窝数据链路连接状态，使用callback方式作为异步方法。 |
| [off_cellularDataFlowChange](arkts-telephony-observer-offcellulardataflowchange-f.md) | 移除订阅蜂窝数据业务的上下行数据流状态，使用callback方式作为异步方法。 |
| [off_iccAccountInfoChange](arkts-telephony-observer-officcaccountinfochange-f.md) | 移除订阅卡帐户变化事件，使用callback方式作为异步方法。 |
| [off_networkStateChange](arkts-telephony-observer-offnetworkstatechange-f.md) | 取消订阅网络状态变化事件，使用callback方式作为异步方法。 |
| [off_signalInfoChange](arkts-telephony-observer-offsignalinfochange-f.md) | 取消订阅信号状态变化事件，使用callback方式作为异步方法。 |
| [off_simStateChange](arkts-telephony-observer-offsimstatechange-f.md) | 移除订阅sim状态更改事件，使用callback方式作为异步方法。 |
| [onCCallStateChange](arkts-telephony-observer-onccallstatechange-f.md) | 三方应用监听运营商通话状态并获取通话号码，使用callback方式作为异步方法。 |
| [onCallStateChange](arkts-telephony-observer-oncallstatechange-f.md) | Callback when the call state corresponding to the default sim card is updated. |
| [onCallStateChange](arkts-telephony-observer-oncallstatechange-f.md) | Callback when the call state corresponding to the monitored {@code slotId} is updated. |
| [onCallStateChangeEx](arkts-telephony-observer-oncallstatechangeex-f.md) | Callback when the telCall state corresponding to the monitored {@code slotId} is updated. |
| [onCellularDataConnectionStateChange](arkts-telephony-observer-oncellulardataconnectionstatechange-f.md) | Callback when the cellular data link connection state corresponding to the default sim card is updated. |
| [onCellularDataConnectionStateChange](arkts-telephony-observer-oncellulardataconnectionstatechange-f.md) | Callback when the cellular data link connection state corresponding to the monitored {@code slotId} is updated. |
| [onCellularDataFlowChange](arkts-telephony-observer-oncellulardataflowchange-f.md) | Callback when the uplink and downlink data flow state of cellular data services corresponding to the default sim card is updated. |
| [onCellularDataFlowChange](arkts-telephony-observer-oncellulardataflowchange-f.md) | Callback when the uplink and downlink data flow state of cellular data services corresponding to the monitored {@code slotId} is updated. |
| [onCommunicationStateChange](arkts-telephony-observer-oncommunicationstatechange-f.md) | 订阅5A网络状态变化事件，使用callback异步回调。 |
| [onGetSimActiveState](arkts-telephony-observer-ongetsimactivestate-f.md) | SIM卡激活状态变化的监听，使用callback方式作为异步方法。 |
| [onIccAccountInfoChange](arkts-telephony-observer-oniccaccountinfochange-f.md) | Receives an ICC account change. This callback is invoked when the ICC account updates and the observer is added to monitor the updates. |
| [onNetworkStateChange](arkts-telephony-observer-onnetworkstatechange-f.md) | Callback when the network state corresponding to the default sim card is updated. |
| [onNetworkStateChange](arkts-telephony-observer-onnetworkstatechange-f.md) | Callback when the network state corresponding to the monitored {@code slotId} is updated. |
| [onSignalInfoChange](arkts-telephony-observer-onsignalinfochange-f.md) | Callback when the signal strength corresponding to the default sim card is updated. |
| [onSignalInfoChange](arkts-telephony-observer-onsignalinfochange-f.md) | Callback when the signal strength corresponding to a monitored {@code slotId} is updated. |
| [onSimStateChange](arkts-telephony-observer-onsimstatechange-f.md) | Callback when the sim state corresponding to the default sim card is updated. |
| [onSimStateChange](arkts-telephony-observer-onsimstatechange-f.md) | Callback when the sim state corresponding to the monitored {@code slotId} is updated. |
| [on_callStateChange](arkts-telephony-observer-oncallstatechange-f.md) | 订阅通话状态变化事件，使用callback方式作为异步方法。 |
| [on_callStateChange](arkts-telephony-observer-oncallstatechange-f.md) | 订阅通话状态变化事件，使用callback方式作为异步方法。 |
| [on_callStateChangeEx](arkts-telephony-observer-oncallstatechangeex-f.md) | 订阅通话状态变化拓展事件，使用callback方式作为异步方法。 |
| [on_cellularDataConnectionStateChange](arkts-telephony-observer-oncellulardataconnectionstatechange-f.md) | 订阅蜂窝数据链路连接状态，使用callback方式作为异步方法。 |
| [on_cellularDataConnectionStateChange](arkts-telephony-observer-oncellulardataconnectionstatechange-f.md) | 订阅指定卡槽位的蜂窝数据链路连接状态，使用callback方式作为异步方法。 |
| [on_cellularDataFlowChange](arkts-telephony-observer-oncellulardataflowchange-f.md) | 订阅蜂窝数据业务的上下行数据流状态，使用callback方式作为异步方法。 |
| [on_cellularDataFlowChange](arkts-telephony-observer-oncellulardataflowchange-f.md) | 订阅指定卡槽位的蜂窝数据业务的上下行数据流状态，使用callback方式作为异步方法。 |
| [on_iccAccountInfoChange](arkts-telephony-observer-oniccaccountinfochange-f.md) | 订阅卡帐户变化事件，使用callback方式作为异步方法。 |
| [on_networkStateChange](arkts-telephony-observer-onnetworkstatechange-f.md) | 订阅网络状态变化事件，使用callback方式作为异步方法。 |
| [on_networkStateChange](arkts-telephony-observer-onnetworkstatechange-f.md) | 订阅指定卡槽位的网络状态变化事件，使用callback方式作为异步方法。 |
| [on_signalInfoChange](arkts-telephony-observer-onsignalinfochange-f.md) | 订阅信号状态变化事件，使用callback方式作为异步方法。 |
| [on_signalInfoChange](arkts-telephony-observer-onsignalinfochange-f.md) | 订阅指定卡槽位的信号状态变化事件，使用callback方式作为异步方法。 |
| [on_simStateChange](arkts-telephony-observer-onsimstatechange-f.md) | 订阅sim状态更改事件，使用callback方式作为异步方法。 |
| [on_simStateChange](arkts-telephony-observer-onsimstatechange-f.md) | 订阅指定卡槽位的sim状态更改事件，使用callback方式作为异步方法。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [offCellInfoChange](arkts-telephony-observer-offcellinfochange-f-sys.md) | Cancel callback when the cell information is updated. |
| [off_cellInfoChange](arkts-telephony-observer-offcellinfochange-f-sys.md) | 取消订阅小区信息变化事件，使用callback方式作为异步方法。 |
| [onCellInfoChange](arkts-telephony-observer-oncellinfochange-f-sys.md) | Callback when the cell information corresponding to the default sim card is updated. |
| [onCellInfoChange](arkts-telephony-observer-oncellinfochange-f-sys.md) | Callback when the cell information corresponding to a monitored {@code slotId} is updated. |
| [on_cellInfoChange](arkts-telephony-observer-oncellinfochange-f-sys.md) | 订阅小区信息变化事件，使用callback方式作为异步方法。 |
| [on_cellInfoChange](arkts-telephony-observer-oncellinfochange-f-sys.md) | 订阅指定卡槽位的小区信息变化事件，使用callback方式作为异步方法。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [CCallStateInfo](arkts-telephony-observer-ccallstateinfo-i.md) | 通话状态相关信息。 |
| [CallStateInfo](arkts-telephony-observer-callstateinfo-i.md) | 通话状态相关信息。 |
| [DataConnectionStateInfo](arkts-telephony-observer-dataconnectionstateinfo-i.md) | 数据连接状态相关信息。 |
| [ObserverOptions](arkts-telephony-observer-observeroptions-i.md) | 电话相关事件订阅参数可选项。 |
| [SimStateData](arkts-telephony-observer-simstatedata-i.md) | SIM卡类型和状态。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LockReason](arkts-telephony-observer-lockreason-e.md) | SIM卡锁类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CCallState](arkts-telephony-observer-ccallstate-t.md) | 运营商通话状态码。 |
| [CallState](arkts-telephony-observer-callstate-t.md) | 通话状态码。 |
| [CardType](arkts-telephony-observer-cardtype-t.md) | 卡类型。 |
| [DataConnectState](arkts-telephony-observer-dataconnectstate-t.md) | 描述蜂窝数据链路连接状态。 |
| [DataFlowType](arkts-telephony-observer-dataflowtype-t.md) | 描述蜂窝数据流类型。 |
| [NetworkState](arkts-telephony-observer-networkstate-t.md) | 网络注册状态。 |
| [RatType](arkts-telephony-observer-rattype-t.md) | 无线接入技术。 |
| [SignalInformation](arkts-telephony-observer-signalinformation-t.md) | 网络信号强度信息对象。 |
| [SimState](arkts-telephony-observer-simstate-t.md) | SIM卡状态。 |
| [TelCallState](arkts-telephony-observer-telcallstate-t.md) | 通话状态码。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CellInformation](arkts-telephony-observer-cellinformation-t-sys.md) | Describes current cell information. |
| [NetworkSearchRealTimeResult](arkts-telephony-observer-networksearchrealtimeresult-t-sys.md) | Callback when the network state corresponding to the default sim card is updated. |
<!--DelEnd-->

