# 使用MediaAssetManager请求媒体资源(C/C++)
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @yixiaoff-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

使用MediaAssetManager可以实现请求媒体资源到目标沙箱路径，本开发指导将以请求一张图片作为示例，向开发者讲解MediaAssetManager相关功能。

请求图片资源的全流程包含：创建MediaAssetManager，设置请求资源，请求图片资源，取消本次请求(可选)。

## 开发步骤及注意事项

在CMake脚本中链接动态库

```c
target_link_libraries(sample PUBLIC libmedia_asset_manager.so)
```

开发者通过引入[media_asset_manager_capi.h](../../reference/apis-media-library-kit/capi-media-asset-manager-capi-h.md)和[media_asset_base_capi.h](../../reference/apis-media-library-kit/capi-media-asset-base-capi-h.md)头文件，使用MediaAssetManager相关API。
详细的API说明请参考[MediaAssetManager API](../../reference/apis-media-library-kit/capi-mediaassetmanager.md)。

> **说明：**
> 开发前，需要参考[开发准备](photoAccessHelper-preparation.md)，申请`ohos.permission.READ_IMAGEVIDEO`权限。

1. 创建实例：OH_MediaAssetManager_Create()。
2. 设置资源：设置资源请求回调、设置资源请求策略、设置源图片Uri和目标Uri。
3. 请求图片资源：调用OH_MediaAssetManager_RequestImageForPath()请求图片资源到目标Uri。
4. 取消请求：调用OH_MediaAssetManager_CancelRequest()。(可选)

## 完整示例

<!-- @[request_media_assets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MediaLibraryKit/RequestMediaAssetsCppSample/entry/src/main/cpp/napi_init.cpp) -->
