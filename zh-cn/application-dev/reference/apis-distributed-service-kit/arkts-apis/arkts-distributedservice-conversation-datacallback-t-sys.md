# DataCallback（系统接口）

```TypeScript
type DataCallback = (networkId: string, msg: ArrayBuffer) => void
```

数据接收回调函数类型。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-conversation-type DataCallback = (networkId: string, msg: ArrayBuffer) => void--><!--Device-conversation-type DataCallback = (networkId: string, msg: ArrayBuffer) => void-End-->

**系统能力：** SystemCapability.Communication.SoftBus.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | 发送数据的源设备的networkId。  |
| msg | ArrayBuffer | 是 | 接收到的数据内容，为ArrayBuffer格式的二进制数据，数据格式与发送端发送的数据格式一致， 由应用层协议定义。  |

