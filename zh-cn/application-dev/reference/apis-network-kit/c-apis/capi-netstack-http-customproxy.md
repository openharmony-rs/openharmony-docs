# Http_CustomProxy

```c
typedef struct Http_CustomProxy {...} Http_CustomProxy
```

## 概述

用户自定义代理配置。

<!--Device-struct Http_CustomProxy {...}--><!--Device-struct Http_CustomProxy {...}-End-->

**系统能力：** SystemCapability.Communication.NetStack

**起始版本：** 20

**相关模块：** [netstack](capi-network-kit-netstack.md)

**所在头文件：** [net_http_type.h](capi-net-http-type-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| const char *host | 代理服务器主机名，如果没有显式设置端口，端口将默认为1080。<br><!--Device-const char *host--><!--Device-const char *host-End--> |
| int32_t port | 主机端口。取值范围[0, 65535]。<br><!--Device-int32_t port--><!--Device-int32_t port-End--> |
| const char *exclusionLists | 不使用代理的主机名列表，主机名支持域名、IP地址以及通配符形式。<br><!--Device-const char *exclusionLists--><!--Device-const char *exclusionLists-End--> |


