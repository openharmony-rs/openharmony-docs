# FaultLogExtensionAbility

```TypeScript
declare class FaultLogExtensionAbility
```

本模块实现故障的延迟通知功能。

[HiAppEvent](arkts-performanceanalysis-hiappevent-n.md)订阅崩溃、应用冻屏事件时，只有当应用下次启动后才能接收上一次的事件。如果应用无法启动或长时间未打开，则存在故障无法及时上报的局限性。

本模块作为该场景的补充。在应用实现FaultLogExtensionAbility后，当应用发生崩溃或冻屏时，系统服务预计会在30分钟后拉起FaultLogExtensionAbility。

开发者可在[onFaultReportReady](#onfaultreportready)中订阅并处理故障事件。

**起始版本：** 21

<!--Device-unnamed-declare class FaultLogExtensionAbility--><!--Device-unnamed-declare class FaultLogExtensionAbility-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.FaultLogger

## ExtensionAbility使用限制

为保障系统安全性和稳定性，防止FaultLogExtensionAbility滥用系统资源，系统对其能力进行管控，不支持部分模块的引用，详情请参考[附录](#附录)。

## 导入模块

```TypeScript
import { FaultLogExtensionAbility } from '@kit.PerformanceAnalysisKit';
```

## onConnect

```TypeScript
onConnect(): void
```

FaultLogExtensionAbility生命周期回调。当系统服务完成连接时调用此接口，用于执行初始化操作，该方法可选择性重写。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FaultLogExtensionAbility-onConnect(): void--><!--Device-FaultLogExtensionAbility-onConnect(): void-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.FaultLogger

**示例**

```TypeScript
export default class MyFaultLogExtension extends FaultLogExtensionAbility {
    onConnect() {
      console.info('onConnect');
    }
}
```

## onDisconnect

```TypeScript
onDisconnect(): void
```

FaultLogExtensionAbility生命周期回调。当系统服务完成断开连接时调用此接口，用于释放资源清理运行状态，该方法可选择性重写。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FaultLogExtensionAbility-onDisconnect(): void--><!--Device-FaultLogExtensionAbility-onDisconnect(): void-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.FaultLogger

**示例**

```TypeScript
export default class MyFaultLogExtension extends FaultLogExtensionAbility {
    onDisconnect() {
      console.info('onDisconnect');
    }
}
```

## onFaultReportReady

```TypeScript
onFaultReportReady(): void
```

FaultLogExtensionAbility回调。系统服务通知FaultLogExtensionAbility可以进行故障处理时，回调此接口，可以在该方法中订阅故障事件进行处理。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FaultLogExtensionAbility-onFaultReportReady(): void--><!--Device-FaultLogExtensionAbility-onFaultReportReady(): void-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.FaultLogger

**示例**

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';

export default class MyFaultLogExtension extends FaultLogExtensionAbility {
    onFaultReportReady() {
        hiAppEvent.addWatcher({
            name: "watcher",
            appEventFilters: [
                {
                    domain: hiAppEvent.domain.OS,
                    names: [hiAppEvent.event.APP_CRASH, hiAppEvent.event.APP_FREEZE]
                }
            ],
            onReceive: (domain: string, appEventGroups: Array<hiAppEvent.AppEventGroup>) => {
                // 进行故障事件处理
            }
        });
    }
}
```

## context

```TypeScript
context: FaultLogExtensionContext
```

FaultLogExtensionAbility的上下文环境，继承自[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。

**类型：** [FaultLogExtensionContext](arkts-performanceanalysis-hiviewdfx-faultlogextensioncontext-faultlogextensioncontext-c.md)

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FaultLogExtensionAbility-context: FaultLogExtensionContext--><!--Device-FaultLogExtensionAbility-context: FaultLogExtensionContext-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.FaultLogger

## 附录

FaultLogExtensionAbility不支持以下模块的引用。

| Kit | 模块 |
| --- | --- |
| Background Tasks Kit | [@ohos.backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-backgroundtaskmanager.md) |
| Background Tasks Kit | [@ohos.resourceschedule.backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-resourceschedule-backgroundtaskmanager.md) |
| Audio Kit | [@ohos.multimedia.audio](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audio.md) |
| AVSession Kit | [@ohos.multimedia.avsession](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avsession.md) |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Camera Kit | [@ohos.multimedia.cameraPicker](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camerapicker.md) |
| Media Library Kit | [multimedia.movingphotoview](../../apis-media-library-kit/arkts-apis/arkts-multimedia-movingphotoview.md) |
| Telephony Kit | [@ohos.telephony.call](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-call.md) |
| Telephony Kit | [@ohos.telephony.sim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sim.md) |
| Telephony Kit | [@ohos.telephony.sms](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sms.md) |
| Basic Services Kit | [@ohos.power](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-power.md) |
| ArkUI | [@ohos.window](../../apis-arkui/arkts-apis/arkts-arkui-window.md) |
| Background Tasks Kit | [@ohos.reminderAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent.md) |
| Background Tasks Kit | [@ohos.reminderAgentManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagentmanager.md) |
| Notification Kit | [@ohos.notification](../../apis-notification-kit/arkts-apis/arkts-notification-notification.md) |
| Notification Kit | [@ohos.notificationManager](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager.md) |
| Notification Kit | [@ohos.notificationSubscribe](../../apis-notification-kit/arkts-apis/arkts-notification-notificationsubscribe.md) |
| Connectivity Kit | [@ohos.wifiext](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifiext.md) |
| Connectivity Kit | [@ohos.wifiManager](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifimanager.md) |
| Connectivity Kit | [@ohos.wifiManagerExt](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifimanagerext.md) |
| IME Kit | [@ohos.inputMethod](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethod.md) |
| Ability Kit | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext.md) |
| User Authentication Kit | [@ohos.userIAM.faceAuth](../../apis-user-authentication-kit/arkts-apis/arkts-userauthentication-useriam-faceauth.md) |
| User Authentication Kit | [@ohos.userIAM.userAuth](../../apis-user-authentication-kit/arkts-apis/arkts-userauthentication-useriam-userauth.md) |
| Sensor Service Kit | [@ohos.vibrator](../../apis-sensor-service-kit/arkts-apis/arkts-sensorservice-vibrator.md) |
| Basic Services Kit | [@ohos.wallpaper](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-wallpaper.md) |
