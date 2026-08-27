# getAppNativeMemInfo

## 导入模块

```TypeScript
```

## getAppNativeMemInfo

```TypeScript
function getAppNativeMemInfo(): NativeMemInfo
```

获取应用进程内存信息。读取/proc/{pid}/smaps_rollup和/proc/{pid}/statm节点的数据。

> **注意**：
> 
> 由于读取/proc/{pid}/smaps_rollup耗时较长，推荐使用异步接口
> [hidebug.getAppNativeMemInfoAsync](arkts-performanceanalysis-hidebug-getappnativememinfoasync-f.md)，以避免应用丢帧或卡顿。
> 
> 推荐使用[hidebug.getRssInfo](arkts-performanceanalysis-hidebug-getrssinfo-f.md)接口获取应用的rss使用信息

**起始版本：** 12

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NativeMemInfo](arkts-performanceanalysis-hidebug-nativememinfo-i.md) | 应用进程内存信息。 |

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let nativeMemInfo: hidebug.NativeMemInfo = hidebug.getAppNativeMemInfo();
console.info(`pss: ${nativeMemInfo.pss}, vss: ${nativeMemInfo.vss}, rss: ${nativeMemInfo.rss}, ` +
  `sharedDirty: ${nativeMemInfo.sharedDirty}, privateDirty: ${nativeMemInfo.privateDirty}, ` +
  `sharedClean: ${nativeMemInfo.sharedClean}, privateClean: ${nativeMemInfo.privateClean}`);
```
