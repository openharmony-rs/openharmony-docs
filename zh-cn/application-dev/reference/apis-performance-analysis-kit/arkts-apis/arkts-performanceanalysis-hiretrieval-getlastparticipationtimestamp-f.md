# getLastParticipationTimestamp

## getLastParticipationTimestamp

```TypeScript
function getLastParticipationTimestamp(): long
```

查询此设备上次参与应用灰度活动的UNIX时间戳，如果此设备从未参与则返回0。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-hiRetrieval-function getLastParticipationTimestamp(): long--><!--Device-hiRetrieval-function getLastParticipationTimestamp(): long-End-->

**系统能力：** SystemCapability.HiviewDFX.HiRetrieval

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 上一次参与应用灰度活动的UNIX时间戳，单位为毫秒。如果此设备从未参与则返回0。 |

