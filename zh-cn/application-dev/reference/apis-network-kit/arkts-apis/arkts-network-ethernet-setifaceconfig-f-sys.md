# setIfaceConfig（系统接口）

## 导入模块

```TypeScript
import { ethernet } from '@kit.NetworkKit';
```

## setIfaceConfig

```TypeScript
function setIfaceConfig(iface: string, ic: InterfaceConfiguration, callback: AsyncCallback<void>): void
```

设置网络接口配置信息，使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

<!--Device-ethernet-function setIfaceConfig(iface: string, ic: InterfaceConfiguration, callback: AsyncCallback<void>): void--><!--Device-ethernet-function setIfaceConfig(iface: string, ic: InterfaceConfiguration, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iface | string | 是 | 网络接口名。 |
| ic | [InterfaceConfiguration](arkts-network-ethernet-interfaceconfiguration-i-sys.md) | 是 | 要设置的网络接口配置信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。成功无返回，失败返回对应错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [2201005](../errorcode-net-ethernet.md#2201005-设备信息不存在) | Device information does not exist. |
| 2201004 | Invalid Ethernet profile. |
| [2201007](../errorcode-net-ethernet.md#2201007-用户配置写入失败) | Ethernet failed to write user configuration information. |
| [2201006](../errorcode-net-ethernet.md#2201006-设备未连接) | Ethernet device not connected. |

**示例**

```TypeScript
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let config: ethernet.InterfaceConfiguration = {
  mode: 0,
  ipAddr: "192.168.xx.xxx",
  route: "192.168.xx.xxx",
  gateway: "192.168.xx.xxx",
  netMask: "255.255.255.0",
  dnsServers: "1.1.1.1"
};

ethernet.setIfaceConfig("eth0", config, (error: BusinessError) => {
  if (error) {
    console.error("setIfaceConfig callback error = " + JSON.stringify(error));
  } else {
    console.info("setIfaceConfig callback ok");
  }
});
```


## setIfaceConfig

```TypeScript
function setIfaceConfig(iface: string, ic: InterfaceConfiguration): Promise<void>
```

设置网络接口配置信息，使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

<!--Device-ethernet-function setIfaceConfig(iface: string, ic: InterfaceConfiguration): Promise<void>--><!--Device-ethernet-function setIfaceConfig(iface: string, ic: InterfaceConfiguration): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iface | string | 是 | 接口名。 |
| ic | [InterfaceConfiguration](arkts-network-ethernet-interfaceconfiguration-i-sys.md) | 是 | 要设置的网络接口配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回执行结果。成功无返回，失败返回对应错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [2201005](../errorcode-net-ethernet.md#2201005-设备信息不存在) | Device information does not exist. |
| 2201004 | Invalid Ethernet profile. |
| [2201007](../errorcode-net-ethernet.md#2201007-用户配置写入失败) | Ethernet failed to write user configuration information. |
| [2201006](../errorcode-net-ethernet.md#2201006-设备未连接) | Ethernet device not connected. |

**示例**

```TypeScript
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let config: ethernet.InterfaceConfiguration = {
  mode: 0,
  ipAddr: "192.168.xx.xxx",
  route: "192.168.xx.xxx",
  gateway: "192.168.xx.xxx",
  netMask: "255.255.255.0",
  dnsServers: "1.1.1.1"
};

const setConfigPromise = ethernet.setIfaceConfig("eth0", config);

setConfigPromise.then(() => {
  console.info("setIfaceConfig promise ok");
}).catch((error: BusinessError)  => {
  console.error("setIfaceConfig promise error = " + JSON.stringify(error));
});
```

