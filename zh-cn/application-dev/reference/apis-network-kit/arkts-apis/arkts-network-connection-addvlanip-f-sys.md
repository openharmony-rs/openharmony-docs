# addVlanIp（系统接口）

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## addVlanIp

```TypeScript
function addVlanIp(ifName: string, vlanId: int, address: LinkAddress): Promise<void>
```

为以太网网卡上对应vlanId的虚拟局域网配置指定的IP地址及子网掩码。使用Promise异步回调。 > **说明：** > > - 本接口当前仅支持PC设备，其他设备类型上调用本接口返回错误码2100002。

**起始版本：** 23

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-connection-function addVlanIp(ifName: string, vlanId: int, address: LinkAddress): Promise<void>--><!--Device-connection-function addVlanIp(ifName: string, vlanId: int, address: LinkAddress): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ifName | string | 是 | 网卡名。 |
| vlanId | int | 是 | vlan标识符，取值范围[0,4094]。 |
| address | LinkAddress | 是 | 链路信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100400](../errorcode-net-connection.md#2100400-传入网卡名不正确非以太网) | The input network interface name is incorrect. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Nonsystem applications use system APIs. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

let ifName = "eth0";
let vlanId = 1;
let netAddress: connection.NetAddress = {
  address: '192.168.1.1',
  family: 1,
  port: 8080
}
let address: connection.LinkAddress = {
  address: netAddress,
  prefixLength: 24
}
connection.addVlanIp(ifName, vlanId, address).then(() => {
  console.info(`Add vlan ip success`);
}).catch((error: BusinessError) => {
  console.error(`Failed to add vlan ip. Code:${error.code}, message:${error.message}`);
});
```

