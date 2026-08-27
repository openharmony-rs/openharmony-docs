# 应用权限组列表

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @xia-bubai-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->

## 使用须知

- 在申请目标权限前，建议开发者先阅读应用权限管控概述-权限组和子权限，了解相关概念，再合理申请对应的权限组。

- 应用请求权限时，同一权限组内的权限将在一个弹窗内请求用户授权。用户同意授权后，权限组内的权限将被统一授权。但位置信息、通讯录、<!--Del-->通话记录、电话、信息、<!--DelEnd-->日历权限组除外。

  以位置信息权限组和相机权限组为例说明。

  - 当应用只申请权限ohos.permission.APPROXIMATELY_LOCATION（属于位置信息权限组）时，用户将收到一个请求位置信息的弹窗，包含单个权限的申请。
  - 当应用同时申请权限ohos.permission.APPROXIMATELY_LOCATION和ohos.permission.LOCATION（均属于位置信息权限组）时，用户将收到一个请求位置信息的弹窗，包含两个权限的申请。
  - 当应用同时申请权限ohos.permission.APPROXIMATELY_LOCATION（属于位置信息权限组）和ohos.permission.CAMERA（属于相机权限组）时，用户将收到请求位置信息、请求使用相机的两个弹窗。

- 当前系统支持的权限组如下所示。各子权限的含义请查阅应用权限列表。

## 位置<!--Del-->信息<!--DelEnd-->

- ohos.permission.LOCATION_IN_BACKGROUND

- ohos.permission.LOCATION

- ohos.permission.APPROXIMATELY_LOCATION

## 相机

- ohos.permission.CAMERA

## 麦克风

- ohos.permission.MICROPHONE

## 通讯录

- ohos.permission.READ_CONTACTS

- ohos.permission.WRITE_CONTACTS

## 日历

- ohos.permission.READ_CALENDAR
 
- ohos.permission.WRITE_CALENDAR
 
- ohos.permission.READ_WHOLE_CALENDAR

- ohos.permission.WRITE_WHOLE_CALENDAR

<!--RP1-->
## 健身运动

- ohos.permission.ACTIVITY_MOTION

## 身体传感器

- ohos.permission.READ_HEALTH_DATA
<!--RP1End-->

## 图片和视频

- ohos.permission.WRITE_IMAGEVIDEO

- ohos.permission.READ_IMAGEVIDEO

- ohos.permission.MEDIA_LOCATION

<!--RP4--><!--RP4End-->

## 音乐和音频

- ohos.permission.WRITE_AUDIO

- ohos.permission.READ_AUDIO

<!--RP2-->
## 广告跟踪

- ohos.permission.APP_TRACKING_CONSENT
<!--RP2End-->

<!--Del-->
## 读取已安装应用列表

- ohos.permission.GET_INSTALLED_BUNDLE_LIST
<!--DelEnd-->

<!--RP3-->
## 多设备协同

- ohos.permission.DISTRIBUTED_DATASYNC

## 蓝牙

- ohos.permission.ACCESS_BLUETOOTH

## 星闪

- ohos.permission.ACCESS_NEARLINK
<!--RP3End-->

<!--Del-->
## 电话

- ohos.permission.ANSWER_CALL

- ohos.permission.MANAGE_VOICEMAIL

## 通话记录

- ohos.permission.READ_CALL_LOG

- ohos.permission.WRITE_CALL_LOG

## 信息

- ohos.permission.READ_CELL_MESSAGES

- ohos.permission.READ_MESSAGES

- ohos.permission.RECEIVE_MMS

- ohos.permission.RECEIVE_SMS

- ohos.permission.RECEIVE_WAP_MESSAGES

- ohos.permission.SEND_MESSAGES
<!--DelEnd-->

## 剪贴板

- ohos.permission.READ_PASTEBOARD

## 截屏

- ohos.permission.CUSTOM_SCREEN_CAPTURE

## 文件夹

> **说明：**
> 仅2in1设备可申请。

- ohos.permission.READ_WRITE_DOWNLOAD_DIRECTORY

- ohos.permission.READ_WRITE_DESKTOP_DIRECTORY
- ohos.permission.READ_WRITE_DOCUMENTS_DIRECTORY

## 文件<sup>(deprecated)</sup>

> **说明：**
> 从API 9开始，支持使用替代方案。

<!--Del-->
- ohos.permission.READ_DOCUMENT

- ohos.permission.WRITE_DOCUMENT
<!--DelEnd-->
- ohos.permission.READ_MEDIA

- ohos.permission.WRITE_MEDIA

**替代方案：**

- 读写媒体库中的图片或视频。

  - 推荐方案（无需申请权限）：使用Picker读取媒体库的图片与视频。使用保存控件/授权弹窗保存媒体库的图片与视频。
  - 受限使用方案：申请受限权限ohos.permission.READ_IMAGEVIDEO或ohos.permission.WRITE_IMAGEVIDEO以读取媒体库的图片与视频。

- 读写媒体库音频文件。

  申请受限权限ohos.permission.READ_AUDIO或ohos.permission.WRITE_AUDIO以读写媒体库的音频文件。

- 读取文件管理器中的文件。

  无需申请权限，通过文件Picker读写文件管理器中的文件。参考：选择用户文件、保存用户文件。

