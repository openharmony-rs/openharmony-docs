# 应用接入歌词组件
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend @devil_red-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

从API version 23开始，系统提供歌词组件功能。歌词组件采用悬浮窗形式显示在系统桌面，组件支持歌词内容展示、隐藏、锁定等操作。本文将说明应用接入歌词组件的开发步骤。

## 具体步骤

1. 调用[isDesktopLyricSupported](../../reference/apis-avsession-kit/arkts-apis-avsession-f.md#avsessionisdesktoplyricsupported23)接口判断系统/设备是否支持歌词组件能力，返回true时表示支持歌词组件能力。

2. 创建[AVSession实例](../avsession/avsession-access-scene.md#创建不同类型的会话)，通过[设置元数据](../avsession/avsession-access-scene.md#设置元数据)填入LRC格式的歌词数据，包含时间标签及对应的歌词文本。不符合LRC格式的歌词数据，系统可能存在解析异常导致无法展示歌词内容。

3. 调用[enableDesktopLyric](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#enabledesktoplyric23)接口进行使能需传入参数true打开歌词组件。

4. 歌词组件使能打开后默认是隐藏（不显示），应用可以通过接口主动显示/隐藏歌词组件，具体接口如下：
   
   **设置可见性：** 调用[setDesktopLyricVisible](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setdesktoplyricvisible23)接口，设置歌词组件是否显示。

   **查询可见性：** 调用[isDesktopLyricVisible](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#isdesktoplyricvisible23)接口，查询当前歌词组件是否显示。

5. 歌词组件使能打开后默认是非锁定状态，应用可以通过接口主动锁定/解锁歌词组件，具体接口如下：

   **设置锁定状态：** 调用[setDesktopLyricState](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setdesktoplyricstate23)接口，设置歌词窗口是否锁定（限制歌词窗口的拖动、设置等操作）。
   
   **查询锁定状态：** 调用[getDesktopLyricState](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#getdesktoplyricstate23)接口，查询当前歌词组件锁定状态。

6. 应用可以通过系统提供的回调监听歌词组件可见性、锁定状态的变化，具体接口如下：

   **监听歌词组件是否可见：** 监听[onDesktopLyricVisibilityChanged](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#ondesktoplyricvisibilitychanged23)，回调返回false，表示当前歌词组件不可见；回调返回true，表示当前歌词组件可见。如需取消该监听，使用[offDesktopLyricVisibilityChanged](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#offdesktoplyricvisibilitychanged23)接口。

   **监听歌词组件是否锁定：** 监听[onDesktopLyricStateChanged](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#ondesktoplyricstatechanged23)，回调返回false，表示当前歌词组件未锁定；回调返回true，表示当前歌词组件锁定。如需取消该监听，使用[offDesktopLyricStateChanged](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#offdesktoplyricstatechanged23)接口。

   > **说明：**
   >
   > 确保AVSession对象在后台播放期间不被系统回收/应用不主动释放，否则会导致歌词组件异常。

<!-- @[setAVSessionInformation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/AVSession/LocalAVSession/AVSessionProvider/entry/src/main/ets/pages/DesktopLyric.ets) -->
