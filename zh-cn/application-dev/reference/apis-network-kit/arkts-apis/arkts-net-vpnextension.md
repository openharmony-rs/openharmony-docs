# @ohos.net.vpnExtension

三方VPN管理模块，支持三方VPN的启动和停止功能。三方VPN是指由第三方提供的VPN服务，它们通常提供更多的功能和更广泛的网络连接选项，包括更多的安全和隐私功能，以及更全面的定制选项。当前提供三方VPN能力主要用于创建虚拟网卡及配置 VPN路由信息，连接隧道过程及内部连接的协议需要应用内部自行实现。 > **说明：** > > 本模块首批接口从 API version 11 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 > 以下模块不支持在VpnExtensionAbility中引用，可能会导致程序异常退出。 > - [@ohos.contact (联系人)](../../apis-contacts-kit/arkts-apis/arkts-contact.md) > - @ohos.geolocation、 > @ohos.geoLocationManager (位置服务) > - [@ohos.multimedia.audio(音频管理)](../../apis-audio-kit/arkts-apis/arkts-multimedia-audio.md) > - [@ohos.multimedia.camera(相机管理)](../../apis-camera-kit/arkts-apis/arkts-multimedia-camera.md) > - [@ohos.telephony.call (拨打电话)](../../apis-telephony-kit/arkts-apis/arkts-telephony-call.md) > - [@ohos.telephony.sim (SIM卡管理)](../../apis-telephony-kit/arkts-apis/arkts-telephony-sim.md) > - [@ohos.telephony.sms (短信服务)](../../apis-telephony-kit/arkts-apis/arkts-telephony-sms.md)

**起始版本：** 11

<!--Device-unnamed-declare namespace vpnExtension--><!--Device-unnamed-declare namespace vpnExtension-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## 导入模块

```TypeScript
import { vpnExtension } from '@kit.NetworkKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createVpnConnection](arkts-network-vpnextension-createvpnconnection-f.md) | 创建一个三方VPN连接对象。 |
| [createVpnObserver](arkts-network-vpnextension-createvpnobserver-f.md) | 创建一个VPN观察者对象。用于监听VPN相关事件。 |
| [startVpnExtensionAbility](arkts-network-vpnextension-startvpnextensionability-f.md) | 启动新的三方VPN功能。使用Promise异步回调。 |
| [stopVpnExtensionAbility](arkts-network-vpnextension-stopvpnextensionability-f.md) | 停止同一应用程序中的服务。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [isAlwaysOnVpnEnabled](arkts-network-vpnextension-isalwaysonvpnenabled-f-sys.md) | 获取always on VPN开关状态。使用Promise异步回调。 |
| [setAlwaysOnVpnEnabled](arkts-network-vpnextension-setalwaysonvpnenabled-f-sys.md) | 设置设备的启用/禁用always on VPN模式。使用Promise异步回调。 |
| [updateVpnAuthorizedState](arkts-network-vpnextension-updatevpnauthorizedstate-f-sys.md) | 更新VPN对话框授权信息。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [VpnConfig](arkts-network-vpnextension-vpnconfig-i.md) | 三方VPN配置参数。 |
| [VpnConnection](arkts-network-vpnextension-vpnconnection-i.md) | VPN连接对象。在调用VpnConnection的方法前，需要先通过vpnExt.createVpnConnection创建VPN连接对象。 |
| [VpnObserver](arkts-network-vpnextension-vpnobserver-i.md) | VPN观察者对象。用于监听VPN相关事件。在调用VpnObserver的方法前，需要先通过[vpnExtension.createVpnObserver](arkts-network-vpnextension-createvpnobserver-f.md) 创建VPN连接对象。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [LinkAddress](arkts-network-vpnextension-linkaddress-t.md) | 获取网络链接信息。 |
| [RouteInfo](arkts-network-vpnextension-routeinfo-t.md) | 获取网络路由信息。 |
| [VpnExtensionContext](arkts-network-vpnextension-vpnextensioncontext-t.md) | VPN扩展的上下文。它允许访问serviceExtension特定资源。 |

