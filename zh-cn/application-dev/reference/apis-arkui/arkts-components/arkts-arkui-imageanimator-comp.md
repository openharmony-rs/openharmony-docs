# ImageAnimator

提供帧动画组件来实现逐帧播放图片的能力，可以配置需要播放的图片列表，每张图片可以配置时长。

> **说明：** > > - 该组件从API版本26.0.0开始支持WithTheme。

## 子组件

无

## ImageAnimator

```TypeScript
ImageAnimator()
```

返回ImageAnimator。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ImageFrameInfo](arkts-arkui-imageframeinfo-i.md) | 图片帧信息集合。 |

## 示例

```TypeScript
### 示例1（播放Resource动画）

通过ImageAnimator组件播放Resource动画。


```

```TypeScript
### 示例2（播放PixelMap动画）

通过ImageAnimator组件播放PixelMap动画。


```

```TypeScript
### 示例3（设置不可见自动停播）

通过[monitorInvisibleArea](arkts-arkui-imageanimator-comp-attribute.md#monitorinvisiblearea)属性实现了当ImageAnimator的[state](#state)属性为AnimationStatus.Running时，控制组件在不可见时停止播放，在可见时恢复播放。
```
