# UkeyAuthExtensionAbility

```TypeScript
declare class UkeyAuthExtensionAbility extends ExtensionAbility
```

UkeyAuthExtensionAbility是用于UKey认证UI显示的ExtensionAbility组件。它继承自[ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md)。您可以实现此类来提供UKey认证UI。UkeyAuthExtensionAbility的UI通过宿主应用启动的[UIExtensionContentSession](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md)进行显示。与UIExtensionAbility不同，UkeyAuthExtensionAbility不提供onForeground和onBackground生命周期回调。仅被授予ohos.permission.START_SYSTEM_DIALOG权限的应用可以启动它。

**继承/实现关系：** UkeyAuthExtensionAbility extends [ExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-extensionability-extensionability-c.md)

**起始版本：** 26.0.1

<!--Device-unnamed-declare class UkeyAuthExtensionAbility extends ExtensionAbility--><!--Device-unnamed-declare class UkeyAuthExtensionAbility extends ExtensionAbility-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## ExtensionAbility使用限制

为保障系统安全性和稳定性，防止UkeyAuthExtensionAbility滥用系统资源，系统对其能力进行管控，不支持部分模块的引用，详情请参考[附录](#附录)。

## 导入模块

```TypeScript
import { UkeyAuthExtensionAbility } from '@kit.DeviceCertificateKit';
```

## onCreate

```TypeScript
onCreate(launchParam: AbilityConstant.LaunchParam): void
```

当UkeyAuthExtensionAbility实例创建时调用。您可以在此回调中执行初始化逻辑（例如定义变量和加载资源）。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UkeyAuthExtensionAbility-onCreate(launchParam: AbilityConstant.LaunchParam): void--><!--Device-UkeyAuthExtensionAbility-onCreate(launchParam: AbilityConstant.LaunchParam): void-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| launchParam | [AbilityConstant.LaunchParam](../../apis-ability-kit/arkts-apis/arkts-ability-abilityconstant-launchparam-i.md) | 是 | 应用启动参数，包括应用启动原因和上次应用退出原因。 |

## onDestroy

```TypeScript
onDestroy(): void | Promise<void>
```

当UkeyAuthExtensionAbility被销毁时调用。您可以在此生命周期中清除资源并保存数据。此API同步返回结果或使用Promise返回结果。**onDestroy()**生命周期回调执行后，应用可能退出。因此，**onDestroy()**中的异步函数（例如异步写入数据库）可能无法执行。建议使用Promise进行异步回调以避免此类问题。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UkeyAuthExtensionAbility-onDestroy(): void | Promise<void>--><!--Device-UkeyAuthExtensionAbility-onDestroy(): void | Promise<void>-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## onSessionCreate

```TypeScript
onSessionCreate(want: Want, session: UIExtensionContentSession): void
```

当UIExtensionContentSession实例创建时调用。您可以在此回调中通过UIExtensionContentSession实例加载页面。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UkeyAuthExtensionAbility-onSessionCreate(want: Want, session: UIExtensionContentSession): void--><!--Device-UkeyAuthExtensionAbility-onSessionCreate(want: Want, session: UIExtensionContentSession): void-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 启动UkeyAuthExtensionAbility时调用方传递的数据。 |
| session | [UIExtensionContentSession](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) | 是 | UIExtensionContentSession实例。 |

## onSessionDestroy

```TypeScript
onSessionDestroy(session: UIExtensionContentSession): void
```

当UIExtensionContentSession被销毁时调用。它通知应用UIExtensionContentSession实例不再可用。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UkeyAuthExtensionAbility-onSessionDestroy(session: UIExtensionContentSession): void--><!--Device-UkeyAuthExtensionAbility-onSessionDestroy(session: UIExtensionContentSession): void-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| session | [UIExtensionContentSession](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md) | 是 | UIExtensionContentSession实例。 |

## context

```TypeScript
context: UkeyAuthExtensionContext
```

UkeyAuthExtensionAbility的上下文。

**类型：** [UkeyAuthExtensionContext](arkts-devicecertificate-security-ukeyauthextensioncontext-ukeyauthextensioncontext-c.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UkeyAuthExtensionAbility-context: UkeyAuthExtensionContext--><!--Device-UkeyAuthExtensionAbility-context: UkeyAuthExtensionContext-End-->

**系统能力：** SystemCapability.Security.CertificateManagerDialog

## 附录

UkeyAuthExtensionAbility不支持以下模块的引用。

| Kit | 模块 |
| --- | --- |
| Ads Kit | [@ohos.advertising.AdComponent](../../apis-ads-kit/arkts-apis/arkts-ads-advertising-adcomponent.md) |
| Ads Kit | [@ohos.advertising.AdsServiceExtensionAbility](../../apis-ads-kit/arkts-apis/arkts-ads-advertising-adsserviceextensionability.md) |
| Ads Kit | [@ohos.advertising.AutoAdComponent](../../apis-ads-kit/arkts-apis/arkts-ads-advertising-autoadcomponent.md) |
| Ads Kit | [@ohos.advertising](../../apis-ads-kit/arkts-apis/arkts-ads-advertising.md) |
| Basic Services Kit | [ai.intelligentVoice](../../apis-basic-services-kit/arkts-apis/arkts-ai-intelligentvoice.md) |
| Mind Spore Lite Kit | [ai.mindSporeLite](../../apis-mind-spore-lite-kit/arkts-apis/arkts-ai-mindsporelite.md) |
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
| Media Library Kit | [multimedia.movingphotoview](../../apis-media-library-kit/arkts-apis/arkts-multimedia-movingphotoview.md) |
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
| Basic Services Kit | [screenLock](../../apis-basic-services-kit/arkts-apis/arkts-screenlock.md) |
| ArkUI | [@ohos.screenshot](../../apis-arkui/arkts-apis/arkts-arkui-screenshot.md) |
| Basic Services Kit | [settings](../../apis-basic-services-kit/arkts-apis/arkts-settings.md) |
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
