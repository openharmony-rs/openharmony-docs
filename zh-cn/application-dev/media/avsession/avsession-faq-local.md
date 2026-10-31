# 本地媒体会话常见问题
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_7KSyM10J; @devil_red-->
<!--Designer: @gcw_7KSyM10J-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

本文汇总音视频应用在本地媒体会话接入[AVSession Kit简介](avsession-overview.md)过程中遇到的典型问题及其定位与解决方法。开发者可结合[媒体会话管理错误码](../../reference/apis-avsession-kit/errorcode-avsession.md)和HiLog日志进一步定位问题。

## 创建AVSession失败

**问题现象**

调用[createAVSession](../../reference/apis-avsession-kit/arkts-apis-avsession-f.md#avsessioncreateavsession10)抛出异常，会话未创建成功。

**可能原因**

- 重复创建AVSession会话对象。一个进程只能存在一个AVSession会话对象。
- 存在频繁创建和销毁AVSession的场景时，旧会话尚未销毁完成。destroy调用是异步过程，如果应用在调用destroy后立即创建新的AVSession，可能因前一个会话尚未完成销毁，导致新会话创建失败。
- context入参无效。createAVSession的context需要使用应用的合法上下文。
- type参数取值非法。type必须为[AVSessionType](../../reference/apis-avsession-kit/arkts-apis-avsession-t.md#avsessiontype10)定义的值（`audio`/`video`/`voice_call`/`video_call`/`photo`），传入其他字符串会导致校验失败。
- 其他必填参数传入非法值。createAVSession的context、tag、type均为必填参数，任一缺失或非法都会抛出异常。

**解决措施**

1. 确认是否已经存在存活的AVSession，必要时先调用[destroy](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#destroy10)释放旧会话后再创建。在创建前还可以通过[getAVSession](../../reference/apis-avsession-kit/arkts-apis-avsession-f.md#avsessiongetavsession22)接口判断当前应用是否已经创建过会话对象，再决定是否销毁旧会话或直接复用已有会话。
2. 频繁创建和销毁场景下，通过媒体会话控制器监听[on('sessionDestroy')](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#onsessiondestroy10)事件，待收到旧会话销毁回调后再创建新的AVSession对象。

    ```TypeScript
    import { avSession } from '@kit.AVSessionKit';

    async destroyAndRecreateAVSession(context: Context) {
        let videoSession: avSession.AVSession;
        let avSessionController: avSession.AVSessionController;
        try {
            // 第一次创建AVSession，并获取其控制器。
            videoSession = await avSession.createAVSession(context, 'VIDEO_SESSION', 'video');
            avSessionController = await videoSession.getController();

            // 注册会话销毁监听，会话销毁后触发回调。
            avSessionController.on('sessionDestroy', async () => {
                // 第二次创建AVSession，销毁后重新创建同类型会话。
                videoSession = await avSession.createAVSession(context, 'VIDEO_SESSION', 'video');
                // 第二次销毁AVSession。
                await videoSession.destroy();
            });

            // 第一次销毁AVSession，触发上述sessionDestroy回调。
            await videoSession.destroy();
        } catch (err) {
            console.error(`AVSession create Error: Code: ${err.code}, message: ${err.message}`);
        }
    }
    ```

3. 推荐通过`this.getUIContext().getHostContext() as Context`获取context，避免传入undefined或非当前UIAbility的上下文。
4. 确保type为[AVSessionType](../../reference/apis-avsession-kit/arkts-apis-avsession-t.md#avsessiontype10)定义的合法取值。
5. 确保所有必填参数均为合法非空值，例如tag避免传入空字符串等无效值。

## 应用退至后台后音视频被强制暂停

**问题现象**

应用切到后台后，音视频播放被系统强制暂停，用户无法继续收听。

**可能原因**

- 未接入AVSession。系统会对未接入AVSession的音视频应用在后台进行强制管控。当流类型为`STREAM_USAGE_MUSIC`、`STREAM_USAGE_MOVIE`、`STREAM_USAGE_AUDIOBOOK`或`STREAM_USAGE_GAME`时，必须接入AVSession。
- 未申请长时任务。仅接入AVSession不足以保证后台播放，还需同时申请长时任务，否则应用进入后台后会被挂起或冻结。
- AVSession实例被回收。AVSession对象需在后台播放业务活动期间一直存在。如果将会话保存在局部变量中，方法返回后对象即被释放，系统判定应用没有有效AVSession实例，会强制暂停音频。
- AVSession创建失败导致应用未持有有效会话。
- 后台播放模式设置不正确。

**解决措施**

1. 参考后台播放中的[接入AVSession](avsession-background-scene.md#接入avsession)完成AVSession接入。
2. 申请AUDIO_PLAYBACK类型[长时任务(ArkTS)](../../task-management/continuous-task.md)。
3. 使用类成员变量保存session实例，并在应用进程结束或退出播放业务时再释放。
4. 参考[创建AVSession失败](#创建avsession失败)中的相关原因逐一排查，确保应用持有有效会话。
5. 应用退至后台前通过[setBackgroundPlayMode](../../reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setbackgroundplaymode24)设置后台播放模式（[BackgroundPlayMode](../../reference/apis-avsession-kit/arkts-apis-avsession-e.md#backgroundplaymode24)），告知系统应用退至后台时是否继续播放：

     - `ENABLE_BACKGROUND_PLAY`（支持后台播放）：应用退至后台时仍继续播放。
     - `DISABLE_BACKGROUND_PLAY`（不支持后台播放）：应用退至后台时不再继续播放。

     其中[AVSessionType](../../reference/apis-avsession-kit/arkts-apis-avsession-t.md#avsessiontype10)为`audio`类型的应用默认值为`ENABLE_BACKGROUND_PLAY`；`video`类型的应用默认值为`DISABLE_BACKGROUND_PLAY`。如果视频类应用希望支持后台放音，需显式设置为`ENABLE_BACKGROUND_PLAY`；如果应用内提供了"是否支持后台播放"的开关，设置的后台播放模式务必与开关状态保持一致，否则可能导致退后台后被强制暂停或系统实况窗展示错误。设置示例如下：

     ```TypeScript
     import { avSession } from '@kit.AVSessionKit';
     import { BusinessError } from '@kit.BasicServicesKit';

     // 假设已创建并持有currentAVSession。
     async setBackgroundPlayMode(currentAVSession: avSession.AVSession) {
       try {
         await currentAVSession.setBackgroundPlayMode(avSession.BackgroundPlayMode.ENABLE_BACKGROUND_PLAY);
         console.info(' Succeeded in setBackgroundPlayMode');
       } catch (err) {
         let error = err as BusinessError;
         console.error(`setBackgroundPlayMode BusinessError: code: ${error.code}, message: ${error.message}`);
       }
     }
     ```

     更多说明请参考[设置后台播放模式](avsession-background-scene.md#设置后台播放模式)。

<!--RP1--><!--RP1End-->