# createVlanInterface（系统接口）

## 导入模块

```TypeScript
```

## createVlanInterface

```TypeScript
function createVlanInterface(ifName: string, vlanId: number): Promise<void>
```

在指定的以太网网卡上，创建一个由vlanId指定的虚拟局域网。使用Promise异步回调。

> **说明：**
> 
> - 本接口当前仅支持PC设备，其他设备类型上调用本接口返回错误码2100002。

**起始版本：** 23

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ifName | string | 是 | 网卡名。 |
| vlanId | number | 是 | vlan标识符，取值范围[0,4094]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Nonsystem applications use system APIs. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [2100400](../errorcode-net-connection.md#2100400-传入网卡名不正确非以太网) | The input network interface name is incorrect. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

let ifName = "eth0";
let vlanId = 1;
connection.createVlanInterface(ifName, vlanId).then(() => {
  console.info(`Create vlan success`);
}).catch((error: BusinessError) => {
  console.error(`Failed to create vlan. Code:${error.code}, message:${error.message}`);
});
```
