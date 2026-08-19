# Socks5Proxy

SOCKS5代理配置信息。

**起始版本：** 26.0.0

<!--Device-connection-export interface Socks5Proxy--><!--Device-connection-export interface Socks5Proxy-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## dnsStrategy

```TypeScript
dnsStrategy?: Socks5DnsStrategy
```

指定DNS解析由系统执行还是由代理服务器执行。 **说明:** 当此项未指定时，如果host有`socks5h://`协议前缀，则DNS解析由代理服务器执行，否则DNS解析由系统执行。

**类型：** [Socks5DnsStrategy](arkts-network-connection-socks5dnsstrategy-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Socks5Proxy-dnsStrategy?: Socks5DnsStrategy--><!--Device-Socks5Proxy-dnsStrategy?: Socks5DnsStrategy-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## exclusionList

```TypeScript
exclusionList?: Array<string>
```

不使用代理的主机名列表，主机名支持域名、IP地址以及通配符形式，详细匹配规则如下： 1、域名匹配规则： （1）完全匹配：代理服务器主机名只要与列表中的任意一个主机名完全相同，就可以匹配。 （2）包含匹配：代理服务器主机名只要包含列表中的任意一个主机名，就可以匹配。 例如，如果在主机名列表中设置了“example.com”，则“example.com”、“www.example.com”、“example.com:80”都会被匹配，而 “www.myexample.com”、“ myexample.com.org”则不会被匹配。 2、IP地址匹配规则：代理服务器主机名只要与列表中的任意一个IP地址完全相同，就可以匹配。 3、域名跟IP地址可以同时添加到列表中进行匹配。 4、单个“*”是唯一有效的通配符，当列表中只有通配符时，将与所有代理服务器主机名匹配，表示禁用代理。通配符只能单独添加，不可以与其他域名、IP地址一起添加到列表中，否则通配符将不生效。 5、匹配规则不区分主机名大小写。 6、匹配主机名时，不考虑http、https、socks5、socks5h等协议前缀。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Socks5Proxy-exclusionList?: Array<string>--><!--Device-Socks5Proxy-exclusionList?: Array<string>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## host

```TypeScript
host: string
```

代理服务器主机名。 **说明:** 当该项为空字符串时，视为未配置SOCKS5代理。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Socks5Proxy-host: string--><!--Device-Socks5Proxy-host: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## password

```TypeScript
password?: string
```

使用代理的用户密码。 **说明:** 需同时设置username参数才会生效。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Socks5Proxy-password?: string--><!--Device-Socks5Proxy-password?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## port

```TypeScript
port: int
```

主机端口。取值范围[0, 65535]。 **说明:** 当参数不在上述取值范围时，视为未配置SOCKS5代理。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Socks5Proxy-port: int--><!--Device-Socks5Proxy-port: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## username

```TypeScript
username?: string
```

使用代理的用户名。 **说明:** 需同时设置password参数才会生效。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Socks5Proxy-username?: string--><!--Device-Socks5Proxy-username?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

