# Image Kit（图片处理服务）
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @zengyawen-->

- [Image Kit简介](image-overview.md)
- 图片开发指导(ArkTS)<!--image-arkts-dev-->
  - 图片解码<!--image-decoding-arts-->
    - [使用ImageSource完成图片解码](image-decoding.md)
    - [使用ImageSource完成多图对象解码](image-picture-decoding.md)
    - [申请图片解码内存](image-allocator-type.md)
  - 图片编码<!--image-encoding-arts-->
    - [使用ImagePacker完成图片编码](image-encoding.md)
    - [使用ImagePacker完成多图对象编码](image-picture-encoding.md)
  - 图片编辑和处理<!--image-editing-arkts-->
    - [使用PixelMap完成图像变换](image-transformation.md)
    - [使用PixelMap完成位图操作](image-pixelmap-operation.md)
    - [编辑图片EXIF信息](image-tool.md)
  - 图片接收<!--image-receiving-arkts-->
    - [使用ImageReceiver完成图片接收](image-receiver.md)
- 图片开发指导(C/C++)<!--image-native-->
  - 图片解码<!--image-decoding-c-->
    - [使用Image_NativeModule完成图片解码](image-source-c.md)
    - [使用Image_NativeModule完成多图对象解码](image-source-picture-c.md)
    - [申请图片解码内存](image-allocator-type-c.md)
  - 图片编码<!--image-encoding-c-->
    - [使用Image_NativeModule完成图片编码](image-packer-c.md)
    - [使用Image_NativeModule完成多图对象编码](image-packer-picture-c.md)
  - 图片编辑和处理<!--image-editing-c-->
    - [使用Image_NativeModule完成位图操作](pixelmap-c.md)
    - [使用ImageEffect编辑图片](image-effect-guidelines.md)
    - [编辑图片EXIF信息](image-tool-c.md)
  - 图片接收<!--image-receiving-c-->
    - [使用Image_NativeModule完成图片接收](image-receiver-c.md)
    - [使用Image_NativeModule处理图像信息](image-info-c.md)
- Image Kit常见问题<!--image-faqs-->
  - [如何处理HEIF图片](image-faqs/heif-adapter-faq.md)
  - [如何获取图片的旋转角度信息](image-faqs/image-rotate-faq.md)
- 图片开发指导(依赖JS对象)(不再推荐)<!--image-native-js-objects-->
    - [图片解码](image-decoding-native.md)
    - [图片编码](image-encoding-native.md)
    - [图像变换](image-transformation-native.md)
    - [位图操作](image-pixelmap-operation-native.md)
    - [图片接收](image-receiver-native.md)
