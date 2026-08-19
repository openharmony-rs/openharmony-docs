# isSharing（系统接口）

## 导入模块

```TypeScript
import { sharing } from '@kit.NetworkKit';
```

## isSharing

```TypeScript
function isSharing(callback: AsyncCallback<boolean>): void
```

获取当前网络共享状态，使用 callback 异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

<!--Device-sharing-function isSharing(callback: AsyncCallback<boolean>): void--><!--Device-sharing-function isSharing(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数，返回 true 代表网络共享中。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [2202011](../errorcode-net-sharing.md#2202011-无法获取网络共享配置) | Cannot get network sharing configuration. |

**示例**

```TypeScript
import { sharing } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

sharing.isSharing((error: BusinessError, data: boolean) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```


## isSharing

```TypeScript
function isSharing(): Promise<boolean>
```

获取当前网络共享状态，使用 Promise 异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

<!--Device-sharing-function isSharing(): Promise<boolean>--><!--Device-sharing-function isSharing(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetSharing

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 以 Promise 形式返回网络共享状态结果，返回 true 代表网络共享中。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [2202011](../errorcode-net-sharing.md#2202011-无法获取网络共享配置) | Cannot get network sharing configuration. |

**示例**

```TypeScript
import { sharing } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

sharing
  .isSharing()
  .then((data: boolean) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

