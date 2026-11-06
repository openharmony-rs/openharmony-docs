# Redirecting Network Traffic (C/C++)
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=3f72f1ff93dbb4460ec97eb48212db08ca38ea5f translatedAt=2026-10-31T06:41:24.028Z pushedAt=2026-10-31T06:41:24.028Z nl=1 -->

## When to Use

Network traffic redirection intercepts TCP packets in the kernel network protocol stack and rewrites their destination addresses to forward matching traffic to a specified proxy server. Typical use cases include:

- Enterprise network auditing: Redirect outbound TCP traffic from specified applications or to specified destinations to an auditing proxy.
- Content filtering proxies: Transparently intercept HTTP/HTTPS traffic at a gateway or endpoint and forward it to a content security proxy.
- Transparent VPN proxies: Transparently direct application traffic that requires a proxy to a local or remote proxy service.

> **NOTE**
>
> Traffic redirection requires system permissions. Declare `ohos.permission.kernel.TRAFFIC_FILTER` in `module.json5` and call the C APIs from native code.

## Constraints

**Permission constraints**

The application must declare the `ohos.permission.kernel.TRAFFIC_FILTER` permission.

## How to Develop

To create and use traffic redirection with the APIs in this topic, first create a Native C++ project and encapsulate the APIs in source files. Call the encapsulated APIs from ArkTS. Use **hilog**, **console.info**, or similar methods to print messages to the console or generate device logs.

### Adding Dependencies

**Adding shared libraries**

Add the following shared libraries to `target_link_libraries` in `CMakeLists.txt`:

```txt
libace_napi.z.so
libhilog_ndk.z.so
libnet_trafficfilter.so
```

**Header files**

<!-- @[header_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->

``` C++
#include <cstdint>
#include <cstring>
#include <string>
#include <sstream>
#include <vector>
#include <algorithm>
#include <arpa/inet.h>

#include "napi/native_api.h"
#include "hilog/log.h"
#include "network/netmanager_ext/net_trafficfilter.h"
```

### Implementing Traffic Redirection

Before you start, ensure that the following prerequisites are met:
- A Native C++ project has been created.
- `ohos.permission.kernel.TRAFFIC_FILTER` has been declared in `requestPermissions` in `module.json5`.

1. Write the API call code in the source file to create a redirector.

   Call [OH_TrafficFilter_CreateRedirector](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_createredirector) to create a traffic redirector. `group_id` identifies the redirector group, and `priority` controls rule priority.

   <!-- @[create_redirector](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   // Parse JS arguments and call OH_TrafficFilter_CreateRedirector to create a redirector.
   constexpr int BUFFER_SIZE = 128;
   constexpr size_t IP_ADDR_BUF_LEN = 16;
   constexpr size_t IPV4_ADDR_LEN = 4;
   constexpr uint32_t DEFAULT_GROUP_ID = 1001;
   constexpr uint32_t DEFAULT_PRIORITY = 100;
   constexpr uint32_t DEFAULT_PACKET_COPY_LEN = 0xFFFF;
   constexpr uint32_t DEFAULT_NFQUEUE_MAXLEN = 1024;
   constexpr uint32_t DEFAULT_NFQUEUE_FLAGS = 1;
   constexpr uint32_t PROTOCOL_TCP = OH_TRAFFICFILTER_PROTO_TCP;
   constexpr uint16_t DEFAULT_HTTP_PORT = 80;
   constexpr uint16_t DEFAULT_PROXY_PORT = 8080;
   constexpr uint16_t HTTPS_PORT = 443;
   constexpr uint16_t PORT_MIN_VALUE = 0;
   constexpr uint16_t PORT_MAX_VALUE = 65535;
   constexpr uint32_t UID_ANY = 4294967295u;
   constexpr size_t INTERFACE_NAME_MAX_LEN = 31;
   constexpr uint8_t IPV4_DEFAULT_PREFIX = 24;
   constexpr uint8_t IPV6_DEFAULT_PREFIX = 64;
   constexpr uint8_t IPV4_PREFIX_MAX = 32;
   constexpr uint8_t IPV6_PREFIX_MAX = 128;
   constexpr uint32_t LOG_DOMAIN_DEFAULT = 0x0000;
   constexpr size_t ARRAY_BRACKET_PAIR_LEN = 2;
   constexpr size_t ARRAY_CONTENT_START_OFFSET = 1;
   
   // JS argument index definitions.
   constexpr int ARG_IDX_GROUP_ID = 0;
   constexpr int ARG_IDX_PRIORITY = 1;
   constexpr int ARG_IDX_PACKET_COPY_LEN = 2;
   constexpr int ARG_IDX_NFQUEUE_MAXLEN = 3;
   constexpr int ARG_IDX_NFQUEUE_FLAGS = 4;
   constexpr int REQUIRED_ARG_COUNT = 5;
   
   // Global redirector instance pointer.
   OH_TrafficFilter_Redirector* g_redirector = nullptr;
   
   static napi_value CreateRedirectorNapi(napi_env env, napi_callback_info info)
   {
       // Obtain the argument count and values passed by the JS call.
       size_t argc = ARG_IDX_NFQUEUE_FLAGS + 1;
       napi_value args[ARG_IDX_NFQUEUE_FLAGS + 1] = {nullptr};
   
       napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
   
       // Initialize parameters with defaults and override them with values supplied by JS.
       uint32_t groupId = DEFAULT_GROUP_ID;
       uint32_t priority = DEFAULT_PRIORITY;
       uint32_t packetCopyLen = DEFAULT_PACKET_COPY_LEN;
       uint32_t nfqueueMaxlen = DEFAULT_NFQUEUE_MAXLEN;
       uint32_t nfqueueFlags = DEFAULT_NFQUEUE_FLAGS;
   
       if (argc > ARG_IDX_GROUP_ID) {
           napi_get_value_uint32(env, args[ARG_IDX_GROUP_ID], &groupId);
       }
       if (argc > ARG_IDX_PRIORITY) {
           napi_get_value_uint32(env, args[ARG_IDX_PRIORITY], &priority);
       }
       if (argc > ARG_IDX_PACKET_COPY_LEN) {
           napi_get_value_uint32(env, args[ARG_IDX_PACKET_COPY_LEN], &packetCopyLen);
       }
       if (argc > ARG_IDX_NFQUEUE_MAXLEN) {
           napi_get_value_uint32(env, args[ARG_IDX_NFQUEUE_MAXLEN], &nfqueueMaxlen);
       }
       if (argc > ARG_IDX_NFQUEUE_FLAGS) {
           napi_get_value_uint32(env, args[ARG_IDX_NFQUEUE_FLAGS], &nfqueueFlags);
       }
   
   // ...
   
       // Call the system API to create a traffic redirector.
       int32_t ret = OH_TrafficFilter_CreateRedirector(groupId, priority, &g_redirector);
   
       // Build the result string and return it to JS.
       char msg[BUFFER_SIZE * 2];
   
       napi_value result;
       napi_create_string_utf8(env, msg, strlen(msg), &result);
       return result;
   }
   ```

2. Add redirection rules. Rules can specify source and destination IP addresses, ports, interfaces, UID ranges, and proxy server addresses.

   Call [OH_TrafficFilter_AddRedirectRule](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_addredirectrule) to add a rule to the redirector. In `OH_TrafficFilter_RedirectRule`, `protocol` is fixed to TCP, `hookPoint` (the Netfilter hook point) supports only `PREROUTING` and `OUTPUT`, and `proxy_ip` and `proxy_port` specify the proxy server address.

   <!-- @[add_redirect_rule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   // Parse the JSON string and call the system API to add a redirection rule.
   static napi_value AddRedirectRuleNapi(napi_env env, napi_callback_info info)
   {
       // Obtain JS call arguments.
       size_t argc = 1;
       napi_value args[1] = {nullptr};
   
       napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);
   
       // Check whether ruleJson is supplied.
       if (argc <= 0) {
           char msg[] = "ERROR: ruleJson parameter required";
           napi_value result;
           napi_create_string_utf8(env, msg, strlen(msg), &result);
           return result;
       }
   
       // Read the JSON string length and allocate a buffer.
       size_t jsonLen = 0;
       napi_get_value_string_utf8(env, args[0], nullptr, 0, &jsonLen);
       char* jsonStr = new char[jsonLen + 1];
       napi_get_value_string_utf8(env, args[0], jsonStr, jsonLen + 1, &jsonLen);
       std::string json(jsonStr);
       delete[] jsonStr;
   
       // Parse the JSON string into an OH_TrafficFilter_RedirectRule structure.
       OH_TrafficFilter_RedirectRule rule;
       int32_t parseRet = BuildRedirectRuleFromJson(json, rule);
       if (parseRet != OH_TRAFFICFILTER_OK) {
           char msg[BUFFER_SIZE];
           napi_value result;
           napi_create_string_utf8(env, msg, strlen(msg), &result);
           return result;
       }
   
       // Call the system API to add a rule to the redirector.
       int32_t ret = OH_TrafficFilter_AddRedirectRule(g_redirector, &rule);
   
       // Build the result string and return it to JS.
       char msg[BUFFER_SIZE * 2];
       napi_value result;
       napi_create_string_utf8(env, msg, strlen(msg), &result);
       return result;
   }
   ```

3. Clear rules and destroy the redirector.

   After testing, clear the rules before destroying the redirector to release the associated resources.
   - Call [OH_TrafficFilter_ClearRedirectRule](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_clearredirectrule) to clear all redirection rules.
   - Call [OH_TrafficFilter_DestroyRedirector](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_destroyredirector) to destroy the redirector.

   <!-- @[clear_redirect_rule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_value ClearRedirectRuleNapi(napi_env env, napi_callback_info info)
   {
       if (g_redirector == nullptr) {
           char msg[] = "ERROR: No redirector exists";
           napi_value result;
           napi_create_string_utf8(env, msg, strlen(msg), &result);
           return result;
       }
   
       int32_t ret = OH_TrafficFilter_ClearRedirectRule(g_redirector);
   
       char msg[BUFFER_SIZE * 2];
       napi_value result;
       napi_create_string_utf8(env, msg, strlen(msg), &result);
       return result;
   }
   ```

   <!-- @[destroy_redirect_rule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_value DestroyRedirectorNapi(napi_env env, napi_callback_info info)
   {
       if (g_redirector != nullptr) {
           OH_TrafficFilter_DestroyRedirector(g_redirector);
           g_redirector = nullptr;
   
           char msg[] = "SUCCESS: Redirector destroyed";
           napi_value result;
           napi_create_string_utf8(env, msg, strlen(msg), &result);
           return result;
       }
       char msg[] = "WARNING: No redirector to destroy";
       napi_value result;
       napi_create_string_utf8(env, msg, strlen(msg), &result);
       return result;
   }
   ```


4. Initialize and export the `napi_value` objects encapsulated through N-API, exposing the functions to JavaScript through the foreign function interface.

   <!-- @[init_exports](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   EXTERN_C_START
   static napi_value Init(napi_env env, napi_value exports)
   {
       napi_property_descriptor desc[] = {
           { "createRedirector", nullptr, CreateRedirectorNapi, nullptr, nullptr, nullptr, napi_default, nullptr },
           { "destroyRedirector", nullptr, DestroyRedirectorNapi, nullptr, nullptr, nullptr, napi_default, nullptr },
           { "addRedirectRule", nullptr, AddRedirectRuleNapi, nullptr, nullptr, nullptr, napi_default, nullptr },
           { "clearRedirectRule", nullptr, ClearRedirectRuleNapi, nullptr, nullptr, nullptr, napi_default, nullptr },
           { "getRuleTemplate", nullptr, GetRuleTemplateNapi, nullptr, nullptr, nullptr, napi_default, nullptr },
           { "queryProcess", nullptr, QueryProcessNapi, nullptr, nullptr, nullptr, napi_default, nullptr }
       };
       napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
       return exports;
   }
   EXTERN_C_END
   ```

5. Use `napi_module_register` in `RegisterEntryModule` to register the objects initialized in the previous step as a Node.js module.

   <!-- @[register_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->
   
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

### Querying the Process That Owns a Connection

[OH_TrafficFilter_QueryProcess](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_queryprocess) queries the process that initiated a connection by its five-tuple: source IP address, destination IP address, source port, destination port, and protocol. It is commonly used to identify traffic ownership before redirection.

<!-- @[query_process](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->

``` C++
// Query the process that initiated the connection using its five-tuple.
struct QueryArgs {
    std::string srcIp;      // Source IP address.
    std::string dstIp;      // Destination IP address.
    uint32_t srcPort = 0;   // Source port.
    uint32_t dstPort = 0;   // Destination port.
    uint32_t protocol = PROTOCOL_TCP; // Protocol type.
};

static std::string ParseQueryArgsFromNapi(napi_env env, const napi_value args[], QueryArgs& queryArgs)
{
    // Parse the five-tuple (source/destination IP addresses, ports, and protocol) from JS arguments.
    int ardIdxDstIp = 2;
    int argIdxDstPort = 3;
    int argIdxProtocol = 4;
    size_t srcIpLen = 0;
    size_t dstIpLen = 0;

    // Obtain the source and destination IP address string lengths.
    napi_get_value_string_utf8(env, args[0], nullptr, 0, &srcIpLen);
    napi_get_value_string_utf8(env, args[ardIdxDstIp], nullptr, 0, &dstIpLen);

    std::vector<char> srcIpBuf(srcIpLen + 1);
    std::vector<char> dstIpBuf(dstIpLen + 1);

    napi_get_value_string_utf8(env, args[0], srcIpBuf.data(), srcIpBuf.size(), &srcIpLen);
    napi_get_value_string_utf8(env, args[ardIdxDstIp], dstIpBuf.data(), dstIpBuf.size(), &dstIpLen);

    queryArgs.srcIp = srcIpBuf.data();
    queryArgs.dstIp = dstIpBuf.data();

    // Obtain the source port, destination port, and protocol type.
    napi_get_value_uint32(env, args[1], &queryArgs.srcPort);
    napi_get_value_uint32(env, args[argIdxDstPort], &queryArgs.dstPort);
    napi_get_value_uint32(env, args[argIdxProtocol], &queryArgs.protocol);

    // Validate the port ranges and protocol type.
    if (queryArgs.srcPort > PORT_MAX_VALUE || queryArgs.dstPort > PORT_MAX_VALUE) {
        return "ERROR: Invalid port value";
    }

    if (queryArgs.protocol != OH_TRAFFICFILTER_PROTO_TCP && queryArgs.protocol != OH_TRAFFICFILTER_PROTO_UDP) {
        return "ERROR: Invalid protocol value (must be TCP=6 or UDP=17)";
    }

    return "";
}

static std::string BuildQueryConnectionInfo(
    napi_env env,
    const napi_value args[],
    OH_TrafficFilter_ConnectionInfo& connectionInfo)
{
    // Build an OH_TrafficFilter_ConnectionInfo structure from the five-tuple.
    QueryArgs queryArgs;
    std::string error = ParseQueryArgsFromNapi(env, args, queryArgs);
    if (!error.empty()) {
        return error;
    }

    OH_LOG_INFO(LOG_APP,
        "QueryProcessNapi - srcIp=%{public}s, srcPort=%{public}u, dstIp=%{public}s, "
        "dstPort=%{public}u, protocol=%{public}u",
        queryArgs.srcIp.c_str(), queryArgs.srcPort,
        queryArgs.dstIp.c_str(), queryArgs.dstPort, queryArgs.protocol);

    memset(&connectionInfo, 0, sizeof(connectionInfo));
    connectionInfo.size = sizeof(OH_TrafficFilter_ConnectionInfo);

    // Parse the source IP address and populate the structure according to the address family.
    connectionInfo.srcIp.family = DetectIPFamilyFromAddr(queryArgs.srcIp);
    if (!ParseIPAddressByFamily(queryArgs.srcIp, connectionInfo.srcIp.family,
        connectionInfo.srcIp.addr)) {
        return "ERROR: Invalid source IP address";
    }
    connectionInfo.srcPort = static_cast<uint16_t>(queryArgs.srcPort);

    connectionInfo.dstIp.family = DetectIPFamilyFromAddr(queryArgs.dstIp);
    if (!ParseIPAddressByFamily(queryArgs.dstIp, connectionInfo.dstIp.family,
        connectionInfo.dstIp.addr)) {
        return "ERROR: Invalid destination IP address";
    }
    connectionInfo.dstPort = static_cast<uint16_t>(queryArgs.dstPort);

    connectionInfo.protocol = static_cast<uint8_t>(queryArgs.protocol);
    return "";
}

static napi_value CreateQueryResponseNapi(
    napi_env env,
    int32_t ret,
    const OH_TrafficFilter_ProcessInfo& processInfo)
{
    char response[BUFFER_SIZE * 2];
    if (ret == OH_TRAFFICFILTER_OK) {
        OH_LOG_INFO(LOG_APP,
            "QueryProcessNapi - Process found: pid=%{public}u, uid=%{public}u",
            processInfo.pid, processInfo.uid);
    } else if (ret == OH_TRAFFICFILTER_ERROR_NOT_FOUND) {
        OH_LOG_ERROR(LOG_APP, "QueryProcessNapi - Process not found");
    } else if (ret == OH_TRAFFICFILTER_ERROR_INVALID_PARAM) {
        OH_LOG_ERROR(LOG_APP, "QueryProcessNapi - Invalid parameters");
    } else {
        OH_LOG_ERROR(LOG_APP, "QueryProcessNapi - Query failed with ret=%{public}d", ret);
    }

    napi_value result;
    napi_create_string_utf8(env, response, strlen(response), &result);
    return result;
}

static napi_value QueryProcessNapi(napi_env env, napi_callback_info info)
{
    // Main entry point for querying the process that owns a connection.
    size_t argc = REQUIRED_ARG_COUNT;
    napi_value args[REQUIRED_ARG_COUNT] = {nullptr};

    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);

    auto CreateStringResult = [env](const char* msg) -> napi_value {
        napi_value result;
        napi_create_string_utf8(env, msg, strlen(msg), &result);
        return result;
    };

    // Validate the number of required arguments.
    if (argc < REQUIRED_ARG_COUNT) {
        return CreateStringResult("ERROR: Missing required parameters");
    }

    // Build the connection information structure.
    OH_TrafficFilter_ConnectionInfo connectionInfo;
    std::string error = BuildQueryConnectionInfo(env, args, connectionInfo);
    if (!error.empty()) {
        return CreateStringResult(error.c_str());
    }

    // Clear the process information structure and set its size.
    OH_TrafficFilter_ProcessInfo processInfo;
    memset(&processInfo, 0, sizeof(processInfo));
    processInfo.size = sizeof(OH_TrafficFilter_ProcessInfo);

    // Call the system API to query process information.
    int32_t ret = OH_TrafficFilter_QueryProcess(&connectionInfo, &processInfo);

    return CreateQueryResponseNapi(env, ret, processInfo);
}
```

## Debugging and Verification

1. Connect the device and open the project in DevEco Studio.
2. Run the project and open the redirection management page.
3. Click **Create Redirector** to create a redirector.
4. Configure the destination IP address, destination port, proxy IP address, and proxy port. Click **Add Redirect Rule** to add the rule.
5. Generate matching TCP traffic on the device, for example by accessing port 80 of the destination IP address, and verify that the traffic is redirected to the proxy server.
6. To query the process that owns a connection, click **Query Process** and enter the five-tuple information.
7. After testing, click **Clear Redirect Rule** to clear the rules, then **Destroy Redirector** to release resources.
