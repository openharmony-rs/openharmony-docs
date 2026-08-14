# registerVsyncCallback（系统接口）

## registerVsyncCallback

```TypeScript
function registerVsyncCallback(callback: Callback<string>): void
```

为profiler注册vsync回调。 AnonyMous Object Rectification.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Profiler-function registerVsyncCallback(callback: Callback<string>): void--><!--Device-Profiler-function registerVsyncCallback(callback: Callback<string>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;string&gt; | 是 | 回调信息为带有ui更新信息的json字符串。 |

