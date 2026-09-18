# HttpResponse

Defines the response to an HTTP request.

**Since:** 6

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## connectionExtraInfo

```TypeScript
connectionExtraInfo?: ConnectionExtraInfo
```

Detailed information about the HTTP request interaction.

**Type:** [ConnectionExtraInfo](arkts-network-http-connectionextrainfo-i.md)

**Since:** 24

**System capability:** SystemCapability.Communication.NetStack

## cookies

```TypeScript
cookies: string
```

Original cookies returned by the server. How to process the cookies is up to your decision.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## header

```TypeScript
header: Object
```

Response header. The return value is a string in JSON format. If you want to use specific content in the response, you need to implement parsing of that content. Common fields and parsing methods are as follows:

- content-type: header['content-type']  
- status-line: header['status-line']  
- date: header.date/header['date']  
- server: header.server/header['server']

**Type:** Object

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## performanceTiming

```TypeScript
performanceTiming: PerformanceTiming
```

Time consumed in each phase of an HTTP request.

**Type:** [PerformanceTiming](arkts-network-http-performancetiming-i.md)

**Since:** 11

**System capability:** SystemCapability.Communication.NetStack

## responseCode

```TypeScript
responseCode: ResponseCode | number
```

Result code for an HTTP request. If the callback function is successfully executed, a result code defined in [ResponseCode](arkts-network-http-responsecode-e.md) will be returned. Otherwise, an error code will be returned in the **err** field in **AsyncCallback**.

**Type:** [ResponseCode](arkts-network-http-responsecode-e.md) &#124; number

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## result

```TypeScript
result: string | Object | ArrayBuffer
```

Response content returned based on **Content-type** in the response header. If **HttpRequestOptions** does not contain the **expectDataType** field, the response content is returned according to the following rules:

- application/json: string in JSON format  
- application/octet-stream: ArrayBuffer  
- image: ArrayBuffer  
- Others: string

If **HttpRequestOptions** contains the **expectDataType** field, the response content must be of the same type as the data returned by the server.

**Type:** string &#124; Object &#124; ArrayBuffer

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack

## resultType

```TypeScript
resultType: HttpDataType
```

Type of the return value.

**Type:** [HttpDataType](arkts-network-http-httpdatatype-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetStack
