# ImageOnCompleteCallback

```TypeScript
export type ImageOnCompleteCallback = (loadEvent?: ImageCompleteEvent) => void
```

图片数据加载成功和解码成功时触发该回调。 当组件的参数类型为 AnimatedDrawableDescriptor时该事件不触发。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type ImageOnCompleteCallback = (loadEvent?: ImageCompleteEvent) => void--><!--Device-unnamed-export type ImageOnCompleteCallback = (loadEvent?: ImageCompleteEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| loadEvent | [ImageCompleteEvent](arkts-na-image-imagecompleteevent-i.md) | 否 |  |

