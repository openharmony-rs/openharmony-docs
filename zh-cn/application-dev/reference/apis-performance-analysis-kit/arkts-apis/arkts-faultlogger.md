# @ohos.faultLogger(故障日志获取)

应用可以使用faultLogger接口查询系统侧缓存的当前应用的故障日志。接口以应用包名和系统分配的UID作为唯一键值。 系统侧保存的应用故障日志数量受系统日志的压力限制， 推荐使用[@ohos.hiviewdfx.hiAppEvent]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_订阅APP\_CRASH及APP\_FREEZE等故障事件。 > **说明：** > > 本模块接口从API version 18开始废弃使用, 该接口不再维护。后续版本推荐使用 > [@ohos.hiviewdfx.hiAppEvent]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_订阅APP\_CRASH，APP\_FREEZE事件。 > > 查阅\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_， > 了解使用hiAppEvent订阅APP\_CRASH的具体信息。 > > 查阅\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_， > 了解使用hiAppEvent订阅APP\_FREEZE的具体信息。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 18

**替代接口：** ohos.hiviewdfx.hiAppEvent

<!--Device-unnamed-declare namespace FaultLogger--><!--Device-unnamed-declare namespace FaultLogger-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.FaultLogger

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [query](arkts-performanceanalysis-faultlogger-query-f.md#query) | 获取当前应用故障信息，该方法通过回调方式获取故障信息数组，故障信息数组内最多上报10份故障信息。 |
| [query](arkts-performanceanalysis-faultlogger-query-f.md#query-1) | 获取当前应用故障信息，该方法通过Promise方式返回故障信息数组，故障信息数组内最多上报10份故障信息。 |
| [querySelfFaultLog](arkts-performanceanalysis-faultlogger-queryselffaultlog-f.md#queryselffaultlog) | 获取当前应用故障信息，该方法通过回调方式获取故障信息数组，故障信息数组内最多上报10份故障信息。 |
| [querySelfFaultLog](arkts-performanceanalysis-faultlogger-queryselffaultlog-f.md#queryselffaultlog-1) | 获取当前应用故障信息，该方法通过Promise方式返回故障信息数组，故障信息数组内最多上报10份故障信息。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [FaultLogInfo](arkts-performanceanalysis-faultlogger-faultloginfo-i.md) | 故障信息数据结构，获取到的故障信息的数据结构。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [FaultType](arkts-performanceanalysis-faultlogger-faulttype-e.md) | 故障类型枚举。 |

