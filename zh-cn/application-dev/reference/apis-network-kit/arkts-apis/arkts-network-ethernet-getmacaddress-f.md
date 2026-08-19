# getMacAddress

## 导入模块

```TypeScript
import { ethernet } from '@kit.NetworkKit';
```

## getMacAddress

```TypeScript
function getMacAddress(): Promise<Array<MacAddressInfo>>
```

获取所有以太网网卡名称及对应网卡的MAC地址信息，使用Promise方式作为异步方法。

**起始版本：** 14

**需要权限：** ohos.permission.GET_ETHERNET_LOCAL_MAC

<!--Device-ethernet-function getMacAddress(): Promise<Array<MacAddressInfo>>--><!--Device-ethernet-function getMacAddress(): Promise<Array<MacAddressInfo>>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[MacAddressInfo](arkts-network-ethernet-macaddressinfo-i.md)&gt;&gt; | 以Promise形式返回接口信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Operation failed. Cannot connect to service. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2201005](../errorcode-net-ethernet.md#2201005-设备信息不存在) | Device information does not exist. |

**示例**

```TypeScript
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.getMacAddress().then((data: Array<ethernet.MacAddressInfo>) => {
  console.info("getMacAddress promise data = " + JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error("getMacAddress promise error = " + JSON.stringify(error));
});
```

