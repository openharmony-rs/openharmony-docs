# @ohos.net.policy (网络策略管理)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

本模块提供网络策略管理能力，采用防火墙技术对用户使用数据流量进行控制管理。

> **说明：**
>
> 本模块首批接口从 API version 10 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```ts
import { policy } from '@kit.NetworkKit';
```

## NetBearType

type NetBearType = connection.NetBearType

网络类型。

**系统能力**：SystemCapability.Communication.NetManager.Core

| 类型   | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| [connection.NetBearType](./js-apis-net-connection.md#netbeartype) | 网络类型。 |



