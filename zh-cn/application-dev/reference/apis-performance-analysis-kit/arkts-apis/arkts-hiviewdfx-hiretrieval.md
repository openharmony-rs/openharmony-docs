# @ohos.hiviewdfx.hiRetrieval

本模块提供应用灰度故障维测能力，支持以下故障类型：RSS内存泄漏、ArkTS-OOM、FD内存泄漏、GPU内存泄漏。应用灰度特性是一种运维态功能，用于精准采集故障日志。开发者在端侧集成应用灰度功能后，该应用可参与应用灰度活动。通过云端平台发布应用灰度任务，可圈选部分设备开启故障日志精准采集，帮助开发者快速定位故障。

**起始版本：** 26.0.0

<!--Device-unnamed-declare namespace hiRetrieval--><!--Device-unnamed-declare namespace hiRetrieval-End-->

**系统能力：** SystemCapability.HiviewDFX.HiRetrieval

## 导入模块

```TypeScript
import { hiRetrieval } from '@kit.PerformanceAnalysisKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getCurrentConfig](arkts-performanceanalysis-hiretrieval-getcurrentconfig-f.md#getcurrentconfig-1) | 获取当前应用灰度活动配置。 |
| [getLastParticipationTimestamp](arkts-performanceanalysis-hiretrieval-getlastparticipationtimestamp-f.md#getlastparticipationtimestamp-1) | 查询此设备上次参与应用灰度活动的UNIX时间戳，如果此设备从未参与则返回0。 |
| [init](arkts-performanceanalysis-hiretrieval-init-f.md#init-1) | 初始化应用灰度模块。多实例应用不支持调用此接口。 |
| [isParticipant](arkts-performanceanalysis-hiretrieval-isparticipant-f.md#isparticipant-1) | 查询此设备是否正在参与应用灰度活动。 |
| [participate](arkts-performanceanalysis-hiretrieval-participate-f.md#participate-1) | 设置此设备参与应用灰度活动。调用后向服务器发送参与灰度消息和应用灰度活动配置，服务器标记此设备为可圈选并记录该应用灰度活动配置作为算法参数。多次调用将更新为最新的应用灰度活动配置。 |
| [quit](arkts-performanceanalysis-hiretrieval-quit-f.md#quit-1) | 设置此设备退出应用灰度活动，退出后此设备将无法在云端被圈选。 |
| [run](arkts-performanceanalysis-hiretrieval-run-f.md#run-1) | 若此设备正在参与应用灰度活动（即已调用participate接口且未调用quit接口），则应用灰度模块开始工作，否则调用该接口不会产生任何效果。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [HiRetrievalConfig](arkts-performanceanalysis-hiretrieval-hiretrievalconfig-i.md) | 应用灰度活动配置。 |

