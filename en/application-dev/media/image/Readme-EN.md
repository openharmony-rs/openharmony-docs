# Image Kit
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

- [Introduction to Image Kit](image-overview.md)
- Image Development (ArkTS)<!--image-arkts-dev-->
  - Image Decoding<!--image-decoding-arts-->
    - [Using ImageSource to Decode Images](image-decoding.md)
    - [Using ImageSource to Decode Pictures](image-picture-decoding.md)
    - [Allocating Memory for Image Decoding](image-allocator-type.md)
  - Image Encoding<!--image-encoding-arts-->
    - [Using ImagePacker to Encode Images](image-encoding.md)
    - [Using ImagePacker to Encode Pictures](image-picture-encoding.md)
  - Image Editing and Processing<!--image-editing-arkts-->
    - [Using PixelMap to Transform Images](image-transformation.md)
    - [Using PixelMap for PixelMap Operations](image-pixelmap-operation.md)
    - [Editing EXIF Data](image-tool.md)
  - Image Receiving<!--image-receiving-arkts-->
    - [Using ImageReceiver to Receive Images](image-receiver.md)
- Image Development (C/C++)<!--image-native-->
  - Image Decoding<!--image-decoding-c-->
    - [Using Image_NativeModule to Decode Images](image-source-c.md)
    - [Using Image_NativeModule to Decode Pictures](image-source-picture-c.md)
    - [Allocating Memory for Image Decoding](image-allocator-type-c.md)
  - Image Encoding<!--image-encoding-c-->
    - [Using Image_NativeModule to Encode Images](image-packer-c.md)
    - [Using Image_NativeModule to Encode Pictures](image-packer-picture-c.md)
  - Image Editing and Processing<!--image-editing-c-->
    - [Using Image_NativeModule for PixelMap Operations](pixelmap-c.md)
    - [Using ImageEffect to Edit Images](image-effect-guidelines.md)
    - [Using Image_NativeModule to Edit EXIF Data](image-tool-c.md)
  - Image Receiving<!--image-receiving-c-->
    - [Using Image_NativeModule to Receive Images](image-receiver-c.md)
    - [Using Image_NativeModule to Process Image Information](image-info-c.md)
- FAQs About Image Kit<!--image-faqs-->
  - [Handling HEIF Images](image-faqs/heif-adapter-faq.md)
  - [Obtaining the Rotation Angle of an Image](image-faqs/image-rotate-faq.md)
  - [Image Kit Exception Handling](image-faqs/image-error-faq.md)
- Image Development (Dependent on JS Objects) (Not Recommended)<!--image-native-js-objects-->
    - [Image Decoding](image-decoding-native.md)
    - [Image Encoding](image-encoding-native.md)
    - [Image Transformation](image-transformation-native.md)
    - [PixelMap Operation](image-pixelmap-operation-native.md)
    - [Image Receiving](image-receiver-native.md)
