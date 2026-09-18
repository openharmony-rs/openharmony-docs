# HttpRequestContext

Defines HTTP request context data. The object instance is passed as a parameter in the [interceptorHandle](arkts-network-http-httpinterceptor-i.md#interceptorhandle) method of the interceptor. You can use this object to obtain and modify the information about the HTTP request.

**Since:** 22

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## body

```TypeScript
body: Object
```

The header of an HTTP request interceptor. It can be modified in an interceptor.

**Type:** Object

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Communication.NetStack

## header

```TypeScript
header: Object
```

The header of an HTTP request interceptor. It can be modified in an interceptor.

**Type:** Object

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Communication.NetStack

## url

```TypeScript
url: string
```

The URL of an HTTP request interceptor. It can be modified in an interceptor.

**Type:** string

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Communication.NetStack
