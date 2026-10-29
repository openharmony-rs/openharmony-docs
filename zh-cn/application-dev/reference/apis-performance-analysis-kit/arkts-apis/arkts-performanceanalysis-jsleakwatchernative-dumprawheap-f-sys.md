# dumpRawHeap（系统接口）

## 导入模块

```TypeScript
```

## dumpRawHeap

```TypeScript
function dumpRawHeap(filePath: string, cb: RawHeapDumpCallback): void
```

异步导出堆快照到给定的文件路径。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-jsLeakWatcherNative-function dumpRawHeap(filePath: string, cb: RawHeapDumpCallback): void--><!--Device-jsLeakWatcherNative-function dumpRawHeap(filePath: string, cb: RawHeapDumpCallback): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 原始堆快照的目标文件路径。 |
| cb | [RawHeapDumpCallback](arkts-performanceanalysis-rawheapdumpcallback-t-sys.md) | 是 | 接收导出结果的回调。 |
