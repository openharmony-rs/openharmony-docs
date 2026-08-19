# findProxyForUrl

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## findProxyForUrl

```TypeScript
function findProxyForUrl(url: string): string
```

通过设置的PAC脚本，解析指定的URL代理地址，返回对应的PAC代理信息。 > **说明：** > > 1、可通过 [setPacFileUrl](arkts-network-connection-setpacfileurl-f.md) 或 [setPacUrl](arkts-network-connection-setpacurl-f.md) 设置PAC脚本。 > 2、如果调用本接口前未设置PAC脚本，则返回空字符串。 > 3、由于[setPacFileUrl](arkts-network-connection-setpacfileurl-f.md)接口支持PC/2in1&lt;sup&gt;20+&lt;/sup&gt;、Phone&lt;sup&gt;23+&lt;/sup&gt;、Tablet&lt;sup&gt;23+&lt;/ &gt; sup>、TV&lt;sup&gt;23+&lt;/sup&gt;设备解析脚本并启用PAC代理能力，因此本接口支持以上设备获取PAC代理信息。 Wearable设备调用本接口功能不生效，返回空字串。

**起始版本：** 20

<!--Device-connection-function findProxyForUrl(url: string): string--><!--Device-connection-function findProxyForUrl(url: string): string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 要查找代理信息的URL。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回代理信息。 |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

let proxyInfo = connection.findProxyForUrl("http://example.com");
console.info(proxyInfo);
```

