# getAppNativeMemInfoWithCache

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getAppNativeMemInfoWithCache

```TypeScript
function getAppNativeMemInfoWithCache(forceRefresh?: boolean): NativeMemInfo
```

获取应用进程内存信息。与`getAppNativeMemInfo`接口相比，该接口使用了缓存机制，以提高性能。缓存的有效期为5分钟。 > **注意** > > 由于读取 /proc/{pid}/smaps_rollup 比较耗时，建议不在主线程中使用该接口。可以通过@ohos.taskpool或@ohos.worker开启异步线程，以避免应用卡顿。

**起始版本：** 23

<!--Device-hidebug-function getAppNativeMemInfoWithCache(forceRefresh?: boolean): NativeMemInfo--><!--Device-hidebug-function getAppNativeMemInfoWithCache(forceRefresh?: boolean): NativeMemInfo-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| forceRefresh | boolean | 否 | 是否需要无视缓存有效性，强制更新缓存值。默认值：false。 true：直接获取当前内存数据并更新缓存值。 false：缓存有效时，直接返回缓存值，缓存失效时获取当前内存数据并更新缓存值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [NativeMemInfo](arkts-performanceanalysis-hidebug-nativememinfo-i.md) | 应用进程内存信息。 |

**示例**

```TypeScript
let nativeMemInfo: hidebug.NativeMemInfo = hidebug.getAppNativeMemInfoWithCache();
console.info(`pss: ${nativeMemInfo.pss}, vss: ${nativeMemInfo.vss}, rss: ${nativeMemInfo.rss}, ` +
  `sharedDirty: ${nativeMemInfo.sharedDirty}, privateDirty: ${nativeMemInfo.privateDirty}, ` +
  `sharedClean: ${nativeMemInfo.sharedClean}, privateClean: ${nativeMemInfo.privateClean}`);
```

