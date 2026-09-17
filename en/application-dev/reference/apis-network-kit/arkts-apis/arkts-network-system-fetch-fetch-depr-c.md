# Fetch

**Table 1** Mapping between data and Content-Type

| data | Content-Type | Description|  
| -------- | -------- | -------- |  
| string | Left unspecified| The default value of Content-Type is **text/plain**, and the value of data is used as the request body.|
| string | Any type| The value of data is used as the request body.|
| Object | Left unspecified| The default value of **Content-Type** is **application/x-www-form-urlencoded**. The **data** value is encoded based on the URL rule and appended in the request body.|
| Object | application/x-www-form-urlencoded | The value of data is encoded based on the URL rule and is used as the request body.|

**Since:** 3

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
```

## fetch

```TypeScript
static fetch(options: {
    /**
     * Resource URL.
     * @syscap SystemCapability.Communication.NetStack
     * @since 3
     */
    url: string;

    /**
     * Request parameter, which can be of the string type or a JSON object.
     * @syscap SystemCapability.Communication.NetStack
     * @since 3
     */
    data?: string | object;

    /**
     * Request header, which accommodates all attributes of the request.
     * @syscap SystemCapability.Communication.NetStack
     * @since 3
     */
    header?: Object;

    /**
     * Request methods available: OPTIONS, GET, HEAD, POST, PUT, DELETE and TRACE. The default value is GET.
     * @syscap SystemCapability.Communication.NetStack
     * @since 3
     */
    method?: string;

    /**
     * The return type can be text, or JSON. By default, the return type is determined based on Content-Type in the header returned by the server.
     * @syscap SystemCapability.Communication.NetStack
     * @since 3
     */
    responseType?: string;

    /**
     * Called when the network data is obtained successfully.
     * @syscap SystemCapability.Communication.NetStack
     * @since 3
     */
    success?: (data: FetchResponse) => void;

    /**
     * Called when the network data fails to be obtained.
     * @syscap SystemCapability.Communication.NetStack
     * @since 3
     */
    fail?: (data: any, code: number) => void;

    /**
     * Called when the execution is completed.
     * @syscap SystemCapability.Communication.NetStack
     * @since 3
     */
    complete?: () => void;
  }): void
```

Obtains data through the network.

**Since:** 3

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | {     /**      * Resource URL.      * @syscap SystemCapability.Communication.NetStack      * @since 3      */     url: string;      /**      * Request parameter, which can be of the string type or a JSON object.      * @syscap SystemCapability.Communication.NetStack      * @since 3      */     data?: string &#124; object;      /**      * Request header, which accommodates all attributes of the request.      * @syscap SystemCapability.Communication.NetStack      * @since 3      */     header?: Object;      /**      * Request methods available: OPTIONS, GET, HEAD, POST, PUT, DELETE and TRACE. The default value is GET.      * @syscap SystemCapability.Communication.NetStack      * @since 3      */     method?: string;      /**      * The return type can be text, or JSON. By default, the return type is determined based on Content-Type in the header returned by the server.      * @syscap SystemCapability.Communication.NetStack      * @since 3      */     responseType?: string;      /**      * Called when the network data is obtained successfully.      * @syscap SystemCapability.Communication.NetStack      * @since 3      */     success?: (data: FetchResponse) =&gt; void;      /**      * Called when the network data fails to be obtained.      * @syscap SystemCapability.Communication.NetStack      * @since 3      */     fail?: (data: any, code: number) =&gt; void;      /**      * Called when the execution is completed.      * @syscap SystemCapability.Communication.NetStack      * @since 3      */     complete?: () =&gt; void;   } | Yes | Options. |
