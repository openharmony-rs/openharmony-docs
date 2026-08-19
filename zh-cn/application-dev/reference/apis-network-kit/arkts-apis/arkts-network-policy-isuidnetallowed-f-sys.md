# isUidNetAllowed（系统接口）

## 导入模块

```TypeScript
import { policy } from '@kit.NetworkKit';
```

## isUidNetAllowed

```TypeScript
function isUidNetAllowed(uid: int, isMetered: boolean, callback: AsyncCallback<boolean>): void
```

判断对应 uid 能否访问计量或非计量网络，使用 callback 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

<!--Device-policy-function isUidNetAllowed(uid: int, isMetered: boolean, callback: AsyncCallback<boolean>): void--><!--Device-policy-function isUidNetAllowed(uid: int, isMetered: boolean, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | int | 是 | app 唯一标识符，取值范围为int32_t范围内的正整数。 |
| isMetered | boolean | 是 | 是否为计量网络。true：是计量网络；false：不是计量网络。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。返回 true 表示这个 uid 可以访问对应的计量网络。 |

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

policy.isUidNetAllowed(11111, true, (error: BusinessError, data: boolean) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```


## isUidNetAllowed

```TypeScript
function isUidNetAllowed(uid: int, isMetered: boolean): Promise<boolean>
```

判断对应 uid 能否访问计量或非计量网络，使用 Promise 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

<!--Device-policy-function isUidNetAllowed(uid: int, isMetered: boolean): Promise<boolean>--><!--Device-policy-function isUidNetAllowed(uid: int, isMetered: boolean): Promise<boolean>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | int | 是 | app 唯一标识符，取值范围为int32_t范围内的正整数。 |
| isMetered | boolean | 是 | 是否为计量网络。true：是计量网络；false：不是计量网络。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise 对象。 返回 true 表示这个uid可以访问计量或非计量网络，返回false表示这个uid不可以访问计量或非计量网络。 |

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
  .isUidNetAllowed(11111, true)
  .then((data: boolean) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```


## isUidNetAllowed

```TypeScript
function isUidNetAllowed(uid: int, iface: string, callback: AsyncCallback<boolean>): void
```

获取对应 uid 能否访问指定的 iface 的网络，使用 callback 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

<!--Device-policy-function isUidNetAllowed(uid: int, iface: string, callback: AsyncCallback<boolean>): void--><!--Device-policy-function isUidNetAllowed(uid: int, iface: string, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | int | 是 | app 唯一标识符，取值范围为int32_t范围内的正整数。 |
| iface | string | 是 | 网络对应的名称 。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。返回 true 表示这个 uid 可以访问对应 iface 的网络。 |

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

policy.isUidNetAllowed(11111, 'wlan0', (error: BusinessError, data: boolean) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```


## isUidNetAllowed

```TypeScript
function isUidNetAllowed(uid: int, iface: string): Promise<boolean>
```

获取对应 uid 能否访问指定的 iface 的网络，使用 Promise 异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.MANAGE_NET_STRATEGY

<!--Device-policy-function isUidNetAllowed(uid: int, iface: string): Promise<boolean>--><!--Device-policy-function isUidNetAllowed(uid: int, iface: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uid | int | 是 | app 唯一标识符，取值范围为int32_t范围内的正整数。 |
| iface | string | 是 | 网络对应的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise 对象。 返回 true 表示对应 uid 能访问指定的 iface 的网络，返回false则表示不能访问。 |

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
  .isUidNetAllowed(11111, 'wlan0')
  .then((data: boolean) => {
    console.info(JSON.stringify(data));
  })
  .catch((error: BusinessError) => {
    console.error(JSON.stringify(error));
  });
```

