# DepthMapCallback（系统接口）

```TypeScript
export declare type DepthMapCallback = (error: BusinessError<void>) => void
```

深度图资源加载完成时的回调函数。使用callback异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare type DepthMapCallback = (error: BusinessError<void>) => void--><!--Device-unnamed-export declare type DepthMapCallback = (error: BusinessError<void>) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| error | [BusinessError](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-businesserror-c.md)&lt;void&gt; | 是 | 深度图资源加载完成时返回的错误信息。加载成功时error.code为0，加载失败时error中包含错误码和错误信息。 |

