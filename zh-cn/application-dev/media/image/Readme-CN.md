# Image Kit（图片处理服务）
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

- Image Kit简介
- 图片开发指导(ArkTS)<!--image-arkts-dev-->
  - 图片解码<!--image-decoding-arts-->
    - 使用ImageSource完成图片解码
    - 使用ImageSource完成多图对象解码
    - 图片解码内存优化(ArkTS)
    - 图片区域解码与下采样(ArkTS)
    - 使用ImageSource获取RAW数据
  - 图片编码<!--image-encoding-arts-->
    - 使用ImagePacker完成图片编码
    - 使用ImagePacker完成多图对象编码
  - 图片编辑和处理<!--image-editing-arkts-->
    - 使用PixelMap完成图像变换
    - 使用PixelMap完成位图操作<!--RP1--><!--RP1End-->
  - 图片元数据处理<!--image-metadata-arkts-->
    - 读取和编辑图片Exif信息
    - 读取和编辑图片XMP元数据
    - 使用ImageSource获取专有元数据
  - 图片接收<!--image-receiving-arkts-->
    - 使用ImageReceiver完成图片接收
- 图片开发指导(C/C++)<!--image-native-->
  - 图片解码<!--image-decoding-c-->
    - 使用Image_NativeModule完成图片解码
    - 使用Image_NativeModule完成多图对象解码
    - 图片解码内存优化(C/C++)
    - 图片区域解码与下采样(C/C++)
    - 使用Image_NativeModule完成动图解码
    - 使用Image_NativeModule完成HDR图片解码
  - 图片编码<!--image-encoding-c-->
    - 使用Image_NativeModule完成图片编码
    - 使用Image_NativeModule完成多图对象编码
  - 图片编辑和处理<!--image-editing-c-->
    - 使用Image_NativeModule完成位图操作
    - 使用ImageEffect编辑图片<!--RP2--><!--RP2End-->
    - 使用Image_NativeModule读取和编辑图片Exif信息
  - 图片接收<!--image-receiving-c-->
    - 使用Image_NativeModule完成图片接收
- Image Kit常见问题<!--image-faqs-->
  - 如何处理HEIF图片
  - 如何获取图片的旋转角度信息
  - Image Kit异常处理
  - Image Kit常见崩溃报错问题
- 图片开发指导(依赖JS对象)(不再推荐)<!--image-native-js-objects-->
    - 图片解码
    - 图片编码
    - 图像变换
    - 位图操作
    - 图片接收
- Image Kit术语
