# @ohos.distributedsched.linkEnhance

linkEnhance模块提供高效的蓝牙连接和数据传输功能，增强设备间连接的稳定性。使用多通道合并算法，增加设备间连接数，提升跨设备数据传输能力，改善用户使用体验。

**起始版本：** 20

<!--Device-unnamed-declare namespace linkEnhance--><!--Device-unnamed-declare namespace linkEnhance-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createConnection](arkts-distributedservice-linkenhance-createconnection-f.md#createconnection-1) | 作为客户端的设备创建连接对象，以便后续向服务端设备发起连接。 |
| [createServer](arkts-distributedservice-linkenhance-createserver-f.md#createserver-1) | 在服务端设备上，应用创建服务。通过start()开启后，该设备可作为服务端被其他设备连接。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConnectResult](arkts-distributedservice-linkenhance-connectresult-i.md) | 客户端调用connect()后，返回的连接结果。 |
| [Connection](arkts-distributedservice-linkenhance-connection-i.md) | 连接对象，提供连接、断连、获取对端设备ID、发送数据、注册/取消注册回调等方法。 |
| [Server](arkts-distributedservice-linkenhance-server-i.md) | 服务对象，提供启动服务、停止服务、关闭服务、注册/取消注册服务端回调等方法。 |

