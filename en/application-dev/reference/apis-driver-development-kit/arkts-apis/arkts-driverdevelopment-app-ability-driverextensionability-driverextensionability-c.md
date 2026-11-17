# DriverExtensionAbility

```TypeScript
declare class DriverExtensionAbility
```

The **DriverExtensionAbility** module provides the ExtensionAbility related to drivers. It provides lifecycle callbacks to be invoked when a driver is created, destroyed, connected, or disconnected.

**Since:** 10

<!--Device-unnamed-declare class DriverExtensionAbility--><!--Device-unnamed-declare class DriverExtensionAbility-End-->

**System capability:** SystemCapability.Driver.ExternalDevice

## ExtensionAbility Usage Restrictions

To ensure system security and stability, DriverExtensionAbility is restricted from abusing system resources. The system controls its capabilities and does not support referencing some modules. For details, see [Appendix](#appendix).

## Modules to Import

```TypeScript
import { DriverExtensionAbility, DriverExtensionContext } from '@kit.DriverDevelopmentKit';
```

## onConnect

```TypeScript
onConnect(want: Want): rpc.RemoteObject | Promise<rpc.RemoteObject>
```

Called following **onCreate()** when a DriverExtensionAbility is started by calling **connectAbility()**. A **RemoteObject** object is returned for communication between the server and client.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-DriverExtensionAbility-onConnect(want: Want): rpc.RemoteObject | Promise<rpc.RemoteObject>--><!--Device-DriverExtensionAbility-onConnect(want: Want): rpc.RemoteObject | Promise<rpc.RemoteObject>-End-->

**System capability:** SystemCapability.Driver.ExternalDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want information related to this DriverExtensionAbility, including the ability name and bundle name. |

**Return value:**

| Type | Description |
| --- | --- |
| [rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md) &#124; Promise&lt;[rpc.RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md)&gt; | **RemoteObject** object used for communication between the server and client, or promise used to return the value. |

**Examples**

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { rpc } from '@kit.IPCKit';
import { Want } from '@kit.AbilityKit';

class StubTest extends rpc.RemoteObject {
    constructor(des: string) {
        super(des);
    }
    onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence, option: rpc.MessageOption) {
      // This interface must be overridden.
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

If the returned [RemoteObject](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-remoteobject-c.md) object depends on an asynchronous API, you can use the asynchronous lifecycle.

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { rpc } from '@kit.IPCKit';
import { Want } from '@kit.AbilityKit';

class StubTest extends rpc.RemoteObject {
    constructor(des: string) {
        super(des);
    }
    onRemoteMessageRequest(code: number, data: rpc.MessageSequence, reply: rpc.MessageSequence, option: rpc.MessageOption) {
      // This interface must be overridden.
      return true;
    }
}
async function getDescriptor() {
    // Call the asynchronous function.
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

Called when a client is disconnected from this DriverExtensionAbility.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-DriverExtensionAbility-onDisconnect(want: Want): void | Promise<void>--><!--Device-DriverExtensionAbility-onDisconnect(want: Want): void | Promise<void>-End-->

**System capability:** SystemCapability.Driver.ExternalDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want information related to this DriverExtensionAbility, including the ability name and bundle name. |

**Examples**

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { Want } from '@kit.AbilityKit';

class DriverExt extends DriverExtensionAbility {
  onDisconnect(want: Want) {
    console.info(`onDisconnect, want: ${want.abilityName}`);
  }
}
```

After the onDisconnect lifecycle callback is executed, the application may exit. As a result, the asynchronous function in onDisconnect may fail to be executed correctly, for example, asynchronously writing data to the database. The asynchronous lifecycle can be used to ensure that the subsequent lifecycle continues after the asynchronous onDisconnect is complete.

```TypeScript
import { DriverExtensionAbility } from '@kit.DriverDevelopmentKit';
import { Want } from '@kit.AbilityKit';

class DriverExt extends DriverExtensionAbility {
  async onDisconnect(want: Want) {
    console.info(`onDisconnect, want: ${want.abilityName}`);
    // Call the asynchronous function.
  }
}
```

## onDump

```TypeScript
onDump(params: Array<string>): Array<string>
```

Dumps client information. It is recommended that developers don't DUMP sensitive information.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-DriverExtensionAbility-onDump(params: Array<string>): Array<string>--><!--Device-DriverExtensionAbility-onDump(params: Array<string>): Array<string>-End-->

**System capability:** SystemCapability.Driver.ExternalDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | Array&lt;string&gt; | Yes | Array of dump command parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | String array containing the dumped client information. |

**Examples**

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

Called when a DriverExtensionAbility is created to initialize the service logic.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-DriverExtensionAbility-onInit(want: Want): void--><!--Device-DriverExtensionAbility-onInit(want: Want): void-End-->

**System capability:** SystemCapability.Driver.ExternalDevice

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want information related to this DriverExtensionAbility, including the ability name and bundle name. |

**Examples**

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

Called when this DriverExtensionAbility is destroyed to clear resources.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-DriverExtensionAbility-onRelease(): void--><!--Device-DriverExtensionAbility-onRelease(): void-End-->

**System capability:** SystemCapability.Driver.ExternalDevice

**Examples**

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

Context of the **DriverExtension**. This context is inherited from **ExtensionContext**.

**Type:** [DriverExtensionContext](arkts-driverdevelopment-driverextensioncontext-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-DriverExtensionAbility-context: DriverExtensionContext--><!--Device-DriverExtensionAbility-context: DriverExtensionContext-End-->

**System capability:** SystemCapability.Driver.ExternalDevice

## Appendix

DriverExtensionAbility does not support referencing the following modules.

| Kit | Module |
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
| Core File Kit | [@ohos.filemanagement.userFileManager](../../apis-core-file-kit/arkts-apis/arkts-corefile-filemanagement-userfilemanager.md) |
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
| Basic Services Kit | [@ohos.settings](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-settings.md) |
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
