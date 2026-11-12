# RequestMethod

```TypeScript
export enum RequestMethod
```

Defines an HTTP request method.

**Since:** 6

<!--Device-http-export enum RequestMethod--><!--Device-http-export enum RequestMethod-End-->

**System capability:** SystemCapability.Communication.NetStack

## CONNECT

```TypeScript
CONNECT = "CONNECT"
```

Establishes a tunnel to the server identified by the target resource.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RequestMethod-CONNECT = "CONNECT"--><!--Device-RequestMethod-CONNECT = "CONNECT"-End-->

**System capability:** SystemCapability.Communication.NetStack

## DELETE

```TypeScript
DELETE = "DELETE"
```

Deletes the specified resource.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RequestMethod-DELETE = "DELETE"--><!--Device-RequestMethod-DELETE = "DELETE"-End-->

**System capability:** SystemCapability.Communication.NetStack

## GET

```TypeScript
GET = "GET"
```

Requests a representation of the specified resource. Requests using **GET** should only retrieve data and should not contain a request body.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RequestMethod-GET = "GET"--><!--Device-RequestMethod-GET = "GET"-End-->

**System capability:** SystemCapability.Communication.NetStack

## HEAD

```TypeScript
HEAD = "HEAD"
```

Requests or a response identical to that of a **GET** request, but without the response body.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RequestMethod-HEAD = "HEAD"--><!--Device-RequestMethod-HEAD = "HEAD"-End-->

**System capability:** SystemCapability.Communication.NetStack

## OPTIONS

```TypeScript
OPTIONS = "OPTIONS"
```

Describes the communication options for the target resource.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RequestMethod-OPTIONS = "OPTIONS"--><!--Device-RequestMethod-OPTIONS = "OPTIONS"-End-->

**System capability:** SystemCapability.Communication.NetStack

## PATCH

```TypeScript
PATCH = "PATCH"
```

Applies partial modifications to a resource.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RequestMethod-PATCH = "PATCH"--><!--Device-RequestMethod-PATCH = "PATCH"-End-->

**System capability:** SystemCapability.Communication.NetStack

## POST

```TypeScript
POST = "POST"
```

Submits an entity to the specified resource, often causing a change in state on the server.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RequestMethod-POST = "POST"--><!--Device-RequestMethod-POST = "POST"-End-->

**System capability:** SystemCapability.Communication.NetStack

## PUT

```TypeScript
PUT = "PUT"
```

Replaces all current representations of the target resource with the request content.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RequestMethod-PUT = "PUT"--><!--Device-RequestMethod-PUT = "PUT"-End-->

**System capability:** SystemCapability.Communication.NetStack

## TRACE

```TypeScript
TRACE = "TRACE"
```

Performs a message loop-back test along the path to the target resource.

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-RequestMethod-TRACE = "TRACE"--><!--Device-RequestMethod-TRACE = "TRACE"-End-->

**System capability:** SystemCapability.Communication.NetStack
