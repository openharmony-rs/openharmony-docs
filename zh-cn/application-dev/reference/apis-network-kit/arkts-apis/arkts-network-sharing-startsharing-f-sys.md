# startSharing（系统接口）

## 导入模块

```TypeScript
```

## startSharing

```TypeScript
function startSharing(type: SharingIfaceType, callback: AsyncCallback<void>): void
```

开启指定类型共享，使用 callback 异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [SharingIfaceType](arkts-network-sharing-sharingifacetype-e-sys.md) | 是 | 共享类型，0：Wi-Fi 1：USB 2：BLUETOOTH。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，返回开启网络共享结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-非法参数值) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Failed to connect to the service. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2202004](../errorcode-net-sharing.md#2202004-共享的iface不可用) | Try to share an unavailable iface. |
| [2202005](../errorcode-net-sharing.md#2202005-wifi共享失败) | WiFi sharing failed. |
| [2202006](../errorcode-net-sharing.md#2202006-蓝牙共享失败) | Bluetooth sharing failed. |
| [2202009](../errorcode-net-sharing.md#2202009-网络共享开启转发错误) | Failed to enable forwarding for network sharing. |
| [2202011](../errorcode-net-sharing.md#2202011-无法获取网络共享配置) | Cannot get network sharing configuration. |

**示例**

```TypeScript
import { sharing } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let SHARING_WIFI = 0;
sharing.startSharing(SHARING_WIFI, (error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```


## startSharing

```TypeScript
function startSharing(type: SharingIfaceType): Promise<void>
```

开启指定类型共享，使用 Promise 异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [SharingIfaceType](arkts-network-sharing-sharingifacetype-e-sys.md) | 是 | 共享类型，0：Wi-Fi 1：USB 2：BLUETOOTH。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 以 Promise 形式返回开启共享执行结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-非法参数值) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Failed to connect to the service. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2202004](../errorcode-net-sharing.md#2202004-共享的iface不可用) | Try to share an unavailable iface. |
| [2202005](../errorcode-net-sharing.md#2202005-wifi共享失败) | WiFi sharing failed. |
| [2202006](../errorcode-net-sharing.md#2202006-蓝牙共享失败) | Bluetooth sharing failed. |
| [2202009](../errorcode-net-sharing.md#2202009-网络共享开启转发错误) | Failed to enable forwarding for network sharing. |
| [2202011](../errorcode-net-sharing.md#2202011-无法获取网络共享配置) | Cannot get network sharing configuration. |

**示例**

```TypeScript
import { sharing } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let SHARING_WIFI = 0;
sharing
  .startSharing(SHARING_WIFI)
  .then(() => {
    console.info('start wifi sharing successful');
  })
  .catch((error: BusinessError) => {
    console.error('start wifi sharing failed');
  });
```
