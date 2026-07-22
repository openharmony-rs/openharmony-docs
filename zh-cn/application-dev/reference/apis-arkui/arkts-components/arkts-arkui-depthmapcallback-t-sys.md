# DepthMapCallback（系统接口）

```TypeScript
declare type DepthMapCallback = (error: BusinessError<void>) => void
```

深度图资源加载完成时的回调函数。使用callback异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type DepthMapCallback = (error: BusinessError<void>) => void--><!--Device-unnamed-declare type DepthMapCallback = (error: BusinessError<void>) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| error | [BusinessError](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-businesserror-i.md)&lt;void&gt; | 是 | 深度图资源加载完成时返回的错误信息。加载成功时error.code为0，加载失败时error中包含错误码和错误信息。  |

