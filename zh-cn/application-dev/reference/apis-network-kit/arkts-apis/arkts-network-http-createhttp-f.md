# createHttp

## 导入模块

```TypeScript
import { http } from '@kit.NetworkKit';
```

## createHttp

```TypeScript
function createHttp(): HttpRequest
```

创建一个HTTP请求，里面包括发起请求、中断请求、订阅/取消订阅HTTP Response Header事件。当发起多个HTTP请求时，需为每个HTTP请求创建对应HttpRequest对象。每一个HttpRequest对象对应一 个HTTP请求。 > **说明：** > > 当该请求使用完毕时，需调用destroy方法释放资源，否则会出现内存泄露问题。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-http-function createHttp(): HttpRequest--><!--Device-http-function createHttp(): HttpRequest-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| HttpRequest | 返回一个HttpRequest对象，里面包括request、requestInStream、requestSync、enableAutoCookie、destroy、on和off方 法。 |

**示例**

```TypeScript
import { http } from '@kit.NetworkKit';

let httpRequest = http.createHttp();
```

