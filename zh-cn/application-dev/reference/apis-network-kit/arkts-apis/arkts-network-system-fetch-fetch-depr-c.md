# Fetch

**表1** data与Content-Type关系 | data | Content-Type | 说明 | | -------- | -------- | -------- | | string | 不设置 | Content-Type默认为&nbsp;text/plain，data值作为请求的body。 | | string | 任意&nbsp;Type | data值作为请求的body。 | | Object | 不设置 | Content-Type默认为application/x-www-form-urlencoded，data按照资源地址规则进行encode拼接作为请求的body。 | | Object | application/x-www-form-urlencoded | data按照资源地址规则进行encode拼接作为请求的body。 |

**起始版本：** 3

<!--Device-unnamed-export default class Fetch--><!--Device-unnamed-export default class Fetch-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

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

**起始版本：** 3

<!--Device-Fetch-static fetch(options: {    /**     * Resource URL.     * @syscap SystemCapability.Communication.NetStack     * @since 3     */    url: string;    /**     * Request parameter, which can be of the string type or a JSON object.     * @syscap SystemCapability.Communication.NetStack     * @since 3     */    data?: string | object;    /**     * Request header, which accommodates all attributes of the request.     * @syscap SystemCapability.Communication.NetStack     * @since 3     */    header?: Object;    /**     * Request methods available: OPTIONS, GET, HEAD, POST, PUT, DELETE and TRACE. The default value is GET.     * @syscap SystemCapability.Communication.NetStack     * @since 3     */    method?: string;    /**     * The return type can be text, or JSON. By default, the return type is determined based on Content-Type in the header returned by the server.     * @syscap SystemCapability.Communication.NetStack     * @since 3     */    responseType?: string;    /**     * Called when the network data is obtained successfully.     * @syscap SystemCapability.Communication.NetStack     * @since 3     */    success?: (data: FetchResponse) => void;    /**     * Called when the network data fails to be obtained.     * @syscap SystemCapability.Communication.NetStack     * @since 3     */    fail?: (data: any, code: number) => void;    /**     * Called when the execution is completed.     * @syscap SystemCapability.Communication.NetStack     * @since 3     */    complete?: () => void;  }): void--><!--Device-Fetch-static fetch(options: {    /**     * Resource URL.     * @syscap SystemCapability.Communication.NetStack     * @since 3     */    url: string;    /**     * Request parameter, which can be of the string type or a JSON object.     * @syscap SystemCapability.Communication.NetStack     * @since 3     */    data?: string | object;    /**     * Request header, which accommodates all attributes of the request.     * @syscap SystemCapability.Communication.NetStack     * @since 3     */    header?: Object;    /**     * Request methods available: OPTIONS, GET, HEAD, POST, PUT, DELETE and TRACE. The default value is GET.     * @syscap SystemCapability.Communication.NetStack     * @since 3     */    method?: string;    /**     * The return type can be text, or JSON. By default, the return type is determined based on Content-Type in the header returned by the server.     * @syscap SystemCapability.Communication.NetStack     * @since 3     */    responseType?: string;    /**     * Called when the network data is obtained successfully.     * @syscap SystemCapability.Communication.NetStack     * @since 3     */    success?: (data: FetchResponse) => void;    /**     * Called when the network data fails to be obtained.     * @syscap SystemCapability.Communication.NetStack     * @since 3     */    fail?: (data: any, code: number) => void;    /**     * Called when the execution is completed.     * @syscap SystemCapability.Communication.NetStack     * @since 3     */    complete?: () => void;  }): void-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | {     /**      * Resource URL.      * @syscap SystemCapability.Communication.NetStack      * @since 3      */     url: string;      /**      * Request parameter, which can be of the string type or a JSON object.      * @syscap SystemCapability.Communication.NetStack      * @since 3      */     data?: string \| object;      /**      * Request header, which accommodates all attributes of the request.      * @syscap SystemCapability.Communication.NetStack      * @since 3      */     header?: Object;      /**      * Request methods available: OPTIONS, GET, HEAD, POST, PUT, DELETE and TRACE. The default value is GET.      * @syscap SystemCapability.Communication.NetStack      * @since 3      */     method?: string;      /**      * The return type can be text, or JSON. By default, the return type is determined based on Content-Type in the header returned by the server.      * @syscap SystemCapability.Communication.NetStack      * @since 3      */     responseType?: string;      /**      * Called when the network data is obtained successfully.      * @syscap SystemCapability.Communication.NetStack      * @since 3      */     success?: (data: FetchResponse) =&gt; void;      /**      * Called when the network data fails to be obtained.      * @syscap SystemCapability.Communication.NetStack      * @since 3      */     fail?: (data: any, code: number) =&gt; void;      /**      * Called when the execution is completed.      * @syscap SystemCapability.Communication.NetStack      * @since 3      */     complete?: () =&gt; void;   } | 是 | Options. |

