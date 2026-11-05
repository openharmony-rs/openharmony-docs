# DriverExtensionAbility

```TypeScript
declare class DriverExtensionAbility
```

DriverExtensionAbility模块提供驱动相关扩展能力，提供驱动创建、销毁、连接、断开等生命周期回调。

**起始版本：** 10

<!--Device-unnamed-declare class DriverExtensionAbility--><!--Device-unnamed-declare class DriverExtensionAbility-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

## ExtensionAbility使用限制

为保障系统安全性和稳定性，防止DriverExtensionAbility滥用系统资源，系统对其能力进行管控，不支持部分模块的引用，详情请参考[附录](#附录)。

## 导入模块

```TypeScript
import { DriverExtensionAbility, DriverExtensionContext } from '@kit.DriverDevelopmentKit';
```

## onConnect

```TypeScript
onConnect(want: Want): rpc.RemoteObject | Promise<rpc.RemoteObject>
```

Extension生命周期回调，会在[onCreate](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-abilitystage-abilitystage-c.md#oncreate)之后回调。返回一个[RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md)对象，用于客户端和服务端进行通信。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DriverExtensionAbility-onConnect(want: Want): rpc.RemoteObject | Promise<rpc.RemoteObject>--><!--Device-DriverExtensionAbility-onConnect(want: Want): rpc.RemoteObject | Promise<rpc.RemoteObject>-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md) &#124; Promise&lt;[rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md)&gt; | 一个RemoteObject对象，用于客户端和服务端进行通信；或一个Promise对象，返回用于通信的RemoteObject对象。 |

**示例**

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { rpc } from '@kit.IPCKit';
import { Want } from '@kit.AbilityKit';

class StubTest extends rpc.RemoteObject {
    constructor(des: string) {
        super(des);
    }
    onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence, option: rpc.MessageOption) {
      // 必须重写此接口
      return true;
    }
}
class DriverExt extends DriverExtensionAbility {
  onConnect(want: Want) {
    console.info(`onConnect , want: ${want.abilityName}`);
    return new StubTest('test');
  }
}
```

如果生成返回值[RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md)依赖一个异步接口，可以使用异步生命周期：

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { rpc } from '@kit.IPCKit';
import { Want } from '@kit.AbilityKit';

class StubTest extends rpc.RemoteObject {
    constructor(des: string) {
        super(des);
    }
    onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence, option: rpc.MessageOption) {
      // 必须重写此接口
      return true;
    }
}
async function getDescriptor() {
    // 调用异步函数...
    return 'asyncTest';
}
class DriverExt extends DriverExtensionAbility {
  async onConnect(want: Want) {
    console.info(`onConnect , want: ${want.abilityName}`);
    let descriptor = await getDescriptor();
    return new StubTest(descriptor);
  }
}
```

## onDisconnect

```TypeScript
onDisconnect(want: Want): void | Promise<void>
```

Extension的生命周期回调，客户端执行断开连接服务时回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DriverExtensionAbility-onDisconnect(want: Want): void | Promise<void>--><!--Device-DriverExtensionAbility-onDisconnect(want: Want): void | Promise<void>-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 |

**示例**

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { Want } from '@kit.AbilityKit';

class DriverExt extends DriverExtensionAbility {
  onDisconnect(want: Want) {
    console.info(`onDisconnect, want: ${want.abilityName}`);
  }
}
```

在执行完onDisconnect生命周期回调后，应用可能会退出，从而可能导致onDisconnect中的异步函数未能正确执行，比如异步写入数据库。可以使用异步生命周期，以确保异步onDisconnect完成后再继续后续的生命周期。

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { Want } from '@kit.AbilityKit';

class DriverExt extends DriverExtensionAbility {
  async onDisconnect(want: Want) {
    console.info(`onDisconnect, want: ${want.abilityName}`);
    // 调用异步函数...
  }
}
```

## onDump

```TypeScript
onDump(params: Array<string>): Array<string>
```

转储客户端信息时调用，建议不要转储敏感信息。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DriverExtensionAbility-onDump(params: Array<string>): Array<string>--><!--Device-DriverExtensionAbility-onDump(params: Array<string>): Array<string>-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | Array&lt;string&gt; | 是 | 转储命令的参数列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 一个string类型的数组，包含转储的客户端信息。 |

**示例**

```TypeScript
class DriverExt extends DriverExtensionAbility {
    onDump(params: Array<string>) {
        console.info(`dump, params: ${JSON.stringify(params)}`);
        return ['params'];
    }
}
```

## onInit

```TypeScript
onInit(want: Want): void
```

Extension生命周期回调，在创建时回调，执行初始化业务逻辑操作。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DriverExtensionAbility-onInit(want: Want): void--><!--Device-DriverExtensionAbility-onInit(want: Want): void-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 |

**示例**

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { Want } from '@kit.AbilityKit';

class DriverExt extends DriverExtensionAbility {
  onInit(want: Want) {
    console.info(`onInit, want: ${want.abilityName}`);
  }
}
```

## onRelease

```TypeScript
onRelease(): void
```

Extension生命周期回调，在销毁时回调，执行资源清理等操作。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DriverExtensionAbility-onRelease(): void--><!--Device-DriverExtensionAbility-onRelease(): void-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

**示例**

```TypeScript
class DriverExt extends DriverExtensionAbility {
  onRelease() {
    console.info('onRelease');
  }
}
```

## context

```TypeScript
context: DriverExtensionContext
```

DriverExtension的上下文环境，继承自ExtensionContext。

**类型：** [DriverExtensionContext](arkts-driverdevelopment-driverextensioncontext-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DriverExtensionAbility-context: DriverExtensionContext--><!--Device-DriverExtensionAbility-context: DriverExtensionContext-End-->

**系统能力：** SystemCapability.Driver.ExternalDevice

## 附录

DriverExtensionAbility不支持以下模块的引用。

| Kit | 模块 |
| --- | --- |
| Ability Kit | [@ohos.abilityAccessCtrl](../../apis-ability-kit/arkts-apis/arkts-ability-abilityaccessctrl.md) |
| Ability Kit | [@ohos.ability.particleAbility](../../apis-ability-kit/arkts-apis/arkts-ability-ability-particleability.md) |
| Accessibility Kit | [@ohos.accessibility.config](../../apis-accessibility-kit/arkts-apis/arkts-accessibility-accessibility-config.md) |
| Basic Services Kit | [@ohos.account.appAccount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-account-appaccount.md) |
| Basic Services Kit | [@ohos.account.distributedAccount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-account-distributedaccount.md) |
| Basic Services Kit | [@ohos.account.osAccount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-account-osaccount.md) |
| Ability Kit | [@ohos.app.ability.abilityManager](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-abilitymanager.md) |
| Ability Kit | [@ohos.app.ability.appManager](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-appmanager.md) |
| Ability Kit | [@ohos.app.ability.missionManager](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-missionmanager.md) |
| Ability Kit | [@ohos.app.ability.quickFixManager](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-quickfixmanager.md) |
| Form Kit | [@ohos.app.form.formHost](../../apis-form-kit/arkts-apis/arkts-form-app-form-formhost.md) |
| Ability Kit | [@ohos.application.abilityManager](../../apis-ability-kit/arkts-apis/arkts-ability-application-abilitymanager.md) |
| Ability Kit | [@ohos.application.appManager](../../apis-ability-kit/arkts-apis/arkts-ability-application-appmanager.md) |
| Form Kit | [@ohos.application.formError](../../apis-form-kit/arkts-apis/arkts-form-application-formerror.md) |
| Form Kit | [@ohos.application.formHost](../../apis-form-kit/arkts-apis/arkts-form-application-formhost.md) |
| Ability Kit | [@ohos.application.missionManager](../../apis-ability-kit/arkts-apis/arkts-ability-application-missionmanager.md) |
| Background Tasks Kit | [@ohos.backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-backgroundtaskmanager.md) |
| Connectivity Kit | [@ohos.bluetooth](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth.md) |
| Connectivity Kit | [@ohos.bluetoothManager](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetoothmanager.md) |
| Ability Kit | [@ohos.bundle](../../apis-ability-kit/arkts-apis/arkts-ability-bundle.md) |
| Ability Kit | [@ohos.bundle.appControl](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-appcontrol.md) |
| Ability Kit | [@ohos.bundle.bundleManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-bundlemanager.md) |
| Ability Kit | [@ohos.bundle.defaultAppManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-defaultappmanager.md) |
| Ability Kit | [@ohos.bundle.distributedBundleManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-distributedbundlemanager.md) |
| Ability Kit | [@ohos.bundle.freeInstall](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-freeinstall.md) |
| Ability Kit | [@ohos.bundle.innerBundleManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-innerbundlemanager.md) |
| Ability Kit | [@ohos.bundle.installer](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-installer.md) |
| Ability Kit | [@ohos.bundle.launcherBundleManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-launcherbundlemanager.md) |
| Background Tasks Kit | [@ohos.bundleState](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-bundlestate.md) |
| Connectivity Kit | [@ohos.connectedTag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-connectedtag.md) |
| Contacts Kit | [@ohos.contact](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact.md) |
| Ability Kit | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context.md) |
| Ability Kit | [@ohos.continuation.continuationManager](../../apis-ability-kit/arkts-apis/arkts-ability-continuation-continuationmanager.md) |
| ArkData | [@ohos.data.distributedData](../../apis-arkdata/arkts-apis/arkts-arkdata-data-distributeddata.md) |
| ArkData | [@ohos.data.distributedDataObject](../../apis-arkdata/arkts-apis/arkts-arkdata-data-distributeddataobject.md) |
| ArkData | [@ohos.data.distributedKVStore](../../apis-arkdata/arkts-apis/arkts-arkdata-data-distributedkvstore.md) |
| ArkData | [@ohos.data.rdb](../../apis-arkdata/arkts-apis/arkts-arkdata-data-rdb.md) |
| ArkData | [@ohos.data.relationalStore](../../apis-arkdata/arkts-apis/arkts-arkdata-data-relationalstore.md) |
| Basic Services Kit | [@ohos.deviceInfo](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-deviceinfo.md) |
| Ability Kit | [@ohos.distributedBundle](../../apis-ability-kit/arkts-apis/arkts-ability-distributedbundle.md) |
| Ability Kit | [@ohos.distributedMissionManager](../../apis-ability-kit/arkts-apis/arkts-ability-distributedmissionmanager.md) |
| MDM Kit | [@ohos.enterprise.adminManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-adminmanager.md) |
| MDM Kit | [@ohos.enterprise.dateTimeManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-datetimemanager.md) |
| MDM Kit | [@ohos.enterprise.deviceInfo](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-deviceinfo.md) |
| Core File Kit | [@ohos.file.fileAccess](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fileaccess.md) |
| Core File Kit | [filemanagement.userFileManager](../../apis-core-file-kit/arkts-apis/arkts-filemanagement-userfilemanager.md) |
| Core File Kit | [@ohos.file.storageStatistics](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-storagestatistics.md) |
| Core File Kit | [@ohos.file.volumeManager](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-volumemanager.md) |
| Location Kit | [@ohos.geolocation](../../apis-location-kit/arkts-apis/arkts-location-geolocation.md) |
| Location Kit | [@ohos.geoLocationManager](../../apis-location-kit/arkts-apis/arkts-location-geolocationmanager.md) |
| Performance Analysis Kit | [@ohos.hidebug](../../apis-performance-analysis-kit/arkts-apis/arkts-performanceanalysis-hidebug.md) |
| Performance Analysis Kit | [@ohos.hiSysEvent](../../apis-performance-analysis-kit/arkts-apis/arkts-performanceanalysis-hisysevent.md) |
| IME Kit | [@ohos.inputMethod](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethod.md) |
| AVSession Kit | [@ohos.multimedia.avsession](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avsession.md) |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Media Kit | [@ohos.multimedia.media](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media.md) |
| Input Kit | [@ohos.multimodalInput.inputMonitor](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-inputmonitor.md) |
| Network Kit | [@ohos.net.connection](../../apis-network-kit/arkts-apis/arkts-network-net-connection.md) |
| Network Kit | [@ohos.net.ethernet](../../apis-network-kit/arkts-apis/arkts-network-net-ethernet.md) |
| Network Kit | [@ohos.net.http](../../apis-network-kit/arkts-apis/arkts-network-net-http.md) |
| Network Kit | [@ohos.net.sharing](../../apis-network-kit/arkts-apis/arkts-network-net-sharing.md) |
| Network Kit | [@ohos.net.socket](../../apis-network-kit/arkts-apis/arkts-network-net-socket.md) |
| Network Kit | [@ohos.net.webSocket](../../apis-network-kit/arkts-apis/arkts-network-net-websocket.md) |
| Connectivity Kit | [@ohos.nfc.cardEmulation](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-cardemulation.md) |
| Connectivity Kit | [@ohos.nfc.controller](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-controller.md) |
| Connectivity Kit | [@ohos.nfc.tag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-tag.md) |
| Notification Kit | [@ohos.notification](../../apis-notification-kit/arkts-apis/arkts-notification-notification.md) |
| Notification Kit | [@ohos.notificationManager](../../apis-notification-kit/arkts-apis/arkts-notification-notificationmanager.md) |
| Notification Kit | [@ohos.notificationSubscribe](../../apis-notification-kit/arkts-apis/arkts-notification-notificationsubscribe.md) |
| Basic Services Kit | [@ohos.power](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-power.md) |
| Ability Kit | [@ohos.privacyManager](../../apis-ability-kit/arkts-apis/arkts-ability-privacymanager.md) |
| Background Tasks Kit | [@ohos.reminderAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent.md) |
| Background Tasks Kit | [@ohos.reminderAgentManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagentmanager.md) |
| Basic Services Kit | [@ohos.request](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-request.md) |
| Background Tasks Kit | [@ohos.resourceschedule.backgroundTaskManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-resourceschedule-backgroundtaskmanager.md) |
| Background Tasks Kit | [@ohos.resourceschedule.usageStatistics](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-resourceschedule-usagestatistics.md) |
| Basic Services Kit | [@ohos.runningLock](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-runninglock.md) |
| ArkUI | [@ohos.screen](../../apis-arkui/arkts-apis/arkts-arkui-screen.md) |
| ArkUI | [@ohos.screenshot](../../apis-arkui/arkts-apis/arkts-arkui-screenshot.md) |
| Sensor Service Kit | [@ohos.sensor](../../apis-sensor-service-kit/arkts-apis/arkts-sensorservice-sensor.md) |
| Basic Services Kit | [settings](../../apis-basic-services-kit/arkts-apis/arkts-settings.md) |
| Basic Services Kit | [@ohos.systemTime](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-systemtime.md) |
| Telephony Kit | [@ohos.telephony.call](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-call.md) |
| Telephony Kit | [@ohos.telephony.data](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-data.md) |
| Telephony Kit | [@ohos.telephony.observer](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-observer.md) |
| Telephony Kit | [@ohos.telephony.radio](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-radio.md) |
| Telephony Kit | [@ohos.telephony.sim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sim.md) |
| Telephony Kit | [@ohos.telephony.sms](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sms.md) |
| Basic Services Kit | [@ohos.update](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-update.md) |
| User Authentication Kit | [@ohos.userIAM.faceAuth](../../apis-user-authentication-kit/arkts-apis/arkts-userauthentication-useriam-faceauth.md) |
| Sensor Service Kit | [@ohos.vibrator](../../apis-sensor-service-kit/arkts-apis/arkts-sensorservice-vibrator.md) |
| Basic Services Kit | [@ohos.wallpaper](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-wallpaper.md) |
| Connectivity Kit | [@ohos.wifi](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifi.md) |
| Connectivity Kit | [@ohos.wifiext](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifiext.md) |
| Connectivity Kit | [@ohos.wifiManager](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifimanager.md) |
| Connectivity Kit | [@ohos.wifiManagerExt](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifimanagerext.md) |
| ArkUI | [@ohos.window](../../apis-arkui/arkts-apis/arkts-arkui-window.md) |
