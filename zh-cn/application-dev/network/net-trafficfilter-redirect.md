# 使用网络流量重定向 (C/C++)
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

## 场景介绍

网络流量重定向能力通过内核网络协议栈拦截并改写 TCP 报文的目的地址，将匹配规则的流量转发到指定的代理服务器。典型应用场景包括：

- 企业网络审计：将指定应用或指定目的地址的出站 TCP 流量重定向到审计代理。
- 内容过滤代理：在网关或终端侧透明拦截 HTTP/HTTPS 流量并转发到内容安全代理。
- VPN 透明代理：将需要代理的应用流量无感知地引流到本地或远程代理服务。

> **说明：**
> 流量重定向能力需要系统权限支持，应用需在 `module.json5` 中声明 `ohos.permission.kernel.TRAFFIC_FILTER` 权限，并在原生侧调用 C API。

相关文档：[Network Kit 简介](net-mgmt-overview.md)

## 约束与限制

**权限约束**

- 应用必须声明 `ohos.permission.kernel.TRAFFIC_FILTER` 系统权限，普通应用无法直接申请。

**版本约束**

- 本文档中涉及的流量重定向接口起始版本为 **API 版本 26.0.0**。

## 开发步骤

使用本文档涉及接口创建并使用流量重定向时，需先创建 Native C++ 工程，在源文件中封装相关接口，然后在 ArkTS 层调用封装好的接口，使用 hilog 或 console.info 等方法将日志打印到控制台或生成设备日志。

### 添加开发依赖

**添加动态链接库**

在 `CMakeLists.txt` 的 `target_link_libraries` 中添加以下共享库：

```txt
libace_napi.z.so
libhilog_ndk.z.so
libnet_trafficfilter.so
```

**头文件**

<!-- @[header_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->

### 实现流量重定向

在开始实现前，请确保已完成以下前置条件：
- 已创建 Native C++ 工程。
- 已在 `module.json5` 的 `requestPermissions` 项中声明 `ohos.permission.kernel.TRAFFIC_FILTER` 权限。

1. 在源文件中编写调用该 API 的代码，实现重定向器的创建。

   使用 [OH_TrafficFilter_CreateRedirector](../reference/apis-network-kit/capi-net-trafficfilter-h.md) 接口创建流量重定向实例。`group_id` 用于标识重定向器分组，`priority` 控制规则优先级。

   <!-- @[create_redirector](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->

2. 添加重定向规则。规则中可配置源/目的 IP、端口、接口、UID 范围以及代理服务器地址。

   使用 [OH_TrafficFilter_AddRedirectRule](../reference/apis-network-kit/capi-net-trafficfilter-h.md) 接口向重定向器添加规则。`OH_TrafficFilter_RedirectRule` 中 `protocol` 固定为 TCP，`hookPoint`（Netfilter 钩子点）仅支持 `PREROUTING` 和 `OUTPUT`，`proxy_ip` 与 `proxy_port` 指定代理服务器地址。

   <!-- @[add_redirect_rule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->

3. 清除规则并销毁重定向器。

   测试完成后，建议先清除规则，再销毁重定向器，释放相关资源。
   - 使用 [OH_TrafficFilter_ClearRedirectRule](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_clearredirectrule) 清除所有重定向规则。
   - 使用 [OH_TrafficFilter_DestroyRedirector](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_destroyredirector) 销毁重定向器。

   <!-- @[clear_redirect_rule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->

   简要说明：`redirector` 为空时直接返回 `-1`。

   <!-- @[destroy_redirect_rule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->

   简要说明：销毁重定向器后会自动释放其占用的系统资源（包括规则），销毁后请将句柄置空，避免重复释放。

4. 初始化并导出通过 N-API 封装的 `napi_value` 类型对象，通过外部函数接口将函数提供给 JavaScript 调用。

   <!-- @[init_exports](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
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

5. 将上一步中初始化成功的对象通过 `RegisterEntryModule` 函数，使用 `napi_module_register` 函数将模块注册到 Node.js 中。

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

### 查询连接所属进程

[OH_TrafficFilter_QueryProcess](../reference/apis-network-kit/capi-net-trafficfilter-h.md) 可根据五元组（源 IP、目的 IP、源端口、目的端口、协议）查询发起该连接的进程信息，常用于在重定向前识别流量归属。

<!-- @[query_process](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->

``` C++
struct QueryArgs {
    std::string srcIp;
    std::string dstIp;
    uint32_t srcPort = 0;
    uint32_t dstPort = 0;
    uint32_t protocol = PROTOCOL_TCP;
};

static std::string ParseQueryArgsFromNapi(napi_env env, const napi_value args[], QueryArgs& queryArgs)
{
    int ardIdxDstIp = 2;
    int argIdxDstPort = 3;
    int argIdxProtocol = 4;
    size_t srcIpLen = 0;
    size_t dstIpLen = 0;

    napi_get_value_string_utf8(env, args[0], nullptr, 0, &srcIpLen);
    napi_get_value_string_utf8(env, args[ardIdxDstIp], nullptr, 0, &dstIpLen);

    std::vector<char> srcIpBuf(srcIpLen + 1);
    std::vector<char> dstIpBuf(dstIpLen + 1);

    napi_get_value_string_utf8(env, args[0], srcIpBuf.data(), srcIpBuf.size(), &srcIpLen);
    napi_get_value_string_utf8(env, args[ardIdxDstIp], dstIpBuf.data(), dstIpBuf.size(), &dstIpLen);

    queryArgs.srcIp = srcIpBuf.data();
    queryArgs.dstIp = dstIpBuf.data();

    napi_get_value_uint32(env, args[1], &queryArgs.srcPort);
    napi_get_value_uint32(env, args[argIdxDstPort], &queryArgs.dstPort);
    napi_get_value_uint32(env, args[argIdxProtocol], &queryArgs.protocol);

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

    connectionInfo.srcIp.family = DetectIPFamilyFromAddr(queryArgs.srcIp);
    if (!ParseIPAddressByFamily(queryArgs.srcIp, connectionInfo.srcIp.family,
        connectionInfo.srcIp.addr)) {
        return "ERROR: Invalid source IP address";
    }
    connectionInfo.src_port = static_cast<uint16_t>(queryArgs.srcPort);

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
        OH_LOG_INFO(LOG_APP, "QueryProcessNapi - Process not found");
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
    size_t argc = REQUIRED_ARG_COUNT;
    napi_value args[REQUIRED_ARG_COUNT] = {nullptr};

    napi_get_cb_info(env, info, &argc, args, nullptr, nullptr);

    auto CreateStringResult = [env](const char* msg) -> napi_value {
        napi_value result;
        napi_create_string_utf8(env, msg, strlen(msg), &result);
        return result;
    };

    if (argc < REQUIRED_ARG_COUNT) {
        return CreateStringResult("ERROR: Missing required parameters");
    }

    OH_TrafficFilter_ConnectionInfo connectionInfo;
    std::string error = BuildQueryConnectionInfo(env, args, connectionInfo);
    if (!error.empty()) {
        return CreateStringResult(error.c_str());
    }

    OH_TrafficFilter_ProcessInfo processInfo;
    memset(&processInfo, 0, sizeof(processInfo));
    processInfo.size = sizeof(OH_TrafficFilter_ProcessInfo);

    int32_t ret = OH_TrafficFilter_QueryProcess(&connectionInfo, &processInfo);

    return CreateQueryResponseNapi(env, ret, processInfo);
}
```

## 调测验证

1. 连接设备，使用 DevEco Studio 打开搭建好的工程。
2. 运行工程，进入重定向管理页面。
3. 点击 **Create Redirector** 按钮创建重定向实例。
4. 配置目标 IP、目标端口、代理 IP 和代理端口，点击 **Add Redirect Rule** 添加规则。
5. 在设备上触发匹配规则的 TCP 流量（例如访问目标 IP 的 80 端口），验证流量被重定向到代理服务器。
6. 如需查询连接归属进程，点击 **Query Process** 并输入五元组信息。
7. 测试完成后，先点击 **Clear Redirect Rule** 清除规则，再点击 **Destroy Redirector** 释放资源。

完整示例代码请参考：[TrafficFilter_Redirect_case](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case)。
