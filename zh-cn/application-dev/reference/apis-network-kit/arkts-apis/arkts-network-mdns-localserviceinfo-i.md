# LocalServiceInfo

MDNS服务信息。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.MDNS

## 导入模块

```TypeScript
import { mdns } from '@kit.NetworkKit';
```

## host

```TypeScript
host?: NetAddress
```

MDNS服务设备的IP地址。采用设备的IP，添加服务和移除服务时候不生效。

**类型：** NetAddress

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.MDNS

## port

```TypeScript
port?: number
```

MDNS服务的端口号。取值范围[0，65535]。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.MDNS

## serviceAttribute

```TypeScript
serviceAttribute?: Array<ServiceAttribute>
```

MDNS服务属性信息。

**类型：** Array&lt;[ServiceAttribute](arkts-network-mdns-serviceattribute-i.md)&gt;

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.MDNS

## serviceName

```TypeScript
serviceName: string
```

MDNS服务的名字。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.MDNS

## serviceType

```TypeScript
serviceType: string
```

MDNS服务的类型。格式：_&lt;name&gt;.&lt;_tcp/_udp&gt;，name长度小于63字符并且不能包含字符'.'。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.MDNS
