# getAppNativeMemInfo

## getAppNativeMemInfo

```TypeScript
function getAppNativeMemInfo(): NativeMemInfo
```

��ȡӦ�ý����ڴ���Ϣ����ȡ/proc/{pid}/smaps_rollup��/proc/{pid}/statm�ڵ�����ݡ�

> **ע��**
>
> ���ڶ�ȡ/proc/{pid}/smaps_rollup��ʱ�ϳ����Ƽ�ʹ���첽�ӿ�hidebug.getAppNativeMemInfoAsync���Ա���Ӧ�ö�֡�򿨶١�
>
> �Ƽ�ʹ��hidebug.getRssInfo�ӿڻ�ȡӦ�õ�rssʹ����Ϣ��

**起始版本：** 12

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| NativeMemInfo | Ӧ�ý����ڴ���Ϣ�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let nativeMemInfo: hidebug.NativeMemInfo = hidebug.getAppNativeMemInfo();
console.info(`pss: ${nativeMemInfo.pss}, vss: ${nativeMemInfo.vss}, rss: ${nativeMemInfo.rss}, ` +
  `sharedDirty: ${nativeMemInfo.sharedDirty}, privateDirty: ${nativeMemInfo.privateDirty}, ` +
  `sharedClean: ${nativeMemInfo.sharedClean}, privateClean: ${nativeMemInfo.privateClean}`);

```

