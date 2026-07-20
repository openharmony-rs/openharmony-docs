# getLastParticipationTimestamp

## 导入模块

```TypeScript
import { hiRetrieval } from '@kit.PerformanceAnalysisKit';
```

<a id="getlastparticipationtimestamp"></a>
## getLastParticipationTimestamp

```TypeScript
function getLastParticipationTimestamp(): number
```

查询此设备上次参与应用灰度活动的UNIX时间戳，如果此设备从未参与则返回0。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-hiRetrieval-function getLastParticipationTimestamp(): long--><!--Device-hiRetrieval-function getLastParticipationTimestamp(): long-End-->

**系统能力：** SystemCapability.HiviewDFX.HiRetrieval

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 上一次参与应用灰度活动的UNIX时间戳，单位为毫秒。如果此设备从未参与则返回0。 |

