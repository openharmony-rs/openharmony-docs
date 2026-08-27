# getRssInfo

## 导入模块

```TypeScript
```

## getRssInfo

```TypeScript
function getRssInfo(): RssInfo
```

获取应用程序进程的物理内存使用信息。读取/proc/{pid}/status节点的数据。

> **注意**：
> 
> 读取/proc/{pid}/status耗时很短，与[hidebug.getAppNativeMemInfo](arkts-performanceanalysis-hidebug-getappnativememinfo-f.md)接口中获取的`rss`值相比存在一点误差，但该
> 接口更加轻量，为避免应用丢帧或卡顿推荐使用该接口。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RssInfo](arkts-performanceanalysis-hidebug-rssinfo-i.md) | 应用进程的物理内存信息。 |

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let rssInfo: hidebug.RssInfo = hidebug.getRssInfo();
console.info(`rss: ${rssInfo.rss}, swapRss: ${rssInfo.swapRss}`);
```
