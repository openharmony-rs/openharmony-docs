# @ohos.screenshot

本模块提供屏幕截图的能力。

**起始版本：** 12

<!--Device-unnamed-declare namespace screenshot--><!--Device-unnamed-declare namespace screenshot-End-->

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

## 导入模块

```TypeScript
import { screenshot } from '@kit.ArkUI';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [capture](arkts-arkui-screenshot-capture-f.md#capture) | 获取屏幕全屏截图，使用Promise异步回调。  此接口可以通过设置不同的displayId截取不同屏幕的截图，且只能截取全屏；[pick](arkts-arkui-screenshot-pick-f.md#pick-1)接口可实现区域截屏。 |
| [pick](arkts-arkui-screenshot-pick-f.md#pick) | 获取屏幕截图，当前仅支持获取displayId为0的屏幕截图（如果需要对扩展屏截图，可以通过[capture](arkts-arkui-screenshot-capture-f.md#capture-1)接口实现），使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [save](arkts-arkui-screenshot-save-f-sys.md#save) | 获取屏幕截图，使用callback异步回调。 |
| [save](arkts-arkui-screenshot-save-f-sys.md#save-1) | 获取屏幕截图，使用callback异步回调。 |
| [save](arkts-arkui-screenshot-save-f-sys.md#save-2) | 获取屏幕截图，使用Promise异步回调。 |
| [saveHdrPicture](arkts-arkui-screenshot-savehdrpicture-f-sys.md#savehdrpicture) | 获取屏幕截图，使用Promise异步回调。SDR为标准动态范围图，HDR为高动态范围图。  - 当物理屏存在HDR资源（包括HDR资源被遮挡）时，无论HDR是否开启，该接口返回一个包含SDR和HDR的PixelMap数组。  - 当物理屏不存在HDR资源时，与[save](arkts-arkui-screenshot-save-f-sys.md#save-1)接口返回一个SDR的PixelMap不同，该接口返回包含一个SDR的PixelMap数组。同时该接口不具备[save](arkts-arkui-screenshot-save-f-sys.md#save-1)接口的裁剪、拉伸、旋转功能。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [CaptureOption](arkts-arkui-screenshot-captureoption-i.md) | 设置截取图像的信息。 |
| [PickInfo](arkts-arkui-screenshot-pickinfo-i.md) | 截取图像的信息。 |
| [Rect](arkts-arkui-screenshot-rect-i.md) | 表示截取图像的区域。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [HdrScreenshotOptions](arkts-arkui-screenshot-hdrscreenshotoptions-i-sys.md) | 设置截取HDR图像的信息。 |
| [ScreenshotOptions](arkts-arkui-screenshot-screenshotoptions-i-sys.md) | 设置截取图像的信息。 |
| [Size](arkts-arkui-screenshot-size-i-sys.md) | 表示截取图像的大小。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DisplayIntentType](arkts-arkui-screenshot-displayintenttype-e-sys.md) | 枚举截图显示意图类型。 |
<!--DelEnd-->

