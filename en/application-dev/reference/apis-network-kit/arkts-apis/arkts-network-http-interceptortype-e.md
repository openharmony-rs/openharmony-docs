# InterceptorType

```TypeScript
export enum InterceptorType
```

Enumerates the types of HTTP interceptors.

| Name | Value|Description |  
| ------ | --|-------------------------------------- |  
| INITIAL_REQUEST |'INITIAL_REQUEST' |Intercepts after the initial HTTP request is assembled.|
| REDIRECTION | 'REDIRECTION' |Intercepts when a redirection response is received.|
| CACHE_CHECKED | 'READ_CACHE' |Intercepts when the HTTP cache is checked and hit.|
| NETWORK_CONNECT | 'CONNECT_NETWORK' |Intercepts before the network request is sent.|
| FINAL_RESPONSE | 'FINAL_RESPONSE' |Intercepts when the final HTTP response is obtained.|

**Since:** 22

<!--Device-http-export enum InterceptorType--><!--Device-http-export enum InterceptorType-End-->

**System capability:** SystemCapability.Communication.NetStack

## INITIAL_REQUEST

```TypeScript
INITIAL_REQUEST = 'INITIAL_REQUEST'
```

Intercept after the initial HTTP request is assembled.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-InterceptorType-INITIAL_REQUEST = 'INITIAL_REQUEST'--><!--Device-InterceptorType-INITIAL_REQUEST = 'INITIAL_REQUEST'-End-->

**System capability:** SystemCapability.Communication.NetStack

## REDIRECTION

```TypeScript
REDIRECTION = 'REDIRECTION'
```

Intercept when we get a redirection responsed and is going to send another request.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-InterceptorType-REDIRECTION = 'REDIRECTION'--><!--Device-InterceptorType-REDIRECTION = 'REDIRECTION'-End-->

**System capability:** SystemCapability.Communication.NetStack

## CACHE_CHECKED

```TypeScript
CACHE_CHECKED = 'READ_CACHE'
```

Intercept after we checked the HTTP cache.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-InterceptorType-CACHE_CHECKED = 'READ_CACHE'--><!--Device-InterceptorType-CACHE_CHECKED = 'READ_CACHE'-End-->

**System capability:** SystemCapability.Communication.NetStack

## NETWORK_CONNECT

```TypeScript
NETWORK_CONNECT = 'CONNECT_NETWORK'
```

Intercept when we perform network connection, such as TLS and TCP.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-InterceptorType-NETWORK_CONNECT = 'CONNECT_NETWORK'--><!--Device-InterceptorType-NETWORK_CONNECT = 'CONNECT_NETWORK'-End-->

**System capability:** SystemCapability.Communication.NetStack

## FINAL_RESPONSE

```TypeScript
FINAL_RESPONSE = 'FINAL_RESPONSE'
```

Intercept when we get the final HTTP response.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-InterceptorType-FINAL_RESPONSE = 'FINAL_RESPONSE'--><!--Device-InterceptorType-FINAL_RESPONSE = 'FINAL_RESPONSE'-End-->

**System capability:** SystemCapability.Communication.NetStack
