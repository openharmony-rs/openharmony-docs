# getAppNativeMemInfoAsync

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getAppNativeMemInfoAsync

```TypeScript
function getAppNativeMemInfoAsync(): Promise<NativeMemInfo>
```

��ȡ/proc/{pid}/smaps_rollup��/proc/{pid}/statm�ڵ�������Ի�ȡӦ�ý����ڴ���Ϣ��ʹ��Promise�첽�ص���

**起始版本：** 20

<!--Device-hidebug-function getAppNativeMemInfoAsync(): Promise<NativeMemInfo>--><!--Device-hidebug-function getAppNativeMemInfoAsync(): Promise<NativeMemInfo>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;NativeMemInfo&gt; | promise���󣬷���Ӧ�ý����ڴ���Ϣ�� |

**示例：**

```TypeScript
hidebug.getAppNativeMemInfoAsync().then((nativeMemInfo: hidebug.NativeMemInfo)=>{
  console.info(`pss: ${nativeMemInfo.pss}, vss: ${nativeMemInfo.vss}, rss: ${nativeMemInfo.rss}, ` +
    `sharedDirty: ${nativeMemInfo.sharedDirty}, privateDirty: ${nativeMemInfo.privateDirty}, ` +
    `sharedClean: ${nativeMemInfo.sharedClean}, privateClean: ${nativeMemInfo.privateClean}`);
});

```

