# WLAN常见问题

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @qq_43802146-->
<!--Designer: @qq_43802146-->
<!--Tester: @furryfurry123-->
<!--Adviser: @zhang_yixin13-->

## 使用wifiManager.getLinkedInfo()获取SSID时，是否需要访问用户位置信息

不需要。
- 原理：wifiManager.getLinkedInfo() 仅获取当前已连接的 Wi-Fi 基础信息（如 SSID、BSSID、信号强度等）。由于设备已经处于连接状态，系统认为用户已知晓当前网络环境，因此不涉及基于 Wi-Fi 扫描的位置隐私保护逻辑。
对比：只有在调用 getScanResult() 进行主动扫描时，才需要申请 ohos.permission.LOCATION 权限，因为扫描结果可用于估算用户物理位置。
注意：虽然获取 SSID 不需要位置权限，但如果需要获取设备 MAC 地址，则需根据策略申请 ohos.permission.GET_WIFI_LOCAL_MAC（物理地址）或使用随机 MAC，但这两者均与位置权限无关。

## App在使用addCandidateConfig连接WiFi时偶现错误码201，需明确错误原因及修复方式以优化用户体验
需要权限： ohos.permission.SET_WIFI_INFO。

错误码含义：在鸿蒙网络框架中，错误码 201 通常对应 权限不足 (Permission Denied) 或 系统服务不可用。
核心原因：
权限缺失：修改 Wi-Fi 配置（包括添加候选网络）属于敏感操作，必须持有 ohos.permission.SET_WIFI_INFO 权限。如果未申请或权限被系统撤销，会直接返回错误。
配置冲突：若该 SSID 已存在于配置列表中且配置冲突，也可能导致写入失败。
修复方案：
检查权限：确保 module.json5 中已声明 ohos.permission.SET_WIFI_INFO，并在运行时（如 API 9+）或初始化阶段正确申请。
异常处理：在代码中捕获该错误码，若因权限导致，引导用户进入设置页手动授权；若因配置冲突，建议先调用 removeConfig 清理旧配置再重新添加。
用户引导：在用户界面增加提示：“需要开启 Wi-Fi 管理权限才能添加网络”，提升容错率。

## 鸿蒙系统是否有API来切换网络，以解决在特定情况下无法连接外网的问题
鸿蒙系统提供了灵活的候选网络管理机制，但默认不会自动回连无连接记录的网络。若需实现“智能切换”或“强制连接”，建议采用以下流程：

添加候选网络：
使用 addCandidateConfig 将目标网络（如备用 Wi-Fi 或热点）配置为候选项。
注意：仅添加配置后，系统不会自动触发连接，除非该网络有“连接记录”且信号优于当前网络。
主动触发连接：
当检测到当前网络无外网访问能力时，调用 connectToCandidateConfig 或 connectToCandidateConfigWithUserAction 方法。
静默连接：connectToCandidateConfig（适用于后台自动切换，需权限）。
用户确认连接：connectToCandidateConfigWithUserAction（先弹出确认框，提升用户体验）。
实现自动回连机制：
一旦连接成功，系统会自动在该设备上生成“连接记录”。此后，若该网络信号变好，系统即可依据策略自动回连，无需再次手动干预。

## 在连接到没有网络的热点时，系统会自动断开连接且未触发Wi-Fi连接状态变化的回调，导致无法正常监听连接状态变化
该网络无互联网访问权限。点击【确定】连接，或【取消】自动切换至更优网络。
