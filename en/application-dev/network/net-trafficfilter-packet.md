# Filtering Network Packets (C/C++)
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=fe0a2a84adc58d56a78ae92def33ee8c273b8b6a translatedAt=2026-10-31T06:41:24.028Z pushedAt=2026-10-31T06:41:24.028Z nl=1 -->

## When to Use

Network packet filtering intercepts packets in the kernel network protocol stack and allows or drops them according to predefined rules. Typical use cases include:

- Firewalls: Restrict network communication for specific applications, IP addresses, ports, or network interfaces.
- Application traffic control: Audit or restrict the network activity of specific processes.

> **NOTE**
>
> Packet filtering requires system permissions. Declare `ohos.permission.kernel.TRAFFIC_FILTER` in `module.json5` and call the C APIs from native code. This system permission can be requested only by system applications or signed privileged applications.

## Constraints

**Permission constraints**

The application must declare the `ohos.permission.kernel.TRAFFIC_FILTER` permission.

## Development Process

The main steps for filtering network packets are as follows:

1. Create a Native C++ project and add the required shared libraries and header files.
2. Declare `ohos.permission.kernel.TRAFFIC_FILTER` in `module.json5`.
3. Encapsulate the C++ APIs for creating a packet controller, adding rules, and registering callbacks.
4. Export the C++ APIs to ArkTS through N-API.
5. Call the encapsulated APIs in ArkTS and verify packet filtering on the device.
6. After testing, unregister callbacks, clear rules, and destroy the controller.

## How to Develop

### Adding Dependencies

**Adding shared libraries**

Add the following shared libraries to `target_link_libraries` in `CMakeLists.txt`:

```txt
libace_napi.z.so
libhilog_ndk.z.so
libnet_trafficfilter.so
```

**Header files**

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

Include the following header files in the C++ source file:

### Implementing Packet Filtering

Before you start, ensure that the following prerequisites are met:
- A Native C++ project has been created.
- `ohos.permission.kernel.TRAFFIC_FILTER` has been declared in `requestPermissions` in `module.json5`.

1. Write the API call code in the source file to create a packet controller.

   Call [OH_TrafficFilter_CreatePacketController](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_createpacketcontroller) to create a packet controller. `group_id` identifies the controller group, and `priority` controls rule priority. `packetCopyMode` and `packetCopyLen` configure the packet copy mode and length for NFQueue (Netfilter Queue, a mechanism for copying packets between the kernel and user space). `nfqueueMaxlen` and `nfqueueFlags` configure the queue length and flags.

   <!-- @[create_packet_controller](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   // Parse JS arguments and create an NFQueue packet controller.
   constexpr int BUFFER_SIZE = 128;
   constexpr int GLOBAL_NETSTACK = 0xFF00;
   constexpr int IP_ADDR_BUF_LEN = 16;
   constexpr int IPV4_ADDR_LEN = 4;
   constexpr int MAX_STR_ARRAY_LEN = 46;
   
   // Default configuration constants: group ID, priority, and NFQueue copy length, queue length, flags, and copy mode.
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
   
   // Argument indices for CreatePacketControllerNapi.
   constexpr int PACKET_CTRL_ARG_IDX_GROUP_ID = 0;
   constexpr int PACKET_CTRL_ARG_IDX_PRIORITY = 1;
   constexpr int PACKET_CTRL_ARG_IDX_PACKET_COPY_LEN = 2;
   constexpr int PACKET_CTRL_ARG_IDX_NFQUEUE_MAXLEN = 3;
   constexpr int PACKET_CTRL_ARG_IDX_NFQUEUE_FLAGS = 4;
   constexpr int PACKET_CTRL_ARG_IDX_PACKET_COPY_MODE = 5;
   
   // Numeric mapping of Netfilter hook points.
   constexpr int HOOK_INPUT_VALUE = 0;
   constexpr int HOOK_OUTPUT_VALUE = 1;
   constexpr int HOOK_FORWARD_VALUE = 2;
   constexpr int HOOK_PREROUTING_VALUE = 3;
   constexpr int HOOK_POSTROUTING_VALUE = 4;
   
   constexpr int ARG_IDX_JS_CALLBACK = 2;
   constexpr int ARG_IDX_RULE_CONFIG = 2;
   
   constexpr size_t MAX_PORT_STRING_LEN = 1024;
   
   // Global controller map and auto-incrementing ID.
   map<int, OH_TrafficFilter_PacketController*> g_controllerMap;
   int g_controllerId = 1;
   
   static const char *TAG = "[packet]";
   
   // Thread-safe function and callback context.
   napi_threadsafe_function tsFn;
   static int g_value = 0;
   
   struct PacketCallbackCtx {
       napi_env env;                       // N-API environment.
       napi_ref jsCallbackRef;             // JS callback reference.
       const OH_TrafficFilter_PacketDesc* packet; // Packet description pointer.
   };
   
   // Global asynchronous callback context.
   auto g_asyncContext = new PacketCallbackCtx();
   
   static napi_value CreatePacketControllerNapi(napi_env env, napi_callback_info info)
   {
       // Obtain JS call arguments.
       size_t argc = PACKET_CTRL_ARG_IDX_PACKET_COPY_MODE + 1;
       napi_value args[PACKET_CTRL_ARG_IDX_PACKET_COPY_MODE + 1] = {nullptr};
   
       napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
   
       // Initialize parameters with defaults and override them with values supplied by JS.
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
   
       // Populate the OH_TrafficFilter_Config structure.
       OH_TrafficFilter_Config config;
       config.size = sizeof(OH_TrafficFilter_Config);
       config.packetCopyLen = packetCopyLen;
       config.nfqueueMaxlen = nfqueueMaxlen;
       config.nfqueueFlags = nfqueueFlags;
       config.packetCopyMode = packetCopyMode;
   
       // Call the system API to create a packet controller.
       OH_TrafficFilter_PacketController* controller = nullptr;
       int32_t ret = OH_TrafficFilter_CreatePacketController(groupId, priority, &config, &controller);
   // ...
   
       // Store the controller in the global map for subsequent operations by ID.
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

2. Add packet filtering rules. Rules can specify source and destination IP addresses, ports, interfaces, UIDs, MAC addresses, TCP flags, and connection tracking states.

   Call [OH_TrafficFilter_AddPacketRule](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_addpacketrule) to add a rule to the specified controller. `OH_TrafficFilter_FilterRule` supports the following match criteria:
   - **IP address**: unrestricted, a single address, CIDR (Classless Inter-Domain Routing, supporting network prefixes such as `192.168.1.0/24`), a range (192.168.1.0 to 192.168.1.10), or multiple addresses (192.168.1.0, 192.168.1.100, ...).
   - **Port**: unrestricted, a single port, a range (such as ports 5050 to 8080), or multiple ports (5050, 5051, 8081, ...).
   - **Interface**: Match by input or output interface name. Prefix matching and negation are supported.
   - **UID range**: Match by application UID range. `UINT32_MAX` means any UID.
   - **MAC address**: Match by source MAC address.
   - **TCP flags**: Match combinations of flags such as SYN, ACK, FIN, RST, PSH, and URG.
   - **Connection tracking**: Match the current state of the connection to which the packet belongs: NEW, ESTABLISHED, RELATED, INVALID, or UNTRACKED.

   Rule logic:
   - Conditions within a single `OH_TrafficFilter_FilterRule` are combined using **AND**.
   - Multiple rules added to the same controller are combined using **OR**.

   <!-- @[add_packet_rule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   // Find the controller by ID and add a packet filtering rule.
   static napi_value AddPacketRuleNapi(napi_env env, napi_callback_info info)
   {
       // Obtain JS call arguments.
       size_t argc = ARG_IDX_RULE_CONFIG;
       napi_value args[ARG_IDX_RULE_CONFIG] = {nullptr};
       napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
   
       // Parse the controller ID and find the corresponding controller.
       uint32_t id = -1;
       napi_get_value_uint32(env, args[0], &id);
       OH_TrafficFilter_PacketController* controller = g_controllerMap[id];
       if (controller == nullptr) {
           napi_value result;
           napi_create_int32(env, -1, &result);
           return result;
       }
   
       // Rule configuration object.
       napi_value configObj = args[1];
   
       // Read the rule priority from the configuration object.
       uint32_t priority = DEFAULT_PRIORITY;
       bool hasProp = false;
       napi_value propVal;
       if (napi_has_named_property(env, configObj, "priority", &hasProp) == napi_ok && hasProp) {
           napi_get_named_property(env, configObj, "priority", &propVal);
           napi_get_value_uint32(env, propVal, &priority);
       }
   
       // Parse the hook point and protocol type.
       OH_TrafficFilter_HookPoint hookPoint = ParseHookPointFromConfig(env, configObj);
       uint32_t protocol = ParseProtocolFromConfig(env, configObj);
   
       // Build an OH_TrafficFilter_FilterRule from the configuration.
       OH_TrafficFilter_FilterRule rule = BuildFilterRuleFromConfig(env, configObj, priority, hookPoint, protocol);
   
       OH_LOG_Print(LOG_APP, LOG_INFO, GLOBAL_NETSTACK, TAG,
                    "AddPacketRuleNapi srcMac: %{public}s", rule.macMatch.srcMac);
   
       // Call the system API to add a filtering rule.
       int ret = OH_TrafficFilter_AddPacketRule(controller, &rule);
       OH_LOG_Print(LOG_APP, LOG_INFO, GLOBAL_NETSTACK, TAG,
                    "AddPacketRuleNapi ret: %{public}d", ret);
   
       napi_value result;
       napi_create_int32(env, ret, &result);
       return result;
   }
   ```

3. Register a packet callback and return an allow or drop decision based on the packet information.

   Call [OH_TrafficFilter_RegisterPacketCallback](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_registerpacketcallback) to register the callback. The callback runs on a non-JS thread. To display packet information in ArkTS, create a thread-safe function using `napi_threadsafe_function`, then call `napi_call_threadsafe_function` in the callback to forward the data to the ArkTS thread.

   <!-- @[register_packet_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   // Register a packet callback to forward kernel packets to JS through a thread-safe function.
   OH_TrafficFilter_PacketDecision MyPacketHandler(
       const OH_TrafficFilter_PacketDesc* packet,
       void* userData)
   {
       // Forward packet information to the JS thread through a thread-safe function.
       napi_acquire_threadsafe_function(tsFn);
       g_asyncContext->packet = packet;
       napi_call_threadsafe_function(tsFn, g_asyncContext, napi_tsfn_nonblocking);
       napi_release_threadsafe_function(tsFn, napi_tsfn_release);
   
       // Drop the packet by default.
       return OH_TRAFFICFILTER_DECISION_DROP;
   }
   
   static napi_value RegisterPacketCallbackNapi(napi_env env, napi_callback_info info)
   {
       // N-API entry point for registering a packet callback.
       size_t argc = ARG_IDX_JS_CALLBACK + 1;
       napi_value args[ARG_IDX_JS_CALLBACK + 1] = {nullptr};
       napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
   
       // Parse the controller ID and find the corresponding controller.
       uint32_t id = -1;
       napi_get_value_uint32(env, args[0], &id);
       OH_TrafficFilter_PacketController* controller = g_controllerMap[id];
       if (controller == nullptr) {
           napi_value result;
           napi_create_int32(env, ERR_CONTROLLER_NOT_FOUND, &result);
           return result;
       }
   
       // Read user-defined data.
       size_t copyLen = 0;
       char buf[BUFFER_SIZE] = {0};
       napi_get_value_string_utf8(env, args[1], buf, BUFFER_SIZE, &copyLen);
       void* userData = reinterpret_cast<void*>(buf);
   
       // Create a thread-safe function to forward packet information to the JS thread.
       napi_value workName;
       napi_create_string_utf8(env, "ThreadSafeCase", NAPI_AUTO_LENGTH, &workName);
       napi_create_threadsafe_function(env, nullptr, nullptr, workName, 0, 1, nullptr, nullptr,
                                       nullptr, ThreadSafeCallJs, &tsFn);
   
       g_asyncContext->env = env;
       napi_create_reference(env, args[ARG_IDX_JS_CALLBACK], 1, &g_asyncContext->jsCallbackRef);
   
       // Register a packet processing callback with the controller.
       int ret = OH_TrafficFilter_RegisterPacketCallback(controller, MyPacketHandler, userData);
       napi_value result;
       napi_create_int32(env, 0, &result);
       return result;
   }
   ```

4. Unregister the callback, clear rules, and destroy the packet controller.

   After testing, release resources in this order: **unregister the callback, clear rules, then destroy the controller**. This prevents packets from reaching the callback during cleanup.
   - Call [OH_TrafficFilter_UnregisterPacketCallback](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_unregisterpacketcallback) to unregister the callback.
   - Call [OH_TrafficFilter_ClearPacketRule](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_clearpacketrule) to clear all rules on the controller.
   - Call [OH_TrafficFilter_DestroyPacketController](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_destroypacketcontroller) to destroy the controller and release resources.

   <!-- @[unregister_packet_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_value UnregisterPacketCallbackNapi(napi_env env, napi_callback_info info)
   {
       size_t argc = 1;
       napi_value args[1] = {nullptr};
       napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
   
       int ret = -1;
       if (argc >= 1) {
           uint32_t id;
           napi_get_value_uint32(env, args[0], &id);
           OH_TrafficFilter_PacketController* controller = g_controllerMap[id];
           if (controller != nullptr) {
               ret = OH_TrafficFilter_UnregisterPacketCallback(controller);
           }
       }
   
       napi_value result;
       napi_create_int32(env, ret, &result);
       return result;
   }
   ```

   <!-- @[clear_packet_rule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_value ClearPacketRuleNapi(napi_env env, napi_callback_info info)
   {
       size_t argc = 1;
       napi_value args[1] = {nullptr};
       napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
   
       uint32_t id;
       if (argc >= 1) {
           napi_get_value_uint32(env, args[0], &id);
       }
   
       int ret = -1;
       OH_TrafficFilter_PacketController* controller = g_controllerMap[id];
       if (controller != nullptr) {
           ret = OH_TrafficFilter_ClearPacketRule(controller);
       }
   
       napi_value result;
       napi_create_int32(env, ret, &result);
       return result;
   }
   ```

   <!-- @[destroy_packet_controller](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_value DestroyPacketControllerNapi(napi_env env, napi_callback_info info)
   {
       size_t argc = 1;
       napi_value args[1] = {nullptr};
   
       napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
   
       uint32_t id;
       if (argc >= 1) {
           napi_get_value_uint32(env, args[0], &id);
       }
   
       int ret = -1;
       OH_LOG_Print(LOG_APP, LOG_INFO, GLOBAL_NETSTACK, TAG,
                    "DestroyPacketControllerNapi id: %{public}d", id);
   
       OH_TrafficFilter_PacketController* controller = g_controllerMap[id];
       if (controller != nullptr) {
           OH_LOG_Print(LOG_APP, LOG_INFO, GLOBAL_NETSTACK, TAG,
                        "DestroyPacketControllerNapi id111: %{public}d", id);
           ret = OH_TrafficFilter_DestroyPacketController(controller);
           g_controllerMap[id] = nullptr;
       }
   
       napi_value result;
       napi_create_int32(env, ret, &result);
       return result;
   }
   ```

5. Initialize and export the `napi_value` objects encapsulated through N-API.

   <!-- @[init_exports](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   EXTERN_C_START
   static napi_value Init(napi_env env, napi_value exports)
   {
       napi_property_descriptor desc[] = {
           { "createPacketController", nullptr, CreatePacketControllerNapi, nullptr, nullptr,
             nullptr, napi_default, nullptr },
           { "destroyPacketController", nullptr, DestroyPacketControllerNapi, nullptr, nullptr,
             nullptr, napi_default, nullptr },
           { "addPacketRule", nullptr, AddPacketRuleNapi, nullptr, nullptr,
             nullptr, napi_default, nullptr },
           { "clearPacketRule", nullptr, ClearPacketRuleNapi, nullptr, nullptr,
             nullptr, napi_default, nullptr },
           { "registerPacketCallback", nullptr, RegisterPacketCallbackNapi, nullptr, nullptr,
             nullptr, napi_default, nullptr },
           { "unregisterPacketCallback", nullptr, UnregisterPacketCallbackNapi, nullptr, nullptr,
             nullptr, napi_default, nullptr }
       };
       napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
       return exports;
   }
   EXTERN_C_END
   ```

6. Use `napi_module_register` in `RegisterEntryModule` to register the initialized objects as a Node.js module.

   <!-- @[register_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Packet_case/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_module demoModule = {
       .nm_version = 1,
       .nm_flags = 0,
       .nm_filename = nullptr,
       .nm_register_func = Init,
       .nm_modname = "entry",
       .nm_priv = nullptr,
       .reserved = { 0 },
   };
   
   extern "C" __attribute__((constructor)) void RegisterEntryModule(void)
   {
       napi_module_register(&demoModule);
   }
   ```

## Debugging and Verification

1. Connect the device and open the project in DevEco Studio.
2. Run the project and open the packet filtering management page.
3. Click **Create PacketController** to create a packet controller.
4. Configure a filtering rule, for example with a specified destination IP address and destination port 80. Click **Add Packet Rule** to add the rule.
5. Click **Register PacketCallback** to register the packet callback.
6. Generate network traffic on the device that matches the rule. Check the packet information received by the callback and the allow or drop decision.
7. After testing, click **Unregister PacketCallback**, **Clear Packet Rule**, and **Destroy PacketController**, in that order, to release resources.
