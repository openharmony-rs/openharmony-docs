# handleDumpTask（系统接口）

## 导入模块

```TypeScript
```

## handleDumpTask

```TypeScript
function handleDumpTask(cb: TaskCallback): void
```

设置导出任务的回调。在GC之后，如果确定有泄漏，则执行传入的回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-jsLeakWatcherNative-function handleDumpTask(cb: TaskCallback): void--><!--Device-jsLeakWatcherNative-function handleDumpTask(cb: TaskCallback): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cb | [TaskCallback](arkts-performanceanalysis-taskcallback-t-sys.md) | 是 | 导出事件的回调。 |
