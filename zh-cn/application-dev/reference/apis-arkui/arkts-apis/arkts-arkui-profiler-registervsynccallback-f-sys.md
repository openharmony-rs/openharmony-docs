# registerVsyncCallback（系统接口）

## registerVsyncCallback

```TypeScript
function registerVsyncCallback(callback: (info: string) => void): void
```

为profiler注册vsync回调。

**起始版本：** 8

<!--Device-Profiler-function registerVsyncCallback(callback: (info: string) => void): void--><!--Device-Profiler-function registerVsyncCallback(callback: (info: string) => void): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (info: string) =&gt; void | 是 | 回调信息为带有ui更新信息的json字符串。 |

