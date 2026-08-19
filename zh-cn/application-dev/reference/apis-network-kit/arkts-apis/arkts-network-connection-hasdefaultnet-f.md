# hasDefaultNet

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## hasDefaultNet

```TypeScript
function hasDefaultNet(callback: AsyncCallback<boolean>): void
```

获取当前是否有可用网络，使用callback异步回调。如果有可用网络，可以使用[getDefaultNet](arkts-network-connection-getdefaultnet-f.md)获取默认网络句柄。

**起始版本：** 23

**需要权限：** ohos.permission.GET_NETWORK_INFO

<!--Device-connection-function hasDefaultNet(callback: AsyncCallback<boolean>): void--><!--Device-connection-function hasDefaultNet(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。返回当前是否有可用网络。true表示当前有可用网络，false表示当前没有可用网络。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.hasDefaultNet((error: BusinessError, data: boolean) => {
  console.error(`Failed to get request.Code:${error.code}, message:${error.message}`);
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```

ArkTS-Sta示例：

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.hasDefaultNet((error: BusinessError|null, data: boolean|undefined) => {
  console.error(`Failed to get request.Code:${error.code}, message:${error.message}`);
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```


## hasDefaultNet

```TypeScript
function hasDefaultNet(): Promise<boolean>
```

获取当前是否有可用网络。使用Promise异步回调。如果有可用网络，可以使用[getDefaultNet](arkts-network-connection-getdefaultnet-f.md)获取默认网络句柄。

**起始版本：** 23

**需要权限：** ohos.permission.GET_NETWORK_INFO

<!--Device-connection-function hasDefaultNet(): Promise<boolean>--><!--Device-connection-function hasDefaultNet(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回当前是否有可用网络。true表示当前有可用网络，false表示当前没有可用网络。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

connection.hasDefaultNet().then((data: boolean) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```

