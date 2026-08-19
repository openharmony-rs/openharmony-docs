# HttpInterceptorChain

HTTP拦截器链。

**起始版本：** 22

<!--Device-http-export class HttpInterceptorChain--><!--Device-http-export class HttpInterceptorChain-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { http } from '@kit.NetworkKit';
```

## addChain

```TypeScript
public addChain(chain: HttpInterceptor[]): boolean
```

向HTTP客户端添加拦截器。 > **说明：** > > 拦截器链中不能包含相同类型的拦截器实例。如果传入相同类型的拦截器，会抛出错误码2300802（Duplicated interceptor type in the chain）。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-HttpInterceptorChain-public addChain(chain: HttpInterceptor[]): boolean--><!--Device-HttpInterceptorChain-public addChain(chain: HttpInterceptor[]): boolean-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| chain | [HttpInterceptor](arkts-network-http-httpinterceptor-i.md)[] | 是 | 拦截器实例组成的拦截链，支持传入单个或者多个不同类型的拦截器。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 拦截器是否添加成功。true表示拦截器添加成功，false表示拦截器没有添加成功。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 2300802 | Duplicated interceptor type in the chain. |
| 2300801 | Parameter type not supported by the interceptor. |
| [2300999](../errorcode-net-http.md#2300999-内部错误) | Internal error. |

## apply

```TypeScript
public apply(httpRequest: HttpRequest): boolean
```

将拦截器链附加到目标HTTP请求。每个HTTP请求实例只能附加一个拦截器链。 > **说明：** > > 将拦截器链附加到[HttpRequest](arkts-network-http-httprequest-i.md)实例后，当该实例发起HTTP请求时，会触发已附加的拦截器链中相应类型的拦截器。 > 更多使用HTTP请求触发拦截器功能，可以参考[HTTP拦截器功能代码示例](../../../network/http-request.md#http拦截器)。 > HTTP拦截器相关能力仅支持 > [HttpRequest.request](arkts-network-http-httprequest-i.md#request)接口，目前暂 > 不支持 > [HttpRequest.requestInStream](arkts-network-http-httprequest-i.md#requestinstream) > (流式传输)接口。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-HttpInterceptorChain-public apply(httpRequest: HttpRequest): boolean--><!--Device-HttpInterceptorChain-public apply(httpRequest: HttpRequest): boolean-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| httpRequest | HttpRequest | 是 | 要发起HTTP请求的[HttpRequest](arkts-network-http-httprequest-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 拦截器是否附加成功。true表示拦截器附加成功，false表示拦截器没有附加成功。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 2300801 | Parameter type not supported by the interceptor. |
| [2300999](../errorcode-net-http.md#2300999-内部错误) | Internal error. |

## getChain

```TypeScript
public getChain(): HttpInterceptor[]
```

获取当前拦截器链中的所有拦截器实例。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-HttpInterceptorChain-public getChain(): HttpInterceptor[]--><!--Device-HttpInterceptorChain-public getChain(): HttpInterceptor[]-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HttpInterceptor](arkts-network-http-httpinterceptor-i.md)[] | 返回通过[addChain]{ |

