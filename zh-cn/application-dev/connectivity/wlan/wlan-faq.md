# WLAN常见问题

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @qq_43802146-->
<!--Designer: @qq_43802146-->
<!--Tester: @furryfurry123-->
<!--Adviser: @zhang_yixin13-->


## 是否有API支持切换网络，以解决在特定情况下无法连接外网的问题

默认情况下，系统不会自动回连无连接记录的网络。

OpenHarmony提供WLAN候选网络相关 API，可用于在当前 Wi-Fi 无外网访问能力时，主动连接应用添加的备用 Wi-Fi/热点。具体流程如下：

1. 添加候选网络：使用 [addCandidateConfig](../../reference/apis-connectivity-kit/js-apis-wifiManager.md#wifimanageraddcandidateconfig) 添加候选网络配置。该操作仅保存候选配置，不会自动连接。添加后的候选网络属于应用维度，与系统 WLAN 页面配置相互隔离。

2. 发起连接：需要切换时，调用 [connectToCandidateConfig](../../reference/apis-connectivity-kit/js-apis-wifiManager.md#wifimanagerconnecttocandidateconfig)(networkId) 发起连接。

3. 用户确认连接（推荐）：如需用户确认后再连接，从 API version 20 起可使用 [connectToCandidateConfigWithUserAction](../../reference/apis-connectivity-kit/js-apis-wifiManager.md#wifimanagerconnecttocandidateconfigwithuseraction20)(networkId)。该接口会弹出用户确认弹窗，用户确认前不会执行连接。可通过错误码区分用户拒绝（2100301）或未响应（2100302）。

> **说明：** 
>
> 对无连接记录的候选网络，系统不会自动回连。通过用户确认并连接成功后，后续可依据系统策略自动回连。

## 在连接到没有网络的热点时，系统自动断开且未触发Wi-Fi连接状态回调，如何正确监听网络状态

系统行为：

- 当设备连接无外网访问能力的热点时，系统会自动断开连接，但此断开过程不会通过 Wi-Fi 连接状态变更回调事件通知应用。
- 这是系统层的主动决策行为，目的是避免设备长时间处于无法上网的网络环境。

原因分析：

系统优先保障用户体验，会自动规避无法访问互联网的网络。当检测到热点无网络连接能力时，系统会立即断开并尝试连接其他可用网络，这个过程不会触发 Wi-Fi 状态变更回调，因此应用无法通过常规回调感知。

解决方案：

应用需要自行检测网络连通性来判断当前网络是否可用。可采用以下方案：

1. 使用 [on('wifiStateChange')](../../reference/apis-connectivity-kit/js-apis-wifiManager.md#onwifistatechange) 监听 Wi-Fi 开关状态变化。

2. 使用 HTTP 请求（如 fetch 或 axios）主动探测网络连通性，例如请求一个已知可用的外网地址，根据响应判断是否可以访问外网。

3. 结合使用 [getLinkedInfo()](../../reference/apis-connectivity-kit/js-apis-wifiManager.md#getlinkedinfo11) 获取当前连接信息，交叉判断网络状态。

> **说明：** 
>
> 不建议依赖 Wi-Fi 状态回调来判断网络连通性，应使用应用层的网络探测机制。
