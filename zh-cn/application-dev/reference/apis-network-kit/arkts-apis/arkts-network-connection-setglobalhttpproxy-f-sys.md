# setGlobalHttpProxy（系统接口）

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## setGlobalHttpProxy

```TypeScript
function setGlobalHttpProxy(httpProxy: HttpProxy, callback: AsyncCallback<void>): void
```

设置网络全局Http代理配置信息，使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

<!--Device-connection-function setGlobalHttpProxy(httpProxy: HttpProxy, callback: AsyncCallback<void>): void--><!--Device-connection-function setGlobalHttpProxy(httpProxy: HttpProxy, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| httpProxy | HttpProxy | 是 | 网络全局Http代理配置信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当成功设置网络全局Http代理配置信息时，error为undefined，否则为错误对象。 |

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
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let exclusionStr = "192.168,baidu.com";
let exclusionArray = exclusionStr.split(',');
let httpProxy: connection.HttpProxy = {
    host: "192.168.xx.xxx",
    port: 8080,
    exclusionList: exclusionArray
}
connection.setGlobalHttpProxy(httpProxy, (err: BusinessError) => {
    if (err) {
        console.error(`setGlobalHttpProxy failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`setGlobalHttpProxy success.`);
});
```


## setGlobalHttpProxy

```TypeScript
function setGlobalHttpProxy(httpProxy: HttpProxy): Promise<void>
```

设置网络全局Http代理配置信息，使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

<!--Device-connection-function setGlobalHttpProxy(httpProxy: HttpProxy): Promise<void>--><!--Device-connection-function setGlobalHttpProxy(httpProxy: HttpProxy): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| httpProxy | HttpProxy | 是 | 网络全局Http代理配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回值的Promise对象。 |

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
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let exclusionStr = "192.168,baidu.com";
let exclusionArray = exclusionStr.split(',');
connection.setGlobalHttpProxy({
  host: "192.168.xx.xxx",
  port: 8080,
  exclusionList: exclusionArray
} as connection.HttpProxy).then(() => {
  console.info("success");
}).catch((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```

