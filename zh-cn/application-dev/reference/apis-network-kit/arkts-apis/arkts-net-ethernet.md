# @ohos.net.ethernet(以太网连接管理)

本模块提供以太网连接管理能力，包括有线网络能力、获取有线网络的IP地址等信息。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

## 导入模块

```TypeScript
import { ethernet } from '@kit.NetworkKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getMacAddress(以太网连接管理)](arkts-network-ethernet-getmacaddress-f.md) | 获取所有以太网网卡名称及对应网卡的MAC地址信息，使用Promise方式作为异步方法。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [disableEthernetInterface(以太网连接管理)](arkts-network-ethernet-disableethernetinterface-f-sys.md) | 禁用以太网接口。 |
| [enableEthernetInterface(以太网连接管理)](arkts-network-ethernet-enableethernetinterface-f-sys.md) | 启用以太网接口。 |
| [getAllActiveIfaces(以太网连接管理)](arkts-network-ethernet-getallactiveifaces-f-sys.md) | 获取活动的网络接口，使用callback异步回调。 |
| [getAllActiveIfaces(以太网连接管理)](arkts-network-ethernet-getallactiveifaces-f-sys.md) | 获取活动的网络接口，使用Promise异步回调。 |
| [getEthernetDeviceInfos(以太网连接管理)](arkts-network-ethernet-getethernetdeviceinfos-f-sys.md) | 获取本机以太网卡的设备信息（如供应商名称、产品名称、最大连接速率等）使用Promise异步回调。 |
| [getIfaceConfig(以太网连接管理)](arkts-network-ethernet-getifaceconfig-f-sys.md) | 获取指定网络接口信息，使用callback异步回调。 |
| [getIfaceConfig(以太网连接管理)](arkts-network-ethernet-getifaceconfig-f-sys.md) | 获取指定网络接口信息，使用Promise异步回调。 |
| [isEthernetEnabled(以太网连接管理)](arkts-network-ethernet-isethernetenabled-f-sys.md) | 检查全局以太网开关是否启用。 |
| [isIfaceActive(以太网连接管理)](arkts-network-ethernet-isifaceactive-f-sys.md) | 判断接口是否已激活，使用callback异步回调。 |
| [isIfaceActive(以太网连接管理)](arkts-network-ethernet-isifaceactive-f-sys.md) | 判断接口是否已激活，使用Promise异步回调。 |
| off(以太网连接管理) | 注销网卡热插拔事件，使用callback异步回调。 |
| on(以太网连接管理) | 注册网卡热插拔事件，使用callback异步回调。 |
| [setIfaceConfig(以太网连接管理)](arkts-network-ethernet-setifaceconfig-f-sys.md) | 设置网络接口配置信息，使用callback异步回调。 |
| [setIfaceConfig(以太网连接管理)](arkts-network-ethernet-setifaceconfig-f-sys.md) | 设置网络接口配置信息，使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [MacAddressInfo(以太网连接管理)](arkts-network-ethernet-macaddressinfo-i.md) | 以太网网卡名称及MAC地址信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EthernetDeviceInfos(以太网连接管理)](arkts-network-ethernet-ethernetdeviceinfos-i-sys.md) | 以太网设备信息。 |
| [InterfaceConfiguration(以太网连接管理)](arkts-network-ethernet-interfaceconfiguration-i-sys.md) | 以太网连接配置网络信息。 |
| [InterfaceStateInfo(以太网连接管理)](arkts-network-ethernet-interfacestateinfo-i-sys.md) | 监听以太网卡状态变化。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DeviceConnectionType(以太网连接管理)](arkts-network-ethernet-deviceconnectiontype-e-sys.md) | 以太网设备连接模式。 |
| [IPSetMode(以太网连接管理)](arkts-network-ethernet-ipsetmode-e-sys.md) | 以太网连接模式。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [HttpProxy(以太网连接管理)](arkts-network-ethernet-httpproxy-t.md) | 网络代理配置信息。 |
