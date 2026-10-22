# @ohos.telephony.observer(电话服务状态监听)

本模块提供订阅管理功能，可以订阅/取消订阅的事件包括：网络状态变化、信号状态变化、通话状态变化、蜂窝数据链路连接状态、蜂窝数据业务的上下行数据流状态、SIM状态变化。

**起始版本：** 6

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
| [off('networkStateChange')](arkts-telephony-observer-off-f.md#offnetworkstatechange) | 取消订阅网络状态变化事件，使用callback方式作为异步方法。 |
| [off('signalInfoChange')](arkts-telephony-observer-off-f.md#offsignalinfochange) | 取消订阅信号状态变化事件，使用callback方式作为异步方法。 |
| [off('cellularDataConnectionStateChange')](arkts-telephony-observer-off-f.md#offcellulardataconnectionstatechange) | 移除订阅蜂窝数据链路连接状态，使用callback方式作为异步方法。 |
| [off('cellularDataFlowChange')](arkts-telephony-observer-off-f.md#offcellulardataflowchange) | 移除订阅蜂窝数据业务的上下行数据流状态，使用callback方式作为异步方法。 |
| [off('callStateChange')](arkts-telephony-observer-off-f.md#offcallstatechange) | 取消订阅通话状态变化事件，使用callback方式作为异步方法。 |
| [off('callStateChangeEx')](arkts-telephony-observer-off-f.md#offcallstatechangeex) | 取消订阅通话状态变化拓展事件，使用callback方式作为异步方法。 |
| [off('simStateChange')](arkts-telephony-observer-off-f.md#offsimstatechange) | 移除订阅sim状态更改事件，使用callback方式作为异步方法。 |
| [off('iccAccountInfoChange')](arkts-telephony-observer-off-f.md#officcaccountinfochange) | 移除订阅卡帐户变化事件，使用callback方式作为异步方法。 |
| [offCCallStateChange](arkts-telephony-observer-offccallstatechange-f.md#offccallstatechange-1) | 取消监听运营商通话状态的回调 |
| [offCommunicationStateChange](arkts-telephony-observer-offcommunicationstatechange-f.md#offcommunicationstatechange-1) | 取消订阅5A网络状态变化事件，使用callback异步回调。 |
| [offGetSimActiveState](arkts-telephony-observer-offgetsimactivestate-f.md#offgetsimactivestate-1) | 取消SIM卡激活状态变化的监听，使用callback方式作为异步方法。 |
| [offVoIPStateChange](arkts-telephony-observer-offvoipstatechange-f.md#offvoipstatechange-1) | VoIP通话状态更新时取消回调。 |
| [on('networkStateChange')](arkts-telephony-observer-on-f.md#onnetworkstatechange) | 订阅网络状态变化事件，使用callback方式作为异步方法。 |
| [on('networkStateChange')](arkts-telephony-observer-on-f.md#onnetworkstatechange) | 订阅指定卡槽位的网络状态变化事件，使用callback方式作为异步方法。 |
| [on('signalInfoChange')](arkts-telephony-observer-on-f.md#onsignalinfochange) | 订阅信号状态变化事件，使用callback方式作为异步方法。 |
| [on('signalInfoChange')](arkts-telephony-observer-on-f.md#onsignalinfochange) | 订阅指定卡槽位的信号状态变化事件，使用callback方式作为异步方法。 |
| [on('cellularDataConnectionStateChange')](arkts-telephony-observer-on-f.md#oncellulardataconnectionstatechange) | 订阅蜂窝数据链路连接状态，使用callback方式作为异步方法。 |
| [on('cellularDataConnectionStateChange')](arkts-telephony-observer-on-f.md#oncellulardataconnectionstatechange) | 订阅指定卡槽位的蜂窝数据链路连接状态，使用callback方式作为异步方法。 |
| [on('cellularDataFlowChange')](arkts-telephony-observer-on-f.md#oncellulardataflowchange) | 订阅蜂窝数据业务的上下行数据流状态，使用callback方式作为异步方法。 |
| [on('cellularDataFlowChange')](arkts-telephony-observer-on-f.md#oncellulardataflowchange) | 订阅指定卡槽位的蜂窝数据业务的上下行数据流状态，使用callback方式作为异步方法。 |
| [on('callStateChange')](arkts-telephony-observer-on-f.md#oncallstatechange) | 订阅通话状态变化事件，使用callback方式作为异步方法。 |
| [on('callStateChange')](arkts-telephony-observer-on-f.md#oncallstatechange) | 订阅通话状态变化事件，使用callback方式作为异步方法。 |
| [on('callStateChangeEx')](arkts-telephony-observer-on-f.md#oncallstatechangeex) | 订阅通话状态变化拓展事件，使用callback方式作为异步方法。 |
| [on('simStateChange')](arkts-telephony-observer-on-f.md#onsimstatechange) | 订阅sim状态更改事件，使用callback方式作为异步方法。 |
| [on('simStateChange')](arkts-telephony-observer-on-f.md#onsimstatechange) | 订阅指定卡槽位的sim状态更改事件，使用callback方式作为异步方法。 |
| [on('iccAccountInfoChange')](arkts-telephony-observer-on-f.md#oniccaccountinfochange) | 订阅卡帐户变化事件，使用callback方式作为异步方法。 |
| [onCCallStateChange](arkts-telephony-observer-onccallstatechange-f.md#onccallstatechange-1) | 运营商通话状态变更时回调 |
| [onCommunicationStateChange](arkts-telephony-observer-oncommunicationstatechange-f.md#oncommunicationstatechange-1) | 订阅5A网络状态变化事件，使用callback异步回调。 |
| [onGetSimActiveState](arkts-telephony-observer-ongetsimactivestate-f.md#ongetsimactivestate-1) | SIM卡激活状态变化的监听，使用callback方式作为异步方法。 |
| [onVoIPStateChange](arkts-telephony-observer-onvoipstatechange-f.md#onvoipstatechange-1) | VoIP通话状态更新时的回调。此回调在以下情况下被调用第三方VoIP应用程序的呼叫状态发生变化，并添加了观察者来监控更新。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [off('cellInfoChange')](arkts-telephony-observer-off-f-sys.md#offcellinfochange) | 取消订阅小区信息变化事件，使用callback方式作为异步方法。 |
| [on('cellInfoChange')](arkts-telephony-observer-on-f-sys.md#oncellinfochange) | 订阅小区信息变化事件，使用callback方式作为异步方法。 |
| [on('cellInfoChange')](arkts-telephony-observer-on-f-sys.md#oncellinfochange) | 订阅指定卡槽位的小区信息变化事件，使用callback方式作为异步方法。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [CallStateInfo](arkts-telephony-observer-callstateinfo-i.md) | 运营商通话状态及号码 |
| [CCallStateInfo](arkts-telephony-observer-ccallstateinfo-i.md) | 通话状态相关信息。 |
| [DataConnectionStateInfo](arkts-telephony-observer-dataconnectionstateinfo-i.md) | 数据连接状态相关信息。 |
| [ObserverOptions](arkts-telephony-observer-observeroptions-i.md) | 电话相关事件订阅参数可选项。 |
| [SimStateData](arkts-telephony-observer-simstatedata-i.md) | SIM卡类型和状态。 |
| [VoIPCallStateInfo](arkts-telephony-observer-voipcallstateinfo-i.md) | VoIP呼叫状态信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CallState](arkts-telephony-observer-callstate-t.md) | 通话状态码。 |
| [CardType](arkts-telephony-observer-cardtype-t.md) | 卡类型。 |
| [CCallState](arkts-telephony-observer-ccallstate-t.md) | 运营商通话状态 |
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

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LockReason](arkts-telephony-observer-lockreason-e.md) | SIM卡锁类型。 |
| [VoIPCallState](arkts-telephony-observer-voipcallstate-e.md) | VoIP呼叫状态枚举。 |
| [VoIPCallType](arkts-telephony-observer-voipcalltype-e.md) | VoIP呼叫类型枚举。 |
