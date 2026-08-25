# 使用网络报文过滤 (C/C++)
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
> 报文过滤能力需要系统权限支持，应用需在 `module.json5` 中声明 `ohos.permission.kernel.TRAFFIC_FILTER` 权限，并在原生侧调用 C API。该权限为系统权限，仅系统应用或经签名的特权应用可申请使用。

## 约束与限制

**权限约束**

应用必须声明 `ohos.permission.kernel.TRAFFIC_FILTER` 系统权限，普通应用无法直接申请。

**版本约束**

- 本文档中涉及的报文过滤接口起始版本为 **API 版本 26.1.0**，低于该版本无对应替代方案。

## 开发流程

使用网络报文过滤能力的主要流程如下：

1. 创建 Native C++ 工程并添加动态链接库与头文件依赖。
2. 在 `module.json5` 中声明 `ohos.permission.kernel.TRAFFIC_FILTER` 权限。
3. 实现报文控制器创建、规则添加、回调注册等 C++ 接口封装。
4. 通过 N-API 将 C++ 接口导出到 ArkTS 层。
5. 在 ArkTS 层调用封装接口，并在设备上验证过滤效果。
6. 测试完成后注销回调、清除规则并销毁控制器。

## 开发步骤

### 添加开发依赖

**添加动态链接库**

在 `CMakeLists.txt` 的 `target_link_libraries` 中添加以下共享库：

```txt
libace_napi.z.so
libhilog_ndk.z.so
libnet_trafficfilter.so
```

**头文件**

在 C++ 源文件中引入以下头文件：

<!-- @[header_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->

在 C++ 源文件中引入以下头文件：

### 实现报文过滤

在开始实现前，请确保已完成以下前置条件：
- 已创建 Native C++ 工程。
- 已在 `module.json5` 的 `requestPermissions` 项中声明 `ohos.permission.kernel.TRAFFIC_FILTER` 权限。

1. 在源文件中编写调用该 API 的代码，实现报文控制器的创建。

   使用 [OH_TrafficFilter_CreatePacketController](../reference/apis-network-kit/capi-net-trafficfilter-h.md) 接口创建报文控制器。其中 `group_id` 用于标识控制器的分组，`priority` 控制规则优先级，`packetCopyMode` 与 `packetCopyLen` 用于配置 NFQueue（Netfilter Queue，内核与用户态交互报文拷贝的队列机制）报文拷贝模式与长度，`nfqueueMaxlen` 与 `nfqueueFlags` 用于设置队列长度与标志位。

   <!-- @[create_packet_controller](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->

   简要说明：`CreatePacketControllerNapi` 接收分组 ID、优先级以及 NFQueue 拷贝模式等配置，创建报文控制器并返回控制器 ID 与错误码。

2. 添加报文过滤规则。规则中可配置源/目的 IP、端口、接口、UID、MAC、TCP 标志位以及连接跟踪状态。

   使用 [OH_TrafficFilter_AddPacketRule](../reference/apis-network-kit/capi-net-trafficfilter-h.md) 接口向指定控制器添加规则。`OH_TrafficFilter_FilterRule` 支持以下匹配条件：
   - **IP 匹配**：任意、单个、CIDR（无类别域间路由，支持如 `192.168.1.0/24` 的网络前缀）、范围、多个。
   - **端口匹配**：任意、单个、范围、多个。
   - **接口匹配**：按入接口或出接口名称匹配，支持前缀匹配和取反。
   - **UID 范围**：按应用 UID 范围匹配，`UINT32_MAX` 表示任意 UID。
   - **MAC 地址匹配**：按源 MAC 地址匹配。
   - **TCP 标志位匹配**：按 SYN/ACK/FIN/RST/PSH/URG 等标志位组合匹配。
   - **连接跟踪匹配**：按连接跟踪状态（NEW/ESTABLISHED/RELATED/INVALID/UNTRACKED）匹配，用于判断报文所属连接的当前状态。

   规则间逻辑：
   - 单个 `OH_TrafficFilter_FilterRule` 内部各条件为**逻辑与**关系。
   - 同一控制器内添加的多个规则为**逻辑或**关系。

   <!-- @[add_packet_rule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->

   简要说明：`OH_TrafficFilter_FilterRule` 内部各条件为逻辑与关系，同一控制器内多个规则为逻辑或关系。

3. 注册报文回调，在回调中根据报文信息返回放行或丢弃决策。

   使用 [OH_TrafficFilter_RegisterPacketCallback](../reference/apis-network-kit/capi-net-trafficfilter-h.md) 接口注册回调函数。回调运行在非 JS 线程，如需将报文信息展示到 ArkTS 层，需通过 `napi_threadsafe_function` 创建线程安全函数，在回调中调用 `napi_call_threadsafe_function` 将数据转发到 ArkTS 线程。

   <!-- @[register_packet_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->

4. 注销回调、清除规则并销毁报文控制器。

   测试完成后，建议按**注销回调 → 清除规则 → 销毁控制器**的顺序释放资源，避免清理过程中仍有报文进入回调。
   - 使用 [OH_TrafficFilter_UnregisterPacketCallback](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_unregisterpacketcallback) 注销回调。
   - 使用 [OH_TrafficFilter_ClearPacketRule](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_clearpacketrule) 清除该控制器上的所有规则。
   - 使用 [OH_TrafficFilter_DestroyPacketController](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_destroypacketcontroller) 销毁控制器并释放资源。

   <!-- @[unregister_packet_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->


   简要说明：`controllerMap_[id]` 为空时返回 `-1`；注销回调前无需额外处理线程安全函数，但应确保不再主动触发新的匹配流量。

   <!-- @[clear_packet_rule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->

   简要说明：清除规则后，已注册的回调仍可能因后续新增规则而被触发；如需完全停止回调，请在清除规则前先注销回调。

   <!-- @[destroy_packet_controller](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->

   简要说明：销毁控制器后会自动释放其占用的系统资源（包括规则），销毁后请将句柄置空，避免重复释放。

5. 初始化并导出通过 N-API 封装的 `napi_value` 类型对象。

   <!-- @[init_exports](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->

6. 将初始化成功的对象通过 `RegisterEntryModule` 函数，使用 `napi_module_register` 函数将模块注册到 Node.js 中。

   <!-- @[register_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->

完整示例代码请参考：[TrafficFilter_Packet_case](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case)。

## 调测验证

1. 连接设备，使用 DevEco Studio 打开搭建好的工程。
2. 运行工程，进入报文过滤管理页面。
3. 点击 **Create PacketController** 按钮创建报文控制器。
4. 配置过滤规则（例如目的 IP 为指定地址、目的端口为 80），点击 **Add Packet Rule** 添加规则。
5. 点击 **Register PacketCallback** 注册报文回调。
6. 在设备上触发匹配规则的网络流量，观察回调中收到的报文信息以及放行/丢弃结果。
7. 测试完成后，依次点击 **Unregister PacketCallback**、**Clear Packet Rule**、**Destroy PacketController** 释放资源。

## 常见问题

**回调没有收到报文信息，可能是什么原因？**

- 检查 `module.json5` 中是否已声明 `ohos.permission.kernel.TRAFFIC_FILTER` 权限。
- 确认过滤规则条件是否过于严格，导致没有报文匹配。
- 确认设备是否支持 Network Kit 扩展能力，以及是否已正确连接设备。

**规则添加失败，返回值非 0，如何处理？**

- 检查传入的 `OH_TrafficFilter_FilterRule` 的 `size` 字段是否正确设置为 `sizeof(OH_TrafficFilter_FilterRule)`。
- 检查 `controller` 是否已通过 `OH_TrafficFilter_CreatePacketController` 成功创建。
- 检查规则中 IP、端口等字段的取值是否在合法范围内。
