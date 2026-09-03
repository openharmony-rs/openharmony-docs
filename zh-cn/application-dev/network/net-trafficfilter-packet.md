# 过滤网络报文 (C/C++)
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

## 场景介绍

网络报文过滤能力在系统内核网络协议栈中拦截网络数据包，根据预设规则决定报文的放行或丢弃。典型应用场景包括：

- 防火墙：限制特定应用、IP、端口或网卡的网络通信。
- 应用流量管控：对特定进程的网络行为进行审计或限制。

> **说明：**

> 报文过滤能力需要系统权限支持，应用需在`module.json5`中声明`ohos.permission.kernel.TRAFFIC_FILTER`权限，并在原生侧调用C API。该权限为系统权限，仅系统应用或经签名的特权应用可申请使用。

## 约束与限制

**权限约束**

应用必须声明`ohos.permission.kernel.TRAFFIC_FILTER`权限。

## 开发流程

使用网络报文过滤能力的主要流程如下：

1. 创建Native C++工程并添加动态链接库与头文件依赖。
2. 在`module.json5`中声明`ohos.permission.kernel.TRAFFIC_FILTER`权限。
3. 实现报文控制器创建、规则添加、回调注册等C++接口封装。
4. 通过N-API将C++接口导出到ArkTS层。
5. 在ArkTS层调用封装接口，并在设备上验证过滤效果。
6. 测试完成后注销回调、清除规则并销毁控制器。

## 开发步骤

### 添加开发依赖

**添加动态链接库**

在`CMakeLists.txt`的`target_link_libraries`中添加以下共享库：

```txt
libace_napi.z.so
libhilog_ndk.z.so
libnet_trafficfilter.so
```

**头文件**

<!-- @[header_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->

在C++源文件中引入以下头文件：

### 实现报文过滤

在开始实现前，请确保已完成以下前置条件：
- 已创建Native C++工程。
- 已在`module.json5`的`requestPermissions`项中声明`ohos.permission.kernel.TRAFFIC_FILTER`权限。

1. 在源文件中编写调用该API的代码，实现报文控制器的创建。

   使用[OH_TrafficFilter_CreatePacketController](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_createpacketcontroller)接口创建报文控制器。其中`group_id`用于标识控制器的分组，`priority`控制规则优先级，`packetCopyMode`与 `packetCopyLen`用于配置NFQueue（Netfilter Queue，内核与用户态交互报文拷贝的队列机制）报文拷贝模式与长度，`nfqueueMaxlen`与`nfqueueFlags`用于设置队列长度与标志位。

   <!-- @[create_packet_controller](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->

2. 添加报文过滤规则。规则中可配置源/目的IP、端口、接口、UID、MAC、TCP标志位以及连接跟踪状态。

   使用[OH_TrafficFilter_AddPacketRule](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_addpacketrule)接口向指定控制器添加规则。`OH_TrafficFilter_FilterRule`支持以下匹配条件：
   - **IP匹配**：不限制、单个、CIDR（无类别域间路由，支持如`192.168.1.0/24`的网络前缀）、范围、多个。
   - **端口匹配**：不限制、单个、范围（如端口5050~8080）、多个（5050,5051,8081，...）。
   - **接口匹配**：按入接口或出接口名称匹配，支持前缀匹配和取反。
   - **UID范围**：按应用UID范围匹配，`UINT32_MAX`表示任意UID。
   - **MAC地址匹配**：按源MAC地址匹配。
   - **TCP标志位匹配**：按SYN/ACK/FIN/RST/PSH/URG等标志位组合匹配。
   - **连接跟踪匹配**：按连接跟踪状态（NEW/ESTABLISHED/RELATED/INVALID/UNTRACKED）匹配，用于判断报文所属连接的当前状态。

   规则间逻辑：
   - 单个`OH_TrafficFilter_FilterRule`内部各条件为**逻辑与**关系。
   - 同一控制器内添加的多个规则为**逻辑或**关系。

   <!-- @[add_packet_rule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->

3. 注册报文回调，在回调中根据报文信息返回放行或丢弃决策。

   使用[OH_TrafficFilter_RegisterPacketCallback](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_registerpacketcallback) 接口注册回调函数。回调运行在非JS线程，如需将报文信息展示到ArkTS层，需通过`napi_threadsafe_function` 创建线程安全函数，在回调中调用`napi_call_threadsafe_function`将数据转发到ArkTS线程。

   <!-- @[register_packet_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->

4. 注销回调、清除规则并销毁报文控制器。

   测试完成后，建议按**注销回调 → 清除规则 → 销毁控制器**的顺序释放资源，避免清理过程中仍有报文进入回调。
   - 使用[OH_TrafficFilter_UnregisterPacketCallback](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_unregisterpacketcallback)注销回调。
   - 使用[OH_TrafficFilter_ClearPacketRule](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_clearpacketrule)清除该控制器上的所有规则。
   - 使用[OH_TrafficFilter_DestroyPacketController](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_destroypacketcontroller)销毁控制器并释放资源。

   <!-- @[unregister_packet_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->

   <!-- @[clear_packet_rule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->

   <!-- @[destroy_packet_controller](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->

5. 初始化并导出通过N-API封装的`napi_value`类型对象。

   <!-- @[init_exports](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->

6. 将初始化成功的对象通过`RegisterEntryModule`函数，使用`napi_module_register`函数将模块注册到Node.js中。

   <!-- @[register_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->

## 调测验证

1. 连接设备，使用DevEco Studio打开搭建好的工程。
2. 运行工程，进入报文过滤管理页面。
3. 点击**Create PacketController**按钮创建报文控制器。
4. 配置过滤规则（例如目的IP为指定地址、目的端口为80），点击**Add Packet Rule**添加规则。
5. 点击 **Register PacketCallback** 注册报文回调。
6. 在设备上触发匹配规则的网络流量，观察回调中收到的报文信息以及放行/丢弃结果。
7. 测试完成后，依次点击**Unregister PacketCallback**、**Clear Packet Rule**、**Destroy PacketController**释放资源。
