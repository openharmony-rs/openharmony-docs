# TrafficFilter

## 概述

声明网络流量过滤与重定向功能的C接口。

**起始版本：** 26.0.0
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [net_trafficfilter.h](capi-net-trafficfilter-h.md) | 声明网络流量过滤与重定向功能的C接口。该头文件提供创建和销毁报文控制器、注册报文回调、添加和清除过滤规则，以及创建和销毁流量重定向器、添加和清除重定向规则的接口。<br>适用于需要在系统层面对网络数据包进行拦截、过滤和重定向的应用场景。 |
| [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md) | 声明网络流量过滤与重定向功能所需的通用类型和错误码。该头文件定义了流量过滤与重定向功能中使用的IP地址、端口、接口等匹配条件结构体，报文过滤规则、重定向规则等配置结构体，以及操作返回的错误码。<br>适用于调用{@link OH_TrafficFilter_CreateRedirector}等接口时构造参数和解析返回值。 |
