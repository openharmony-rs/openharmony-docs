# Network

**起始版本：** 3

<!--Device-unnamed-export default class Network--><!--Device-unnamed-export default class Network-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
```

## getType

```TypeScript
static getType(options?: {
    /**
     * Called when the network type is obtained.
     * @syscap SystemCapability.Communication.NetManager.Core
     * @since 3
     */
    success?: (data: NetworkResponse) => void;
    /**
     * Called when the network type fails to be obtained.
     * @syscap SystemCapability.Communication.NetManager.Core
     * @since 3
     */
    fail?: (data: any, code: number) => void;
    /**
     * Called when the execution is completed.
     * @syscap SystemCapability.Communication.NetManager.Core
     * @since 3
     */
    complete?: () => void;
  }): void
```

Obtains the network type.

**起始版本：** 3

<!--Device-Network-static getType(options?: {    /**     * Called when the network type is obtained.     * @syscap SystemCapability.Communication.NetManager.Core     * @since 3     */    success?: (data: NetworkResponse) => void;    /**     * Called when the network type fails to be obtained.     * @syscap SystemCapability.Communication.NetManager.Core     * @since 3     */    fail?: (data: any, code: number) => void;    /**     * Called when the execution is completed.     * @syscap SystemCapability.Communication.NetManager.Core     * @since 3     */    complete?: () => void;  }): void--><!--Device-Network-static getType(options?: {    /**     * Called when the network type is obtained.     * @syscap SystemCapability.Communication.NetManager.Core     * @since 3     */    success?: (data: NetworkResponse) => void;    /**     * Called when the network type fails to be obtained.     * @syscap SystemCapability.Communication.NetManager.Core     * @since 3     */    fail?: (data: any, code: number) => void;    /**     * Called when the execution is completed.     * @syscap SystemCapability.Communication.NetManager.Core     * @since 3     */    complete?: () => void;  }): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | {     /**      * Called when the network type is obtained.      * @syscap SystemCapability.Communication.NetManager.Core      * @since 3      */     success?: (data: NetworkResponse) =&gt; void;     /**      * Called when the network type fails to be obtained.      * @syscap SystemCapability.Communication.NetManager.Core      * @since 3      */     fail?: (data: any, code: number) =&gt; void;     /**      * Called when the execution is completed.      * @syscap SystemCapability.Communication.NetManager.Core      * @since 3      */     complete?: () =&gt; void;   } | 否 | Options. |

## subscribe

```TypeScript
static subscribe(options?: {
    /**
     * Called when the network connection state changes.
     * @syscap SystemCapability.Communication.NetManager.Core
     * @since 3
     */
    success?: (data: NetworkResponse) => void;
    /**
     * Called when the listening fails.
     * @syscap SystemCapability.Communication.NetManager.Core
     * @since 3
     */
    fail?: (data: any, code: number) => void;
  }): void
```

Listens to the network connection state. If this method is called multiple times, the last call takes effect.

**起始版本：** 3

<!--Device-Network-static subscribe(options?: {    /**     * Called when the network connection state changes.     * @syscap SystemCapability.Communication.NetManager.Core     * @since 3     */    success?: (data: NetworkResponse) => void;    /**     * Called when the listening fails.     * @syscap SystemCapability.Communication.NetManager.Core     * @since 3     */    fail?: (data: any, code: number) => void;  }): void--><!--Device-Network-static subscribe(options?: {    /**     * Called when the network connection state changes.     * @syscap SystemCapability.Communication.NetManager.Core     * @since 3     */    success?: (data: NetworkResponse) => void;    /**     * Called when the listening fails.     * @syscap SystemCapability.Communication.NetManager.Core     * @since 3     */    fail?: (data: any, code: number) => void;  }): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | {     /**      * Called when the network connection state changes.      * @syscap SystemCapability.Communication.NetManager.Core      * @since 3      */     success?: (data: NetworkResponse) =&gt; void;     /**      * Called when the listening fails.      * @syscap SystemCapability.Communication.NetManager.Core      * @since 3      */     fail?: (data: any, code: number) =&gt; void;   } | 否 | Options. |

## unsubscribe

```TypeScript
static unsubscribe(): void
```

取消监听网络连接状态。

**起始版本：** 3

<!--Device-Network-static unsubscribe(): void--><!--Device-Network-static unsubscribe(): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

