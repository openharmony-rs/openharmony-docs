# 双路预览图像数据处理问题
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 问题现象

双路预览中，通过[ImageReceiver](../../reference/apis-image-kit/arkts-apis-image-ImageReceiver.md)接收的预览流图像数据不可用，出现无法处理或画面花屏（图像错位、颜色异常）等问题。

## 可能原因

双路预览中，用于图像处理的第一路预览流通过[ImageReceiver](../../reference/apis-image-kit/arkts-apis-image-ImageReceiver.md)的Surface获取图像数据后，在处理该数据时需要设置正确的像素格式和行对齐才能正常解析。具体原因如下：

1. 注册ImageReceiver的[on](../../reference/apis-image-kit/arkts-apis-image-ImageReceiver.md#on9)监听，回调返回[Image](../../reference/apis-image-kit/arkts-apis-image-Image.md)图像数据后，调用[createPixelMap](../../reference/apis-image-kit/arkts-apis-image-f.md#imagecreatepixelmap8)处理图像数据时，未将Image中的format格式正确映射为对应的PixelMapFormat，导致像素格式不匹配，图像数据无法正确解析。

2. 应用未正确处理[Component](../../reference/apis-image-kit/arkts-apis-image-i.md#component9).byteBuffer中的行对齐数据，相机输出图像时每行像素可能包含用于内存对齐的额外字节，直接使用会导致图像画面错位或花屏。

## 解决措施

1. 注册ImageReceiver的[on](../../reference/apis-image-kit/arkts-apis-image-ImageReceiver.md#on9)监听，回调返回[Image](../../reference/apis-image-kit/arkts-apis-image-Image.md)图像数据后，将Image中的format映射为对应的[PixelMapFormat](../../reference/apis-image-kit/arkts-apis-image-e.md#pixelmapformat7)，再调用[createPixelMap](../../reference/apis-image-kit/arkts-apis-image-f.md#imagecreatepixelmap8)创建PixelMap。Image和PixelMap的映射关系可参考双路预览(ArkTS)中[用于处理图像的第一路预览流](camera-dual-channel-preview.md#用于处理图像的第一路预览流)的步骤3。

2. 处理行对齐数据，确保图像数据中不包含多余的行对齐字节。

   通过[Component](../../reference/apis-image-kit/arkts-apis-image-i.md#component9)的rowStride获取行对齐字节数，与图像宽度width比较，若stride不等于width，则需要去除多余的行对齐字节。可参考以下方式：

   - 方式一：逐行拷贝有效像素数据到新buffer，去除行对齐数据后调用[createPixelMap](../../reference/apis-image-kit/arkts-apis-image-f.md#imagecreatepixelmap8)。
   - 方式二：以stride × height创建PixelMap，调用[cropSync](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md#cropsync12)裁剪多余像素。
