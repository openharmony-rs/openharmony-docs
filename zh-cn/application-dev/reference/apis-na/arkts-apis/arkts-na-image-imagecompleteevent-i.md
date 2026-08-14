# ImageCompleteEvent

图片数据加载成功和解码成功时触发回调的返回对象。 当组件的参数类型为[AnimatedDrawableDescriptor] AnimatedDrawableDescriptor时该事件不触发。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface ImageCompleteEvent--><!--Device-unnamed-export interface ImageCompleteEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## componentHeight

```TypeScript
componentHeight: int
```

组件的高。 单位：像素

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageCompleteEvent-componentHeight: int--><!--Device-ImageCompleteEvent-componentHeight: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## componentWidth

```TypeScript
componentWidth: int
```

组件的宽。 单位：像素

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageCompleteEvent-componentWidth: int--><!--Device-ImageCompleteEvent-componentWidth: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentHeight

```TypeScript
contentHeight: int
```

图片实际绘制的高度。 单位：像素 **说明：** 仅在loadingStatus返回1时有效。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageCompleteEvent-contentHeight: int--><!--Device-ImageCompleteEvent-contentHeight: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentOffsetX

```TypeScript
contentOffsetX: int
```

实际绘制内容相对于组件自身的x轴偏移。 单位：像素 **说明：** 仅在loadingStatus返回1时有效。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageCompleteEvent-contentOffsetX: int--><!--Device-ImageCompleteEvent-contentOffsetX: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentOffsetY

```TypeScript
contentOffsetY: int
```

实际绘制内容相对于组件自身的y轴偏移。 单位：像素 **说明：** 仅在loadingStatus返回1时有效。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageCompleteEvent-contentOffsetY: int--><!--Device-ImageCompleteEvent-contentOffsetY: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentWidth

```TypeScript
contentWidth: int
```

图片实际绘制的宽度。 单位：像素 **说明：** 仅在loadingStatus返回1时有效。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageCompleteEvent-contentWidth: int--><!--Device-ImageCompleteEvent-contentWidth: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height: int
```

图片的高。 单位：像素

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageCompleteEvent-height: int--><!--Device-ImageCompleteEvent-height: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## loadingStatus

```TypeScript
loadingStatus: int
```

图片加载成功的状态值。 **说明：** 返回的状态值为0时，表示图片数据加载成功。返回的状态值为1时，表示图片解码成功。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageCompleteEvent-loadingStatus: int--><!--Device-ImageCompleteEvent-loadingStatus: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width: int
```

图片的宽。 单位：像素

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageCompleteEvent-width: int--><!--Device-ImageCompleteEvent-width: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

