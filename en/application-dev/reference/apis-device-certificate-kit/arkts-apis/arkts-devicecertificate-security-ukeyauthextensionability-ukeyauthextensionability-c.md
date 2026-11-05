# UkeyAuthExtensionAbility

```TypeScript
declare class UkeyAuthExtensionAbility extends ExtensionAbility
```

UkeyAuthExtensionAbility is an ExtensionAbility component for UKey authentication UI display. It inherits from [ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md). You can implement this class to provide UKey authentication UI. The UI of a UkeyAuthExtensionAbility is displayed through a [UIExtensionContentSession](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) started by the host application. Unlike the UIExtensionAbility, the UkeyAuthExtensionAbility does not provide onForeground and onBackground lifecycle callbacks. Only applications granted ohos.permission.START_SYSTEM_DIALOG can start it.

**Inheritance/Implementation:** UkeyAuthExtensionAbility extends [ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md)

**Since:** 26.0.1

<!--Device-unnamed-declare class UkeyAuthExtensionAbility extends ExtensionAbility--><!--Device-unnamed-declare class UkeyAuthExtensionAbility extends ExtensionAbility-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## ExtensionAbility Usage Restrictions

To ensure system security and stability, UkeyAuthExtensionAbility is restricted from abusing system resources. The system controls its capabilities and does not support referencing some modules. For details, see [Appendix](#appendix).

## Modules to Import

```TypeScript
import { UkeyAuthExtensionAbility } from '@kit.DeviceCertificateKit';
```

## onCreate

```TypeScript
onCreate(launchParam: AbilityConstant.LaunchParam): void
```

Called when a UkeyAuthExtensionAbility instance is created. You can execute initialization logic (such as defining variables and loading resources) within this callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UkeyAuthExtensionAbility-onCreate(launchParam: AbilityConstant.LaunchParam): void--><!--Device-UkeyAuthExtensionAbility-onCreate(launchParam: AbilityConstant.LaunchParam): void-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| launchParam | [AbilityConstant.LaunchParam](../../apis-ability-kit/arkts-apis/arkts-ability-abilityconstant-launchparam-i.md) | Yes | Parameters for application launch, including the reason for application launch and the reason for the last application exit. |

## onDestroy

```TypeScript
onDestroy(): void | Promise<void>
```

Called when a UkeyAuthExtensionAbility is destroyed. You can clear resources and save data during this lifecycle. This API returns the result synchronously or uses a promise to return the result. After the **onDestroy()** lifecycle callback is executed, the application may exit. Consequently, the asynchronous function (for example, asynchronously writing data to the database) in **onDestroy()** may fail to be executed. Using a Promise for asynchronous callback is recommended to prevent such issues.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UkeyAuthExtensionAbility-onDestroy(): void | Promise<void>--><!--Device-UkeyAuthExtensionAbility-onDestroy(): void | Promise<void>-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## onSessionCreate

```TypeScript
onSessionCreate(want: Want, session: UIExtensionContentSession): void
```

Called when a UIExtensionContentSession instance is created. You can load a page through the UIExtensionContentSession instance within this callback.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UkeyAuthExtensionAbility-onSessionCreate(want: Want, session: UIExtensionContentSession): void--><!--Device-UkeyAuthExtensionAbility-onSessionCreate(want: Want, session: UIExtensionContentSession): void-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Data passed by the caller when launching the UkeyAuthExtensionAbility. |
| session | [UIExtensionContentSession](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) | Yes | UIExtensionContentSession instance. |

## onSessionDestroy

```TypeScript
onSessionDestroy(session: UIExtensionContentSession): void
```

Called when a UIExtensionContentSession is destroyed. It informs applications that the UIExtensionContentSession instance is no longer available for use.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UkeyAuthExtensionAbility-onSessionDestroy(session: UIExtensionContentSession): void--><!--Device-UkeyAuthExtensionAbility-onSessionDestroy(session: UIExtensionContentSession): void-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| session | [UIExtensionContentSession](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) | Yes | UIExtensionContentSession instance. |

## context

```TypeScript
context: UkeyAuthExtensionContext
```

Context of the UkeyAuthExtensionAbility.

**Type:** [UkeyAuthExtensionContext](arkts-devicecertificate-security-ukeyauthextensioncontext-ukeyauthextensioncontext-c.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-UkeyAuthExtensionAbility-context: UkeyAuthExtensionContext--><!--Device-UkeyAuthExtensionAbility-context: UkeyAuthExtensionContext-End-->

**System capability:** SystemCapability.Security.CertificateManagerDialog

## Appendix

UkeyAuthExtensionAbility does not support referencing the following modules.

| Kit | Module |
| --- | --- |
| Ads Kit | [@ohos.advertising.AdComponent](../../apis-ads-kit/arkts-apis/arkts-ads-advertising-adcomponent.md) |
| Ads Kit | [@ohos.advertising.AdsServiceExtensionAbility](../../apis-ads-kit/arkts-apis/arkts-ads-advertising-adsserviceextensionability.md) |
| Ads Kit | [@ohos.advertising.AutoAdComponent](../../apis-ads-kit/arkts-apis/arkts-ads-advertising-autoadcomponent.md) |
| Ads Kit | [@ohos.advertising](../../apis-ads-kit/arkts-apis/arkts-ads-advertising.md) |
| Basic Services Kit | [@ohos.ai.intelligentVoice](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-ai-intelligentvoice.md) |
| MindSpore Lite Kit | [@ohos.ai.mindSporeLite](../../apis-mind-spore-lite-kit/arkts-apis/arkts-mindsporelite-ai-mindsporelite.md) |
| Form Kit | [@ohos.app.form.formAgent](../../apis-form-kit/arkts-apis/arkts-form-app-form-formagent.md) |
| Form Kit | [@ohos.app.form.formBindingData](../../apis-form-kit/arkts-apis/arkts-form-app-form-formbindingdata.md) |
| Form Kit | [@ohos.app.form.FormEditExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formeditextensionability.md) |
| Form Kit | [@ohos.app.form.FormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability.md) |
| Form Kit | [@ohos.app.form.formHost](../../apis-form-kit/arkts-apis/arkts-form-app-form-formhost.md) |
| Form Kit | [@ohos.app.form.formInfo](../../apis-form-kit/arkts-apis/arkts-form-app-form-forminfo.md) |
| Form Kit | [@ohos.app.form.formObserver](../../apis-form-kit/arkts-apis/arkts-form-app-form-formobserver.md) |
| Form Kit | [@ohos.app.form.formProvider](../../apis-form-kit/arkts-apis/arkts-form-app-form-formprovider.md) |
| Form Kit | [@ohos.app.form.LiveFormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-liveformextensionability.md) |
| ArkUI | [@ohos.atomicservice.AtomicServiceNavigation](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicservicenavigation.md) |
| ArkUI | [@ohos.atomicservice.AtomicServiceSearch](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicservicesearch.md) |
| ArkUI | [@ohos.atomicservice.AtomicServiceTabs](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicservicetabs.md) |
| ArkUI | [@ohos.atomicservice.AtomicServiceWeb](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-atomicserviceweb.md) |
| ArkUI | [@ohos.atomicservice.HalfScreenLaunchComponent](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-halfscreenlaunchcomponent.md) |
| ArkUI | [@ohos.atomicservice.InterstitialDialogAction](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-interstitialdialogaction.md) |
| ArkUI | [@ohos.atomicservice.NavPushPathHelper](../../apis-arkui/arkts-apis/arkts-arkui-atomicservice-navpushpathhelper.md) |
| Connectivity Kit | [@ohos.bluetooth.a2dp](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-a2dp.md) |
| Connectivity Kit | [@ohos.bluetooth.access](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-access.md) |
| Connectivity Kit | [@ohos.bluetooth.baseProfile](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-baseprofile.md) |
| Connectivity Kit | [@ohos.bluetooth.ble](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-ble.md) |
| Connectivity Kit | [@ohos.bluetooth.common](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-common.md) |
| Connectivity Kit | [@ohos.bluetooth.connection](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-connection.md) |
| Connectivity Kit | [@ohos.bluetooth.constant](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-constant.md) |
| Connectivity Kit | [@ohos.bluetooth](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth.md) |
| Connectivity Kit | [@ohos.bluetooth.hfp](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-hfp.md) |
| Connectivity Kit | [@ohos.bluetooth.hid](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-hid.md) |
| Connectivity Kit | [@ohos.bluetoothManager](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetoothmanager.md) |
| Connectivity Kit | [@ohos.bluetooth.map](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-map.md) |
| Connectivity Kit | [@ohos.bluetooth.opp](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-opp.md) |
| Connectivity Kit | [@ohos.bluetooth.pan](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-pan.md) |
| Connectivity Kit | [@ohos.bluetooth.pbap](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-pbap.md) |
| Connectivity Kit | [@ohos.bluetooth.socket](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-socket.md) |
| Connectivity Kit | [@ohos.bluetooth.wearDetection](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-bluetooth-weardetection.md) |
| Calendar Kit | [@ohos.calendarManager](../../apis-calendar-kit/arkts-apis/arkts-calendar-calendarmanager.md) |
| Connectivity Kit | [@ohos.connectedTag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-connectedtag.md) |
| Contacts Kit | [@ohos.contact](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact.md) |
| Ability Kit | [@ohos.distributedBundle](../../apis-ability-kit/arkts-apis/arkts-ability-distributedbundle.md) |
| Distributed Service Kit | [@ohos.distributedDeviceManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager.md) |
| Distributed Service Kit | [@ohos.distributedHardware.deviceManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributedhardware-devicemanager.md) |
| Distributed Service Kit | [@ohos.distributedHardware.hardwareManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributedhardware-hardwaremanager.md) |
| Mechanic Kit | [@ohos.distributedHardware.mechanicManager](../../apis-mechanic-kit/arkts-apis/arkts-mechanic-distributedhardware-mechanicmanager.md) |
| Ability Kit | [@ohos.distributedMissionManager](../../apis-ability-kit/arkts-apis/arkts-ability-distributedmissionmanager.md) |
| Distributed Service Kit | [@ohos.distributedsched.abilityConnectionManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributedsched-abilityconnectionmanager.md) |
| Distributed Service Kit | [@ohos.distributedsched.linkEnhance](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributedsched-linkenhance.md) |
| Distributed Service Kit | [@ohos.distributedsched.proxyChannelManager](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributedsched-proxychannelmanager.md) |
| Data Protection Kit | [@ohos.dlpPermission](../../apis-data-protection-kit/arkts-apis/arkts-dataprotection-dlppermission.md) |
| MDM Kit | [@ohos.enterprise.accountManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-accountmanager.md) |
| MDM Kit | [@ohos.enterprise.adminManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-adminmanager.md) |
| MDM Kit | [@ohos.enterprise.applicationManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-applicationmanager.md) |
| MDM Kit | [@ohos.enterprise.bluetoothManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-bluetoothmanager.md) |
| MDM Kit | [@ohos.enterprise.browser](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-browser.md) |
| MDM Kit | [@ohos.enterprise.bundleManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-bundlemanager.md) |
| MDM Kit | [@ohos.enterprise.common](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-common.md) |
| MDM Kit | [@ohos.enterprise.dateTimeManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-datetimemanager.md) |
| MDM Kit | [@ohos.enterprise.deviceControl](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-devicecontrol.md) |
| MDM Kit | [@ohos.enterprise.deviceInfo](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-deviceinfo.md) |
| MDM Kit | [@ohos.enterprise.deviceSettings](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-devicesettings.md) |
| MDM Kit | [@ohos.enterprise.EnterpriseAdminExtensionAbility](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-enterpriseadminextensionability.md) |
| MDM Kit | [@ohos.enterprise.locationManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-locationmanager.md) |
| MDM Kit | [@ohos.enterprise.networkManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-networkmanager.md) |
| MDM Kit | [@ohos.enterprise.restrictions](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-restrictions.md) |
| MDM Kit | [@ohos.enterprise.securityManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-securitymanager.md) |
| MDM Kit | [@ohos.enterprise.systemManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-systemmanager.md) |
| MDM Kit | [@ohos.enterprise.telephonyManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-telephonymanager.md) |
| MDM Kit | [@ohos.enterprise.usbManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-usbmanager.md) |
| MDM Kit | [@ohos.enterprise.wifiManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-wifimanager.md) |
| Location Kit | [@ohos.geolocation](../../apis-location-kit/arkts-apis/arkts-location-geolocation.md) |
| Location Kit | [@ohos.geoLocationManager](../../apis-location-kit/arkts-apis/arkts-location-geolocationmanager.md) |
| ArkUI | [@ohos.mediaquery](../../apis-arkui/arkts-apis/arkts-arkui-mediaquery.md) |
| arkui | [mediaquery.static](../../apis-arkui/arkts-apis/arkts-mediaquery-static.md) |
| Audio Kit | [@ohos.multimedia.audio](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audio.md) |
| Audio Kit | [@ohos.multimedia.audioHaptic](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audiohaptic.md) |
| AVSession Kit | [@ohos.multimedia.avCastPicker](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avcastpicker.md) |
| AVSession Kit | [@ohos.multimedia.avCastPickerParam](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avcastpickerparam.md) |
| Avsession Kit | [multimedia.avCastPicker.static](../../apis-avsession-kit/arkts-apis/arkts-multimedia-avcastpicker-static.md) |
| AVSession Kit | [@ohos.multimedia.avInputCastPicker](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avinputcastpicker.md) |
| Avsession Kit | [multimedia.avInputCastPicker.static](../../apis-avsession-kit/arkts-apis/arkts-multimedia-avinputcastpicker-static.md) |
| AVSession Kit | [@ohos.multimedia.avsession](../../apis-avsession-kit/arkts-apis/arkts-avsession-multimedia-avsession.md) |
| Audio Kit | [@ohos.multimedia.avVolumePanel](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-avvolumepanel.md) |
| Audio Kit | [multimedia.avVolumePanel.static](../../apis-audio-kit/arkts-apis/arkts-multimedia-avvolumepanel-static.md) |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Camera Kit | [@ohos.multimedia.cameraPicker](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camerapicker.md) |
| DRM Kit | [@ohos.multimedia.drm](../../apis-drm-kit/arkts-apis/arkts-drm-multimedia-drm.md) |
| Image Kit | [@ohos.multimedia.image](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) |
| Media Kit | [@ohos.multimedia.media](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media.md) |
| Media Library Kit | [@ohos.multimedia.movingphotoview](../../apis-media-library-kit/arkts-components/arkts-medialibrary-multimedia-movingphotoview.md) |
| Image Kit | [@ohos.multimedia.sendableImage](../../apis-image-kit/arkts-apis/arkts-image-multimedia-sendableimage.md) |
| Audio Kit | [@ohos.multimedia.systemSoundManager](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-systemsoundmanager.md) |
| Image Kit | [@ohos.multimedia.videoProcessingEngine](../../apis-image-kit/arkts-apis/arkts-image-multimedia-videoprocessingengine.md) |
| Network Kit | [@ohos.net.connection](../../apis-network-kit/arkts-apis/arkts-network-net-connection.md) |
| Network Kit | [@ohos.net.eap](../../apis-network-kit/arkts-apis/arkts-network-net-eap.md) |
| Network Kit | [@ohos.net.ethernet](../../apis-network-kit/arkts-apis/arkts-network-net-ethernet.md) |
| Network Kit | [@ohos.net.http](../../apis-network-kit/arkts-apis/arkts-network-net-http.md) |
| Network Kit | [@ohos.net.mdns](../../apis-network-kit/arkts-apis/arkts-network-net-mdns.md) |
| Network Kit | [@ohos.net.netFirewall](../../apis-network-kit/arkts-apis/arkts-network-net-netfirewall.md) |
| Network Kit | [@ohos.net.networkSecurity](../../apis-network-kit/arkts-apis/arkts-network-net-networksecurity.md) |
| Network Kit | [@ohos.net.policy](../../apis-network-kit/arkts-apis/arkts-network-net-policy.md) |
| Network Kit | [@ohos.net.sharing](../../apis-network-kit/arkts-apis/arkts-network-net-sharing.md) |
| Network Kit | [@ohos.net.statistics](../../apis-network-kit/arkts-apis/arkts-network-net-statistics.md) |
| Network Kit | [@ohos.net.vpn](../../apis-network-kit/arkts-apis/arkts-network-net-vpn.md) |
| Network Kit | [@ohos.net.vpnExtension](../../apis-network-kit/arkts-apis/arkts-network-net-vpnextension.md) |
| Network Kit | [@ohos.net.webSocket](../../apis-network-kit/arkts-apis/arkts-network-net-websocket.md) |
| Connectivity Kit | [@ohos.nfc.cardEmulation](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-cardemulation.md) |
| Connectivity Kit | [@ohos.nfc.controller](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-controller.md) |
| Connectivity Kit | [@ohos.nfc.tag](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-tag.md) |
| Basic Services Kit | [@ohos.pasteboard](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-pasteboard.md) |
| ArkUI | [@ohos.PiPWindow](../../apis-arkui/arkts-apis/arkts-arkui-pipwindow.md) |
| Basic Services Kit | [@ohos.scan](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-scan.md) |
| Basic Services Kit | [@ohos.screenLock](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-screenlock.md) |
| ArkUI | [@ohos.screenshot](../../apis-arkui/arkts-apis/arkts-arkui-screenshot.md) |
| Basic Services Kit | [@ohos.settings](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-settings.md) |
| Telephony Kit | [@ohos.telephony.call](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-call.md) |
| Telephony Kit | [@ohos.telephony.data](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-data.md) |
| Telephony Kit | [@ohos.telephony.esim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-esim.md) |
| Telephony Kit | [@ohos.telephony.observer](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-observer.md) |
| Telephony Kit | [@ohos.telephony.radio](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-radio.md) |
| Telephony Kit | [@ohos.telephony.sim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sim.md) |
| Telephony Kit | [@ohos.telephony.sms](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sms.md) |
| Telephony Kit | [@ohos.telephony.vcard](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-vcard.md) |
| ArkTS | [@ohos.transfer](../../apis-arkts/arkts-apis/arkts-arkts-transfer.md) |
| Basic Services Kit | [@ohos.wallpaper](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-wallpaper.md) |
| Basic Services Kit | [@ohos.WallpaperExtensionAbility](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-wallpaperextensionability.md) |
| Ability Kit | [@ohos.wantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent.md) |
| ArkWeb | [@ohos.web.netErrorList](../../apis-arkweb/arkts-apis/arkts-arkweb-web-neterrorlist.md) |
| arkweb | [web.netErrorList.static](../../apis-arkweb/arkts-apis/arkts-web-neterrorlist-static.md) |
| ArkWeb | [@ohos.web.WebNativeMessagingExtensionAbility](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webnativemessagingextensionability.md) |
| arkweb | [web.WebNativeMessagingExtensionAbility.static](../../apis-arkweb/arkts-apis/arkts-web-webnativemessagingextensionability-static.md) |
| ArkWeb | [@ohos.web.WebNativeMessagingExtensionContext](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webnativemessagingextensioncontext.md) |
| arkweb | [web.WebNativeMessagingExtensionContext.static](../../apis-arkweb/arkts-apis/arkts-web-webnativemessagingextensioncontext-static.md) |
| ArkWeb | [@ohos.web.webNativeMessagingExtensionManager](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webnativemessagingextensionmanager.md) |
| arkweb | [web.webNativeMessagingExtensionManager.static](../../apis-arkweb/arkts-apis/arkts-web-webnativemessagingextensionmanager-static.md) |
| ArkWeb | [@ohos.web.webview](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webview.md) |
| arkweb | [web.webview.static](../../apis-arkweb/arkts-apis/arkts-web-webview-static.md) |
| Connectivity Kit | [@ohos.wifi](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifi.md) |
| Connectivity Kit | [@ohos.wifiext](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifiext.md) |
| Connectivity Kit | [@ohos.wifiManager](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifimanager.md) |
| Connectivity Kit | [@ohos.wifiManagerExt](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-wifimanagerext.md) |
