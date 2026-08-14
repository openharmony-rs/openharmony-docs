# getAppNativeMemInfoAsync

## getAppNativeMemInfoAsync

```TypeScript
function getAppNativeMemInfoAsync(): Promise<NativeMemInfo>
```

读取/proc/{pid}/smaps_rollup和/proc/{pid}/statm节点的数据以获取应用进程内存信息，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-hidebug-function getAppNativeMemInfoAsync(): Promise<NativeMemInfo>--><!--Device-hidebug-function getAppNativeMemInfoAsync(): Promise<NativeMemInfo>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[NativeMemInfo](arkts-performanceanalysis-hidebug-nativememinfo-i.md)&gt; | promise对象，返回应用进程内存信息。 |

## 示例

```TypeScript
hidebug.getAppNativeMemInfoAsync().then((nativeMemInfo: hidebug.NativeMemInfo)=>{
  console.info(`pss: ${nativeMemInfo.pss}, vss: ${nativeMemInfo.vss}, rss: ${nativeMemInfo.rss}, ` +
    `sharedDirty: ${nativeMemInfo.sharedDirty}, privateDirty: ${nativeMemInfo.privateDirty}, ` +
    `sharedClean: ${nativeMemInfo.sharedClean}, privateClean: ${nativeMemInfo.privateClean}`);
});
```

