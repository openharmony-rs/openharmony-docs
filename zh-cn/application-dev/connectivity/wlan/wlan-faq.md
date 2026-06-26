# WLAN常见问题

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @qq_43802146-->
<!--Designer: @qq_43802146-->
<!--Tester: @furryfurry123-->
<!--Adviser: @zhang_yixin13-->

## Wi-Fi扫描与候选配置接口FAQ

**概述**

本文档针对 startScan、getScanInfoList及addCandidateConfig 三个接口，归纳其常见错误码、典型错误信息、根因定位方法及推荐解决方案，适用于系统级Wi-Fi服务异常或接口调用失败的排查场景。

1. startScan接口[@ohos.wifiManager (WLAN)](../../reference/apis-connectivity-kit/js-apis-wifiManager.md#wifimanagerstartscan21)。

1.1 错误信息：Permission denied。
根因：调用进程缺少必要的 Wi-Fi 扫描权限。
定位方法：过滤系统日志，查找包含 "Scan:" 前缀的权限校验相关打印。
解决方案：检查调用方的 Android 权限声明（如 ACCESS_FINE_LOCATION、ACCESS_COARSE_LOCATION、CHANGE_WIFI_STATE），确保已动态获取且系统授权通过。

1.2 错误信息：Scanning service is not enabled。[WIFI错误码](../../reference/apis-connectivity-kit/errorcode-wifi.md)。
根因：系统级 Wi-Fi 扫描服务处于不可用状态，可能由服务进程异常或驱动状态异常引起。
定位方法：查看系统服务状态日志。
解决方案：建议先关闭再重新开启 Wi-Fi 功能，若无效则执行系统重启以恢复扫描服务。

1.3 错误信息：Operation failed。[WIFI错误码](../../reference/apis-connectivity-kit/errorcode-wifi.md)。
该通用失败可能由多种底层原因触发，请根据日志关键字进一步区分：
| 日志关键字 | 根因说明 | 解决方案 |
| -------- | -------- | -------- |
| Scan not allowed（结合 "extern scan not allow"）| 当前不允许发起扫描，常见于Wi-Fi未开启或系统处于省电空闲状态。| 确认Wi-Fi已开启，并退出省电/空闲模式后重试。 |
| scanStyle is | 当前请求为低优先级（LP）扫描，但系统不支持 LP 类型扫描。| 调整扫描策略，使用普通扫描优先级，或确认设备固件是否支持LP扫描。 |
| Have no allowed band or freq | 扫描参数中未指定合法的频段或信道，导致扫描无法执行。 | 检查传入的扫描配置，确保包含有效的频段或信道列表。 |
| StoreRequestScanConfig failed | 待处理的扫描请求数量已达系统上限，无法再存入新任务。 | 减少扫描并发频率，或等待已有任务完成后重试。 |
| CreateMessage failed | 系统内部创建扫描消息对象失败，可能为内存或IPC异常。| 开关 Wi-Fi 或重启设备。 |
| 无上述特定关键字 | 其他系统内部异常。	| 优先尝试开关Wi-Fi，若问题持续则执行设备重启。 |

2. getScanInfoList接口[@ohos.wifiManager (WLAN)](../../reference/apis-connectivity-kit/js-apis-wifiManager.md#wifimanagergetscaninfolist10)。

2.1 错误信息：Permission denied。[WIFI错误码](../../reference/apis-connectivity-kit/errorcode-wifi.md)。
根因：调用方缺少获取扫描结果所需的权限。
定位方法：过滤日志，查找包含 "GetScanInfoList:" 前缀的权限检查记录。
解决方案：确认已声明并授予ACCESS_FINE_LOCATION等必要权限。

2.2 错误信息：Operation failed。
根因：系统内部状态异常导致无法返回扫描结果列表，通常为Wi-Fi服务或驱动层临时故障。
解决方案：首先尝试开关Wi-Fi，若问题未能解决，则重启设备恢复系统状态。

3. addCandidateConfig 接口[@ohos.wifiManager (WLAN)](../../reference/apis-connectivity-kit/js-apis-wifiManager.md#wifimanageraddcandidateconfig)

3.1 错误信息：Operation failed。[WIFI错误码](../../reference/apis-connectivity-kit/errorcode-wifi.md)。

3.1.1 日志包含 "AddCandidateConfig failed, exceed max num:"
根因：当前已添加的候选配置数量超过系统允许的最大值（16 个）。
解决方案：减少传入的配置数量，确保不超过上限；若需更新配置，建议先移除旧配置再添加新配置。

3.1.2 无特定日志关键字（其他内部错误）
根因：系统内部异常，可能为Wi-Fi服务状态异常或配置格式错误。
解决方案：执行开关Wi-Fi或重启设备以恢复服务。

3.2 错误信息：Capability not supported。

3.2.1 日志包含 "AddCandidateConfig unsupport wep key"
根因：当前系统或固件不支持WEP加密类型的候选配置。
解决方案：移除WEP加密配置，改用受支持的加密方式（如 WPA2/WPA3）。

