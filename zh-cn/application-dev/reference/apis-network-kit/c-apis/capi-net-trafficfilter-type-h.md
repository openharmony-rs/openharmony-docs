# net_trafficfilter_type.h

## 概述

声明网络流量过滤与重定向功能所需的通用类型和错误码。该头文件定义了流量过滤与重定向功能中使用的IP地址、端口、接口等匹配条件结构体，报文过滤规则、重定向规则等配置结构体，以及操作返回的错误码。<br>适用于调用{@link OH_TrafficFilter_CreateRedirector}等接口时构造参数和解析返回值。

**库：** libnet_trafficfilter.so

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**起始版本：** 26.0.0

**相关模块：** [TrafficFilter](capi-trafficfilter.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_TrafficFilter_IPAddress](capi-trafficfilter-oh-trafficfilter-ipaddress.md) | OH_TrafficFilter_IPAddress | 二进制形式的IP地址，支持IPv4和IPv6。 |
| [OH_TrafficFilter_IPCidr](capi-trafficfilter-oh-trafficfilter-ipcidr.md) | OH_TrafficFilter_IPCidr | CIDR（Classless Inter-Domain Routing，无类别域间路由）匹配的IP匹配值。 |
| [OH_TrafficFilter_IPRange](capi-trafficfilter-oh-trafficfilter-iprange.md) | OH_TrafficFilter_IPRange | 范围匹配的IP匹配值。 |
| [OH_TrafficFilter_IPMulti](capi-trafficfilter-oh-trafficfilter-ipmulti.md) | OH_TrafficFilter_IPMulti | 多IP匹配的IP匹配值。 |
| [OH_TrafficFilter_IPMatch](capi-trafficfilter-oh-trafficfilter-ipmatch.md) | OH_TrafficFilter_IPMatch | IP匹配条件。 |
| [OH_TrafficFilter_InterfaceMatch](capi-trafficfilter-oh-trafficfilter-interfacematch.md) | OH_TrafficFilter_InterfaceMatch | 接口匹配条件。 |
| [OH_TrafficFilter_PortRange](capi-trafficfilter-oh-trafficfilter-portrange.md) | OH_TrafficFilter_PortRange | 范围匹配的端口匹配值。 |
| [OH_TrafficFilter_PortMulti](capi-trafficfilter-oh-trafficfilter-portmulti.md) | OH_TrafficFilter_PortMulti | 多端口匹配的端口匹配值。 |
| [OH_TrafficFilter_PortMatch](capi-trafficfilter-oh-trafficfilter-portmatch.md) | OH_TrafficFilter_PortMatch | 端口匹配条件。 |
| [OH_TrafficFilter_ConnectionInfo](capi-trafficfilter-oh-trafficfilter-connectioninfo.md) | OH_TrafficFilter_ConnectionInfo | 连接信息结构体。描述一条网络连接的五元组信息（源IP、目的IP、源端口、目的端口、协议类型），用于查询发起该连接的进程信息。<br>初始化规则：调用{@link OH_TrafficFilter_QueryProcess}之前，调用者必须将该结构体清零（例如使用memset），然后将{@link size}设置为调用者分配的结构体实际大小，通常为sizeof(OH_TrafficFilter_ConnectionInfo)。<br>二进制兼容规则（ABI，即应用程序二进制接口，保证新旧版本编译的代码能互相识别结构体布局）：系统通过{@link size}来确定哪些字段可以被安全读取。如果{@link size}小于当前接口所需的最小大小，接口将返回[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode)。如果{@link size}大于系统已知的大小，多余的字段将被忽略。 |
| [OH_TrafficFilter_ProcessInfo](capi-trafficfilter-oh-trafficfilter-processinfo.md) | OH_TrafficFilter_ProcessInfo | 进程信息结构体。存储{@link OH_TrafficFilter_QueryProcess}返回的进程信息。<br>初始化规则：调用{@link OH_TrafficFilter_QueryProcess}之前，调用者必须将该结构体清零（例如使用memset），然后将{@link size}设置为调用者分配的结构体实际大小，通常为sizeof(OH_TrafficFilter_ProcessInfo)。<br>二进制兼容规则（ABI，即应用程序二进制接口，保证新旧版本编译的代码能互相识别结构体布局）：系统通过{@link size}来确定哪些输出字段可以被安全写入。只有被{@link size}完全覆盖的字段才会被系统写入。如果{@link size}小于读取{@link size}字段本身所需的最小大小，接口将返回[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode)。如果{@link size}大于系统已知的大小，多余的字段将被忽略。<br>输出有效性规则：当{@link OH_TrafficFilter_QueryProcess}返回[OH_TRAFFICFILTER_OK](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode)时，被{@link size}覆盖的字段包含有效的输出值。当接口返回错误时，调用者不应依赖{@link size}以外的输出字段的值。 |
| [OH_TrafficFilter_RedirectRule](capi-trafficfilter-oh-trafficfilter-redirectrule.md) | OH_TrafficFilter_RedirectRule | 流量重定向规则。定义TCP流量重定向规则，将匹配的流量重定向到指定的代理服务器。<br>初始化规则：调用{@link OH_TrafficFilter_AddRedirectRule}之前，调用者必须将该结构体清零（例如使用memset），然后将{@link size}设置为调用者分配的结构体实际大小，通常为sizeof(OH_TrafficFilter_RedirectRule)。<br>二进制兼容规则（ABI，即应用程序二进制接口，保证新旧版本编译的代码能互相识别结构体布局）：系统通过{@link size}来确定哪些字段可以被安全读取。如果{@link size}小于当前接口所需的最小大小，接口将返回[OH_TRAFFICFILTER_ERROR_INVALID_PARAM](capi-net-trafficfilter-type-h.md#oh_trafficfilter_errcode)。如果{@link size}大于系统已知的大小，多余的字段将被忽略。<br>失败规则：如果{@link OH_TrafficFilter_AddRedirectRule}返回错误，不保证规则已被添加或生效。调用者应在假设规则生效之前检查返回值。 |
| [OH_TrafficFilter_PacketDesc](capi-trafficfilter-oh-trafficfilter-packetdesc.md) | OH_TrafficFilter_PacketDesc | 报文描述符包含五元组信息和报文数据 |
| [OH_TrafficFilter_Config](capi-trafficfilter-oh-trafficfilter-config.md) | OH_TrafficFilter_Config | NFQueue配置结构体- 如果`config`为**NULL**，实现将应用以下默认值：- `packetCopyLen` = 0xFFFF（拷贝整个报文）- `nfqueueMaxlen` = 0 （使用系统默认值，即1024）- `nfqueueFlags` = OH_TRAFFICFILTER_NFQUEUE_FLAG_FAIL_OPEN- 如果`config`为**非NULL**，调用者**必须**：1. 将整个结构体零初始化（例如`memset(&cfg, 0, sizeof(cfg))`）。2. 设置`size` = `sizeof(OH_TrafficFilter_Config)`。3. 将所有其他字段设置为定义范围内的有效值（见下文）。- **未遵守**此约定（例如`size`不正确、字段值超出范围）将导致接口返回`OH_TRAFFICFILTER_ERROR_INVALID_PARAM`。 |
| [OH_TrafficFilter_MACMatch](capi-trafficfilter-oh-trafficfilter-macmatch.md) | OH_TrafficFilter_MACMatch | MAC地址匹配条件基于MAC地址匹配报文仅支持源MAC地址 |
| [OH_TrafficFilter_TCPFlagsMatch](capi-trafficfilter-oh-trafficfilter-tcpflagsmatch.md) | OH_TrafficFilter_TCPFlagsMatch | TCP标志匹配条件基于TCP标志设置匹配TCP报文 |
| [OH_TrafficFilter_ConntrackMatch](capi-trafficfilter-oh-trafficfilter-conntrackmatch.md) | OH_TrafficFilter_ConntrackMatch | 连接跟踪匹配条件基于连接跟踪状态匹配报文 |
| [OH_TrafficFilter_FilterRule](capi-trafficfilter-oh-trafficfilter-filterrule.md) | OH_TrafficFilter_FilterRule | 报文过滤规则定义报文匹配条件。1. **初始化约定（调用方）**：- 调用者必须在使用前将整个结构体**零初始化**（例如通过`memset`）。- `size`字段**必须**显式设置为`sizeof(OH_TrafficFilter_FilterRule)`。- 如果`size`小于`sizeof(OH_TrafficFilter_FilterRule)`，实现将仅读取截至`size`的稳定前缀字段，忽略后续字节。2. **读取约定（实现方）**：- 实现严格根据`size`值确定有效字段范围。- 如果`size` < `sizeof(OH_TrafficFilter_FilterRule)`，实现将其视为旧版本，仅读取与该大小兼容的前缀字段。- 如果`size`为0或指针为NULL，实现必须返回错误。 |
| [OH_TrafficFilter_Redirector](capi-trafficfilter-oh-trafficfilter-redirector.md) | OH_TrafficFilter_Redirector | 流量重定向器。 |
| [OH_TrafficFilter_PacketController](capi-trafficfilter-oh-trafficfilter-packetcontroller.md) | OH_TrafficFilter_PacketController | 报文控制器 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_TrafficFilter_ErrCode](#oh_trafficfilter_errcode) | OH_TrafficFilter_ErrCode | 流量过滤与重定向错误码。 |
| [OH_TrafficFilter_IPMatchType](#oh_trafficfilter_ipmatchtype) | OH_TrafficFilter_IPMatchType | IP匹配类型。 |
| [OH_TrafficFilter_IPFamily](#oh_trafficfilter_ipfamily) | OH_TrafficFilter_IPFamily | IP地址族。 |
| [OH_TrafficFilter_PortMatchType](#oh_trafficfilter_portmatchtype) | OH_TrafficFilter_PortMatchType | 端口匹配类型。 |
| [OH_TrafficFilter_HookPoint](#oh_trafficfilter_hookpoint) | OH_TrafficFilter_HookPoint | 钩子点类型，指定规则在网络协议栈中生效的位置。报文经过内核网络协议栈时会在不同阶段触发钩子点，规则在对应钩子点处对报文进行拦截。例如INPUT链处理进入本机的报文，OUTPUT链处理本机发出的报文。 |
| [OH_TrafficFilter_PacketDecision](#oh_trafficfilter_packetdecision) | OH_TrafficFilter_PacketDecision | 报文决策类型 |
| [OH_TrafficFilter_PacketCopyMode](#oh_trafficfilter_packetcopymode) | OH_TrafficFilter_PacketCopyMode | 报文拷贝模式枚举 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| OH_TRAFFICFILTER_IP_ADDRLEN       16 | IP地址字节数组最大长度（兼容IPv4和IPv6）。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_MAX_MULTI_IP_COUNT  16 | 多IP匹配支持的最大IP数量。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_MAX_MULTI_PORT_COUNT 64 | 多端口匹配支持的最大端口数量。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_NFQUEUE_COPY_META   0 | NFQueue报文拷贝模式：仅拷贝元数据。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_NFQUEUE_COPY_PACKET 0xFFFF | NFQueue报文拷贝模式：拷贝整个报文。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_DEFAULT_COPY_LEN    0xFFFF | 默认NFQueue报文拷贝长度（字节）。设置为0xFFFF表示拷贝整个报文，较小的值（如128）仅拷贝报文头。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_DEFAULT_QUEUE_MAXLEN  1024 | 默认NFQueue最大队列长度（报文数量）。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_NFQUEUE_FLAG_FAIL_OPEN  0x1 | NFQueue队列标志：FAIL-OPEN模式。当用户态进程崩溃时，内核自动放行报文以避免网络中断。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_MAC_ADDRSTRLEN       18 | MAC地址字符串最大长度（XX:XX:XX:XX:XX:XX）<br>**起始版本：** 26.1.0 |
| OH_TRAFFICFILTER_MIN_PRIORITY        1 | 最小优先级值。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_MAX_PRIORITY        10000 | 最大优先级值。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_MIN_GROUP_ID        1 | 最小Group ID值。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_MAX_GROUP_ID        65535 | 最大Group ID值。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_IFNAMSIZ            32 | 网络接口名称最大长度。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_PROTO_ANY           0 OH_TRAFFICFILTER_PROTO_TCP           6 OH_TRAFFICFILTER_PROTO_UDP           17 OH_TRAFFICFILTER_PROTO_ICMP          1 OH_TRAFFICFILTER_PROTO_ICMPV6        58 | 协议类型常量：任意协议。<br>**起始版本：** 26.0.0 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef OH_TrafficFilter_PacketDecision (\*OH_TrafficFilter_PacketCallback)(const OH_TrafficFilter_PacketDesc* packet, void* userData)](#oh_trafficfilter_packetcallback) | OH_TrafficFilter_PacketCallback | 报文回调函数类型 |

## 枚举类型说明

### OH_TrafficFilter_ErrCode

```c
enum OH_TrafficFilter_ErrCode
```

**描述**

流量过滤与重定向错误码。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_TRAFFICFILTER_OK = 0 | 操作成功。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_E_BASE = 29410000 | 错误码基值。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_ERROR_PERMISSION_DENIED = 201 | 缺少权限。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_ERROR_INVALID_PARAM = (OH_TRAFFICFILTER_E_BASE + 101) | 参数错误（无效的优先级、IP地址、端口或Group ID）。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_ERROR_NOT_FOUND = (OH_TRAFFICFILTER_E_BASE + 102) | 资源未找到（规则、目标、进程或Group ID未找到）。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_ERROR_TOO_MANY_RULES = (OH_TRAFFICFILTER_E_BASE + 103) | 规则数量过多。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_ERROR_GROUP_ID_IN_USE = (OH_TRAFFICFILTER_E_BASE + 104) | Group ID已被占用。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_ERROR_NFQUEUE_ERROR = (OH_TRAFFICFILTER_E_BASE + 105) | NFQueue错误（初始化失败或无可用队列）。<br>**起始版本：** 26.0.0 |

### OH_TrafficFilter_IPMatchType

```c
enum OH_TrafficFilter_IPMatchType
```

**描述**

IP匹配类型。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_TRAFFICFILTER_IP_MATCH_ANY = 0 | 任意IP。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_IP_MATCH_SINGLE | 单个IP。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_IP_MATCH_CIDR | CIDR格式（如192.168.1.0/24，表示匹配该子网内的所有IP）。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_IP_MATCH_RANGE | IP范围。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_IP_MATCH_MULTI | 多个IP。<br>**起始版本：** 26.0.0 |

### OH_TrafficFilter_IPFamily

```c
enum OH_TrafficFilter_IPFamily
```

**描述**

IP地址族。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_TRAFFICFILTER_IP_FAMILY_UNSPEC = 0 | 未指定的IP地址族。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_IP_FAMILY_V4 = 1 | IPv4地址族。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_IP_FAMILY_V6 = 2 | IPv6地址族。<br>**起始版本：** 26.0.0 |

### OH_TrafficFilter_PortMatchType

```c
enum OH_TrafficFilter_PortMatchType
```

**描述**

端口匹配类型。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_TRAFFICFILTER_PORT_MATCH_ANY = 0 | 任意端口。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_PORT_MATCH_SINGLE | 单个端口。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_PORT_MATCH_RANGE | 端口范围。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_PORT_MATCH_MULTI | 多个端口。<br>**起始版本：** 26.0.0 |

### OH_TrafficFilter_HookPoint

```c
enum OH_TrafficFilter_HookPoint
```

**描述**

钩子点类型，指定规则在网络协议栈中生效的位置。报文经过内核网络协议栈时会在不同阶段触发钩子点，规则在对应钩子点处对报文进行拦截。例如INPUT链处理进入本机的报文，OUTPUT链处理本机发出的报文。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_TRAFFICFILTER_HOOK_INPUT = 0 | INPUT链，处理进入本机的报文。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_HOOK_OUTPUT | OUTPUT链，处理本机发出的报文。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_HOOK_FORWARD | FORWARD链，处理本机转发的报文。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_HOOK_PREROUTING | PREROUTING链，处理刚到达网卡、尚未路由的报文。<br>**起始版本：** 26.0.0 |
| OH_TRAFFICFILTER_HOOK_POSTROUTING | POSTROUTING链，处理即将从网卡发出的报文。<br>**起始版本：** 26.0.0 |

### OH_TrafficFilter_PacketDecision

```c
enum OH_TrafficFilter_PacketDecision
```

**描述**

报文决策类型

**起始版本：** 26.1.0

| 枚举项 | 描述 |
| -- | -- |
| OH_TRAFFICFILTER_DECISION_ACCEPT = 0 | 接收报文<br>**起始版本：** 26.1.0 |
| OH_TRAFFICFILTER_DECISION_DROP | 丢弃报文<br>**起始版本：** 26.1.0 |

### OH_TrafficFilter_PacketCopyMode

```c
enum OH_TrafficFilter_PacketCopyMode
```

**描述**

报文拷贝模式枚举

**起始版本：** 26.1.0

| 枚举项 | 描述 |
| -- | -- |
| OH_TRAFFICFILTER_COPY_MODE_META = 0 | 仅拷贝元数据（不拷贝报文数据）<br>**起始版本：** 26.1.0 |
| OH_TRAFFICFILTER_COPY_MODE_HEADER = 1 | 仅拷贝报文头（由packetCopyLen指定）<br>**起始版本：** 26.1.0 |
| OH_TRAFFICFILTER_COPY_MODE_FULL = 2 | 拷贝整个报文<br>**起始版本：** 26.1.0 |
| OH_TRAFFICFILTER_COPY_MODE_MAXLEN = 3 | 按指定最大长度拷贝报文<br>**起始版本：** 26.1.0 |


## 函数说明

### OH_TrafficFilter_PacketCallback()

```c
typedef OH_TrafficFilter_PacketDecision (*OH_TrafficFilter_PacketCallback)(const OH_TrafficFilter_PacketDesc* packet, void* userData)
```

**描述**

报文回调函数类型

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_TrafficFilter_PacketDesc](capi-trafficfilter-oh-trafficfilter-packetdesc.md)\* packet | 报文描述符 |
| void\* userData | 用户数据 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_TrafficFilter_PacketDecision](capi-net-trafficfilter-type-h.md#oh_trafficfilter_packetdecision) | 报文决策（接收或丢弃） |


