# RssInfo

����Ӧ�ý��̵������ڴ���Ϣ��

**起始版本：** 24

<!--Device-hidebug-interface RssInfo--><!--Device-hidebug-interface RssInfo-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## rss

```TypeScript
rss: bigint
```

ʵ��ռ�õ������ڴ��С��Resident Set Size������������ҳ���ļ�ӳ��ҳ�͹����ڴ�ҳ����KBΪ��λ�����㷽ʽ��/proc/{pid}/status: VmRss��

**类型：** bigint

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-RssInfo-rss: bigint--><!--Device-RssInfo-rss: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## swapRss

```TypeScript
swapRss: bigint
```

��������������������˽��ҳ�ܴ�С����KBΪ��λ�����㷽ʽ��/proc/{pid}/status: VmSwap��

**类型：** bigint

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-RssInfo-swapRss: bigint--><!--Device-RssInfo-swapRss: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

