# 应用接入桌面歌词
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend@devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

从API version 23开始，支持应用接入桌面歌词功能，将歌词以悬浮窗形式展示在系统桌面，让用户无需进入应用即可查看歌词，适用于音乐播放器或有歌词展示需求的音频类应用。

桌面歌词采用悬浮窗形式显示，支持歌词内容的同步展示、窗口显示/隐藏控制及锁定操作。该功能可帮助应用快速实现桌面歌词显示能力，提升用户听歌体验。

实现桌面歌词功能，需遵循以下流程：

  1. 创建会话。
  2. 判断当前系统版本是否支持桌面歌词功能，若支持则设置歌词元数据。
  3. 通过接口控制歌词的使能与显示状态。
  4. 监听系统侧的状态变化以同步UI。
  5. 在退出时正确销毁会话。
  
## 具体步骤

1. 首先创建[AVSession实例](../avsession/avsession-access-scene.md#创建不同类型的会话)，通过[设置元数据](../avsession/avsession-access-scene.md#设置元数据)填入符合LRC格式的歌词内容。系统播控中心将解析该内容，实现歌词内容的同步展示。歌词内容必须包含时间标签及对应歌词文本。

   > **说明：**
   >
   > - 设置元数据时，必须包含lyric字段，否则桌面歌词功能无法生效。

2. 应用根据自身业务需求，调用接口控制桌面歌词的使能与显示状态，同时提供用户入口供用户手动操作。可调用以下接口：

   - **判断是否支持桌面歌词：** 调用[isDesktopLyricSupported](../../reference/apis-avsession-kit/arkts-apis-avsession-f.md#avsessionisdesktoplyricsupported23)接口，判断应用是否支持桌面歌词功能。
   - **使能桌面歌词：** 调用[enableDesktopLyric](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#enabledesktoplyric23)接口，启用桌面歌词。
   - **设置可见性：** 调用[setDesktopLyricVisible](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setdesktoplyricvisible23)接口，切换歌词窗口的可见性状态。
   - **设置锁定状态：** 调用[setDesktopLyricState](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setdesktoplyricstate23)接口，设置歌词窗口的锁定状态，从而限制歌词窗口的拖动或关闭操作。

3. 应用监听系统侧发出的桌面歌词状态变更通知，响应桌面歌词组件的控制并同步刷新应用内UI。

    应用需监听系统侧发出的桌面歌词状态变更通知（如用户在系统设置中关闭了歌词），以便同步刷新应用内的开关状态。

   > **说明：**
   > 
   > - 必须响应[onDesktopLyricEnabled](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#ondesktoplyricenabled23)和[offDesktopLyricEnabled](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#offdesktoplyricenabled23)回调，根据回调值更新UI，确保应用内UI与系统实际状态一致。

4. 当应用退出时，必须销毁当前会话。

    当应用退出或不再需要播放媒体时，必须主动销毁AVSession。销毁操作将导致关联的桌面歌词组件自动跟随退出。再次启动时，需重新初始化AVSession以恢复会话。

   > **说明：**
   >
   > - 确保AVSession对象在后台播放期间不被系统回收，否则会导致歌词中断。

   <!-- @[setAVSessionInformation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/DesktopLyric.ets) -->
