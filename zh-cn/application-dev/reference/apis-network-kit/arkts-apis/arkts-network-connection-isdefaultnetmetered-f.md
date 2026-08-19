# isDefaultNetMetered

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## isDefaultNetMetered

```TypeScript
function isDefaultNetMetered(callback: AsyncCallback<boolean>): void
```

检查当前默认网络上的数据流量使用是否被计费（例如：WiFi网络不会被计费，蜂窝网络会被计费）。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_NETWORK_INFO

<!--Device-connection-function isDefaultNetMetered(callback: AsyncCallback<boolean>): void--><!--Device-connection-function isDefaultNetMetered(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。返回当前网络上的数据流量是否被计费。true表示会被计费，false表示不会被计费。 |

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

connection.isDefaultNetMetered((error: BusinessError, data: boolean) => {
  console.error(`Failed to get request.Code:${error.code}, message:${error.message}`);
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```

ArkTS-Sta示例：

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.isDefaultNetMetered((error: BusinessError|null, data: boolean|undefined) => {
  console.error(`Failed to get request.Code:${error.code}, message:${error.message}`);
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```


## isDefaultNetMetered

```TypeScript
function isDefaultNetMetered(): Promise<boolean>
```

检查当前默认网络上的数据流量使用是否被计费（例如：WiFi网络不会被计费，蜂窝网络会被计费）。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_NETWORK_INFO

<!--Device-connection-function isDefaultNetMetered(): Promise<boolean>--><!--Device-connection-function isDefaultNetMetered(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回当前网络上的数据流量是否被计费。true表示会被计费，false表示不会被计费。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

connection.isDefaultNetMetered().then((data: boolean) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```

