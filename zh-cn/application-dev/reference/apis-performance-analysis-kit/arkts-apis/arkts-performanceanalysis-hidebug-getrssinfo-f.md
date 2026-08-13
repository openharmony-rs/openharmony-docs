# getRssInfo

## getRssInfo

```TypeScript
function getRssInfo(): RssInfo
```

获取应用程序进程的物理内存使用信息。读取/proc/{pid}/status节点的数据。 > **注意** > > 读取/proc/{pid}/status耗时很短，与hidebug.getAppNativeMemInfo接口中获取的`rss`值相比存在一点误差，但该接口更加轻量，为避免应用丢帧或卡顿推荐使用该接口。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-hidebug-function getRssInfo(): RssInfo--><!--Device-hidebug-function getRssInfo(): RssInfo-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RssInfo](arkts-performanceanalysis-hidebug-rssinfo-i.md) | 应用进程的物理内存信息。 |

## 示例

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let rssInfo: hidebug.RssInfo = hidebug.getRssInfo();
console.info(`rss: ${rssInfo.rss}, swapRss: ${rssInfo.swapRss}`);
```

