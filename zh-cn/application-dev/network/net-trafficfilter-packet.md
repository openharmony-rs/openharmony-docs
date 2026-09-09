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

``` C++
#include "napi/native_api.h"
#include <cstdint>
#include <cstring>
#include <string>
#include <vector>
#include <map>
#include <algorithm>
#include <arpa/inet.h>
#include "hilog/log.h"
#include "network/netmanager_ext/net_trafficfilter.h"
```

在C++源文件中引入以下头文件：

### 实现报文过滤

在开始实现前，请确保已完成以下前置条件：
- 已创建Native C++工程。
- 已在`module.json5`的`requestPermissions`项中声明`ohos.permission.kernel.TRAFFIC_FILTER`权限。

1. 在源文件中编写调用该API的代码，实现报文控制器的创建。

   使用[OH_TrafficFilter_CreatePacketController](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_createpacketcontroller)接口创建报文控制器。其中`group_id`用于标识控制器的分组，`priority`控制规则优先级，`packetCopyMode`与 `packetCopyLen`用于配置NFQueue（Netfilter Queue，内核与用户态交互报文拷贝的队列机制）报文拷贝模式与长度，`nfqueueMaxlen`与`nfqueueFlags`用于设置队列长度与标志位。

   <!-- @[create_packet_controller](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   // 报文控制器创建：解析 JS 入参并创建 NFQueue 报文控制器
   constexpr int BUFFER_SIZE = 128;
   constexpr int GLOBAL_NETSTACK = 0xFF00;
   constexpr int IP_ADDR_BUF_LEN = 16;
   constexpr int IPV4_ADDR_LEN = 4;
   constexpr int MAX_STR_ARRAY_LEN = 46;
   
   // 默认配置常量：分组 ID、优先级、NFQueue 拷贝长度/队列长度/标志位/拷贝模式
   constexpr uint32_t DEFAULT_GROUP_ID = 1001;
   constexpr uint32_t DEFAULT_PRIORITY = 100;
   constexpr uint32_t DEFAULT_PACKET_COPY_LEN = 0xFFFF;
   constexpr uint32_t DEFAULT_NFQUEUE_MAXLEN = 1024;
   constexpr uint32_t DEFAULT_NFQUEUE_FLAGS = 1;
   constexpr uint32_t DEFAULT_PACKET_COPY_MODE = 2;
   constexpr int PORT_MIN_VALUE = 0;
   constexpr int PORT_MAX_VALUE = 65535;
   constexpr int MAX_PORT_MULTI_COUNT = 16;
   constexpr int MAX_IP_MULTI_COUNT = 8;
   constexpr int32_t ERR_CONTROLLER_NOT_FOUND = 29410101;
   constexpr int DUMMY_CALLBACK_ARG = 23;
   
   // CreatePacketControllerNapi的参数索引
   constexpr int PACKET_CTRL_ARG_IDX_GROUP_ID = 0;
   constexpr int PACKET_CTRL_ARG_IDX_PRIORITY = 1;
   constexpr int PACKET_CTRL_ARG_IDX_PACKET_COPY_LEN = 2;
   constexpr int PACKET_CTRL_ARG_IDX_NFQUEUE_MAXLEN = 3;
   constexpr int PACKET_CTRL_ARG_IDX_NFQUEUE_FLAGS = 4;
   constexpr int PACKET_CTRL_ARG_IDX_PACKET_COPY_MODE = 5;
   
   // Netfilter钩子点数值映射
   constexpr int HOOK_INPUT_VALUE = 0;
   constexpr int HOOK_OUTPUT_VALUE = 1;
   constexpr int HOOK_FORWARD_VALUE = 2;
   constexpr int HOOK_PREROUTING_VALUE = 3;
   constexpr int HOOK_POSTROUTING_VALUE = 4;
   
   constexpr int ARG_IDX_JS_CALLBACK = 2;
   constexpr int ARG_IDX_RULE_CONFIG = 2;
   
   constexpr size_t MAX_PORT_STRING_LEN = 1024;
   
   // 全局控制器映射表与自增ID
   map<int, OH_TrafficFilter_PacketController*> g_controllerMap;
   int g_controllerId = 1;
   
   static const char *TAG = "[packet]";
   
   // 线程安全函数与回调上下文
   napi_threadsafe_function tsFn;
   static int g_value = 0;
   
   struct PacketCallbackCtx {
       napi_env env;                       // N-API环境
       napi_ref jsCallbackRef;             // JS回调引用
       const OH_TrafficFilter_PacketDesc* packet; // 报文描述指针
   };
   
   // 全局异步回调上下文
   auto g_asyncContext = new PacketCallbackCtx();
   
   static napi_value CreatePacketControllerNapi(napi_env env, napi_callback_info info)
   {
       // 获取JS调用参数
       size_t argc = PACKET_CTRL_ARG_IDX_PACKET_COPY_MODE + 1;
       napi_value args[PACKET_CTRL_ARG_IDX_PACKET_COPY_MODE + 1] = {nullptr};
   
       napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
   
       // 使用默认值初始化参数，若JS端传入则覆盖
       uint32_t groupId = DEFAULT_GROUP_ID;
       uint32_t priority = DEFAULT_PRIORITY;
       uint32_t packetCopyLen = DEFAULT_PACKET_COPY_LEN;
       uint32_t nfqueueMaxlen = DEFAULT_NFQUEUE_MAXLEN;
       uint32_t nfqueueFlags = DEFAULT_NFQUEUE_FLAGS;
       uint32_t packetCopyMode = DEFAULT_PACKET_COPY_MODE;
   
       if (argc > PACKET_CTRL_ARG_IDX_GROUP_ID) {
           napi_get_value_uint32(env, args[PACKET_CTRL_ARG_IDX_GROUP_ID], &groupId);
       }
       if (argc > PACKET_CTRL_ARG_IDX_PRIORITY) {
           napi_get_value_uint32(env, args[PACKET_CTRL_ARG_IDX_PRIORITY], &priority);
       }
       if (argc > PACKET_CTRL_ARG_IDX_PACKET_COPY_LEN) {
           napi_get_value_uint32(env, args[PACKET_CTRL_ARG_IDX_PACKET_COPY_LEN], &packetCopyLen);
       }
       if (argc > PACKET_CTRL_ARG_IDX_NFQUEUE_MAXLEN) {
           napi_get_value_uint32(env, args[PACKET_CTRL_ARG_IDX_NFQUEUE_MAXLEN], &nfqueueMaxlen);
       }
       if (argc > PACKET_CTRL_ARG_IDX_PACKET_COPY_MODE) {
           napi_get_value_uint32(env, args[PACKET_CTRL_ARG_IDX_PACKET_COPY_MODE], &packetCopyMode);
       }
   
       // 填充OH_TrafficFilter_Config配置结构体
       OH_TrafficFilter_Config config;
       config.size = sizeof(OH_TrafficFilter_Config);
       config.packetCopyLen = packetCopyLen;
       config.nfqueueMaxlen = nfqueueMaxlen;
       config.nfqueueFlags = nfqueueFlags;
       config.packetCopyMode = packetCopyMode;
   
       // 调用系统API创建报文控制器
       OH_TrafficFilter_PacketController* controller = nullptr;
       int32_t ret = OH_TrafficFilter_CreatePacketController(groupId, priority, &config, &controller);
   // ...
   
       // 将控制器存入全局映射表，便于后续按ID操作
       g_controllerMap[g_controllerId] = controller;
   
       napi_value resultObj;
       napi_create_object(env, &resultObj);
   
       napi_value retValue;
       napi_create_int32(env, ret, &retValue);
       napi_set_named_property(env, resultObj, "ret", retValue);
   
       napi_value id;
       napi_create_int32(env, g_controllerId, &id);
       napi_set_named_property(env, resultObj, "id", id);
   
       g_controllerId++;
   
       return resultObj;
   }
   ```

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
