# getAppNativeMemInfo

## getAppNativeMemInfo

```TypeScript
function getAppNativeMemInfo(): NativeMemInfo
```

��ȡӦ�ý����ڴ���Ϣ����ȡ/proc/{pid}/smaps\_rollup��/proc/{pid}/statm�ڵ�����ݡ� > **ע��** > > ���ڶ�ȡ/proc/{pid}/smaps\_rollup��ʱ�ϳ����Ƽ�ʹ���첽�ӿ�hidebug.getAppNativeMemInfoAsync���Ա���Ӧ�ö�֡�򿨶١� > > �Ƽ�ʹ��hidebug.getRssInfo�ӿڻ�ȡӦ�õ�rssʹ����Ϣ��

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-hidebug-function getAppNativeMemInfo(): NativeMemInfo--><!--Device-hidebug-function getAppNativeMemInfo(): NativeMemInfo-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Ӧ�ý����ڴ���Ϣ�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let nativeMemInfo: hidebug.NativeMemInfo = hidebug.getAppNativeMemInfo();
console.info(`pss: ${nativeMemInfo.pss}, vss: ${nativeMemInfo.vss}, rss: ${nativeMemInfo.rss}, ` +
  `sharedDirty: ${nativeMemInfo.sharedDirty}, privateDirty: ${nativeMemInfo.privateDirty}, ` +
  `sharedClean: ${nativeMemInfo.sharedClean}, privateClean: ${nativeMemInfo.privateClean}`);
```

