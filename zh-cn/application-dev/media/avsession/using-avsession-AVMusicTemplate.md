# 使用音频模板
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_gyH0B0hP-->
<!--Designer: @ccfriend-->
<!--Tester: @chen-gong1-->
<!--Adviser: @w_Machine_cc-->

从API version 23开始，支持媒体应用通过音频模板接入播控中心（系统应用），实现音视频在播控中心进行统一的界面显示和播控管理，减少应用侧开发工作量。该文档介绍音频模板接口能力及开发基本流程，包括通过音频模板接入播控中心、上报媒体相关信息（标题、作者、播放状态等）至播控中心、响应播控中心下发的操作（播放、暂停、搜索、收藏）指令等。

音频模板同时支持音频和视频内容，且两者的接入方式相同。本文档以音频场景为例进行说明。

> **说明：**
>
> 本功能仅支持在API version 23及以上版本的Car设备工程中使用。创建工程时，请在Device type中选择“Car”。

## 基本概念

音频模板（AVMusicTemplate）：用于描述音频模板相关能力的类，包含标识当前媒体会话的ID（sessionId）、会话标签（sessionTag）等属性，以及与播控中心进行数据交互的操作方法。媒体应用可通过音频模板向播控中心上报媒体相关信息，以及响应播控中心的操作指令。

## 接口说明

详细的API说明请参考[AVMusicTemplate](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplate.md)。

## 开发步骤

媒体应用接入音频模板的基本步骤如下所示：

1. 在进程启动时，调用接口[createAVMusicTemplate](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-f.md#avmusictemplatecreateavmusictemplate)创建音频模板实例（每个媒体应用创建一个音频模板实例，无需重复创建）并初始化音频模板。

   以下示例代码仅展示创建AVMusicTemplate对象的接口调用，应用在真正使用时，需要参考接口[@ohos.backgroundTaskManager (后台任务管理)](../../reference/apis-backgroundtasks-kit/js-apis-backgroundTaskManager.md)确保AVMusicTemplate对象实例在应用后台播放业务活动期间一直存在，避免被系统回收、释放，导致后台发声时被系统管控。

   <!-- @[ability_create_template](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/AVSession/TemplateProvider/entry/src/main/ets/entryability/EntryAbility.ets) -->
   
   <!-- @[manager_create_template](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/AVSession/TemplateProvider/entry/src/main/ets/manager/TemplateManager.ets) -->
   
2. 注册事件监听，在监听到事件后可提供应用数据给音频模板使用。监听接口详情请查看[AVMusicTemplate](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplate.md)。

   音频模板主界面显示需要同时注册如下两个接口：

   - [onQueryMainTabs](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplate.md#onquerymaintabs)：注册查询主标签事件监听。提供主界面展示的TAB数据集合，并规定“我的主页”的tabId为"minePage"。
   - [onQueryMediaTabContent](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplate.md#onquerymediatabcontent)：注册查询媒体标签内容事件监听。根据tabId提供页面展示内容数据。
   
   <!-- @[template_register_listener](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/AVSession/TemplateProvider/entry/src/main/ets/manager/TemplateManager.ets) -->

3. 在音频模板无法直接感知的场景（登录、下载等），需要媒体应用主动向音频模板同步数据。同步接口详情请查看[AVMusicTemplate](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplate.md)。

   例如，扫码登录成功的场景。当用户在音频模板界面扫码登录时，由于登录状态只有媒体应用能感知，所以需要调用接口[setUserInfo](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplate.md#setuserinfo)给音频模板同步数据。
   
   <!-- @[set_user_info](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/AVSession/TemplateProvider/entry/src/main/ets/manager/TemplateManager.ets) -->
   
4. 媒体应用启动时注册的事件监听需要在应用退出时注销，以释放资源。注销接口详情请查看[AVMusicTemplate](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplate.md)。

   <!-- @[unregister_listener](https://gitcode.com/openharmony/applications_app_samples/blob/OpenHarmony_feature_sta_20260331/code/DocsSample/Media/AVSession/TemplateProvider/entry/src/main/ets/manager/TemplateManager.ets) -->