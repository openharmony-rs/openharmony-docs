# 音频模板开发指南(仅对系统应用开放)
OpenHarmony系统预置的媒体中心，作为音频模板控制方与音视频应用进行交互，包括获取媒体信息进行展示以及下发播控命令等。系统应用开发者也可以根据需要，按照本章节的内容自行开发一款新的系统应用，作为音频模板控制方的角色，与系统中的音视频应用进行交互。音频模板控制方支持音频和视频，接入方式相同，以下仅以音频为例。

## 基本概念

- 音频模板控制器（AVMusicTemplateController）：包含标识媒体会话的ID（sessionId），是否已销毁（isDestroy）等。可通过其查询和接受媒体应用相关信息，并下发播控指令。


## 接口说明

详细的API说明请参考[AVMusicTemplateController API](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplateController.md)。

## 开发步骤

系统应用作为音频模板控制方接入音频模板的基本步骤如下所示：

1. 创建音频模板控制器（每一个音频应用对应一个模板控制器，且不需要重复创建），监听音频模板状态。当音频模板创建时，根据创建sessionId创建控制器。当音频模板销毁时，销毁控制器。需要如下接口，详情请查看[模板API接口](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplate-f.md)。

   - getAllAVMusicTemplateDescriptors：获取所有的音频模板描述。
   - onAVMusicTemplateCreate：音频模板创建事件。
   - onAVMusicTemplateDestroy：音频模板销毁事件。
   
   <!-- @[create_controller](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateController/entry/src/main/ets/manager/ControllerManager.ets) -->
   
2. 音频模板控制方根据需要查询音频模板提供方相关的信息，用于界面展示（需要音频模板提供方注册相关接口）。例如主界面展示需要先获取主标签TAB，然后根据tabId查询标签页内容，需要接口如下，详情请查看[AVMusicTemplateController API](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplateController.md)。

   - queryMainTabs：查询主标签。
   - queryMediaTabContent：查询媒体标签内容。
   
   <!-- @[query_home_content](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateController/entry/src/main/ets/manager/ControllerManager.ets) -->
   
3. 音频模板控制方根据操作下发指令给媒体提供方（需要媒体提供方已经注册相关监听）。例如搜播需要接口如下，详情请查看[AVMusicTemplateController API](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplateController.md)。

   - playForSearch：搜播。支持音视频，示例仅以音频为例。视频需将实体类SearchPlayInfo的成员变量更换为SearchPlayVideoInfo类型的videoInfo。

   <!-- @[play_for_search](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateController/entry/src/main/ets/manager/ControllerManager.ets) -->
   
4. 在不能实时获得数据的场景下，音频模板控制方需要注册监听，接受音频模板提供方主动同步过来的数据。例如登录导致用户信息变化的场景，需要如下接口，详情请查看[AVMusicTemplateController API](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplateController.md)。

   - onUserInfoChange：用户信息变化事件。用户在音频模板控制方界面扫码登录，而登录状态只有音频模板控制方才能感知，此时需要注册改监听接受数据。
   
   <!-- @[register_user_info_change](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateController/entry/src/main/ets/manager/ControllerManager.ets) -->
   
5. 在音频模板控制方应用退出时及时取消事件监听，并释放资源。详情请查看[模板API接口](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplate-f.md)和[AVMusicTemplateController API](../../reference/apis-avsession-kit/arkts-apis-avsession-AVMusicTemplateController.md)。

   <!-- @[release](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/TemplateController/entry/src/main/ets/manager/ControllerManager.ets) -->
