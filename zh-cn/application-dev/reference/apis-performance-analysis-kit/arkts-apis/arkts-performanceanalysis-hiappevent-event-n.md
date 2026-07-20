# event

提供事件名称常量，包括系统事件名称常量和应用事件名称常量。<br>应用事件名称常量是为开发者在调用Write接口进行应用事件打点时预留的可选自定义事件名称。

**起始版本：** 9

<!--Device-hiAppEvent-namespace event--><!--Device-hiAppEvent-namespace event-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## 汇总

### 常量

| 名称 | 说明 |
| --- | --- |
| [USER_LOGIN](arkts-performanceanalysis-event-con.md#user_login) | 用户登录事件。预留的应用事件名称常量。  **原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。 |
| [USER_LOGOUT](arkts-performanceanalysis-event-con.md#user_logout) | 用户登出事件。预留的应用事件名称常量。  **原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。 |
| [DISTRIBUTED_SERVICE_START](arkts-performanceanalysis-event-con.md#distributed_service_start) | 分布式服务启动事件。预留的应用事件名称常量。  **原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。 |
| [APP_CRASH](arkts-performanceanalysis-event-con.md#app_crash) | 应用崩溃事件。系统事件名称常量。  **原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。 |
| [APP_FREEZE](arkts-performanceanalysis-event-con.md#app_freeze) | 应用冻屏事件。系统事件名称常量。  **原子化服务API：** 从API version 11开始，该参数支持在原子化服务中使用。 |
| [APP_LAUNCH](arkts-performanceanalysis-event-con.md#app_launch) | 应用启动耗时事件。系统事件名称常量。  **原子化服务API：** 从API version 12开始，该参数支持在原子化服务中使用。 |
| [SCROLL_JANK](arkts-performanceanalysis-event-con.md#scroll_jank) | 应用滑动丢帧事件。系统事件名称常量。  **原子化服务API：** 从API version 12开始，该参数支持在原子化服务中使用。 |
| [CPU_USAGE_HIGH](arkts-performanceanalysis-event-con.md#cpu_usage_high) | 应用CPU高负载事件。系统事件名称常量。  **原子化服务API：** 从API version 12开始，该参数支持在原子化服务中使用。 |
| [BATTERY_USAGE](arkts-performanceanalysis-event-con.md#battery_usage) | 应用24h功耗器件分解统计事件。系统事件名称常量。  **原子化服务API：** 从API version 12开始，该参数支持在原子化服务中使用。 |
| [RESOURCE_OVERLIMIT](arkts-performanceanalysis-event-con.md#resource_overlimit) | 应用资源泄漏事件。系统事件名称常量。  **原子化服务API：** 从API version 12开始，该参数支持在原子化服务中使用。 |
| [ADDRESS_SANITIZER](arkts-performanceanalysis-event-con.md#address_sanitizer) | 应用地址越界事件。系统事件名称常量。  **原子化服务API：** 从API version 12开始，该参数支持在原子化服务中使用。 |
| [MAIN_THREAD_JANK](arkts-performanceanalysis-event-con.md#main_thread_jank) | 应用主线程超时事件。系统事件名称常量。  **原子化服务API：** 从API version 12开始，该参数支持在原子化服务中使用。 |
| [APP_KILLED](arkts-performanceanalysis-event-con.md#app_killed) | 应用终止事件。系统事件名称常量。  **原子化服务API：** 从API version 20开始，该参数支持在原子化服务中使用。 |
| [APP_HICOLLIE](arkts-performanceanalysis-event-con.md#app_hicollie) | 应用任务执行超时事件。系统事件名称常量。  **原子化服务API：** 从API version 21开始，该参数支持在原子化服务中使用。 |
| [AUDIO_JANK_FRAME](arkts-performanceanalysis-event-con.md#audio_jank_frame) | 应用音频卡顿事件。系统事件名称常量。  **原子化服务API：** 从API version 21开始，该参数支持在原子化服务中使用。 |
| [SCROLL_ARKWEB_FLING_JANK](arkts-performanceanalysis-event-con.md#scroll_arkweb_fling_jank) | ArkWeb抛滑丢帧事件。系统事件名称常量。  **原子化服务API：** 从API version 23开始，该参数支持在原子化服务中使用。 |
| [appFreezeWarning](arkts-performanceanalysis-event-con.md#appfreezewarning) | 应用冻屏告警事件。系统事件名称常量。  26.0.0  **模型约束：** 此接口仅可在Stage模型下使用。  **原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。 |

