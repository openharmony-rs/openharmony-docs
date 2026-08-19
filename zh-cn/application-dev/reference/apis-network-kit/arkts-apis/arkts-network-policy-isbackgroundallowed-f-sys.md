# isBackgroundAllowed（系统接口）

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## isBackgroundAllowed

```TypeScript
function isBackgroundAllowed(callback: AsyncCallback<boolean>): void
```

获取当前应用是否允许后台访问网络，使用 callback 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

<!--Device-policy-function isBackgroundAllowed(callback: AsyncCallback<boolean>): void--><!--Device-policy-function isBackgroundAllowed(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。返回 true 代表后台策略为允许，失败返回错误码错误信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

policy.isBackgroundAllowed((error: BusinessError, data: boolean) => {
  console.error(JSON.stringify(error));
 console.info(JSON.stringify(data));
});
```


## isBackgroundAllowed

```TypeScript
function isBackgroundAllowed(): Promise<boolean>
```

获取当前应用是否允许后台访问网络，使用 Promise 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

<!--Device-policy-function isBackgroundAllowed(): Promise<boolean>--><!--Device-policy-function isBackgroundAllowed(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise 对象。 返回 true 表示后台策略为允许，返回false表示后台策略不允许。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

policy
  .isBackgroundAllowed()
  .then((data: boolean) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

