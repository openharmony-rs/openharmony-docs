# @ohos.telephony.observer(电话服务状态监听)

本模块提供订阅管理功能，可以订阅/取消订阅的事件包括：网络状态变化、信号状态变化、通话状态变化、蜂窝数据链路连接状态、蜂窝数据业务的上下行数据流状态、SIM状态变化。

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.StateRegistry

## 导入模块

```TypeScript
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [off(电话服务状态监听)](arkts-telephony-observer-off-f.md#offnetworkstatechange) | 取消订阅网络状态变化事件，使用callback方式作为异步方法。 |
| [off(电话服务状态监听)](arkts-telephony-observer-off-f.md#offsignalinfochange) | 取消订阅信号状态变化事件，使用callback方式作为异步方法。 |
| [off(电话服务状态监听)](arkts-telephony-observer-off-f.md#offcellulardataconnectionstatechange) | 移除订阅蜂窝数据链路连接状态，使用callback方式作为异步方法。 |
| [off(电话服务状态监听)](arkts-telephony-observer-off-f.md#offcellulardataflowchange) | 移除订阅蜂窝数据业务的上下行数据流状态，使用callback方式作为异步方法。 |
| [off(电话服务状态监听)](arkts-telephony-observer-off-f.md#offcallstatechange) | 取消订阅通话状态变化事件，使用callback方式作为异步方法。 |
| [off(电话服务状态监听)](arkts-telephony-observer-off-f.md#offcallstatechangeex) | 取消订阅通话状态变化拓展事件，使用callback方式作为异步方法。 |
| [off(电话服务状态监听)](arkts-telephony-observer-off-f.md#offsimstatechange) | 移除订阅sim状态更改事件，使用callback方式作为异步方法。 |
| [off(电话服务状态监听)](arkts-telephony-observer-off-f.md#officcaccountinfochange) | 移除订阅卡帐户变化事件，使用callback方式作为异步方法。 |
| [offCCallStateChange(电话服务状态监听)](arkts-telephony-observer-offccallstatechange-f.md) | 取消三方应用监听运营商通话状态并获取通话号码，使用callback方式作为异步方法。 |
| [offCommunicationStateChange(电话服务状态监听)](arkts-telephony-observer-offcommunicationstatechange-f.md) | 取消订阅5A网络状态变化事件，使用callback异步回调。 |
| [offGetSimActiveState(电话服务状态监听)](arkts-telephony-observer-offgetsimactivestate-f.md) | 取消SIM卡激活状态变化的监听，使用callback方式作为异步方法。 |
| [on(电话服务状态监听)](arkts-telephony-observer-on-f.md#onnetworkstatechange) | 订阅网络状态变化事件，使用callback方式作为异步方法。 |
| [on(电话服务状态监听)](arkts-telephony-observer-on-f.md#onnetworkstatechange) | 订阅指定卡槽位的网络状态变化事件，使用callback方式作为异步方法。 |
| [on(电话服务状态监听)](arkts-telephony-observer-on-f.md#onsignalinfochange) | 订阅信号状态变化事件，使用callback方式作为异步方法。 |
| [on(电话服务状态监听)](arkts-telephony-observer-on-f.md#onsignalinfochange) | 订阅指定卡槽位的信号状态变化事件，使用callback方式作为异步方法。 |
| [on(电话服务状态监听)](arkts-telephony-observer-on-f.md#oncellulardataconnectionstatechange) | 订阅蜂窝数据链路连接状态，使用callback方式作为异步方法。 |
| [on(电话服务状态监听)](arkts-telephony-observer-on-f.md#oncellulardataconnectionstatechange) | 订阅指定卡槽位的蜂窝数据链路连接状态，使用callback方式作为异步方法。 |
| [on(电话服务状态监听)](arkts-telephony-observer-on-f.md#oncellulardataflowchange) | 订阅蜂窝数据业务的上下行数据流状态，使用callback方式作为异步方法。 |
| [on(电话服务状态监听)](arkts-telephony-observer-on-f.md#oncellulardataflowchange) | 订阅指定卡槽位的蜂窝数据业务的上下行数据流状态，使用callback方式作为异步方法。 |
| [on(电话服务状态监听)](arkts-telephony-observer-on-f.md#oncallstatechange) | 订阅通话状态变化事件，使用callback方式作为异步方法。 |
| [on(电话服务状态监听)](arkts-telephony-observer-on-f.md#oncallstatechange) | 订阅通话状态变化事件，使用callback方式作为异步方法。 |
| [on(电话服务状态监听)](arkts-telephony-observer-on-f.md#oncallstatechangeex) | 订阅通话状态变化拓展事件，使用callback方式作为异步方法。 |
| [on(电话服务状态监听)](arkts-telephony-observer-on-f.md#onsimstatechange) | 订阅sim状态更改事件，使用callback方式作为异步方法。 |
| [on(电话服务状态监听)](arkts-telephony-observer-on-f.md#onsimstatechange) | 订阅指定卡槽位的sim状态更改事件，使用callback方式作为异步方法。 |
| [on(电话服务状态监听)](arkts-telephony-observer-on-f.md#oniccaccountinfochange) | 订阅卡帐户变化事件，使用callback方式作为异步方法。 |
| [onCCallStateChange(电话服务状态监听)](arkts-telephony-observer-onccallstatechange-f.md) | 三方应用监听运营商通话状态并获取通话号码，使用callback方式作为异步方法。 |
| [onCommunicationStateChange(电话服务状态监听)](arkts-telephony-observer-oncommunicationstatechange-f.md) | 订阅5A网络状态变化事件，使用callback异步回调。 |
| [onGetSimActiveState(电话服务状态监听)](arkts-telephony-observer-ongetsimactivestate-f.md) | SIM卡激活状态变化的监听，使用callback方式作为异步方法。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| off(电话服务状态监听) | 取消订阅小区信息变化事件，使用callback方式作为异步方法。 |
| on(电话服务状态监听) | 订阅小区信息变化事件，使用callback方式作为异步方法。 |
| on(电话服务状态监听) | 订阅指定卡槽位的小区信息变化事件，使用callback方式作为异步方法。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [CallStateInfo(电话服务状态监听)](arkts-telephony-observer-callstateinfo-i.md) | 通话状态相关信息。 |
| [CCallStateInfo(电话服务状态监听)](arkts-telephony-observer-ccallstateinfo-i.md) | 通话状态相关信息。 |
| [DataConnectionStateInfo(电话服务状态监听)](arkts-telephony-observer-dataconnectionstateinfo-i.md) | 数据连接状态相关信息。 |
| [ObserverOptions(电话服务状态监听)](arkts-telephony-observer-observeroptions-i.md) | 电话相关事件订阅参数可选项。 |
| [SimStateData(电话服务状态监听)](arkts-telephony-observer-simstatedata-i.md) | SIM卡类型和状态。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LockReason(电话服务状态监听)](arkts-telephony-observer-lockreason-e.md) | SIM卡锁类型。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CallState(电话服务状态监听)](arkts-telephony-observer-callstate-t.md) | 通话状态码。 |
| [CardType(电话服务状态监听)](arkts-telephony-observer-cardtype-t.md) | 卡类型。 |
| [CCallState(电话服务状态监听)](arkts-telephony-observer-ccallstate-t.md) | 运营商通话状态码。 |
| [DataConnectState(电话服务状态监听)](arkts-telephony-observer-dataconnectstate-t.md) | 描述蜂窝数据链路连接状态。 |
| [DataFlowType(电话服务状态监听)](arkts-telephony-observer-dataflowtype-t.md) | 描述蜂窝数据流类型。 |
| [NetworkState(电话服务状态监听)](arkts-telephony-observer-networkstate-t.md) | 网络注册状态。 |
| [RatType(电话服务状态监听)](arkts-telephony-observer-rattype-t.md) | 无线接入技术。 |
| [SignalInformation(电话服务状态监听)](arkts-telephony-observer-signalinformation-t.md) | 网络信号强度信息对象。 |
| [SimState(电话服务状态监听)](arkts-telephony-observer-simstate-t.md) | SIM卡状态。 |
| [TelCallState(电话服务状态监听)](arkts-telephony-observer-telcallstate-t.md) | 通话状态码。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [CellInformation(电话服务状态监听)](arkts-telephony-observer-cellinformation-t-sys.md) | Describes current cell information. |
| [NetworkSearchRealTimeResult(电话服务状态监听)](arkts-telephony-observer-networksearchrealtimeresult-t-sys.md) | Callback when the network state corresponding to the default sim card is updated. |
<!--DelEnd-->
