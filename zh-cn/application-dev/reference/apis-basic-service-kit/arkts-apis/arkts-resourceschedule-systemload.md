# @ohos.resourceschedule.systemload

系统根据当前温度、负载以及是否处于高负载场景等信息决策出系统负载融合档位，并在档位变化时通知已注册的应用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace systemLoad--><!--Device-unnamed-declare namespace systemLoad-End-->

**系统能力：** SystemCapability.ResourceSchedule.SystemLoad

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [getLevel](arkts-basicservices-systemload-getlevel-f.md#getLevel) | 获取系统负载融合档位，使用promise异步回调。 |
| [offSystemLoadChange](arkts-basicservices-systemload-offsystemloadchange-f.md#offSystemLoadChange) | Unregister system load callback for perception system load change |
| off_systemLoadChange | 取消注册系统负载回调，使用callback异步回调。 |
| [onSystemLoadChange](arkts-basicservices-systemload-onsystemloadchange-f.md#onSystemLoadChange) | Register system load callback for perception system load change |
| on_systemLoadChange | 注册系统负载回调，感知系统负载融合档位变化，使用callback异步回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SystemLoadLevel](arkts-basicservices-systemload-systemloadlevel-e.md) | 系统负载融合档位。 |

