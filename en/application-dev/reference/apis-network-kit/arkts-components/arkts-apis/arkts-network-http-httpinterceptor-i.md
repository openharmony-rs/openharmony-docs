# HttpInterceptor

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

```TypeScript
### interceptorHandle

interceptorHandle(reqContext: HttpRequestContext, rspContext: HttpResponse): Promise<ChainContinue>

Intercepts the HTTP processing and modifies it as required.

Atomic service API: This API can be used in atomic services since API version 22.

System capability: SystemCapability.Communication.NetStack

Parameters

Return value
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
