# HttpInterceptor

```TypeScript
export interface HttpInterceptor
```

Defines the HTTP interceptor API, which is used to define the interception processing function.

**Since:** 22

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## interceptorHandle

```TypeScript
interceptorHandle(reqContext: HttpRequestContext, rspContext: HttpResponse): Promise<ChainContinue>
```

Intercepts the HTTP processing and modifies it as required.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reqContext | [HttpRequestContext](arkts-network-http-httprequestcontext-i.md) | Yes | the context of the target HTTP request. |
| rspContext | [HttpResponse](arkts-network-http-httpresponse-i.md) | Yes | the context of the target HTTP response. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ChainContinue](arkts-network-http-chaincontinue-t.md)&gt; | Continues the HTTP processing or stops and returns an HTTP response. |

**Examples**

### interceptorHandle

interceptorHandle(reqContext: HttpRequestContext, rspContext: HttpResponse): Promise<ChainContinue>

Intercepts the HTTP processing and modifies it as required.

Atomic service API: This API can be used in atomic services since API version 22.

System capability: SystemCapability.Communication.NetStack

Parameters

Return value

```TypeScript
import { http } from '@kit.NetworkKit';

// Create a custom interceptor.
class CustomInterceptor implements http.HttpInterceptor {
  interceptorType: http.InterceptorType = http.InterceptorType.INITIAL_REQUEST;

  async interceptorHandle(reqContext: http.HttpRequestContext, rspContext: http.HttpResponse): Promise<http.ChainContinue> {
    // Add the authentication header in the initial request phase.
    reqContext.header['Authorization'] = 'Bearer token';
    console.info('Interceptor: Added authorization header');
    return true; // Continue to process the interceptor chain.
  }
}

let customInterceptor = new CustomInterceptor();
```

## interceptorType

```TypeScript
interceptorType: InterceptorType
```

The type of this interceptor. It defines when this intercptor would be called.

**Type:** [InterceptorType](arkts-network-http-interceptortype-e.md)

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Communication.NetStack
