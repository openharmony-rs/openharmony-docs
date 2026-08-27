# addCustomDnsRule

## 导入模块

```TypeScript
```

## addCustomDnsRule

```TypeScript
function addCustomDnsRule(host: string, ip: Array<string>, callback: AsyncCallback<void>): void
```

为当前应用程序添加自定义host和对应的IP地址的映射。使用callback异步回调。

> **说明：**
> 
> 不需要时可调用[removeCustomDnsRule](arkts-network-connection-removecustomdnsrule-f.md)删除某一条自定义规则或调用
> [clearCustomDnsRules](arkts-network-connection-clearcustomdnsrules-f.md)删除当前应用程序的所有的自定义DNS规则 。

**起始版本：** 11

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | string | 是 | 需要自定义解析的主机名。 |
| ip | Array & lt;string & gt; | 是 | 主机名所映射的IP地址列表。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当为当前应用程序添加自定义host和对应的ip地址的映射成功，error为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.addCustomDnsRule("xxxx", ["xx.xx.xx.xx","xx.xx.xx.xx"], (error: BusinessError, data: void) => {
  if (error) {
    console.error(`Failed to get add custom dns rule. Code:${error.code}, message:${error.message}`);
    return;
  }
  console.info("Succeeded to get data: " + JSON.stringify(data));
})
```


## addCustomDnsRule

```TypeScript
function addCustomDnsRule(host: string, ip: Array<string>): Promise<void>
```

为当前应用程序添加自定义host和对应的IP地址的映射。使用Promise异步回调。

> **说明：**
> 
> 不需要时可调用[removeCustomDnsRule](arkts-network-connection-removecustomdnsrule-f.md)删除某一条自定义规则或调用
> [clearCustomDnsRules](arkts-network-connection-clearcustomdnsrules-f.md)删除当前应用程序的所有的自定义DNS规则 。

**起始版本：** 11

**需要权限：** ohos.permission.INTERNET

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| host | string | 是 | 需要自定义解析的主机名。 |
| ip | Array & lt;string & gt; | 是 | 主机名所映射的IP地址列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.addCustomDnsRule("xxxx", ["xx.xx.xx.xx","xx.xx.xx.xx"]).then(() => {
    console.info("success");
}).catch((error: BusinessError) => {
    console.error(`Failed to get request.Code:${error.code}, message:${error.message}`);
})
```
