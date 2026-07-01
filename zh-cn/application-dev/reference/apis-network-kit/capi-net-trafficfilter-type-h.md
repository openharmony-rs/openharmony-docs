# net-trafficfilter-type.h

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

## 概述

定义流量过滤模块C接口需要的数据结构、宏定义和枚举类型。该模块提供流量重定向规则配置、IP/端口匹配条件、连接五元组信息、进程信息以及错误码定义。

**引用文件：** <network/netmanager_ext/net_trafficfilter_type.h>

**库：** libnet_trafficfilter.so

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**起始版本：** 26.0.0

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_TrafficFilter_IPAddress](#oh_trafficfilter_ipaddress) | OH_TrafficFilter_IPAddress | IP地址结构体，支持IPv4和IPv6。 |
| [OH_TrafficFilter_IPCidr](#oh_trafficfilter_ipcidr) | OH_TrafficFilter_IPCidr | CIDR格式IP匹配结构体。 |
| [OH_TrafficFilter_IPRange](#oh_trafficfilter_iprange) | OH_TrafficFilter_IPRange | IP范围匹配结构体。 |
| [OH_TrafficFilter_IPMulti](#oh_trafficfilter_ipmulti) | OH_TrafficFilter_IPMulti | 多IP匹配结构体。 |
| [OH_TrafficFilter_IPMatch](#oh_trafficfilter_ipmatch) | OH_TrafficFilter_IPMatch | IP匹配条件结构体。 |
| [OH_TrafficFilter_InterfaceMatch](#oh_trafficfilter_interfacematch) | OH_TrafficFilter_InterfaceMatch | 网络接口匹配条件结构体。 |
| [OH_TrafficFilter_PortRange](#oh_trafficfilter_portrange) | OH_TrafficFilter_PortRange | 端口范围匹配结构体。 |
| [OH_TrafficFilter_PortMulti](#oh_trafficfilter_portmulti) | OH_TrafficFilter_PortMulti | 多端口匹配结构体。 |
| [OH_TrafficFilter_PortMatch](#oh_trafficfilter_portmatch) | OH_TrafficFilter_PortMatch | 端口匹配条件结构体。 |
| [OH_TrafficFilter_ConnectionInfo](#oh_trafficfilter_connectioninfo) | OH_TrafficFilter_ConnectionInfo | 连接五元组信息结构体。 |
| [OH_TrafficFilter_ProcessInfo](#oh_trafficfilter_processinfo) | OH_TrafficFilter_ProcessInfo | 进程信息结构体。 |
| [OH_TrafficFilter_Redirector](#oh_trafficfilter_redirector) | OH_TrafficFilter_Redirector | 流量重定向实例句柄。 |
| [OH_TrafficFilter_RedirectRule](#oh_trafficfilter_redirectrule) | OH_TrafficFilter_RedirectRule | TCP流量重定向规则结构体。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_TrafficFilter_ErrCode](#oh_trafficfilter_errcode) | OH_TrafficFilter_ErrCode | 定义流量过滤模块错误码。 |
| [OH_TrafficFilter_IPMatchType](#oh_trafficfilter_ipmatchtype) | OH_TrafficFilter_IPMatchType | 定义IP匹配类型。 |
| [OH_TrafficFilter_IPFamily](#oh_trafficfilter_ipfamily) | OH_TrafficFilter_IPFamily | 定义IP地址族。 |
| [OH_TrafficFilter_PortMatchType](#oh_trafficfilter_portmatchtype) | OH_TrafficFilter_PortMatchType | 定义端口匹配类型。 |
| [OH_TrafficFilter_HookPoint](#oh_trafficfilter_hookpoint) | OH_TrafficFilter_HookPoint | 定义网络Hook点类型。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| OH_TRAFFICFILTER_IP_ADDRLEN 16 | IP地址最大长度，兼容IPv4和IPv6。IPv4使用前4字节，IPv6使用全部16字节。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_MAX_MULTI_IP_COUNT 16 | 多IP匹配支持的最大IP数量。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_MAX_MULTI_PORT_COUNT 64 | 多端口匹配支持的最大端口数量。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_NFQUEUE_COPY_META 0 | NFQueue数据包复制模式，仅复制元数据。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_NFQUEUE_COPY_PACKET 0xFFFF | NFQueue数据包复制模式，复制完整数据包。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_DEFAULT_COPY_LEN 0xFFFF | NFQueue默认数据包复制长度。设置为0xFFFF表示复制完整数据包，较小值表示只复制指定长度的数据。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_DEFAULT_QUEUE_MAXLEN 1024 | NFQueue默认最大队列长度，单位为数据包数量。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_NFQUEUE_FLAG_FAIL_OPEN 0x1 | NFQueue队列标志，FAIL-OPEN模式。用户态进程异常退出时，内核自动放行数据包以避免网络中断。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_MIN_PRIORITY 1 | 最小优先级值。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_MAX_PRIORITY 10000 | 最大优先级值。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_MIN_GROUP_ID 1 | 最小组ID值。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_MAX_GROUP_ID 65535 | 最大组ID值。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_IFNAMSIZ 32 | 网络接口名称最大长度。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_PROTO_ANY 0 | 任意协议。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_PROTO_TCP 6 | TCP协议。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_PROTO_UDP 17 | UDP协议。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_PROTO_ICMP 1 | ICMP协议。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_PROTO_ICMPV6 58 | ICMPv6协议。<br>**起始版本：** 26.0.0 |

## 枚举类型说明

### OH_TrafficFilter_ErrCode

```c
typedef enum OH_TrafficFilter_ErrCode {
    OH_TRAFFICFILTER_OK = 0,
    OH_TRAFFICFILTER_E_BASE = 29410000,
    OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED = 201,
    OH_TRAFFICFILTER_ERROR_INVALID_PARAM = (OH_TRAFFICFILTER_E_BASE + 101),
    OH_TRAFFICFILTER_ERROR_NOT_FOUND = (OH_TRAFFICFILTER_E_BASE + 102),
    OH_TRAFFICFILTER_ERROR_TOO_MANY_RULES = (OH_TRAFFICFILTER_E_BASE + 103),
    OH_TRAFFICFILTER_ERROR_GROUP_ID_IN_USE = (OH_TRAFFICFILTER_E_BASE + 104),
    OH_TRAFFICFILTER_ERROR_NFQUEUE_ERROR = (OH_TRAFFICFILTER_E_BASE + 105),
} OH_TrafficFilter_ErrCode;
```

**描述**

定义流量过滤模块错误码。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_TRAFFICFILTER_OK = 0 | 操作成功。 |
| OH_TRAFFICFILTER_E_BASE = 29410000 | 错误码基值。 |
| OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED = 201 | 权限被拒绝。 |
| OH_TRAFFICFILTER_ERROR_INVALID_PARAM = (OH_TRAFFICFILTER_E_BASE + 101) | 参数非法，例如优先级、IP地址、端口或组ID非法。 |
| OH_TRAFFICFILTER_ERROR_NOT_FOUND = (OH_TRAFFICFILTER_E_BASE + 102) | 资源未找到，例如规则、目标、进程或组ID不存在。 |
| OH_TRAFFICFILTER_ERROR_TOO_MANY_RULES = (OH_TRAFFICFILTER_E_BASE + 103) | 添加的规则数量超过限制。 |
| OH_TRAFFICFILTER_ERROR_GROUP_ID_IN_USE = (OH_TRAFFICFILTER_E_BASE + 104) | 组ID已被使用。 |
| OH_TRAFFICFILTER_ERROR_NFQUEUE_ERROR = (OH_TRAFFICFILTER_E_BASE + 105) | NFQueue错误，例如初始化失败或无可用队列。 |

### OH_TrafficFilter_IPMatchType

```c
typedef enum OH_TrafficFilter_IPMatchType {
    OH_TRAFFICFILTER_IP_MATCH_ANY = 0,
    OH_TRAFFICFILTER_IP_MATCH_SINGLE,
    OH_TRAFFICFILTER_IP_MATCH_CIDR,
    OH_TRAFFICFILTER_IP_MATCH_RANGE,
    OH_TRAFFICFILTER_IP_MATCH_MULTI
} OH_TrafficFilter_IPMatchType;
```

**描述**

定义IP匹配类型。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_TRAFFICFILTER_IP_MATCH_ANY = 0 | 匹配任意IP。 |
| OH_TRAFFICFILTER_IP_MATCH_SINGLE = 1 | 匹配单个IP。 |
| OH_TRAFFICFILTER_IP_MATCH_CIDR = 2 | 匹配CIDR格式的IP网段。 |
| OH_TRAFFICFILTER_IP_MATCH_RANGE = 3 | 匹配IP范围。 |
| OH_TRAFFICFILTER_IP_MATCH_MULTI = 4 | 匹配多个IP。 |

### OH_TrafficFilter_IPFamily

```c
typedef enum OH_TrafficFilter_IPFamily {
    OH_TRAFFICFILTER_IP_FAMILY_UNSPEC = 0,
    OH_TRAFFICFILTER_IP_FAMILY_V4 = 1,
    OH_TRAFFICFILTER_IP_FAMILY_V6 = 2
} OH_TrafficFilter_IPFamily;
```

**描述**

定义IP地址族。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_TRAFFICFILTER_IP_FAMILY_UNSPEC = 0 | 未指定IP地址族。 |
| OH_TRAFFICFILTER_IP_FAMILY_V4 = 1 | IPv4地址族。 |
| OH_TRAFFICFILTER_IP_FAMILY_V6 = 2 | IPv6地址族。 |

### OH_TrafficFilter_PortMatchType

```c
typedef enum OH_TrafficFilter_PortMatchType {
    OH_TRAFFICFILTER_PORT_MATCH_ANY = 0,
    OH_TRAFFICFILTER_PORT_MATCH_SINGLE,
    OH_TRAFFICFILTER_PORT_MATCH_RANGE,
    OH_TRAFFICFILTER_PORT_MATCH_MULTI
} OH_TrafficFilter_PortMatchType;
```

**描述**

定义端口匹配类型。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_TRAFFICFILTER_PORT_MATCH_ANY = 0 | 匹配任意端口。 |
| OH_TRAFFICFILTER_PORT_MATCH_SINGLE = 1 | 匹配单个端口。 |
| OH_TRAFFICFILTER_PORT_MATCH_RANGE = 2 | 匹配端口范围。 |
| OH_TRAFFICFILTER_PORT_MATCH_MULTI = 3 | 匹配多个端口。 |

### OH_TrafficFilter_HookPoint

```c
typedef enum OH_TrafficFilter_HookPoint {
    OH_TRAFFICFILTER_HOOK_INPUT = 0,
    OH_TRAFFICFILTER_HOOK_OUTPUT,
    OH_TRAFFICFILTER_HOOK_FORWARD,
    OH_TRAFFICFILTER_HOOK_PREROUTING,
    OH_TRAFFICFILTER_HOOK_POSTROUTING
} OH_TrafficFilter_HookPoint;
```

**描述**

定义网络Hook点类型。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_TRAFFICFILTER_HOOK_INPUT = 0 | INPUT链。 |
| OH_TRAFFICFILTER_HOOK_OUTPUT = 1 | OUTPUT链。 |
| OH_TRAFFICFILTER_HOOK_FORWARD = 2 | FORWARD链。 |
| OH_TRAFFICFILTER_HOOK_PREROUTING = 3 | PREROUTING链。 |
| OH_TRAFFICFILTER_HOOK_POSTROUTING = 4 | POSTROUTING链。 |

## 结构体说明

### OH_TrafficFilter_IPAddress

```c
typedef struct OH_TrafficFilter_IPAddress {
    OH_TrafficFilter_IPFamily family;
    uint8_t addr[OH_TRAFFICFILTER_IP_ADDRLEN];
} OH_TrafficFilter_IPAddress;
```

**描述**

IP地址结构体，支持IPv4和IPv6。

**起始版本：** 26.0.0

**成员：**

| 成员 | 描述 |
| -- | -- |
| OH_TrafficFilter_IPFamily family | 地址族。未显式设置时默认使用IPv4。 |
| uint8_t addr[OH_TRAFFICFILTER_IP_ADDRLEN] | IP地址字节数组，以网络字节序存储。IPv4使用addr[0]到addr[3]存储IPv4地址，addr[4]到addr[15]必须置0；IPv6使用addr[0]到addr[15]存储IPv6地址。若字节数据与family要求的地址布局不匹配，使用该结构体的接口将返回`OH_TRAFFICFILTER_ERROR_INVALID_PARAM`。 |

### OH_TrafficFilter_IPCidr

```c
typedef struct OH_TrafficFilter_IPCidr {
    OH_TrafficFilter_IPAddress base;
    uint8_t prefixLen;
} OH_TrafficFilter_IPCidr;
```

**描述**

CIDR格式IP匹配结构体。

**起始版本：** 26.0.0

**成员：**

| 成员 | 描述 |
| -- | -- |
| OH_TrafficFilter_IPAddress base | CIDR网段的基础IP地址。 |
| uint8_t prefixLen | CIDR前缀长度。IPv4合法范围为0~32，IPv6合法范围为0~128。 |

### OH_TrafficFilter_IPRange

```c
typedef struct OH_TrafficFilter_IPRange {
    OH_TrafficFilter_IPAddress start;
    OH_TrafficFilter_IPAddress end;
} OH_TrafficFilter_IPRange;
```

**描述**

IP范围匹配结构体。

**起始版本：** 26.0.0

**成员：**

| 成员 | 描述 |
| -- | -- |
| OH_TrafficFilter_IPAddress start | IP范围起始地址。 |
| OH_TrafficFilter_IPAddress end | IP范围结束地址。 |

### OH_TrafficFilter_IPMulti

```c
typedef struct OH_TrafficFilter_IPMulti {
    uint32_t ipCount;
    OH_TrafficFilter_IPAddress ips[OH_TRAFFICFILTER_MAX_MULTI_IP_COUNT];
} OH_TrafficFilter_IPMulti;
```

**描述**

多IP匹配结构体。

**起始版本：** 26.0.0

**成员：**

| 成员 | 描述 |
| -- | -- |
| uint32_t ipCount | IP地址数量。 |
| OH_TrafficFilter_IPAddress ips[OH_TRAFFICFILTER_MAX_MULTI_IP_COUNT] | IP地址数组。 |

### OH_TrafficFilter_IPMatch

```c
typedef struct OH_TrafficFilter_IPMatch {
    OH_TrafficFilter_IPMatchType type;
    bool invert;
    union {
        OH_TrafficFilter_IPAddress single;
        OH_TrafficFilter_IPCidr cidr;
        OH_TrafficFilter_IPRange range;
        OH_TrafficFilter_IPMulti multi;
    } value;
} OH_TrafficFilter_IPMatch;
```

**描述**

IP匹配条件结构体。

**起始版本：** 26.0.0

**成员：**

| 成员 | 描述 |
| -- | -- |
| OH_TrafficFilter_IPMatchType type | IP匹配类型。 |
| bool invert | 是否反转匹配结果。 |
| OH_TrafficFilter_IPAddress single | 单IP匹配值，当`type`为`OH_TRAFFICFILTER_IP_MATCH_SINGLE`时使用。 |
| OH_TrafficFilter_IPCidr cidr | CIDR匹配值，当`type`为`OH_TRAFFICFILTER_IP_MATCH_CIDR`时使用。 |
| OH_TrafficFilter_IPRange range | IP范围匹配值，当`type`为`OH_TRAFFICFILTER_IP_MATCH_RANGE`时使用。 |
| OH_TrafficFilter_IPMulti multi | 多IP匹配值，当`type`为`OH_TRAFFICFILTER_IP_MATCH_MULTI`时使用。 |

### OH_TrafficFilter_InterfaceMatch

```c
typedef struct OH_TrafficFilter_InterfaceMatch {
    bool enabled;
    bool invert;
    bool isPrefix;
    char ifName[OH_TRAFFICFILTER_IFNAMSIZ];
} OH_TrafficFilter_InterfaceMatch;
```

**描述**

网络接口匹配条件结构体。

**起始版本：** 26.0.0

**成员：**

| 成员 | 描述 |
| -- | -- |
| bool enabled | 是否启用接口匹配。 |
| bool invert | 是否反转匹配结果。 |
| bool isPrefix | 是否按接口名前缀进行匹配。 |
| char ifName[OH_TRAFFICFILTER_IFNAMSIZ] | 接口名称。字符串必须以UTF-8编码且以NUL结尾。缓冲区容量为`OH_TRAFFICFILTER_IFNAMSIZ`字节，含终止NUL字符，因此接口名最大长度为`OH_TRAFFICFILTER_IFNAMSIZ - 1`字节（不含终止NUL）。若`enabled`为true，此字符串不能为空。若字符串在`OH_TRAFFICFILTER_IFNAMSIZ`字节内未NUL结尾，或其长度超过`OH_TRAFFICFILTER_IFNAMSIZ - 1`字节，使用该结构体的接口将返回`OH_TRAFFICFILTER_ERROR_INVALID_PARAM`。若`enabled`为false，此字段被忽略，建议将缓冲区清零。 |

### OH_TrafficFilter_PortRange

```c
typedef struct OH_TrafficFilter_PortRange {
    uint16_t startPort;
    uint16_t endPort;
} OH_TrafficFilter_PortRange;
```

**描述**

端口范围匹配结构体。

**起始版本：** 26.0.0

**成员：**

| 成员 | 描述 |
| -- | -- |
| uint16_t startPort | 端口范围起始端口。 |
| uint16_t endPort | 端口范围结束端口。 |

### OH_TrafficFilter_PortMulti

```c
typedef struct OH_TrafficFilter_PortMulti {
    uint32_t portCount;
    uint16_t ports[OH_TRAFFICFILTER_MAX_MULTI_PORT_COUNT];
} OH_TrafficFilter_PortMulti;
```

**描述**

多端口匹配结构体。

**起始版本：** 26.0.0

**成员：**

| 成员 | 描述 |
| -- | -- |
| uint32_t portCount | 端口数量。 |
| uint16_t ports[OH_TRAFFICFILTER_MAX_MULTI_PORT_COUNT] | 端口数组。 |

### OH_TrafficFilter_PortMatch

```c
typedef struct OH_TrafficFilter_PortMatch {
    OH_TrafficFilter_PortMatchType type;
    bool invert;
    union {
        uint16_t single;
        OH_TrafficFilter_PortRange range;
        OH_TrafficFilter_PortMulti multi;
    } value;
} OH_TrafficFilter_PortMatch;
```

**描述**

端口匹配条件结构体。

**起始版本：** 26.0.0

**成员：**

| 成员 | 描述 |
| -- | -- |
| OH_TrafficFilter_PortMatchType type | 端口匹配类型。 |
| bool invert | 是否反转匹配结果。 |
| uint16_t single | 单端口匹配值，当`type`为`OH_TRAFFICFILTER_PORT_MATCH_SINGLE`时使用。 |
| OH_TrafficFilter_PortRange range | 端口范围匹配值，当`type`为`OH_TRAFFICFILTER_PORT_MATCH_RANGE`时使用。 |
| OH_TrafficFilter_PortMulti multi | 多端口匹配值，当`type`为`OH_TRAFFICFILTER_PORT_MATCH_MULTI`时使用。 |

### OH_TrafficFilter_ConnectionInfo

```c
typedef struct OH_TrafficFilter_ConnectionInfo {
    uint32_t size;
    OH_TrafficFilter_IPAddress srcIp;
    uint16_t srcPort;
    OH_TrafficFilter_IPAddress dstIp;
    uint16_t dstPort;
    uint8_t protocol;
} OH_TrafficFilter_ConnectionInfo;
```

**描述**

连接五元组信息结构体。

**初始化规则：** 调用`OH_TrafficFilter_QueryProcess`前，调用方必须将此结构体清零（例如使用memset），然后将`size`设置为调用方实际分配的结构体大小，通常为sizeof(OH_TrafficFilter_ConnectionInfo)。

**ABI兼容性规则：** 库侧根据`size`判断可安全读取的字段范围。若`size`小于当前API要求的最小大小，函数返回`OH_TRAFFICFILTER_ERROR_INVALID_PARAM`。若`size`大于库侧已知的大小，多余字段被忽略。未来版本新增字段在未使用时应保持零值初始化。

**起始版本：** 26.0.0

**成员：**

| 成员 | 描述 |
| -- | -- |
| uint32_t size | 调用方实际分配的结构体大小。调用接口前必须设置。 |
| OH_TrafficFilter_IPAddress srcIp | 源IP地址，支持IPv4和IPv6。 |
| uint16_t srcPort | 源端口。0表示任意源端口。 |
| OH_TrafficFilter_IPAddress dstIp | 目的IP地址，支持IPv4和IPv6。 |
| uint16_t dstPort | 目的端口。0表示任意目的端口。 |
| uint8_t protocol | 协议类型。支持 `OH_TRAFFICFILTER_PROTO_TCP` 和 `OH_TRAFFICFILTER_PROTO_UDP`。 |

### OH_TrafficFilter_ProcessInfo

```c
typedef struct OH_TrafficFilter_ProcessInfo {
    uint32_t size;
    uint32_t pid;
    uint32_t uid;
} OH_TrafficFilter_ProcessInfo;
```

**描述**

进程信息结构体。

**初始化规则：** 调用`OH_TrafficFilter_QueryProcess`前，调用方必须将此结构体清零（例如使用memset），然后将`size`设置为调用方实际分配的结构体大小，通常为sizeof(OH_TrafficFilter_ProcessInfo)。

**ABI兼容性规则：** 库侧根据`size`判断可安全写入的输出字段范围。仅`size`完全覆盖的字段才会被库侧写入。若`size`小于读取`size`字段自身所需的最小大小，函数返回`OH_TRAFFICFILTER_ERROR_INVALID_PARAM`。若`size`大于库侧已知的大小，多余字段被忽略。

**输出有效性规则：** 当`OH_TrafficFilter_QueryProcess`返回`OH_TRAFFICFILTER_OK`时，`size`覆盖范围内的字段包含有效输出值。当函数返回错误时，调用方不得依赖`size`以外的输出字段值。

**起始版本：** 26.0.0

**成员：**

| 成员 | 描述 |
| -- | -- |
| uint32_t size | 调用方实际分配的结构体大小。调用接口前必须设置。库侧只回填`size`覆盖范围内的字段。 |
| uint32_t pid | 进程ID。 |
| uint32_t uid | 用户ID。 |

### OH_TrafficFilter_Redirector

```c
typedef struct OH_TrafficFilter_Redirector OH_TrafficFilter_Redirector;
```

**描述**

流量重定向实例句柄。

**起始版本：** 26.0.0

### OH_TrafficFilter_RedirectRule

```c
typedef struct OH_TrafficFilter_RedirectRule {
    uint32_t size;
    uint32_t priority;
    OH_TrafficFilter_HookPoint hookPoint;
    uint8_t protocol;
    OH_TrafficFilter_IPMatch srcIp;
    OH_TrafficFilter_PortMatch srcPort;
    OH_TrafficFilter_IPMatch dstIp;
    OH_TrafficFilter_PortMatch dstPort;
    OH_TrafficFilter_InterfaceMatch inInterface;
    OH_TrafficFilter_InterfaceMatch outInterface;
    uint32_t uidStart;
    uint32_t uidEnd;
    OH_TrafficFilter_IPAddress proxyIp;
    uint16_t proxyPort;
} OH_TrafficFilter_RedirectRule;
```

**描述**

TCP流量重定向规则结构体，用于将匹配条件的流量重定向到指定代理服务器。

**初始化规则：** 调用`OH_TrafficFilter_AddRedirectRule`前，调用方必须将此结构体清零（例如使用memset），然后将`size`设置为调用方实际分配的结构体大小，通常为sizeof(OH_TrafficFilter_RedirectRule)。

**ABI兼容性规则：** 库侧根据`size`判断可安全读取的字段范围。若`size`小于当前API要求的最小大小，函数返回`OH_TRAFFICFILTER_ERROR_INVALID_PARAM`。若`size`大于库侧已知的大小，多余字段被忽略。未来版本新增字段在未使用时应保持零值初始化。

**失败规则：** 若`OH_TrafficFilter_AddRedirectRule`返回错误，该规则不保证已被添加或生效，调用方应在确认返回值后再假定规则生效。

**起始版本：** 26.0.0

**成员：**

| 成员 | 描述 |
| -- | -- |
| uint32_t size | 调用方实际分配的结构体大小。调用接口前必须设置。 |
| uint32_t priority | 规则优先级。数值越小优先级越高，与包过滤规则优先级规则一致。 |
| OH_TrafficFilter_HookPoint hookPoint | Hook点。当前重定向规则仅支持`OH_TRAFFICFILTER_HOOK_PREROUTING`和`OH_TRAFFICFILTER_HOOK_OUTPUT`。 |
| uint8_t protocol | 协议类型。当前重定向规则固定为TCP，即 `OH_TRAFFICFILTER_PROTO_TCP`。 |
| OH_TrafficFilter_IPMatch srcIp | 源IP匹配条件。 |
| OH_TrafficFilter_PortMatch srcPort | 源端口匹配条件。 |
| OH_TrafficFilter_IPMatch dstIp | 目的IP匹配条件。 |
| OH_TrafficFilter_PortMatch dstPort | 目的端口匹配条件。 |
| OH_TrafficFilter_InterfaceMatch inInterface | 入接口匹配条件。 |
| OH_TrafficFilter_InterfaceMatch outInterface | 出接口匹配条件。 |
| uint32_t uidStart | 应用UID范围起始值。`UINT32_MAX` 表示任意UID。 |
| uint32_t uidEnd | 应用UID范围结束值。`UINT32_MAX` 表示任意UID。 |
| OH_TrafficFilter_IPAddress proxyIp | 代理服务器IP地址，支持IPv4和IPv6。 |
| uint16_t proxyPort | 代理服务器端口。 |
