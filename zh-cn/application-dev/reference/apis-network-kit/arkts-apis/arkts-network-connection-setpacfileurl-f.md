# setPacFileUrl

## 导入模块

```TypeScript
```

## setPacFileUrl

```TypeScript
function setPacFileUrl(pacFileUrl: string): void
```

设置PAC脚本（Proxy Auto-Configuration Script，代理自动配置脚本）的URL地址，并启动PAC代理能力，比如：http://127.0.0.1:21998/PacProxyScript.pac 。可通 过调用[findProxyForUrl](arkts-network-connection-findproxyforurl-f.md)解析URL地址来获取代理信息。

> **注意：**
> 
> 1、本接口当前在PC/2in1&lt;sup&gt;20+&lt;/sup&gt;、Phone&lt;sup&gt;23+&lt;/sup&gt;、Tablet&lt;sup&gt;23+&lt;/sup&gt;、TV&lt;sup&gt;23+&lt;/sup&gt;设备上支持解析脚本并启用PAC代理能力，
> Wearable设备类型上只保存脚本地址，不会启用PAC代理能力。

> 2、该接口不会校验URL真实性，在启动PAC代理时，若URL有误，则启动代理失败，返回2100002错误码。

**起始版本：** 20

**需要权限：** ohos.permission.SET_PAC_URL

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pacFileUrl | string | 是 | 当前PAC脚本的URL地址。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

let pacFileUrl = "http://example.com/proxy.pac";
connection.setPacFileUrl(pacFileUrl);
```
