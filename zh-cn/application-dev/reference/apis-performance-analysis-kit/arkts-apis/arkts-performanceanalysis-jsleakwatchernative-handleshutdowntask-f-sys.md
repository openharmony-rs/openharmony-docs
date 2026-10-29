# handleShutdownTask（系统接口）

## 导入模块

```TypeScript
```

## handleShutdownTask

```TypeScript
function handleShutdownTask(cb: TaskCallback): void
```

注册停止jsleakwatcher任务回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-jsLeakWatcherNative-function handleShutdownTask(cb: TaskCallback): void--><!--Device-jsLeakWatcherNative-function handleShutdownTask(cb: TaskCallback): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiChecker

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cb | [TaskCallback](arkts-performanceanalysis-taskcallback-t-sys.md) | 是 | jsLeakWatcher停止时执行的回调。 |
