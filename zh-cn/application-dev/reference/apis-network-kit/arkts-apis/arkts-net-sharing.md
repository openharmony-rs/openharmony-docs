# @ohos.net.sharing

网络共享管理模块用于将设备网络连接共享给其他连接设备。

**起始版本：** 23

<!--Device-unnamed-declare namespace sharing--><!--Device-unnamed-declare namespace sharing-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

## 导入模块

```TypeScript
import { sharing } from '@kit.NetworkKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getSharableRegexes](arkts-network-sharing-getsharableregexes-f-sys.md) | 获取指定类型网卡名称正则表达式列表，使用 callback 异步回调。 |
| [getSharableRegexes](arkts-network-sharing-getsharableregexes-f-sys.md) | 获取指定类型网卡名称正则表达式列表，使用 Promise 异步回调。 |
| [getSharingIfaces](arkts-network-sharing-getsharingifaces-f-sys.md) | 获取指定状态的网卡名称列表，使用 callback 异步回调。 |
| [getSharingIfaces](arkts-network-sharing-getsharingifaces-f-sys.md) | 获取指定状态的网卡名称列表，使用 Promise 异步回调。 |
| [getSharingState](arkts-network-sharing-getsharingstate-f-sys.md) | 获取指定类型网络共享状态，使用 callback 异步回调。 |
| [getSharingState](arkts-network-sharing-getsharingstate-f-sys.md) | 获取指定类型网络共享状态，使用 Promise 异步回调。 |
| [getStatsRxBytes](arkts-network-sharing-getstatsrxbytes-f-sys.md) | 获取共享网络接收数据量，使用 callback 异步回调。 |
| [getStatsRxBytes](arkts-network-sharing-getstatsrxbytes-f-sys.md) | 获取共享网络接收数据量，使用 Promise 异步回调。 |
| [getStatsTotalBytes](arkts-network-sharing-getstatstotalbytes-f-sys.md) | 获取共享网络总数据量，使用 callback 异步回调。 |
| [getStatsTotalBytes](arkts-network-sharing-getstatstotalbytes-f-sys.md) | 获取共享网络总数据量，使用 Promise 异步回调。 |
| [getStatsTxBytes](arkts-network-sharing-getstatstxbytes-f-sys.md) | 获取共享网络发送数据量，使用 callback 异步回调。 |
| [getStatsTxBytes](arkts-network-sharing-getstatstxbytes-f-sys.md) | 获取共享网络发送数据量，使用 Promise 异步回调。 |
| [isSharing](arkts-network-sharing-issharing-f-sys.md) | 获取当前网络共享状态，使用 callback 异步回调。 |
| [isSharing](arkts-network-sharing-issharing-f-sys.md) | 获取当前网络共享状态，使用 Promise 异步回调。 |
| [isSharingSupported](arkts-network-sharing-issharingsupported-f-sys.md) | 判断是否支持网络共享，使用 callback 异步回调。 |
| [isSharingSupported](arkts-network-sharing-issharingsupported-f-sys.md) | 判断是否支持网络共享，使用 Promise 异步回调。 |
| [off_interfaceSharingStateChange](arkts-network-sharing-offinterfacesharingstatechange-f-sys.md#offinterfacesharingstatechange) | 注销网卡网络共享状态变化事件，使用 callback 异步回调。 |
| [off_sharingStateChange](arkts-network-sharing-offsharingstatechange-f-sys.md#offsharingstatechange) | 注销网络共享状态变化事件，使用 callback 异步回调。 |
| [off_sharingUpstreamChange](arkts-network-sharing-offsharingupstreamchange-f-sys.md#offsharingupstreamchange) | 注销上行网络变化事件，使用 callback 异步回调。 |
| [on_interfaceSharingStateChange](arkts-network-sharing-oninterfacesharingstatechange-f-sys.md#oninterfacesharingstatechange) | 注册网卡网络共享状态变化事件，使用 callback 异步回调。 |
| [on_sharingStateChange](arkts-network-sharing-onsharingstatechange-f-sys.md#onsharingstatechange) | 注册网络共享状态变化事件，使用 callback 异步回调。 |
| [on_sharingUpstreamChange](arkts-network-sharing-onsharingupstreamchange-f-sys.md#onsharingupstreamchange) | 注册上行网络变化事件，使用 callback 异步回调。 |
| [startSharing](arkts-network-sharing-startsharing-f-sys.md) | 开启指定类型共享，使用 callback 异步回调。 |
| [startSharing](arkts-network-sharing-startsharing-f-sys.md) | 开启指定类型共享，使用 Promise 异步回调。 |
| [stopSharing](arkts-network-sharing-stopsharing-f-sys.md) | 关闭指定类型共享，使用 callback 异步回调。 |
| [stopSharing](arkts-network-sharing-stopsharing-f-sys.md) | 关闭指定类型共享，使用 Promise 异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [InterfaceSharingStateInfo](arkts-network-sharing-interfacesharingstateinfo-i-sys.md) | 唤醒在网络共享模式下的变化时的监听器。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SharingIfaceState](arkts-network-sharing-sharingifacestate-e-sys.md) | 网络共享状态。 |
| [SharingIfaceType](arkts-network-sharing-sharingifacetype-e-sys.md) | 网络共享类型。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [NetHandle](arkts-network-sharing-nethandle-t.md) | 数据网络的句柄。在调用NetHandle的方法之前，需要先获取NetHandle对象。 |

