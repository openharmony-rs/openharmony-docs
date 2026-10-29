# handleGCTask（系统接口）

## 导入模块

```TypeScript
```

## handleGCTask

```TypeScript
function handleGCTask(cb: TaskCallback): void
```

触发并启动周期性GC任务。当期限到期时，自动触发传入的调用。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-jsLeakWatcherNative-function handleGCTask(cb: TaskCallback): void--><!--Device-jsLeakWatcherNative-function handleGCTask(cb: TaskCallback): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cb | [TaskCallback](arkts-performanceanalysis-taskcallback-t-sys.md) | 是 | GC事件的回调。 |
