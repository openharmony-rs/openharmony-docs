# @ohos.secureElement(安全单元的通道管理)

本模块主要用于操作及管理安全单元（SecureElement，简称SE），电子设备上可能存在的安全单元有eSE（Embedded SE）和SIM卡。文档中出现的SE服务为SEService实例，参见 [createService](arkts-connectivity-omapi-createservice-f.md)。对于文档中出现以下类型说明：  
| 类型 | 说明 | | ------- | ---------------------------------------------- | | Reader | 此类的实例表示该设备支持的SE，如果支持eSE、SIM和SIM2，则返回3个实例，其中SIM2从API version 22开始支持。 | | Session | 此类的实例表示在某个SE Reader实例上创建连接会话。 | | Channel | 此类的实例表示在某个Session实例上创建通道，可能为基础通道或逻辑通道。 |

**起始版本：** 10

**系统能力：** SystemCapability.Communication.SecureElement

## 导入模块

```TypeScript
import { omapi } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createService(安全单元的通道管理)](arkts-connectivity-omapi-createservice-f.md) | 建立一个可用于连接到系统中所有可用SE的新连接（服务）。连接过程较为耗时，所以此方法仅提供异步方式。使用Promise异步回调。仅当[isConnected](arkts-connectivity-omapi-seservice-i.md#isconnected)方法返回true时，该返回SEService对象是可用的。 |
| [newSEService(安全单元的通道管理)](arkts-connectivity-omapi-newseservice-f.md#newseserviceservicestate) | 建立一个可用于连接到系统中所有可用SE的新连接（服务）。连接过程较为耗时，所以此方法仅提供异步方式进行的。使用callback异步回调。仅当指定的回调或者当[isConnected](arkts-connectivity-omapi-seservice-i.md#isconnected)方法返回true时，该返回SEService对象是可用的。 |
| [off(安全单元的通道管理)](arkts-connectivity-omapi-off-f.md#offstatechanged) | 取消订阅服务状态更改事件。 |
| [on(安全单元的通道管理)](arkts-connectivity-omapi-on-f.md#onstatechanged) | 注册监听服务状态变化事件。调用[omapi.newSEService](arkts-connectivity-omapi-newseservice-f.md#newseserviceservicestate)或[omapi.createService](arkts-connectivity-omapi-createservice-f.md)创建服务成功后再用on接口注册回调。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Channel(安全单元的通道管理)](arkts-connectivity-omapi-channel-i.md) | Channel的实例表示在某个Session实例上创建通道，可能为基础通道或逻辑通道。通过 [Session.openBasicChannel](arkts-connectivity-omapi-session-i.md#openbasicchannel)或 [Session.openLogicalChannel](arkts-connectivity-omapi-session-i.md#openlogicalchannel)获取Channel实例。 |
| [Reader(安全单元的通道管理)](arkts-connectivity-omapi-reader-i.md) | Reader的实例表示该设备支持的SE，如果支持eSE、SIM和SIM2，则返回3个实例，其中SIM2从API version 22开始支持。通过 [SEService.getReaders](arkts-connectivity-omapi-seservice-i.md#getreaders)获取Reader实例。 |
| [SEService(安全单元的通道管理)](arkts-connectivity-omapi-seservice-i.md) | SEService表示可用于连接到系统中所有可用SE的连接（服务），通过[createService](arkts-connectivity-omapi-createservice-f.md)获取SEService实例。 |
| [Session(安全单元的通道管理)](arkts-connectivity-omapi-session-i.md) | Session的实例表示在某个SE Reader实例上创建连接会话。通过[Reader.openSession](arkts-connectivity-omapi-reader-i.md#opensession)获取Session实例。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ServiceState(安全单元的通道管理)](arkts-connectivity-omapi-servicestate-e.md) | 定义不同的SE服务状态值。 |
