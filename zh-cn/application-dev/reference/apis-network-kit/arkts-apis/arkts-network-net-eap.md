# @ohos.net.eap(扩展认证)

该模块提供了第三方客户端接入802.1X认证（一种基于端口的网络接入控制协议）流程的机制，支撑客户端的定制认证等功能。

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Eap

## 导入模块

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [logOffEthEap](arkts-network-eap-logoffetheap-f.md) | 该接口用于指定一个以太网卡从EAP已认证状态退出。 |
| [regCustomEapHandler](arkts-network-eap-regcustomeaphandler-f.md) | 用于指定需要定制化处理的EAP报文类型和对应的处理callback。使用callback异步回调。 |
| [replyCustomEapData](arkts-network-eap-replycustomeapdata-f.md) | 该接口用于通知系统已完成该步定制化处理。 |
| [startEthEap](arkts-network-eap-startetheap-f.md) | 该接口用于指定一个以太网卡发起EAP认证。 |
| [unregCustomEapHandler](arkts-network-eap-unregcustomeaphandler-f.md) | 用于指定需要取消定制化处理的EAP报文类型和对应的处理callback。使用callback异步回调。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [EapData](arkts-network-eap-eapdata-i.md) | EAP信息。 |
| [EthEapProfile](arkts-network-eap-etheapprofile-i.md) | 可扩展身份验证协议配置信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CustomResult](arkts-network-eap-customresult-e.md) | 表示EAP认证处理结果的枚举。 |
| [EapMethod](arkts-network-eap-eapmethod-e.md) | 表示EAP认证方式的枚举。 |
| [Phase2Method](arkts-network-eap-phase2method-e.md) | 表示第二阶段认证方式的枚举。 |
