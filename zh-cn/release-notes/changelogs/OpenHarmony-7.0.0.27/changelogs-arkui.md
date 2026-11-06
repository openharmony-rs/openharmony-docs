# ArkUI子系统变更说明

## cl.arkui.1 Image组件autoResize属性默认行为变更

**访问级别**

公共能力

**变更原因**

图片解码后的宽×高像素乘积超过5000万时，按原图尺寸解码会占用大量内存，内存压力大甚至存在稳定性问题。为控制内存占用，该场景下[autoResize](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-image.md#autoresize)属性默认值变更为true，即图片解码过程中开启降采样解码。该判断仅与图片像素尺寸相关，与图片文件大小及图片格式无关。

**变更影响**

此变更涉及应用适配。

- 变更前：未设置[autoResize](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-image.md#autoresize)时，Image组件的autoResize属性默认为false，即图片解码过程中不自动缩放，按原图尺寸解码。

- 变更后：未设置autoResize时，如果图片解码后的宽×高像素乘积超过5000万，Image组件的autoResize默认设置为true，此时图片解码过程中会自动缩放，根据显示区域尺寸降采样解码。

**起始 API Level**

7

**变更发生版本**

从OpenHarmony SDK 7.0.0.27开始。

**变更的接口/组件**

Image的autoResize属性。

**适配指导**

默认行为变更。如果应用加载宽×高像素乘积大于5000万的图片且需要保留原图显示质量（例如需要对大图进行放大查看细节），可设置autoResize为false，按原图尺寸解码。

```ts
Image($r('app.media.large_image'))
  .autoResize(false)
```
