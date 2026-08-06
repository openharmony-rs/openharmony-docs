# NativeMemInfo

����Ӧ�ý��̵��ڴ���Ϣ��

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-hidebug-interface NativeMemInfo--><!--Device-hidebug-interface NativeMemInfo-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## privateClean

```TypeScript
privateClean: bigint
```

˽�иɾ��ڴ��С����KBΪ��λ�����㷽ʽ��/proc/{pid}/smaps\_rollup: Private\_Clean��

**类型：** bigint

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-NativeMemInfo-privateClean: bigint--><!--Device-NativeMemInfo-privateClean: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## privateDirty

```TypeScript
privateDirty: bigint
```

˽�����ڴ��С����KBΪ��λ�����㷽ʽ��/proc/{pid}/smaps\_rollup: Private\_Dirty��

**类型：** bigint

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-NativeMemInfo-privateDirty: bigint--><!--Device-NativeMemInfo-privateDirty: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## pss

```TypeScript
pss: bigint
```

ʵ��ռ�õ������ڴ��С(�������乲����ռ�õ��ڴ�)����KBΪ��λ�����㷽ʽ��/proc/{pid}/smaps\_rollup: Pss + SwapPss��

**类型：** bigint

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-NativeMemInfo-pss: bigint--><!--Device-NativeMemInfo-pss: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## rss

```TypeScript
rss: bigint
```

ʵ��ռ�õ������ڴ��С(����������ռ��)����KBΪ��λ�����㷽ʽ��/proc/{pid}/smaps\_rollup: Rss��

**类型：** bigint

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-NativeMemInfo-rss: bigint--><!--Device-NativeMemInfo-rss: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## sharedClean

```TypeScript
sharedClean: bigint
```

�������ڴ��С����KBΪ��λ�����㷽ʽ��/proc/{pid}/smaps\_rollup: Shared\_Clean��

**类型：** bigint

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-NativeMemInfo-sharedClean: bigint--><!--Device-NativeMemInfo-sharedClean: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## sharedDirty

```TypeScript
sharedDirty: bigint
```

�������ڴ��С����KBΪ��λ�����㷽ʽ��/proc/{pid}/smaps\_rollup: Shared\_Dirty��

**类型：** bigint

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-NativeMemInfo-sharedDirty: bigint--><!--Device-NativeMemInfo-sharedDirty: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## vss

```TypeScript
vss: bigint
```

ռ�õ������ڴ��С(������������ռ�õ��ڴ�)����KBΪ��λ�����㷽ʽ��/proc/{pid}/statm: size * 4��

**类型：** bigint

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-NativeMemInfo-vss: bigint--><!--Device-NativeMemInfo-vss: bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

