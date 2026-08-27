# getEthernetDeviceInfos（系统接口）

## 导入模块

```TypeScript
import { ethernet } from '@kit.NetworkKit';
```

## getEthernetDeviceInfos

```TypeScript
function getEthernetDeviceInfos(): Promise<Array<EthernetDeviceInfos>>
```

获取本机以太网卡的设备信息（如供应商名称、产品名称、最大连接速率等）使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[EthernetDeviceInfos](arkts-network-ethernet-ethernetdeviceinfos-i-sys.md)&gt;&gt; | Promise对象，返回本次执行结果。成功返回以太网设备信息列表，失败返回对应错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [2201005](../errorcode-net-ethernet.md#2201005-设备信息不存在) | Device information does not exist. |

**示例**

```TypeScript
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.getEthernetDeviceInfos().then((data: Array<ethernet.EthernetDeviceInfos>) => {
  console.info("getEthernetDeviceInfos data.length = " + JSON.stringify(data.length));
  for (let i = 0; i < data.length; i++) {
    console.info("getEthernetDeviceInfos = " + JSON.stringify(data[i]));
  }
}).catch((err: BusinessError) => {
  console.error("getEthernetDeviceInfos err = " + err.code);
});
```
