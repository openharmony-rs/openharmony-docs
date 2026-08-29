# Network

**起始版本：** 3

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

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | {     /**      * Called when the network type is obtained.      * @syscap SystemCapability.Communication.NetManager.Core      * @since 3      */     success?: (data: NetworkResponse) =&gt; void;     /**      * Called when the network type fails to be obtained.      * @syscap SystemCapability.Communication.NetManager.Core      * @since 3      */     fail?: (data: any, code: number) =&gt; void;     /**      * Called when the execution is completed.      * @syscap SystemCapability.Communication.NetManager.Core      * @since 3      */     complete?: () =&gt; void;   } | 否 | Options. |

**示例**

```TypeScript
export default class Network {
  getType() {
    network.getType({
      success: (data) => {
        console.info('success get network type:' + data.type);
      }
    });
  }
}
```

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

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | {     /**      * Called when the network connection state changes.      * @syscap SystemCapability.Communication.NetManager.Core      * @since 3      */     success?: (data: NetworkResponse) =&gt; void;     /**      * Called when the listening fails.      * @syscap SystemCapability.Communication.NetManager.Core      * @since 3      */     fail?: (data: any, code: number) =&gt; void;   } | 否 | Options. |

**示例**

```TypeScript
export default class Network {
  subscribe() {
    network.subscribe({
      success: (data) => {
        console.info('success get network type:' + data.type);
      }
    });
  }
}
```

## unsubscribe

```TypeScript
static unsubscribe(): void
```

取消监听网络连接状态。

**起始版本：** 3

**系统能力：** SystemCapability.Communication.NetManager.Core

**示例**

```TypeScript
import network from '@system.network';

network.unsubscribe();
```
