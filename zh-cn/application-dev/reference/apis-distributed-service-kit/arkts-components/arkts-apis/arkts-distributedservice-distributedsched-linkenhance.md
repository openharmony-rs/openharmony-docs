# @ohos.distributedsched.linkEnhance(增强连接)

linkEnhance模块提供高效的蓝牙连接和数据传输功能，增强设备间连接的稳定性。使用多通道合并算法解决传统蓝牙连接不稳定、连接数量受限等问题，提升跨设备数据传输能力，改善用户使用体验。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { linkEnhance } from '@kit.DistributedServiceKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createConnection](arkts-distributedservice-linkenhance-createconnection-f.md) | 作为客户端的设备创建连接对象。创建Connection对象后，订阅on('connectResult')，然后调用connect()方法向服务端设备发起连接，连接成功后，可通过sendData()发送数据，当连接不需要使用，可调用close()销毁连接对象释放资源。 |
| [createServer](arkts-distributedservice-linkenhance-createserver-f.md) | 在服务端设备上，应用创建服务。通过start()开启后，该设备可作为服务端被其他设备连接。使用完毕后，需调用close()销毁Server对象释放资源。若需重新使用，需重新创建Server对象。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Connection](arkts-distributedservice-linkenhance-connection-i.md) | 连接对象，提供连接、断连、获取对端设备ID、发送数据、注册/取消注册回调等方法。 |
| [ConnectResult](arkts-distributedservice-linkenhance-connectresult-i.md) | 客户端调用connect()后，返回的连接结果。 |
| [Server](arkts-distributedservice-linkenhance-server-i.md) | 服务对象，提供启动服务、停止服务、关闭服务、注册/取消注册服务端回调等方法。 |
