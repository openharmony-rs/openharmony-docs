# DistributedExtensionAbility

```TypeScript
declare class DistributedExtensionAbility
```

DistributedExtensionAbility模块提供分布式相关扩展能力，提供分布式创建、销毁、连接的生命周期回调。

**起始版本：** 20

<!--Device-unnamed-declare class DistributedExtensionAbility--><!--Device-unnamed-declare class DistributedExtensionAbility-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## ExtensionAbility使用限制

为保障系统安全性和稳定性，防止DistributedExtensionAbility滥用系统资源，系统对其能力进行管控，不支持部分模块的引用，详情请参考[附录](#附录)。

## 导入模块

```TypeScript
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';
```

## onCollaborate

```TypeScript
onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult
```

Extension生命周期回调，在多设备限定协同场景下，协同方应用被拉起过程中返回是否接受协同的结果，返回结果决定协同流程是否继续。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DistributedExtensionAbility-onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult--><!--Device-DistributedExtensionAbility-onCollaborate(wantParam: Record<string, Object>): AbilityConstant.CollaborateResult-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wantParam | Record&lt;string, Object&gt; | 是 | 协同回调参数，键值对对象，携带调用方传输的协同相关数据。开发者可通过"ohos.extra.param.key.supportCollaborateIndex"和"CollaborationValues"等key值获取这些数据，以决定是否接受协同请求及处理协同逻辑，影响协同流程是否继续。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [AbilityConstant.CollaborateResult](../../apis-ability-kit/arkts-apis/arkts-ability-abilityconstant-collaborateresult-e.md) | 表示协同方应用是否接受协同的结果。取值包括：**ACCEPT**表示接受协同，协同流程继续；**REJECT**表示拒绝协同，协同流程终止。 |

**示例**

```TypeScript
import { abilityConnectionManager, DistributedExtensionAbility } from '@kit.DistributedServiceKit';
import { AbilityConstant } from '@kit.AbilityKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onCollaborate(wantParam: Record<string, Object>) {
    console.info(`DistributedExtension onCollabRequest Accept to the result of Ability collaborate`);
    const collaborationValues = wantParam["CollaborationValues"] as abilityConnectionManager.CollaborationValues;
    if (!collaborationValues) {
      console.error('Failed to get collaborationValues.');
      return AbilityConstant.CollaborateResult.REJECT;
    }
    console.info(`onCollab, collaborationValues: ${JSON.stringify(collaborationValues)}`);
    return AbilityConstant.CollaborateResult.ACCEPT;
  }
}
```

## onCreate

```TypeScript
onCreate(want: Want): void
```

Extension生命周期回调，在创建时回调，执行初始化业务逻辑操作。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DistributedExtensionAbility-onCreate(want: Want): void--><!--Device-DistributedExtensionAbility-onCreate(want: Want): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 当前Extension相关的Want信息，用于携带创建Extension所需的初始化配置信息。 |

**示例**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onCreate(want: Want) {
    console.info(`DistributedExtension Create ok`);
    console.info(`DistributedExtension on Create want: ${JSON.stringify(want)}`);
    console.info(`DistributedExtension Create end`);
  }
}
```

## onDestroy

```TypeScript
onDestroy(): void
```

Extension生命周期回调，在销毁时回调，执行资源清理等操作。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DistributedExtensionAbility-onDestroy(): void--><!--Device-DistributedExtensionAbility-onDestroy(): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**示例**

```TypeScript
import { DistributedExtensionAbility } from '@kit.DistributedServiceKit';

export default class DistributedExtension extends DistributedExtensionAbility {
  onDestroy() {
    console.info('DistributedExtension onDestroy ok');
  }
}
```

## context

```TypeScript
context: DistributedExtensionContext
```

DistributedExtension（协同Extension）的上下文环境，继承自ExtensionContext。

**类型：** [DistributedExtensionContext](arkts-distributedservice-application-distributedextensioncontext-distributedextensioncontext-c.md)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DistributedExtensionAbility-context: DistributedExtensionContext--><!--Device-DistributedExtensionAbility-context: DistributedExtensionContext-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 附录

DistributedExtensionAbility不支持以下模块的引用。

| Kit | 模块 |
| --- | --- |
| Ability Kit | [@ohos.ability.featureAbility](../../apis-ability-kit/arkts-apis/arkts-ability-ability-featureability.md) |
| Ability Kit | [@ohos.ability.particleAbility](../../apis-ability-kit/arkts-apis/arkts-ability-ability-particleability.md) |
| Accessibility Kit | [@ohos.accessibility.config](../../apis-accessibility-kit/arkts-apis/arkts-accessibility-accessibility-config.md) |
| Basic Services Kit | [@ohos.account.appAccount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-account-appaccount.md) |
| Basic Services Kit | [@ohos.account.distributedAccount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-account-distributedaccount.md) |
| Basic Services Kit | [@ohos.account.osAccount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-account-osaccount.md) |
| Form Kit | [@ohos.app.form.formBindingData](../../apis-form-kit/arkts-apis/arkts-form-app-form-formbindingdata.md) |
| Form Kit | [@ohos.app.form.FormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability.md) |
| Form Kit | [@ohos.app.form.formHost](../../apis-form-kit/arkts-apis/arkts-form-app-form-formhost.md) |
| Form Kit | [@ohos.app.form.formInfo](../../apis-form-kit/arkts-apis/arkts-form-app-form-forminfo.md) |
| Form Kit | [@ohos.app.form.formProvider](../../apis-form-kit/arkts-apis/arkts-form-app-form-formprovider.md) |
| Form Kit | [@ohos.application.formBindingData](../../apis-form-kit/arkts-apis/arkts-form-application-formbindingdata.md) |
| Form Kit | [@ohos.application.formError](../../apis-form-kit/arkts-apis/arkts-form-application-formerror.md) |
| Form Kit | [@ohos.application.formHost](../../apis-form-kit/arkts-apis/arkts-form-application-formhost.md) |
| Form Kit | [@ohos.application.formInfo](../../apis-form-kit/arkts-apis/arkts-form-application-forminfo.md) |
| Form Kit | [@ohos.application.formProvider](../../apis-form-kit/arkts-apis/arkts-form-application-formprovider.md) |
| Connectivity Kit | [@ohos.connectedTag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-connectedtag.md) |
| Contacts Kit | [@ohos.contact](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact.md) |
| Ability Kit | [@ohos.continuation.continuationManager](../../apis-ability-kit/arkts-apis/arkts-ability-continuation-continuationmanager.md) |
| Media Library Kit | [@ohos.file.AlbumPickerComponent](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-albumpickercomponent.md) |
| Media Library Kit | [@ohos.file.photoAccessHelper](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-photoaccesshelper.md) |
| Media Library Kit | [@ohos.file.PhotoPickerComponent](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-photopickercomponent.md) |
| Core File Kit | [@ohos.file.picker](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-picker.md) |
| Media Library Kit | [@ohos.file.RecentPhotoComponent](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-recentphotocomponent.md) |
| Media Library Kit | [@ohos.file.sendablePhotoAccessHelper](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-sendablephotoaccesshelper.md) |
| IME Kit | [@ohos.inputMethod](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethod.md) |
| Audio Kit | [@ohos.multimedia.audio](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audio.md) |
| AVSession Kit | [@ohos.multimedia.avsession](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avsession.md) |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Camera Kit | [@ohos.multimedia.cameraPicker](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camerapicker.md) |
| Media Library Kit | [multimedia.movingphotoview](../../apis-media-library-kit/arkts-apis/arkts-multimedia-movingphotoview.md) |
| Input Kit | [@ohos.multimodalInput.inputMonitor](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-inputmonitor.md) |
| Connectivity Kit | [@ohos.nfc.cardEmulation](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-cardemulation.md) |
| Connectivity Kit | [@ohos.nfc.controller](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-controller.md) |
| Connectivity Kit | [@ohos.nfc.tag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-tag.md) |
| Connectivity Kit | [nfctech](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfctech.md) |
| Notification Kit | [@ohos.notification](../../apis-notification-kit/arkts-apis/arkts-notification-notification.md) |
| Notification Kit | [@ohos.notificationManager](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager.md) |
| Notification Kit | [@ohos.notificationSubscribe](../../apis-notification-kit/arkts-apis/arkts-notification-notificationsubscribe.md) |
| Basic Services Kit | [@ohos.power](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-power.md) |
| ArkUI | [@ohos.prompt](../../apis-arkui/arkts-apis/arkts-arkui-prompt.md) |
| ArkUI | [@ohos.promptAction](../../apis-arkui/arkts-apis/arkts-arkui-promptaction.md) |
| Background Tasks Kit | [@ohos.reminderAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent.md) |
| Background Tasks Kit | [@ohos.reminderAgentManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagentmanager.md) |
| ArkUI | [@ohos.screen](../../apis-arkui/arkts-apis/arkts-arkui-screen.md) |
| ArkUI | [@ohos.screenshot](../../apis-arkui/arkts-apis/arkts-arkui-screenshot.md) |
| Ability Kit | [ServiceExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-serviceextensioncontext.md) |
| Connectivity Kit | [tagSession](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-tagsession.md) |
| Telephony Kit | [@ohos.telephony.call](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-call.md) |
| Telephony Kit | [@ohos.telephony.sim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sim.md) |
| Telephony Kit | [@ohos.telephony.sms](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sms.md) |
| Telephony Kit | [telephony.voipCall](../../apis-telephony-kit/arkts-apis/arkts-telephony-voipcall.md) |
| Ability Kit | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext.md) |
| User Authentication Kit | [@ohos.userIAM.faceAuth](../../apis-user-authentication-kit/arkts-apis/arkts-userauthentication-useriam-faceauth.md) |
| User Authentication Kit | [@ohos.userIAM.userAuth](../../apis-user-authentication-kit/arkts-apis/arkts-userauthentication-useriam-userauth.md) |
| Sensor Service Kit | [@ohos.vibrator](../../apis-sensor-service-kit/arkts-apis/arkts-sensorservice-vibrator.md) |
| Basic Services Kit | [@ohos.wallpaper](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-wallpaper.md) |
| ArkUI | [@ohos.window](../../apis-arkui/arkts-apis/arkts-arkui-window.md) |
