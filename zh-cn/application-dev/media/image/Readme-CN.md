# Image Kit（图片处理服务）
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

- [Image Kit简介](image-overview.md)
- 图片开发指导(ArkTS)<!--image-arkts-dev-->
  - 图片解码<!--image-decoding-arts-->
    - [使用ImageSource完成图片解码](image-decoding.md)
    - [使用ImageSource完成多图对象解码](image-picture-decoding.md)
    - [图片解码内存优化(ArkTS)](image-allocator-type.md)
    - [图片区域解码与下采样(ArkTS)](image-region-and-downsampling.md)
    - [使用ImageSource获取RAW数据](image-raw-data.md)
  - 图片编码<!--image-encoding-arts-->
    - [使用ImagePacker完成图片编码](image-encoding.md)
    - [使用ImagePacker完成多图对象编码](image-picture-encoding.md)
  - 图片编辑和处理<!--image-editing-arkts-->
    - [使用PixelMap完成图像变换](image-transformation.md)
    - [使用PixelMap完成位图操作](image-pixelmap-operation.md)<!--RP1--><!--RP1End-->
    - [读取和编辑图片Exif信息](image-tool.md)
  - 图片接收<!--image-receiving-arkts-->
    - [使用ImageReceiver完成图片接收](image-receiver.md)
- 图片开发指导(C/C++)<!--image-native-->
  - 图片解码<!--image-decoding-c-->
    - [使用Image_NativeModule完成图片解码](image-source-c.md)
    - [使用Image_NativeModule完成多图对象解码](image-source-picture-c.md)
    - [图片解码内存优化(C/C++)](image-allocator-type-c.md)
    - [图片区域解码与下采样(C/C++)](image-region-and-downsampling-c.md)
    - [使用Image_NativeModule完成动图解码](image-animated-decoding-c.md)
    - [使用Image_NativeModule完成HDR图片解码](image-hdr-decoding-c.md)
  - 图片编码<!--image-encoding-c-->
    - [使用Image_NativeModule完成图片编码](image-packer-c.md)
    - [使用Image_NativeModule完成多图对象编码](image-packer-picture-c.md)
  - 图片编辑和处理<!--image-editing-c-->
    - [使用Image_NativeModule完成位图操作](pixelmap-c.md)
    - [使用ImageEffect编辑图片](image-effect-guidelines.md)<!--RP2--><!--RP2End-->
    - [使用Image_NativeModule读取和编辑图片Exif信息](image-tool-c.md)
  - 图片接收<!--image-receiving-c-->
    - [使用Image_NativeModule完成图片接收](image-receiver-c.md)
- Image Kit常见问题<!--image-faqs-->
  - [如何处理HEIF图片](image-faqs/heif-adapter-faq.md)
  - [如何获取图片的旋转角度信息](image-faqs/image-rotate-faq.md)
  - [Image Kit异常处理](image-faqs/image-error-faq.md)
  - [Image Kit常见崩溃报错问题](image-faqs/image-common-mistakes.md)
- 图片开发指导(依赖JS对象)(不再推荐)<!--image-native-js-objects-->
    - [图片解码](image-decoding-native.md)
    - [图片编码](image-encoding-native.md)
    - [图像变换](image-transformation-native.md)
    - [位图操作](image-pixelmap-operation-native.md)
    - [图片接收](image-receiver-native.md)
