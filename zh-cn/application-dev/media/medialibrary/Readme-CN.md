# Media Library Kit（媒体文件管理服务）

<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xuchangda; @yixiaoff-->
<!--Designer: @guxinggang; @liweilu1-->
<!--Tester: @wangbeibei; @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

- [Media Library Kit 简介](photoAccessHelper-overview.md)
- [使用Picker选择媒体库资源](photoAccessHelper-photoviewpicker.md)
- [保存媒体库资源](photoAccessHelper-savebutton.md)<!--RP1--><!--RP1End-->
- 动态照片<!--movingphoto-->
  - [访问和管理动态照片资源](photoAccessHelper-movingphoto.md)
  - [使用MovingPhotoView播放动态照片](movingphotoview-guidelines.md)<!--RP2--><!--RP2End-->
- 受限开放能力<!--restricted-open-capabilities-->
  - [开发准备](photoAccessHelper-preparation.md)
  - [媒体资源使用指导](photoAccessHelper-resource-guidelines.md)
  - [用户相册资源使用指导](photoAccessHelper-userAlbum-guidelines.md)
  - [系统相册资源使用指导](photoAccessHelper-systemAlbum-guidelines.md)
  - [媒体资源变更通知相关指导](photoAccessHelper-notify-guidelines.md)
  - [使用MediaAssetManager请求媒体资源(C/C++)](using-ndk-mediaassetmanager-for-request-resource.md)<!--RP3--><!--RP3End-->
- Media Library Kit常见问题<!--media-library-kit-frequently-asked-questions-->
  - [如何正确管理媒体库资产](medialibrary-faqs/medialibrary-asset-management-faq.md)
  - [如何正确判断媒体资源类型](medialibrary-faqs/medialibrary-asset-judgment-faq.md)
  - [查看的媒体图片未包含地理位置信息](medialibrary-faqs/medialibrary-asset-hidesensitive-faq.md)
  - 查询类失败故障模式说明<!--query-class-failure-mode-description-->
    - [参数的基本合法性错误故障模式说明](medialibrary-faqs/medialibrary-failure-mode-description/query-class-failure-mode-description/parameter-basic-legality-failure-mode-description.md)
    - [媒体库模块参数错误故障模式说明](medialibrary-faqs/medialibrary-failure-mode-description/query-class-failure-mode-description/medialibrary-module-param-error-fault-mode-desc.md)
    - [内部失败故障模式说明](medialibrary-faqs/medialibrary-failure-mode-description/query-class-failure-mode-description/internal-failure-failure-mode-description.md)
    - [权限授权错误故障模式说明](medialibrary-faqs/medialibrary-failure-mode-description/query-class-failure-mode-description/permission-authorization-error-fault-mode-description.md)
  - 写入类失败故障模式说明<!--write-class-failure-mode-description-->
    - 创建失败故障模式说明<!--creation-failed-description-of-failure-mode-->
      - [权限授权失败故障模式说明](medialibrary-faqs/medialibrary-failure-mode-description/write-class-failure-mode-description/creation-failed-description-of-failure-mode/permission-auth-error-fault-mode-desc.md)
      - [存储IO失败故障模式说明](medialibrary-faqs/medialibrary-failure-mode-description/write-class-failure-mode-description/creation-failed-description-of-failure-mode/storage-io-failure-fault-mode-description.md)
      - [参数的基本合法性错误故障模式说明](medialibrary-faqs/medialibrary-failure-mode-description/write-class-failure-mode-description/creation-failed-description-of-failure-mode/parameter-basic-legality-failure-mode-desc.md)
      - [显示名称无效创建失败故障模式说明](medialibrary-faqs/medialibrary-failure-mode-description/write-class-failure-mode-description/creation-failed-description-of-failure-mode/invalid-display-name-fault-mode-description.md)
      - [对象成员属性不存在错误故障模式说明](medialibrary-faqs/medialibrary-failure-mode-description/write-class-failure-mode-description/creation-failed-description-of-failure-mode/obj-member-prop-not-exist-fault-description.md)
      - [不支持的操作故障模式说明](medialibrary-faqs/medialibrary-failure-mode-description/write-class-failure-mode-description/creation-failed-description-of-failure-mode/unsupported-operation-fault-mode-desc.md)
    - 删除失败故障模式说明<!--deletion-failed-fault-mode-description-->
      - [用户文件管理器模块参数错误故障模式说明](medialibrary-faqs/medialibrary-failure-mode-description/write-class-failure-mode-description/deletion-failed-fault-mode-description/user-file-manager-param-error-fault-mode-desc.md)
      - [权限不足故障模式说明](medialibrary-faqs/medialibrary-failure-mode-description/write-class-failure-mode-description/deletion-failed-fault-mode-description/insufficient-permissions-fault-mode-description.md)
    - 修改元数据失败故障模式说明<!--metadata-modify-failure-mode-description-->
      - [操作的文件不存在故障模式说明](medialibrary-faqs/medialibrary-failure-mode-description/write-class-failure-mode-description/metadata-modify-failure-mode-description/file-not-exist-operate-failure-mode-description.md)
- [Media Library Kit术语](mediaLibrary-glossary.md)

