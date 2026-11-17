# ProfilerCallback

```TypeScript
type ProfilerCallback = (result: ProfilerResult) => void
```

Profiler回调函数类型。

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-hidebug-type ProfilerCallback = (result: ProfilerResult) => void--><!--Device-hidebug-type ProfilerCallback = (result: ProfilerResult) => void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | [ProfilerResult](arkts-performanceanalysis-hidebug-profilerresult-i.md) | 是 | Profiler 结果. |
