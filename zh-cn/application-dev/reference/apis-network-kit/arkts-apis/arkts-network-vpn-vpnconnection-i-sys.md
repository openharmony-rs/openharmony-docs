# VpnConnection（系统接口）

VPN 连接对象。在调用 VpnConnection 的方法前，需要先通过[vpn.createVpnConnection](arkts-network-vpn-createvpnconnection-f-sys.md)创建 VPN 连接对象。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { vpn } from '@kit.NetworkKit';
```

## destroy

```TypeScript
destroy(callback: AsyncCallback<void>): void
```

销毁启动的 VPN 网络，使用 callback 方式作为异步方法。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_VPN

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，成功时，error 为 undefined，失败返回错误码错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Operation failed. Cannot connect to service. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { vpn } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private VpnConnection: vpn.VpnConnection = vpn.createVpnConnection(this.context);
  Destroy(): void {
    this.VpnConnection.destroy((error: BusinessError) => {
      console.error(JSON.stringify(error));
    });
  }
  build() { }
}
```

## destroy

```TypeScript
destroy(): Promise<void>
```

销毁启动的 VPN 网络，使用 Promise 方式作为异步方法。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_VPN

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 以 Promise 形式返回设定结果，失败返回错误码错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Operation failed. Cannot connect to service. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { vpn } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private VpnConnection: vpn.VpnConnection = vpn.createVpnConnection(this.context);
  Destroy(): void {
    this.VpnConnection.destroy().then(() => {
      console.info("destroy success.");
    }).catch((err: BusinessError) => {
      console.error("destroy fail" + JSON.stringify(err));
    });
  }
  build() { }
}
```

## protect

```TypeScript
protect(socketFd: number, callback: AsyncCallback<void>): void
```

保护套接字不受 VPN 连接影响，通过该套接字发送的数据将直接基于物理网络收发，因此其流量不会通过 VPN 转发，使用 callback 方式作为异步方法。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_VPN

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| socketFd | number | 是 | 指定保护的 socketfd, 该文件描述符通过 [getSocketFd](arkts-network-socket-tcpsocket-i.md#getsocketfd)获取。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，成功时，error 为 undefined，失败返回错误码错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-非法参数值) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Operation failed. Cannot connect to service. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2203004](../errorcode-net-vpn.md#2203004-无效描述符) | Invalid socket file descriptor. |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { socket, vpn } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private VpnConnection: vpn.VpnConnection = vpn.createVpnConnection(this.context);

  Protect(): void {
    let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
    let ipAddress: socket.NetAddress = {
      address: "0.0.0.0"
    }
    tcp.bind(ipAddress);
    let netAddress: socket.NetAddress = {
      address: "192.168.1.11",
      port: 8888
    }
    let addressConnect: socket.TCPConnectOptions = {
      address: netAddress,
      timeout: 6000
    }
    tcp.connect(addressConnect);
    tcp.getSocketFd().then((tunnelFd: number) => {
      console.info("tunnelFd: " + tunnelFd);
      this.VpnConnection.protect(tunnelFd, (error: BusinessError) => {
        console.error(JSON.stringify(error));
      });
    });
  }
  build() { }
}
```

## protect

```TypeScript
protect(socketFd: number): Promise<void>
```

保护套接字不受 VPN 连接影响，通过该套接字发送的数据将直接基于物理网络收发，因此其流量不会通过 VPN 转发, 使用 Promise 方式作为异步方法。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_VPN

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| socketFd | number | 是 | 指定保护的 socketfd, 该文件描述符通过 [getSocketFd](arkts-network-socket-tcpsocket-i.md#getsocketfd)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 以 Promise 形式返回设定结果，失败返回错误码错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-非法参数值) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Operation failed. Cannot connect to service. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2203004](../errorcode-net-vpn.md#2203004-无效描述符) | Invalid socket file descriptor. |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { socket, vpn } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private VpnConnection: vpn.VpnConnection = vpn.createVpnConnection(this.context);

  Protect(): void {
    let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
    let ipAddress: socket.NetAddress = {
      address: "0.0.0.0"
    }
    tcp.bind(ipAddress);
    let netAddress: socket.NetAddress = {
      address: "192.168.1.11",
      port: 8888
    }
    let addressConnect: socket.TCPConnectOptions = {
      address: netAddress,
      timeout: 6000
    }
    tcp.connect(addressConnect);
    tcp.getSocketFd().then((tunnelFd: number) => {
      console.info("tunnelFd: " + tunnelFd);
      this.VpnConnection.protect(tunnelFd).then(() => {
        console.info("protect success.");
      }).catch((err: BusinessError) => {
        console.error("protect fail" + JSON.stringify(err));
      });
    });
  }
  build() { }
}
```

## setUp

```TypeScript
setUp(config: VpnConfig, callback: AsyncCallback<number>): void
```

使用 config 创建一个 vpn 网络，使用 callback 方式作为异步方法。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_VPN

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | VpnConfig | 是 | 指定 VPN 网络的配置信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，当成功启动 VPN 网络时，返回虚拟网卡的文件描述符 fd, error 为 undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-非法参数值) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Operation failed. Cannot connect to service. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2203001](../errorcode-net-vpn.md#2203001-vpn创建失败) | VPN creation denied. Check the user type. |
| [2203002](../errorcode-net-vpn.md#2203002-vpn已存在) | VPN already exists. |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { vpn } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private VpnConnection: vpn.VpnConnection = vpn.createVpnConnection(this.context);
  SetUp(): void {
    let config: vpn.VpnConfig = {
      addresses: [{
        address: {
          address: "10.0.0.5",
          family: 1
        },
        prefixLength: 24
      }],
      mtu: 1400,
      dnsAddresses: ["114.114.114.114"]
    }
    this.VpnConnection.setUp(config, (error: BusinessError, data: number) => {
      console.error(JSON.stringify(error));
      console.info("tunfd: " + JSON.stringify(data));
    });
  }
  build() { }
}
```

## setUp

```TypeScript
setUp(config: VpnConfig): Promise<number>
```

使用 config 创建一个 vpn 网络，使用 Promise 方式作为异步方法。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_VPN

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | VpnConfig | 是 | 指定 VPN 网络的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | 以 Promise 形式返回获取结果，返回指定虚拟网卡的文件描述符 fd。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-非法参数值) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Operation failed. Cannot connect to service. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2203001](../errorcode-net-vpn.md#2203001-vpn创建失败) | VPN creation denied. Check the user type. |
| [2203002](../errorcode-net-vpn.md#2203002-vpn已存在) | VPN already exists. |

**示例**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { vpn } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private VpnConnection: vpn.VpnConnection = vpn.createVpnConnection(this.context);
  SetUp(): void {
    let config: vpn.VpnConfig = {
      addresses: [{
        address: {
          address: "10.0.0.5",
          family: 1
        },
        prefixLength: 24
      }],
      mtu: 1400,
      dnsAddresses: ["114.114.114.114"]
    }
    this.VpnConnection.setUp(config).then((data: number) => {
      console.info("setUp success, tunfd: " + JSON.stringify(data));
    }).catch((err: BusinessError) => {
      console.error("setUp fail" + JSON.stringify(err));
    });
  }
  build() { }
}
```
