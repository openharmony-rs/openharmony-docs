# TrafficFilter

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

## 概述

实现网络流量过滤与重定向功能。流量过滤是指在系统内核网络协议栈中拦截网络数据包（报文），根据预设规则决定报文的放行或丢弃，适用于防火墙、家长控制、应用流量管控等场景。<br> 流量重定向是指将匹配规则的TCP流量转发到指定的代理服务器，适用于企业网络审计、内容过滤代理、VPN透明代理等场景。<br> 使用时，先创建控制器或重定向器实例，再添加过滤或重定向规则，即可对网络流量进行管控。使用完毕后需调用对应的销毁接口释放资源。

**起始版本：** 26.0.0
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [net_trafficfilter.h](capi-net-trafficfilter-h.md) | 声明网络流量过滤与重定向功能的C接口。该头文件提供创建和销毁报文控制器、注册报文回调、添加和清除过滤规则，以及创建和销毁流量重定向器、添加和清除重定向规则的接口。<br> 适用于需要在系统层面对网络数据包进行拦截、过滤和重定向的应用场景。 |
| [net_trafficfilter_type.h](capi-net-trafficfilter-type-h.md) | 声明网络流量过滤与重定向功能所需的通用类型和错误码。该头文件定义了流量过滤与重定向功能中使用的IP地址、端口、接口等匹配条件结构体，报文过滤规则、重定向规则等配置结构体，以及操作返回的错误码。<br> 适用于调用[OH_TrafficFilter_CreateRedirector](capi-net-trafficfilter-h.md#oh_trafficfilter_createredirector)等接口时构造参数和解析返回值。 |
