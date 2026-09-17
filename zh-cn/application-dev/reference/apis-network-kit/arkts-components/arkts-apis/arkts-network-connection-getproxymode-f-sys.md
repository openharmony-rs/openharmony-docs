# getProxyMode（系统接口）

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getProxyMode

```TypeScript
function getProxyMode(): Promise<ProxyMode>
```

获取当前的代理模式。使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ProxyMode](arkts-network-connection-proxymode-e-sys.md)&gt; | Promise对象，返回当前代理模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getProxyMode().then(mode => {
    console.info("Current proxy mode:", mode);
}).catch((error: BusinessError) => {
    console.error("Error getting proxy mode:", error);
});
```
