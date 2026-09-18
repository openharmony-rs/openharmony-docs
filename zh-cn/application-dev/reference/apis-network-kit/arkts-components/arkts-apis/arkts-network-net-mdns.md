# @ohos.net.mdns(MDNS管理)

MDNS即多播DNS（Multicast DNS），提供局域网内的本地服务添加、移除、发现、解析等能力。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.MDNS

## 导入模块

```TypeScript
import { mdns } from '@kit.NetworkKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addLocalService](arkts-network-mdns-addlocalservice-f.md) | 添加一个MDNS服务，使用callback方式作为异步方法。 |
| [addLocalService](arkts-network-mdns-addlocalservice-f.md) | 添加一个MDNS服务，使用Promise方式作为异步方法。 |
| [createDiscoveryService](arkts-network-mdns-creatediscoveryservice-f.md) | 返回一个DiscoveryService对象，该对象用于发现指定服务类型（serviceType）的MDNS服务。 |
| [removeLocalService](arkts-network-mdns-removelocalservice-f.md) | 移除一个MDNS服务，使用callback方式作为异步方法。 |
| [removeLocalService](arkts-network-mdns-removelocalservice-f.md) | 移除一个MDNS服务，使用Promise方式作为异步方法。 |
| [resolveLocalService](arkts-network-mdns-resolvelocalservice-f.md) | 解析一个MDNS服务，使用callback方式作为异步方法。 |
| [resolveLocalService](arkts-network-mdns-resolvelocalservice-f.md) | 解析一个MDNS服务，使用Promise方式作为异步方法。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DiscoveryEventInfo](arkts-network-mdns-discoveryeventinfo-i.md) | 监听到的MDNS服务事件信息。 |
| [DiscoveryService](arkts-network-mdns-discoveryservice-i.md) | 指定服务类型的发现服务对象。 |
| [LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md) | MDNS服务信息。 |
| [ServiceAttribute](arkts-network-mdns-serviceattribute-i.md) | MDNS服务属性信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [MdnsError](arkts-network-mdns-mdnserror-e.md) | MDNS错误信息。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [NetAddress](arkts-network-mdns-netaddress-t.md) | 获取网络地址。 |
