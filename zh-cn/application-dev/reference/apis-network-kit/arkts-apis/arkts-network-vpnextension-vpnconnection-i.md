# VpnConnection

VPN连接对象。在调用VpnConnection的方法前，需要先通过vpnExt.createVpnConnection创建VPN连接对象。

**起始版本：** 11

<!--Device-vpnExtension-export interface VpnConnection--><!--Device-vpnExtension-export interface VpnConnection-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## 导入模块

```TypeScript
import { vpnExtension } from '@kit.NetworkKit';
```

## addRoute

```TypeScript
addRoute(routes: RouteInfo[], vpnId?: string): Promise<void>
```

为VPN网络添加路由

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VpnConnection-addRoute(routes: RouteInfo[], vpnId?: string): Promise<void>--><!--Device-VpnConnection-addRoute(routes: RouteInfo[], vpnId?: string): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| routes | RouteInfo[] | 是 | VPN接口的路由数组。 |
| vpnId | string | 否 | vpn唯一标识 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 函数返回的promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2200001](../errorcode-net-ethernet.md#2200001-非法参数值) | Invalid parameter value. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Operation failed. Cannot connect to service. |

## create

```TypeScript
create(config: VpnConfig): Promise<int>
```

使用config创建一个VPN网络。使用Promise异步回调。 > **说明：** > > 建议在不需要VPN网络的时候配对调用[destroy()](#destroy)或 > [destroy(vpnId: string)](#destroy)接口销毁启动的VPN网络，并执行资源清理等操作。

**起始版本：** 11

<!--Device-VpnConnection-create(config: VpnConfig): Promise<int>--><!--Device-VpnConnection-create(config: VpnConfig): Promise<int>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | VpnConfig | 是 | 指定VPN网络的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | 以 Promise 形式返回获取结果，返回指定虚拟网卡的文件描述符 fd。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2200001](../errorcode-net-ethernet.md#2200001-非法参数值) | Invalid parameter value. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Operation failed. Cannot connect to service. |
| [2203001](../errorcode-net-vpn.md#2203001-vpn创建失败) | VPN creation denied, please check the user type. |
| [2203002](../errorcode-net-vpn.md#2203002-vpn已存在) | VPN exist already, please execute destroy first. |

**示例**

```TypeScript
import { vpnExtension, VpnExtensionAbility } from '@kit.NetworkKit';
import { common, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let context: vpnExtension.VpnExtensionContext;
export default class MyVpnExtAbility extends VpnExtensionAbility {
  private tunIp: string = '10.0.0.5';
  private blockedAppName: string = 'com.example.myvpndemo';
  onCreate(want: Want) {
    let vpnConnection : vpnExtension.VpnConnection = vpnExtension.createVpnConnection(context);
    console.info("vpn createVpnConnection: " + JSON.stringify(vpnConnection));
    this.SetupVpn();
    
    // 不需要VPN网络时，调用destroy()接口销毁启动的VPN网络，并执行资源清理等操作。
    vpnConnection.destroy().then(() => {
      console.info("destroy success.");
    }).catch((error : BusinessError) => {
      console.error(`destroy fail. Code:${error.code}, message:${error.message}`);
    });
  }
  SetupVpn() {
        class Address {
            address: string;
            family: number;

            constructor(address: string, family: number) {
                this.address = address;
                this.family = family;
            }
        }

        class AddressWithPrefix {
            address: Address;
            prefixLength: number;

            constructor(address: Address, prefixLength: number) {
                this.address = address;
                this.prefixLength = prefixLength;
            }
        }

        class Config {
            addresses: AddressWithPrefix[];
            mtu: number;
            dnsAddresses: string[];
            trustedApplications: string[];
            blockedApplications: string[];

            constructor(
                tunIp: string,
                blockedAppName: string
            ) {
                this.addresses = [
                    new AddressWithPrefix(new Address(tunIp, 1), 24)
                ];
                this.mtu = 1400;
                this.dnsAddresses = ["114.114.114.114"];
                this.trustedApplications = [];
                this.blockedApplications = [blockedAppName];
            }
        }

        let config = new Config(this.tunIp, this.blockedAppName);

        try {
            let vpnConnection : vpnExtension.VpnConnection = vpnExtension.createVpnConnection(context);
            vpnConnection.create(config).then((data) => {
                hilog.error(0x0000, 'developTag', 'tunfd: %{public}s', JSON.stringify(data) ?? '');
            })
        } catch (error) {
            hilog.error(0x0000, 'developTag', 'VPN setUp fail: %{public}s', JSON.stringify(error) ?? '');
        }
    }
}
```

## delRoute

```TypeScript
delRoute(routes: RouteInfo[], vpnId?: string): Promise<void>
```

删除VPN网络的路由

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-VpnConnection-delRoute(routes: RouteInfo[], vpnId?: string): Promise<void>--><!--Device-VpnConnection-delRoute(routes: RouteInfo[], vpnId?: string): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| routes | RouteInfo[] | 是 | VPN接口的路由数组。 |
| vpnId | string | 否 | vpn唯一标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 函数返回的promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2200001](../errorcode-net-ethernet.md#2200001-非法参数值) | Invalid parameter value. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Operation failed. Cannot connect to service. |

## destroy

```TypeScript
destroy(): Promise<void>
```

销毁启动的VPN网络。使用Promise异步回调。

**起始版本：** 11

<!--Device-VpnConnection-destroy(): Promise<void>--><!--Device-VpnConnection-destroy(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Operation failed. Cannot connect to service. |

**示例**

```TypeScript
import { vpnExtension, VpnExtensionAbility } from '@kit.NetworkKit';
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context: vpnExtension.VpnExtensionContext;
export default class MyVpnExtAbility extends VpnExtensionAbility {
  onCreate(want: Want) {
    let vpnConnection : vpnExtension.VpnConnection = vpnExtension.createVpnConnection(context);
    console.info("VPN createVpnConnection: " + JSON.stringify(vpnConnection));
    vpnConnection.destroy().then(() => {
      console.info("destroy success.");
    }).catch((error : BusinessError) => {
      console.error("destroy fail" + JSON.stringify(error));
    });
  }
}
```

## destroy

```TypeScript
destroy(vpnId: string): Promise<void>
```

根据vpnId销毁指定的VPN网络。使用Promise异步回调。

**起始版本：** 20

<!--Device-VpnConnection-destroy(vpnId: string): Promise<void>--><!--Device-VpnConnection-destroy(vpnId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| vpnId | string | 是 | vpn唯一标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19900002](../errorcode-net-vpn.md#19900002-系统内部错误) | System internal error. |
| [19900001](../errorcode-net-vpn.md#19900001-无效参数) | Invalid parameter value. |

**示例**

```TypeScript
import { vpnExtension, VpnExtensionAbility } from '@kit.NetworkKit';
import { BusinessError } from "@kit.BasicServicesKit";

export default class MyVpnExtAbility extends VpnExtensionAbility {
  onCreate() {
    let vpnConnection = vpnExtension.createVpnConnection(this.context);

    // 可通过generateVpnId()获取vpnId
    let vpnId = 'testVpnId';
    vpnConnection.destroy(vpnId).then(() => {
      console.info("destroy success");
    }).catch((error: BusinessError) => {
      console.error(`destroy fail, Code is ${error.code}, message is ${error.message}`);
    });
  }
}
```

## generateVpnId

```TypeScript
generateVpnId(): Promise<string>
```

生成VPN唯一标识。使用Promise异步回调。 如需使用系统多VPN能力，需调用该接口生成vpnId，配置到VpnConfig中。 > **注意** > > 当前系统多VPN能力仅支持IPv4。

**起始版本：** 20

<!--Device-VpnConnection-generateVpnId(): Promise<string>--><!--Device-VpnConnection-generateVpnId(): Promise<string>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | 以Promise形式返回获取结果，返回vpnId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19900002](../errorcode-net-vpn.md#19900002-系统内部错误) | System internal error. |
| [19900001](../errorcode-net-vpn.md#19900001-无效参数) | Invalid parameter value. |

**示例**

```TypeScript
import { vpnExtension, VpnExtensionAbility } from '@kit.NetworkKit';
import { BusinessError } from "@kit.BasicServicesKit";

export default class MyVpnExtAbility extends VpnExtensionAbility {
  onCreate() {
    let vpnConnection = vpnExtension.createVpnConnection(this.context);
    vpnConnection.generateVpnId().then((data) => {
      if (data) {
        console.info("generateVpnId success, vpnId = " + JSON.stringify(data));
      }
    }).catch((error: BusinessError) => {
      console.error(`generateVpnId fail, Code is ${error.code}, message is ${error.message}`);
    });
  }
}
```

## protect

```TypeScript
protect(socketFd: int): Promise<void>
```

保护套接字不受VPN连接影响，通过该套接字发送的数据将直接基于物理网络收发，因此其流量不会通过VPN转发。使用Promise方式作为异步方法。

**起始版本：** 11

<!--Device-VpnConnection-protect(socketFd: int): Promise<void>--><!--Device-VpnConnection-protect(socketFd: int): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| socketFd | int | 是 | 指定保护的 socketfd，该文件描述符通过 [getSocketFd](arkts-network-socket-tcpsocket-i.md#getsocketfd)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2200001](../errorcode-net-ethernet.md#2200001-非法参数值) | Invalid parameter value. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Operation failed. Cannot connect to service. |
| [2203004](../errorcode-net-vpn.md#2203004-无效描述符) | Invalid socket file descriptor. |

**示例**

```TypeScript
import { vpnExtension, VpnExtensionAbility } from '@kit.NetworkKit';
import { common, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let g_tunnelFd = -1;
let context: vpnExtension.VpnExtensionContext;
export default class MyVpnExtAbility extends VpnExtensionAbility {
  private vpnServerIp: string = '192.168.31.13';
  onCreate(want: Want) {
    let vpnConnection : vpnExtension.VpnConnection = vpnExtension.createVpnConnection(context);
    console.info("VPN createVpnConnection: " + JSON.stringify(vpnConnection));
    this.CreateTunnel();
    this.Protect();
  }
  CreateTunnel() {
      g_tunnelFd = 8888;
  }
  Protect() {
        hilog.info(0x0000, 'developTag', '%{public}s', 'VPN Protect');
        let vpnConnection : vpnExtension.VpnConnection = vpnExtension.createVpnConnection(context);
        vpnConnection.protect(g_tunnelFd).then(() => {
            hilog.info(0x0000, 'developTag', '%{public}s', 'VPN Protect Success');
        }).catch((err : Error) => {
            hilog.error(0x0000, 'developTag', 'VPN Protect Failed %{public}s', JSON.stringify(err) ?? '');
        })
  }
}
```

## protectProcessNet

```TypeScript
protectProcessNet(): Promise<void>
```

保护应用进程不受VPN连接影响，被保护的进程直接基于物理网络收发数据，流量不通过VPN转发。使用Promise异步回调。

**起始版本：** 22

<!--Device-VpnConnection-protectProcessNet(): Promise<void>--><!--Device-VpnConnection-protectProcessNet(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**示例**

```TypeScript
import { vpnExtension, VpnExtensionAbility } from '@kit.NetworkKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let g_tunnelFd = -1;
export default class MyVpnExtAbility  extends VpnExtensionAbility {
  onCreate() {
    let vpnConnection = vpnExtension.createVpnConnection(this.context);
    console.info("VPN createVpnConnection: " + JSON.stringify(vpnConnection));
    this.ProtectNetByProcess();
  }
  CreateTunnel() {
    g_tunnelFd = 8888;
  }
  ProtectNetByProcess() {
    hilog.info(0x0000, 'developTag', '%{public}s', 'vpn ProtectNetByProcess');
    let vpnConnection = vpnExtension.createVpnConnection(this.context);
    vpnConnection.protectProcessNet().then(() => {
      hilog.info(0x0000, 'developTag', '%{public}s', 'vpn ProtectNetByProcess Success');
      this.CreateTunnel();
    }).catch((err: Error) => {
      hilog.error(0x0000, 'developTag', 'vpn ProtectNetByProcess Failed %{public}s', JSON.stringify(err) ?? '');
    })
  }
}
```

