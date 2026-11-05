# LiveFormExtensionAbility

```TypeScript
declare class LiveFormExtensionAbility extends ExtensionAbility
```

互动卡片扩展类，用于实现互动卡片的提供方功能。包含互动卡片提供方接收创建和销毁互动卡片的通知接口，开发者可在这些回调中实现卡片的初始化、数据绑定、资源清理等逻辑。[onLiveFormCreate](#onliveformcreate)在用户切换互动卡片状态为激活态时触发，用于初始化和数据绑定；[onLiveFormDestroy](#onliveformdestroy)在用户切换互动卡片状态为非激活态时触发，用于资源清理。两者形成完整的生命周期管理，应确保在create中分配的资源在destroy中正确释放。

**继承/实现关系：** LiveFormExtensionAbility extends [ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md)

**起始版本：** 20

<!--Device-unnamed-declare class LiveFormExtensionAbility extends ExtensionAbility--><!--Device-unnamed-declare class LiveFormExtensionAbility extends ExtensionAbility-End-->

**系统能力：** SystemCapability.Ability.Form

## ExtensionAbility使用限制

为保障系统安全性和稳定性，防止LiveFormExtensionAbility滥用系统资源，系统对其能力进行管控，不支持部分模块的引用，详情请参考[附录](#附录)。

## 导入模块

```TypeScript
import { LiveFormExtensionAbility, LiveFormInfo } from '@kit.FormKit';
```

## onLiveFormCreate

```TypeScript
onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession): void
```

LiveFormExtensionAbility实例创建完成的回调。当用户切换到互动卡片激活态时，系统会自动调用此回调，开发者可在此回调中进行卡片初始化、数据绑定等操作。

- 与onLiveFormDestroy()方法成对使用，构成完整的互动卡片生命周期。  
- 当互动卡片切换为非激活态时，系统会自动调用onLiveFormDestroy()进行资源清理。  
- 开发者应确保在onLiveFormCreate中申请的资源在onLiveFormDestroy中正确释放，避免内存泄漏。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-LiveFormExtensionAbility-onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession): void--><!--Device-LiveFormExtensionAbility-onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| liveFormInfo | [LiveFormInfo](arkts-form-app-form-liveformextensionability-liveforminfo-i.md) | 是 | 互动卡片信息，用于标识处于激活态的互动卡片，包括卡片id等信息。 |
| session | [UIExtensionContentSession](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) | 是 | LiveFormExtensionAbility的界面会话对象，用于管理与卡片的交互会话。 |

**示例**

```TypeScript
import { UIExtensionContentSession } from '@kit.AbilityKit';
import { LiveFormExtensionAbility, LiveFormInfo } from '@kit.FormKit';

const TAG: string = '[testTag] LiveFormExtAbility';

export default class LiveFormExtAbility extends LiveFormExtensionAbility {
  onLiveFormCreate(liveFormInfo: LiveFormInfo, session: UIExtensionContentSession) {
    console.info(TAG, `onLiveFormCreate, formId: ${liveFormInfo.formId}`);
  }
}
```

## onLiveFormDestroy

```TypeScript
onLiveFormDestroy(liveFormInfo: LiveFormInfo): void
```

LiveFormExtensionAbility生命周期回调，在销毁时回调，执行资源清理等操作。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-LiveFormExtensionAbility-onLiveFormDestroy(liveFormInfo: LiveFormInfo): void--><!--Device-LiveFormExtensionAbility-onLiveFormDestroy(liveFormInfo: LiveFormInfo): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| liveFormInfo | [LiveFormInfo](arkts-form-app-form-liveformextensionability-liveforminfo-i.md) | 是 | 互动卡片信息，用于标识处于非激活态的互动卡片，包括卡片id等信息。 |

**示例**

```TypeScript
import { LiveFormExtensionAbility, LiveFormInfo } from '@kit.FormKit';

const TAG: string = '[testTag] LiveFormExtAbility';

export default class LiveFormExtAbility extends LiveFormExtensionAbility {
  onLiveFormDestroy(liveFormInfo: LiveFormInfo) {
    console.info(TAG, `onLiveFormDestroy, formId: ${liveFormInfo.formId}`);
  }
}
```

## context

```TypeScript
context: LiveFormExtensionContext
```

LiveFormExtensionAbility的上下文环境，继承自[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)。

**类型：** [LiveFormExtensionContext](arkts-form-liveformextensioncontext-c.md)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

<!--Device-LiveFormExtensionAbility-context: LiveFormExtensionContext--><!--Device-LiveFormExtensionAbility-context: LiveFormExtensionContext-End-->

**系统能力：** SystemCapability.Ability.Form

## 附录

LiveFormExtensionAbility不支持以下模块的引用。

| Kit | 模块 |
| --- | --- |
| Ability Kit | [@ohos.ability.featureAbility](../../apis-ability-kit/arkts-apis/arkts-ability-ability-featureability.md) |
| Ability Kit | [@ohos.ability.particleAbility](../../apis-ability-kit/arkts-apis/arkts-ability-ability-particleability.md) |
| Accessibility Kit | [@ohos.accessibility.config](../../apis-accessibility-kit/arkts-apis/arkts-accessibility-accessibility-config.md) |
| Basic Services Kit | [@ohos.account.appAccount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-account-appaccount.md) |
| Basic Services Kit | [@ohos.account.distributedAccount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-account-distributedaccount.md) |
| Basic Services Kit | [@ohos.account.osAccount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-account-osaccount.md) |
| Ability Kit | [@ohos.app.ability.quickFixManager](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-quickfixmanager.md) |
| Form Kit | [@ohos.app.form.formHost](../../apis-form-kit/arkts-apis/arkts-form-app-form-formhost.md) |
| Form Kit | [@ohos.application.formHost](../../apis-form-kit/arkts-apis/arkts-form-application-formhost.md) |
| Background Tasks Kit | [@ohos.backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-backgroundtaskmanager.md) |
| Ability Kit | [@ohos.bundle.bundleMonitor](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-bundlemonitor.md) |
| Ability Kit | [@ohos.bundle.distributedBundleManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-distributedbundlemanager.md) |
| Ability Kit | [@ohos.bundle.freeInstall](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-freeinstall.md) |
| Ability Kit | [@ohos.bundle.innerBundleManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-innerbundlemanager.md) |
| Ability Kit | [@ohos.bundle.installer](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-installer.md) |
| Ability Kit | [@ohos.bundle.launcherBundleManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-launcherbundlemanager.md) |
| Connectivity Kit | [@ohos.connectedTag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-connectedtag.md) |
| Contacts Kit | [@ohos.contact](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact.md) |
| Ability Kit | [@ohos.continuation.continuationManager](../../apis-ability-kit/arkts-apis/arkts-ability-continuation-continuationmanager.md) |
| ArkData | [@ohos.data.distributedData](../../apis-arkdata/arkts-apis/arkts-arkdata-data-distributeddata.md) |
| ArkData | [@ohos.data.distributedDataObject](../../apis-arkdata/arkts-apis/arkts-arkdata-data-distributeddataobject.md) |
| ArkData | [@ohos.data.distributedKVStore](../../apis-arkdata/arkts-apis/arkts-arkdata-data-distributedkvstore.md) |
| Ability Kit | [@ohos.distributedBundle](../../apis-ability-kit/arkts-apis/arkts-ability-distributedbundle.md) |
| Ability Kit | [@ohos.distributedMissionManager](../../apis-ability-kit/arkts-apis/arkts-ability-distributedmissionmanager.md) |
| MDM Kit | [@ohos.enterprise.adminManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-adminmanager.md) |
| Mdm Kit | [enterprise.dataTimeManager](../../apis-mdm-kit/arkts-apis/arkts-enterprise-datatimemanager.md) |
| MDM Kit | [@ohos.enterprise.deviceInfo](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-deviceinfo.md) |
| Core File Kit | [filemanagement.userFileManager](../../apis-core-file-kit/arkts-apis/arkts-filemanagement-userfilemanager.md) |
| Performance Analysis Kit | [@ohos.hidebug](../../apis-performance-analysis-kit/arkts-apis/arkts-performanceanalysis-hidebug.md) |
| Audio Kit | [@ohos.multimedia.audio](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audio.md) |
| AVSession Kit | [@ohos.multimedia.avsession](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avsession.md) |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Media Kit | [@ohos.multimedia.media](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media.md) |
| Connectivity Kit | [@ohos.nfc.cardEmulation](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-cardemulation.md) |
| Connectivity Kit | [@ohos.nfc.controller](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-controller.md) |
| Connectivity Kit | [@ohos.nfc.tag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-tag.md) |
| Notification Kit | [@ohos.notification](../../apis-notification-kit/arkts-apis/arkts-notification-notification.md) |
| Notification Kit | [@ohos.notificationManager](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager.md) |
| Notification Kit | [@ohos.notificationSubscribe](../../apis-notification-kit/arkts-apis/arkts-notification-notificationsubscribe.md) |
| Ability Kit | [@ohos.privacyManager](../../apis-ability-kit/arkts-apis/arkts-ability-privacymanager.md) |
| Background Tasks Kit | [@ohos.reminderAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent.md) |
| Background Tasks Kit | [@ohos.reminderAgentManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagentmanager.md) |
| Basic Services Kit | [@ohos.request](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-request.md) |
| Background Tasks Kit | [@ohos.resourceschedule.backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-resourceschedule-backgroundtaskmanager.md) |
| Background Tasks Kit | [@ohos.resourceschedule.usageStatistics](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-resourceschedule-usagestatistics.md) |
| Telephony Kit | [@ohos.telephony.call](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-call.md) |
| Telephony Kit | [@ohos.telephony.data](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-data.md) |
| Telephony Kit | [@ohos.telephony.observer](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-observer.md) |
| Telephony Kit | [@ohos.telephony.radio](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-radio.md) |
| Telephony Kit | [@ohos.telephony.sim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sim.md) |
| Telephony Kit | [@ohos.telephony.sms](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sms.md) |
| Basic Services Kit | [@ohos.update](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-update.md) |
| User Authentication Kit | [@ohos.userIAM.faceAuth](../../apis-user-authentication-kit/arkts-apis/arkts-userauthentication-useriam-faceauth.md) |
| User Authentication Kit | [@ohos.userIAM.userAuth](../../apis-user-authentication-kit/arkts-apis/arkts-userauthentication-useriam-userauth.md) |
| Basic Services Kit | [@ohos.wallpaper](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-wallpaper.md) |
| ArkUI | [@ohos.window](../../apis-arkui/arkts-apis/arkts-arkui-window.md) |
| Ability Kit | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context.md) |
| Ability Kit | [ServiceExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-serviceextensioncontext.md) |
| Ability Kit | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext.md) |
| Connectivity Kit | [nfctech](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfctech.md) |
| Connectivity Kit | [tagSession](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-tagsession.md) |
| Core File Kit | [@ohos.file.picker](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-picker.md) |
| Media Library Kit | [@ohos.file.sendablePhotoAccessHelper](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-sendablephotoaccesshelper.md) |
| Media Library Kit | [@ohos.file.AlbumPickerComponent](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-albumpickercomponent.md) |
| Media Library Kit | [@ohos.file.PhotoPickerComponent](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-photopickercomponent.md) |
| Media Library Kit | [@ohos.file.RecentPhotoComponent](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-recentphotocomponent.md) |
| Media Library Kit | [multimedia.movingphotoview](../../apis-media-library-kit/arkts-apis/arkts-multimedia-movingphotoview.md) |
| Camera Kit | [@ohos.multimedia.cameraPicker](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camerapicker.md) |
| Basic Services Kit | [@ohos.pasteboard](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-pasteboard.md) |
| Calendar Kit | [@ohos.calendarManager](../../apis-calendar-kit/arkts-apis/arkts-calendar-calendarmanager.md) |
| AVSession Kit | [@ohos.multimedia.avCastPicker](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avcastpicker.md) |
