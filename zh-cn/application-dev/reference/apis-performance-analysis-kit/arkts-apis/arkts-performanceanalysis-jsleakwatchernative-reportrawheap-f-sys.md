# reportRawHeap（系统接口）

## 导入模块

```TypeScript
```

## reportRawHeap

```TypeScript
function reportRawHeap(report: RawHeapReport): void
```

上报快照导出的结果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-jsLeakWatcherNative-function reportRawHeap(report: RawHeapReport): void--><!--Device-jsLeakWatcherNative-function reportRawHeap(report: RawHeapReport): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| report | [RawHeapReport](arkts-performanceanalysis-hiviewdfx-jsleakwatchernative-rawheapreport-i-sys.md) | 是 | 堆快照导出的信息。 |
