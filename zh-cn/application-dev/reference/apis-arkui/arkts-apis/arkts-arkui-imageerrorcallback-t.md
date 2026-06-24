# ImageErrorCallback

```TypeScript
type ImageErrorCallback = (error: ImageError) => void
```

图片加载异常时触发此回调。

当组件的参数类型为[AnimatedDrawableDescriptor](arkts-arkui-animateddrawabledescriptor-c.md#AnimatedDrawableDescriptor)时该
事件不触发。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| error | ImageError | 是 | 图片加载异常时触发回调的返回对象。 [since 11] |

