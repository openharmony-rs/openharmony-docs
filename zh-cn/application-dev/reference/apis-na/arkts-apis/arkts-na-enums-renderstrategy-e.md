# RenderStrategy

定义组件绘制圆角的模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare enum RenderStrategy--><!--Device-unnamed-export declare enum RenderStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FAST

```TypeScript
FAST = 0
```

在线绘制模式，组件进行圆角内容绘制时，绘制内容被裁剪成圆角，直接绘制到主画布上。 **说明：**使用在线绘制模式，在部分场景下可能会有显示效果异常，例如：圆角组件内叠加模糊效果后背景色会有相互影响，导致出现渐变叠加的效果，具体表现可参考 [示例3（设置离屏圆角）](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#示例3设置离屏圆角)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderStrategy-FAST = 0--><!--Device-RenderStrategy-FAST = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## OFFSCREEN

```TypeScript
OFFSCREEN = 1
```

离屏绘制模式，组件进行圆角内容绘制时，绘制内容先不带圆角绘制到离屏画布上，随后对离屏画布上的内容进行一次圆角裁切并绘制到主画布上。 **说明：** 1. 离屏绘制模式相比在线绘制模式会带来额外的性能损失。 2. 离屏绘制模式是指将内容绘制到主画布之前，先在一个额外的画布上完成绘制工作，然后将绘制结果绘制到主画布上。 3. 离屏绘制模式仅针对需要多层组件切圆角的场景使用，单组件需设置clip属性、背景或前景色时才可使能离屏绘制模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderStrategy-OFFSCREEN = 1--><!--Device-RenderStrategy-OFFSCREEN = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

