# @ohos.net.sharing(网络共享管理)

网络共享管理模块用于将设备网络连接共享给其他连接设备。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

## 导入模块

```TypeScript
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getSharableRegexes(网络共享管理)](arkts-network-sharing-getsharableregexes-f-sys.md) | 获取指定类型网卡名称正则表达式列表，使用 callback 异步回调。 |
| [getSharableRegexes(网络共享管理)](arkts-network-sharing-getsharableregexes-f-sys.md) | 获取指定类型网卡名称正则表达式列表，使用 Promise 异步回调。 |
| [getSharingIfaces(网络共享管理)](arkts-network-sharing-getsharingifaces-f-sys.md) | 获取指定状态的网卡名称列表，使用 callback 异步回调。 |
| [getSharingIfaces(网络共享管理)](arkts-network-sharing-getsharingifaces-f-sys.md) | 获取指定状态的网卡名称列表，使用 Promise 异步回调。 |
| [getSharingState(网络共享管理)](arkts-network-sharing-getsharingstate-f-sys.md) | 获取指定类型网络共享状态，使用 callback 异步回调。 |
| [getSharingState(网络共享管理)](arkts-network-sharing-getsharingstate-f-sys.md) | 获取指定类型网络共享状态，使用 Promise 异步回调。 |
| [getStatsRxBytes(网络共享管理)](arkts-network-sharing-getstatsrxbytes-f-sys.md) | 获取共享网络接收数据量，使用 callback 异步回调。 |
| [getStatsRxBytes(网络共享管理)](arkts-network-sharing-getstatsrxbytes-f-sys.md) | 获取共享网络接收数据量，使用 Promise 异步回调。 |
| [getStatsTotalBytes(网络共享管理)](arkts-network-sharing-getstatstotalbytes-f-sys.md) | 获取共享网络总数据量，使用 callback 异步回调。 |
| [getStatsTotalBytes(网络共享管理)](arkts-network-sharing-getstatstotalbytes-f-sys.md) | 获取共享网络总数据量，使用 Promise 异步回调。 |
| [getStatsTxBytes(网络共享管理)](arkts-network-sharing-getstatstxbytes-f-sys.md) | 获取共享网络发送数据量，使用 callback 异步回调。 |
| [getStatsTxBytes(网络共享管理)](arkts-network-sharing-getstatstxbytes-f-sys.md) | 获取共享网络发送数据量，使用 Promise 异步回调。 |
| [isSharing(网络共享管理)](arkts-network-sharing-issharing-f-sys.md) | 获取当前网络共享状态，使用 callback 异步回调。 |
| [isSharing(网络共享管理)](arkts-network-sharing-issharing-f-sys.md) | 获取当前网络共享状态，使用 Promise 异步回调。 |
| [isSharingSupported(网络共享管理)](arkts-network-sharing-issharingsupported-f-sys.md) | 判断是否支持网络共享，使用 callback 异步回调。 |
| [isSharingSupported(网络共享管理)](arkts-network-sharing-issharingsupported-f-sys.md) | 判断是否支持网络共享，使用 Promise 异步回调。 |
| off(网络共享管理) | 注销网络共享状态变化事件，使用 callback 异步回调。 |
| off(网络共享管理) | 注销网卡网络共享状态变化事件，使用 callback 异步回调。 |
| off(网络共享管理) | 注销上行网络变化事件，使用 callback 异步回调。 |
| on(网络共享管理) | 注册网络共享状态变化事件，使用 callback 异步回调。 |
| on(网络共享管理) | 注册网卡网络共享状态变化事件，使用 callback 异步回调。 |
| on(网络共享管理) | 注册上行网络变化事件，使用 callback 异步回调。 |
| [startSharing(网络共享管理)](arkts-network-sharing-startsharing-f-sys.md) | 开启指定类型共享，使用 callback 异步回调。 |
| [startSharing(网络共享管理)](arkts-network-sharing-startsharing-f-sys.md) | 开启指定类型共享，使用 Promise 异步回调。 |
| [stopSharing(网络共享管理)](arkts-network-sharing-stopsharing-f-sys.md) | 关闭指定类型共享，使用 callback 异步回调。 |
| [stopSharing(网络共享管理)](arkts-network-sharing-stopsharing-f-sys.md) | 关闭指定类型共享，使用 Promise 异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [InterfaceSharingStateInfo(网络共享管理)](arkts-network-sharing-interfacesharingstateinfo-i-sys.md) | 唤醒在网络共享模式下的变化时的监听器。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SharingIfaceState(网络共享管理)](arkts-network-sharing-sharingifacestate-e-sys.md) | 网络共享状态。 |
| [SharingIfaceType(网络共享管理)](arkts-network-sharing-sharingifacetype-e-sys.md) | 网络共享类型。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [NetHandle(网络共享管理)](arkts-network-sharing-nethandle-t.md) | 数据网络的句柄。在调用NetHandle的方法之前，需要先获取NetHandle对象。 |
