# HttpInterceptor

HTTP拦截器接口。用户可以实现此接口来定义拦截处理函数。

**起始版本：** 22

<!--Device-http-export interface HttpInterceptor--><!--Device-http-export interface HttpInterceptor-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { http } from '@kit.NetworkKit';
```

## interceptorHandle

```TypeScript
interceptorHandle(reqContext: HttpRequestContext, rspContext: HttpResponse): Promise<ChainContinue>
```

拦截HTTP处理过程并进行所需的更改。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-HttpInterceptor-interceptorHandle(reqContext: HttpRequestContext, rspContext: HttpResponse): Promise<ChainContinue>--><!--Device-HttpInterceptor-interceptorHandle(reqContext: HttpRequestContext, rspContext: HttpResponse): Promise<ChainContinue>-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reqContext | [HttpRequestContext](arkts-network-http-httprequestcontext-i.md) | 是 | the context of the target HTTP request. |
| rspContext | HttpResponse | 是 | the context of the target HTTP response. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ChainContinue](arkts-network-http-chaincontinue-t.md)&gt; | 继续HTTP处理或终止并返回HTTP响应。 |

**示例**

```TypeScript
import { http } from '@kit.NetworkKit';

// 创建自定义拦截器
class CustomInterceptor implements http.HttpInterceptor {
  interceptorType: http.InterceptorType = http.InterceptorType.INITIAL_REQUEST;

  async interceptorHandle(reqContext: http.HttpRequestContext, rspContext: http.HttpResponse): Promise<http.ChainContinue> {
    // 在初始请求阶段添加认证头
    reqContext.header['Authorization'] = 'Bearer token';
    console.info('Interceptor: Added authorization header');
    return true; // 继续处理拦截器链
  }
}

let customInterceptor = new CustomInterceptor();
```

## interceptorType

```TypeScript
interceptorType: InterceptorType
```

The type of this interceptor. It defines when this intercptor would be called.

**类型：** [InterceptorType](arkts-network-http-interceptortype-e.md)

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-HttpInterceptor-interceptorType: InterceptorType--><!--Device-HttpInterceptor-interceptorType: InterceptorType-End-->

**系统能力：** SystemCapability.Communication.NetStack

