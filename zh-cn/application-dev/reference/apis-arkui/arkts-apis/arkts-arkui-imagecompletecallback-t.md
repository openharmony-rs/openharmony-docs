# ImageCompleteCallback

```TypeScript
export type ImageCompleteCallback = (result: ImageLoadResult) => void
```

图片加载成功和解码成功时触发的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type ImageCompleteCallback = (result: ImageLoadResult) => void--><!--Device-unnamed-export type ImageCompleteCallback = (result: ImageLoadResult) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | [ImageLoadResult](arkts-arkui-imagespan-imageloadresult-i.md) | 是 | 图片数据加载成功和解码成功触发回调时返回的对象。 |

