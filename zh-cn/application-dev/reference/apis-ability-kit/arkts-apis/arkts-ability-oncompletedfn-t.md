# OnCompletedFn

```TypeScript
type OnCompletedFn = (error: BusinessError<void>) => void
```

所有启动任务完成时的回调函数。

**起始版本：** 23

<!--Device-unnamed-type OnCompletedFn = (error: BusinessError<void>) => void--><!--Device-unnamed-type OnCompletedFn = (error: BusinessError<void>) => void-End-->

**系统能力：** SystemCapability.Ability.AppStartup

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| error | [BusinessError](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-businesserror-c.md)&lt;void&gt; | 是 | 错误信息。 |

