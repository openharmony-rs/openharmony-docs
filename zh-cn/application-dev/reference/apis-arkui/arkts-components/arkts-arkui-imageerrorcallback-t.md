# ImageErrorCallback

```TypeScript
type ImageErrorCallback = (error: ImageError) => void
```

图片加载异常时触发此回调。 当组件的参数类型为[AnimatedDrawableDescriptor]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_时该事件不触发。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-type ImageErrorCallback = (error: ImageError) => void--><!--Device-unnamed-type ImageErrorCallback = (error: ImageError) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| error | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 图片加载异常时触发回调的返回对象。 |

