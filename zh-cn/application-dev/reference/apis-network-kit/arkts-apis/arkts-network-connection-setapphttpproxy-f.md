# setAppHttpProxy

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## setAppHttpProxy

```TypeScript
function setAppHttpProxy(httpProxy: HttpProxy): void
```

设置应用级Http代理配置信息。 > **说明：** > > 若需使用本接口所配置的代理信息，则需在[HttpRequestOptions](arkts-network-http-httprequestoptions-i.md)字段中将usingProxy设置为true以启用代理转 > 发。本接口仅负责配置代理规则，不校验代理服务的有效性。

**起始版本：** 23

<!--Device-connection-function setAppHttpProxy(httpProxy: HttpProxy): void--><!--Device-connection-function setAppHttpProxy(httpProxy: HttpProxy): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| httpProxy | HttpProxy | 是 | 网络应用级Http代理配置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid http proxy. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { http } from '@kit.NetworkKit';

// 将exclusionStr以逗号分隔为数组。
let exclusionStr = "192.168,test.com";
// exclusionArray将exclusionStr以逗号分隔为数组。
let exclusionArray = exclusionStr.split(',');
connection.setAppHttpProxy({
  host: "192.168.xx.xxx",
  port: 8080,
  exclusionList: exclusionArray
} as connection.HttpProxy);
let httpRequest = http.createHttp();
let options: http.HttpRequestOptions = {
  usingProxy: true, // 选择使用网络代理，从API 10开始支持该属性。
};
// 发起一个HTTP请求。
httpRequest.request("EXAMPLE_URL", options, (err: BusinessError, data: http.HttpResponse) => {
  if (!err) {
   console.info('Succeeded to get result: ' + JSON.stringify(data.result));
   console.info('Succeeded to get code: ' + JSON.stringify(data.responseCode));
   console.info('Succeeded to get type: ' + JSON.stringify(data.resultType));
   console.info('Succeeded to get header: ' + JSON.stringify(data.header));
   console.info('Succeeded to get cookies: ' + JSON.stringify(data.cookies)); // 从API version 8开始支持cookie。
  } else {
   console.error(`Failed to get request. Code:${err.code}, message:${err.message}`);
  }
});
```

