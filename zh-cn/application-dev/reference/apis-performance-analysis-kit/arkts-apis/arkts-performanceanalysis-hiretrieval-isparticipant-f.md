# isParticipant

## 导入模块

```TypeScript
import { hiRetrieval } from '@kit.PerformanceAnalysisKit';
```

<a id="isparticipant"></a>
## isParticipant

```TypeScript
function isParticipant(): boolean
```

查询此设备是否正在参与应用灰度活动。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-hiRetrieval-function isParticipant(): boolean--><!--Device-hiRetrieval-function isParticipant(): boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiRetrieval

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 标识此设备现在是否正在参与应用灰度活动，true表示正在参与，false表示未参与。 |

