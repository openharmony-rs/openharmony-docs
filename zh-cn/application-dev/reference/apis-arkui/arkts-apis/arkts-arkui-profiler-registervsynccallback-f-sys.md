# registerVsyncCallback（系统接口）

## registerVsyncCallback

```TypeScript
function registerVsyncCallback(callback: (info: string) => void): void
```

为profiler注册vsync回调。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**测试接口：** 此接口仅在自动化测试脚本中使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (info: string) =&gt; void | 是 | 回调信息为带有ui更新信息的json字符串。 |
