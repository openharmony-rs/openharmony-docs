# WLAN常见问题

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @qq_43802146-->
<!--Designer: @qq_43802146-->
<!--Tester: @furryfurry123-->
<!--Adviser: @zhang_yixin13-->

## 使用wifiManager.getLinkedInfo()获取SSID时，是否需要访问用户位置信息

不需要。

wifiManager.getLinkedInfo()仅获取当前已连接的Wi-Fi基础信息（如 SSID、BSSID、信号强度等）。由于设备已经处于连接状态，系统认为用户已知晓当前网络环境，因此不涉及基于 Wi-Fi 扫描的位置隐私保护逻辑。

只有在调用 getScanResult() 进行主动扫描时，才需要申请 ohos.permission.LOCATION 权限，因为扫描结果可用于估算用户物理位置。

虽然获取 SSID 不需要位置权限，但如果需要获取设备 MAC 地址，则需根据策略申请 ohos.permission.GET_WIFI_LOCAL_MAC（物理地址）或使用随机 MAC，但这两者均与位置权限无关。

## 在使用addCandidateConfig连接Wi-Fi时偶现错误码201
需要权限： ohos.permission.SET_WIFI_INFO。

错误码含义：在鸿蒙网络框架中，错误码 201 通常对应 权限不足 (Permission Denied) 或 系统服务不可用。
核心原因：
权限缺失：修改 Wi-Fi 配置（包括添加候选网络）属于敏感操作，必须持有 ohos.permission.SET_WIFI_INFO 权限。如果未申请或权限被系统撤销，会直接返回错误。
配置冲突：若该 SSID 已存在于配置列表中且配置冲突，也可能导致写入失败。
修复方案：
检查权限：确保 module.json5 中已声明 ohos.permission.SET_WIFI_INFO，并在运行时（如 API 9+）或初始化阶段正确申请。

## 是否有API支持切换网络，以解决在特定情况下无法连接外网的问题

默认情况下，系统不会自动回连无连接记录的网络。

OpenHarmony提供WLAN候选网络相关 API，可用于在当前 Wi-Fi 无外网访问能力时，主动连接应用添加的备用 Wi-Fi/热点。具体流程如下：

1. 添加候选网络：使用 [addCandidateConfig](../../reference/apis-connectivity-kit/js-apis-wifiManager.md#addcandidateconfig7) 添加候选网络配置。该操作仅保存候选配置，不会自动连接。添加后的候选网络属于应用维度，与系统 WLAN 页面配置相互隔离。
2. 发起连接：需要切换时，调用 [connectToCandidateConfig](../../reference/apis-connectivity-kit/js-apis-wifiManager.md#connecttocandidateconfig7)(networkId) 发起连接。
3. 用户确认连接（推荐）：如需用户确认后再连接，从 API version 20 起可使用 [connectToCandidateConfigWithUserAction](../../reference/apis-connectivity-kit/js-apis-wifiManager.md#connecttocandidateconfigwithuseraction20)(networkId)。该接口会弹出用户确认弹窗，用户确认前不会执行连接。可通过错误码区分用户拒绝（2100301）或未响应（2100302）。

> **说明：** 
>
> 对无连接记录的候选网络，系统不会自动回连。通过用户确认并连接成功后，后续可依据系统策略自动回连。

## 在连接到没有网络的热点时，系统自动断开且未触发Wi-Fi连接状态变化回调，如何正确监听网络状态
当前网络无法访问互联网。点击【使用】连接，或点击【不使用】以继续搜索更佳网络。
