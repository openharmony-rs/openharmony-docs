# ImageCompleteCallback

```TypeScript
type ImageCompleteCallback = (result: ImageLoadResult) => void
```

图片加载成功和解码成功时触发的回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type ImageCompleteCallback = (result: ImageLoadResult) => void--><!--Device-unnamed-type ImageCompleteCallback = (result: ImageLoadResult) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | ImageLoadResult | 是 | 图片数据加载成功和解码成功触发回调时返回的对象。 |

