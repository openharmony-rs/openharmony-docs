# 重定向网络流量 (C/C++)
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

## 场景介绍

网络流量重定向能力通过内核网络协议栈拦截并改写TCP报文的目的地址，将匹配规则的流量转发到指定的代理服务器。典型应用场景包括：

- 企业网络审计：将指定应用或指定目的地址的出站TCP流量重定向到审计代理。
- 内容过滤代理：在网关或终端侧透明拦截HTTP/HTTPS流量并转发到内容安全代理。
- VPN透明代理：将需要代理的应用流量无感知地引流到本地或远程代理服务。

> **说明：**

> 流量重定向能力需要系统权限支持，应用需在`module.json5`中声明`ohos.permission.kernel.TRAFFIC_FILTER`权限，并在原生侧调用C API。

## 约束与限制

**权限约束**

应用必须声明`ohos.permission.kernel.TRAFFIC_FILTER`权限。

## 开发步骤

使用本文档涉及接口创建并使用流量重定向时，需先创建Native C++工程，在源文件中封装相关接口，然后在ArkTS层调用封装好的接口，使用hilog或console.info等方法将日志打印到控制台或生成设备日志。

### 添加开发依赖

**添加动态链接库**

在`CMakeLists.txt`的`target_link_libraries`中添加以下共享库：

```txt
libace_napi.z.so
libhilog_ndk.z.so
libnet_trafficfilter.so
```

**头文件**

<!-- @[header_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->

### 实现流量重定向

在开始实现前，请确保已完成以下前置条件：
- 已创建Native C++工程。
- 已在`module.json5`的`requestPermissions`项中声明`ohos.permission.kernel.TRAFFIC_FILTER`权限。

1. 在源文件中编写调用该API的代码，实现重定向器的创建。

   使用[OH_TrafficFilter_CreateRedirector](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_createredirector)接口创建流量重定向实例。`group_id`用于标识重定向器分组，`priority`控制规则优先级。

   <!-- @[create_redirector](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->

2. 添加重定向规则。规则中可配置源/目的IP、端口、接口、UID范围以及代理服务器地址。

   使用[OH_TrafficFilter_AddRedirectRule](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_addredirectrule)接口向重定向器添加规则。`OH_TrafficFilter_RedirectRule`中`protocol`固定为TCP，`hookPoint`（Netfilter钩子点）仅支持`PREROUTING`和`OUTPUT`，`proxy_ip`与`proxy_port`指定代理服务器地址。

   <!-- @[add_redirect_rule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->

3. 清除规则并销毁重定向器。

   测试完成后，建议先清除规则，再销毁重定向器，释放相关资源。
   - 使用[OH_TrafficFilter_ClearRedirectRule](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_clearredirectrule)清除所有重定向规则。
   - 使用[OH_TrafficFilter_DestroyRedirector](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_destroyredirector)销毁重定向器。

   <!-- @[clear_redirect_rule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->

   <!-- @[destroy_redirect_rule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->


4. 初始化并导出通过N-API封装的`napi_value`类型对象，通过外部函数接口将函数提供给JavaScript调用。

   <!-- @[init_exports](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->

5. 将上一步中初始化成功的对象通过`RegisterEntryModule`函数，使用`napi_module_register`函数将模块注册到Node.js中。

   <!-- @[register_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->

### 查询连接所属进程

[OH_TrafficFilter_QueryProcess](../reference/apis-network-kit/capi-net-trafficfilter-h.md#oh_trafficfilter_queryprocess) 可根据五元组（源IP、目的IP、源端口、目的端口、协议）查询发起该连接的进程信息，常用于在重定向前识别流量归属。

<!-- @[query_process](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/TrafficFilter_Redirect_case/entry/src/main/cpp/napi_init.cpp) -->

## 调测验证

1. 连接设备，使用DevEco Studio打开搭建好的工程。
2. 运行工程，进入重定向管理页面。
3. 点击**Create Redirector**按钮创建重定向实例。
4. 配置目标IP、目标端口、代理IP和代理端口，点击**Add Redirect Rule**添加规则。
5. 在设备上触发匹配规则的TCP流量（例如访问目标IP的80端口），验证流量被重定向到代理服务器。
6. 如需查询连接归属进程，点击**Query Process**并输入五元组信息。
7. 测试完成后，先点击**Clear Redirect Rule**清除规则，再点击**Destroy Redirector**释放资源。
