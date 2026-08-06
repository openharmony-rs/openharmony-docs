# RssInfo

����Ӧ�ý��̵������ڴ���Ϣ��

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

<!--Device-hidebug-interface RssInfo--><!--Device-hidebug-interface RssInfo-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## rss

```TypeScript
rss: bigint
```

ʵ��ռ�õ������ڴ��С��Resident Set Size������������ҳ���ļ�ӳ��ҳ�͹����ڴ�ҳ����KBΪ��λ�����㷽ʽ��/proc/{pid}/status: VmRss��

**类型：** bigint

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

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

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-RssInfo-swapRss: bigint--><!--Device-RssInfo-swapRss: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

