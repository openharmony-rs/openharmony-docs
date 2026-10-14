# OpenHarmony 7.0 Release

<!-- md-trans-meta sourceCommit=1a8f0e29e1613d776fbcf3f45c154ce0bec32757 translatedAt=2026-09-17T04:10:04.342Z pushedAt=2026-09-17T12:04:16.953Z -->

## Copyright and License Notice

The contributions to this project are licensed to the OpenAtom Foundation under the ***Developer Certificate of Origin (DCO)***. This project is a collective work composed of many open source software components, and the copyright of this collective work is owned by the OpenAtom Foundation. The OpenAtom Foundation grants you a license to this collective work under the Apache License 2.0 (hereinafter referred to as **Apache 2.0**).

You may use this project only in compliance with Apache 2.0 and the corresponding open source licenses applicable to the open source software components contained in this project. You can obtain a copy of Apache 2.0 at the following URL:
**[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0#/session/_blank)**

Unless required by applicable law or agreed to in writing, software distributed under the applicable open source license is provided on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. For the specific grants and restrictions under the applicable open source license, see the original text of the license.

## Version Overview

OpenHarmony 7.0 Release further enhances system support and application development capabilities based on OpenHarmony 6.1 Release:

- At the system level, support is added for development boards powered by the UNISOC P7885 chipset. Lightweight systems can also be adapted for a smaller footprint to reduce resource usage.

  > **NOTE**

  > The new system-level capabilities were first released in OpenHarmony 6.1 LTS.

- In terms of the application framework, more fine-grained app control is supported. For example, you can obtain the Ability exit reason and AbilityStage startup and loading information. Modular object capabilities based on ModularObjectExtensionAbility and self-distributed plugin management are added. ArkUI introduces multiple V2 components, lazy-loading layout components, smart gestures, system materials, responsive environment variables, and more to further enhance UI interactions. It also supports dynamic layout containers, nested scrolling for Tabs, and global reuse of custom components. ArkWeb further enhances web page control capabilities, with its kernel upgraded to Chromium 144 and support added for URL allowlist control, web security configuration, and more. The media framework adds capabilities such as audio PCM processing and playback, ad insertion, offline caching and download, screen recording pause and resume, and enhanced audio device management. Other new capabilities include compression and decompression, window mode settings, configurable parameters for multithreading detection, enhanced enterprise account and app management, custom WebSocket ports, memory export listeners, and unified SDK support.

The following describes the new capabilities.

### System

The standard system adds support for the "Unisoc P7885 chip development board", which supports the following capabilities:

- Supports 5G cellular communication, providing network registration, calling, SMS, and data functions.

- Supports unified rendering.

- Supports GNSS satellite status information reporting, and can identify and report satellite data such as GPS, BeiDou, and GLONASS.

- Adapts the SparkLink driver, supports SparkLink SLE 1.0, and supports SparkLink pairing, connection, and data transmission.

- Onboard adaptation of six types of sensors: accelerometer, gyroscope, magnetometer, proximity sensor, ambient light sensor, and motor.

- Onboard 36-pin standard PCI-E interface, with the external board supporting USB + Gigabit Ethernet interfaces or other standard PCI-E cards.

The preceding capabilities are already supported in OpenHarmony 6.1 LTS.

### Ability Kit

  - Provides C APIs for declaring a ModularObject dispatcher, offering cross-process deferred binding invocation capabilities based on type library metadata. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-ability-kit/capi-modular-object-dispatcher-h.md))

  - Provides C APIs for declaring a ModularObjectExtensionAbility instance, including capabilities such as registering lifecycle callback functions and obtaining the context. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-ability-kit/capi-modular-object-extension-ability-h.md))

  - Provides C APIs for declaring the ModularObjectExtensionAbility context, including functions such as starting a UIAbility, destroying the ModularObjectExtensionAbility itself, and creating and destroying IPC objects. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-ability-kit/capi-modular-object-extension-context-h.md))

  - Provides C APIs for declaring the management of ModularObjectExtensionAbility, including capabilities such as querying ModularObjectExtensionAbility information, connecting, and disconnecting. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-ability-kit/capi-modular-object-extension-manager-h.md))

- Introduces C APIs for NativeAbility data information, used to obtain information such as the Ability instance ID, Ability name, and napi_env. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-ability-kit/capi-native-ability-wrapper-h.md))

- Introduces C APIs for declaring connection options of ExtensionAbility, providing callback interfaces for successful connection, disconnection, and connection failure. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-ability-kit/capi-connect-options-h.md))

- Adds the capability to define auto-fill request information, allowing applications to define the type of information to be auto-filled. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-ability-kit/js-apis-inner-application-autoFillRequest.md))

- Bundle management introduces the pluginBundleManager module, which provides applications with the capability to manage self-distributed plugins, including installing and uninstalling local plugins. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-ability-kit/js-apis-pluginBundleManager.md))

- The information field of the last Ability exit adds support for obtaining the exit reason. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#lastexitdetailinfo18))

- The AbilityStage context adds the launchElement field, which is used to inform the application of the Ability being loaded when AbilityStage calls onCreate, so that resources can be loaded dynamically. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-ability-kit/js-apis-inner-application-abilityStageContext.md#properties))

- The AbilityStage component manager adds a callback for when AbilityStage is about to create the first Ability ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#onabouttocreateability24)), as well as a callback for when the process starts from an application snapshot ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-ability-kit/js-apis-app-ability-abilityStage.md#onlaunchfromhypersnap24)).

- Adds support for obtaining the application name with a specified bundle name and clone index. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetapplicationlabel))

- Adds C APIs for managing ModularObjectExtensionAbility, providing capabilities such as querying ModularObjectExtensionAbility information, connecting, and disconnecting. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-ability-kit/capi-modular-object-extension-manager-h.md))

### Distributed Data Management

- The data sharing capability adds support for publishing configurations of multiple value types for sharing across applications. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkdata/js-apis-data-dataShare.md#publish20))

- Adds a synchronous method for creating or opening an existing relational database. The synchronous method blocks the thread until an RdbStore is obtained. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkdata/arkts-apis-data-relationalStore-f.md#relationalstoregetrdbstoresync24))

### Graphics

- The font drawing capability of the drawing module adds support for obtaining the outline path of text, and simultaneously supports the font fallback capability. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-Font.md#gettextpathwithfallback))

- Adds support for applying a high dynamic range (HDR) imaging brightening effect to component content. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkgraphics2d/js-apis-uiEffect.md#hdrbrightnessratio24))

- Adds support for the AIHDR format of videos. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkgraphics2d/js-apis-hdrCapability.md#hdrformat))

- The drawing module adds a class for processing coordinate points, supporting negation of coordinate points and setting of offsets. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkgraphics2d/arkts-apis-graphics-drawing-PointUtils.md))

### Image

- Introduces the [WebP image metadata class](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-image-kit/arkts-apis-image-WebPMetadata.md), [GIF image metadata class](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-image-kit/arkts-apis-image-GifMetadata.md), [JFIF image metadata class](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-image-kit/arkts-apis-image-JfifMetadata.md), [TIFF image metadata class](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-image-kit/arkts-apis-image-TiffMetadata.md), [PNG image metadata class](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-image-kit/arkts-apis-image-PngMetadata.md), and [AVIS image metadata class](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-image-kit/arkts-apis-image-AvisMetadata.md), which are used to store metadata of images in the corresponding formats.

- Introduces [Extensible Metadata Platform (XMP) metadata](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-image-kit/arkts-apis-image-XMPMetadata.md).

### ArkUI

- New multiple components implemented based on state management (V2), including [ChipV2](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipV2.md), [ChipGroupV2](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipGroupV2.md), [CounterV2](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-CounterV2.md), [PopupV2](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-PopupV2.md), [SwipeRefresherV2](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SwipeRefresherV2.md), and [TreeViewV2](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-TreeViewV2.md).

- New smart gesture capabilities ([Guide](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/ui/arkts-common-events-smartgesture-event.md)):

  - New smart gesture APIs, providing capabilities for smart gesture enabling, listening, selected state control, and dynamic decision-making of smart gesture behavior. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkts-apis-uicontext-smartgesturecontroller.md))

  - Interaction attributes add response to smart gestures. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-smart-gesture-shortcut.md))

- Scrolling and sliding components add the lazy-loading waterfall flow layout component [LazyVWaterFlowLayout](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ts-container-lazyvwaterflowlayout.md), the lazy-loading vertical linear layout component [LazyColumnLayout](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ts-container-lazycolumnlayout.md), and the lazy-loading dynamic layout container component [LazyDynamicLayout](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ts-container-lazydynamiclayout.md).

- Responsive environment variable components add the environment variable container [WithEnv](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ts-container-with-env.md) and the custom environment variable [@CustomEnv](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ts-custom-env-property.md).

- New DatePickerComponent component for selecting the date (year, month, day) and time (hour, minute, second). ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-DatePickerComponent.md))

- New SelectionContainer component for providing cross-node text selection, copy, and menu extension capabilities for multiple text nodes. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-selectioncontainer.md))

- New support for setting debugging labels to help developers distinguish similar nodes and improve development and analysis debugging efficiency. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-inspector-label.md))

- The ChipGroup component adds support for configuring the system material background in the normal and activated states through backgroundSystemMaterial and activatedBackgroundSystemMaterial. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-ChipGroup.md#example-6-setting-system-material-style))

- The SelectionMenu component adds support for configuring the system material of the menu background panel through backgroundSystemMaterial. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SelectionMenu.md#example-3-setting-the-background-material))

- The DatePickerDialog popup component adds the systemMaterial configuration item to support the system material effect. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ts-methods-datepicker-dialog.md#datepickerdialogoptions))

- The C API introduces immersive material types and API declarations. ([C API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-native-material-h.md))

- The component dynamic attributes add the hovered state style. ([ArkTS API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#applyhoveredattribute), [C API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-common-attributes-h.md#arkui_uistate))

- Text components add support for the tail indent attribute (tailIndents), including: the Text component ([ArkTS API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-text.md#tailindents), [C API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-native-node-h-nodeattributetype-text.md#node_text_tail_indents)) and styled strings ([ArkTS API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ts-universal-styled-string.md#properties-9), [C API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-styled-string-h.md#oh_arkui_paragraphstyle_settailindents))

- The custom component lifecycle adds the [@ComponentActive](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#componentactive) decorator for the transition of a component from the inactive state to the active state, and the [@ComponentInactive](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md#componentinactive) decorator for the transition of a component from the active state to the inactive state. ([Guide](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/ui/state-management/arkts-custom-components-new-lifecycle.md#active-and-inactive-lifecycles-of-a-custom-component))

- Custom components support cross-Ability migration. ([Guide](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/ui/state-management/arkts-create-custom-components.md#cross-ability-migration-of-custom-components))

- Adds C APIs for multiple components: [OH_ArkUI_DecorationStyleOptions](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-decorationstyleoptions.md), [OH_ArkUI_TextDataDetectorConfig](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md), [OH_ArkUI_TextEditorSelectionMenuOptions](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-texteditorselectionmenuoptions.md), [OH_ArkUI_TextEditorPlaceholderOptions](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-texteditorplaceholderoptions.md), [OH_ArkUI_TextEditorStyledStringController](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-texteditorstyledstringcontroller.md), [OH_ArkUI_TextEditorParagraphStyle](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-texteditorparagraphstyle.md), [OH_ArkUI_ShadowOptions](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-shadowoptions.md), and [OH_ArkUI_TextEditorTextStyle](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-arkui-nativemodule-oh-arkui-texteditortextstyle.md).

- Adds a set of C APIs for styled strings. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-styled-string-h.md#oh_arkui_styledstringkey))

- Supports dispatching events with a competition strategy to the target UI component node. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/js-apis-arkui-builderNode.md#postinputeventwithstrategy24))

- Adds support for obtaining the root node of the page corresponding to a UIContext. ([ArkTS API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getpagerootnode24), [C API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-native-node-h.md#oh_arkui_nativemodule_getpagerootnodehandlebycontext))

- The Text component adds support for obtaining the position information of the nearest character based on coordinates. ([ArkTS API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ts-text-common.md#getcharacterpositionatcoordinate24), [C API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-styled-string-h.md#oh_arkui_textlayoutmanager_getcharacterpositionatcoordinate))

- Adds an asynchronous drag-and-drop notification API that specifies whether to perform a cut or copy operation in the drop behavior ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-drag-and-drop-h.md#oh_arkui_notifysuggesteddropoperation)), and specifies whether to execute the animation of the drop behavior ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-drag-and-drop-h.md#oh_arkui_notifydisabledefaultdropanimation)).

- Adds the onNeedSoftkeyboard callback, which allows developers to configure the soft keyboard to remain open after focus transfer. ([ArkTS API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ts-universal-events-onneedsoftkeyboard.md), [C API Reference - NODE_ON_NEED_SOFTKEYBOARD](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/capi-native-node-h.md#arkui_nodeeventtype))

- The segmented button adds the enableStateAnimation configuration item, which specifies whether to execute a system animation when the bound state variable of selectedIndexes changes. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ohos-arkui-advanced-SegmentButton.md#segmentbutton-1))

- The Tabs component adds support for nested scrolling. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-ts/ts-container-tabs.md#nestedscroll24))

- JS components add a rotation crown event listening API. ([API Reference - ArkUI.Full](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-js/js-components-common-monitorcrownevents.md), [API Reference - ArkUI.Lite](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkui-js-lite/js-lite-common-monitorcrownevents.md))

- Introduces a dynamic layout container component that supports switching between different layout algorithms at runtime without changing the state of child components. ([Guide](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/ui/arkts-layout-development-dynamiclayout.md))

- Introduces global reuse capabilities for custom components, allowing a reuse pool to be configured for specified \@Reusable/\@ReusableV2 reusable components to provide global reuse capabilities. ([Guide](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/ui/state-management/arkts-global-reuse-pool.md))

### Window Management

- Adds support for destroying the page content (UIContent) of a window (WindowStage) on demand. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/arkts-apis-window-WindowStage.md#releaseuicontent24))

- Introduces the flash control window. A flash control window is a small window floating over the home screen or an application UI, providing flexible window management capabilities, including determining whether the device supports the flash control window feature and creating a flash control window controller to start, update, or stop the flash control window. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkui/js-apis-floatView.md))

### ArkWeb

- ArkWeb upgrades the Chromium kernel from version 132 to version 144 based on the upstream community. For details, see [Summary of Differences Between ArkWeb Versions](https://gitcode.com/openharmony-tpc/chromium_src/blob/master/web/ReleaseNote/ArkWeb_132_144.md).

- ArkWeb web requests support the User-Agent Client Hints feature. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkweb/arkts-apis-webview-WebviewController.md#setuseragentclienthintsenabled24))

- ArkWeb introduces a switch for enabling the default context menu, which controls whether the default context menu is enabled. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkweb/arkts-basic-components-web-attributes.md#enabledefaultcontextmenu24))

- Sets a URL allowlist for web pages. Only URLs in the allowlist are allowed to load or redirect; otherwise, they are intercepted and an alert page is displayed. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkweb/arkts-apis-webview-WebviewController.md#seturltrustlist24))

- In the callback for download task completion, adds support for obtaining the original URL of the download item ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkweb/arkts-apis-webview-WebDownloadItem.md#getoriginalurl24)); adds support for obtaining the URL of the referring page ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkweb/arkts-apis-webview-WebDownloadItem.md#getreferrerurl24)).

- Introduces a class for configuring security feature options, used to set security configuration properties for web pages. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-arkweb/arkts-apis-webview-SecurityParams.md))


### Media

**Media Management**

- Adds C APIs that support processing audio PCM data before playback ([C API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setpcmprocessorcallback)), and support setting the maximum amount of data that the callback function can return at a time after audio processing before playback ([C API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-media-kit/capi-avplayer-h.md#oh_avplayer_setpcmprocessormaxlen)).

- Adds ArkTS APIs and C APIs that support pausing and resuming screen recording during the recording process. ([ArkTS API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-media-kit/arkts-apis-media-i.md#avscreencapturestrategy20), [C API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforpause))

- Adds C APIs that support screen recording of all windows of a specified application. ([C API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-media-kit/capi-native-avscreen-capture-base-h.md#oh_capturepickermode))

- Adds a callback function for privacy protection settings to the C APIs, used to respond to privacy protection events captured during screen capture and screen recording. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_setprivacyprotectcallback))

- Adds C API support for obtaining multi-display recording capability information ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_getmultidisplaycapturecapability)), and for selecting multiple displays for recording through DisplayID ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_getmultidisplayidsselected)).

**Audio**

- Introduces the audio device enhancement manager. ([ArkTS API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-audio-kit/arkts-apis-audio-AudioDeviceEnhanceManager.md), [C API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-audio-kit/capi-native-audio-device-enhance-manager-h.md))

- Introduces C/C++-based audio format conversion capabilities. ([Guide](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/media/audio/audio-suite-format-converter.md))

- Audio capture and audio rendering add support for setting independent audio session policies and behavior parameters. ([API Reference - Audio Capture](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-audio-kit/arkts-apis-audio-AudioCapturer.md#setindependentaudiosessionstrategy24), [API Reference - Audio Rendering](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-audio-kit/arkts-apis-audio-AudioRenderer.md#setindependentaudiosessionstrategy24))

- Introduces the OH_MIDI C API, which allows applications to connect to external MIDI devices (such as MIDI keyboards, electronic organs, and MIDI controllers) over USB or Bluetooth BLE. It supports sending and receiving MIDI messages, device enumeration, and hot-plug listening, and can be used in scenarios such as music creation, instrument recording and teaching, and MIDI device control. ([Guide](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/media/audio/midi-overview.md))

- Introduces C APIs that provide declarations for input audio format, output audio format underlying data structures, and format conversion interfaces. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-audio-kit/capi-native-audio-converter-h.md))

**Playback Control Framework**

- Adds support for setting the list of playback speeds supported by an application. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setsupportedplayspeeds))

- Adds support for setting the list of loop modes supported by an application. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setsupportedloopmodes))

- Adds support for setting the list of control types supported by an application. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setmediacentercontroltype))

- Adds the capability to obtain the list of playback speeds supported by an application through AVSessionController. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#getsupportedplayspeeds))

- Adds the capability to obtain the list of loop modes supported by an application through AVSessionController. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#getsupportedloopmodes))

- Adds the capability to obtain the list of control types supported by an application through AVSessionController. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#getmediacentercontroltype))

- Adds the registration of listening events for changes to the playback speed list. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#onsupportedplayspeedschange))

- Adds the registration of listening events for changes to the loop mode list. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#onsupportedloopmodeschange))

- Adds the registration of listening events for changes to the control type list. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSessionController.md#onmediacentercontroltypechanged))

- Adds support for setting the background playback mode. An application can inform the system whether it supports background playback, and the system decides whether to display the live capsule based on this capability. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-AVSession.md#setbackgroundplaymode24))

- The AVSession enums newly define enumerations for extra keys used in different scenarios. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-avsession-kit/arkts-apis-avsession-e.md#extrakey))

**Camera**

- The C API adds the declaration of the metadata object extension concept. ([C API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-camera-kit/capi-metadata-object-ext-h.md))

- Adds support for creating a deferred preview output object, which replaces the ordinary preview output object in the data stream during stream configuration ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#createdeferredpreviewoutput24)). It also supports configuring the surface for deferred preview ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#adddeferredsurface24)).

- Adds a set of professional camera capabilities for photo/video recording modes, including flash, optical image stabilization, exposure, manual focus, ISO sensitivity, and physical aperture invocation and configuration.

**Audio/Video Codec**

- Adds support for encoding and decoding the Cinepak media format. ([Guide](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/media/avcodec/avcodec-support-formats.md#media-codec))

- The H.265 hardware encoder adds support for CBRHQ (constant bitrate high quality mode). ([Guide](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/media/avcodec/video-encoding-configuration-typical-scenarios.md#low-latency-encoding-scenarios))

### File Management

- Adds support for a compression and decompression module, providing applications with data compression and decompression capabilities for scenarios such as file packaging and distribution, reducing storage usage, and accelerating network transmission. ([Guide](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/file-management/archive-overview.md))

- Adds the UNCACHE parameter when opening a file or directory, supporting reading and writing files without page caching. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-core-file-kit/js-apis-file-fs.md#fileioopen))

- Adds the listFileExt method to support recursive listing and custom file name filtering. You can configure the recursion parameter in options to recursively list the relative paths of all files. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-core-file-kit/js-apis-file-fs.md#fileiolistfileext))

- Adds support for developers to use the file mmap capability set (creating a file mapping object based on a file descriptor or file object) to achieve efficient file read and write access. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-core-file-kit/js-apis-file-fs.md#fileiommap))

- Adds support for applications to donate their own sandbox directories to the system for sharing, so that other applications can directly obtain the files in the directories through the file manager. ([Guide](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/file-management/share-app-file-configuration.md))

### Enterprise Customization

- Account management for enterprise devices introduces APIs for creating a normal system account ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-mdm-kit/js-apis-enterprise-accountManager.md#accountmanagercreatenormalosaccount)), removing a system account ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-mdm-kit/js-apis-enterprise-accountManager.md#accountmanagerremoveosaccount)), and switching a system account ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-mdm-kit/js-apis-enterprise-accountManager.md#accountmanageractivateosaccount)).

- Application management for enterprise devices adds support for querying the window state information list of a specified application. It can query information such as whether the application is in the bottom Dock bar and whether the current application window is displayed in the foreground. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-mdm-kit/js-apis-enterprise-applicationManager.md#applicationmanagergetapplicationwindowstates))

- In kiosk mode, adds support for entering the recent tasks bar through the swipe-up-and-hold gesture (ALLOW_GESTURE_CONTROL) and entering the side DOCK bar through the edge-swipe-inward-and-hold gesture (ALLOW_SIDE_DOCK). ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-mdm-kit/js-apis-enterprise-applicationManager.md#kioskfeature20))

- Adds the capability to install and uninstall enterprise re-signature certificates. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-mdm-kit/js-apis-enterprise-securityManager.md#securitymanagerinstallenterpriseresignaturecertificate24))

- Adds the capability to add an application to the bottom quick-launch bar of a PC/2-in-1 device based on a position index. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-mdm-kit/js-apis-enterprise-applicationManager.md#applicationmanageradddockapp24))

- Device settings management supports adding, deleting, and querying the list of hidden settings items under the current user. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-mdm-kit/js-apis-enterprise-deviceSettings.md#devicesettingsaddhiddensettingsmenu24))

### Background Task Management

The countdown reminder instance object adds the parameters repeatInterval (repeat period) and repeatCount (repeat count). ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-backgroundtasks-kit/js-apis-reminderAgentManager.md#reminderrequesttimer))

### Basic Communications

- Adds support for obtaining Wi-Fi connection information through the C API. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-connectivity-kit/capi-oh-wifi-h.md#oh_wifi_getlinkedinfo))

- Adds A2DP playback state broadcast and SCO broadcast events. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-basic-services-kit/common_event/commonEventManager-definitions.md#common_event_bluetooth_a2dpsource_play_state_change24))

### Network Management

- The optional parameters for establishing a WebSocket connection now support `supportOriginPort`, which controls whether the Origin field carries a custom port number. ([API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-network-kit/js-apis-webSocket.md#websocketrequestoptions))

- TLS supports certificate chain verification and can verify up to 1000 certificates by passing an array. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-network-kit/js-apis-socket.md#tlssecureoptions9))

### Content Embedding Service

Introduces the Content Embed content embedding service, which provides framework capabilities for embedding and collaboratively editing documents across applications, and encapsulates client-side and server-side development APIs for developers to quickly implement cross-application document embedding and collaboration. ([Guide](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/content-embed/content-embed-kit-overview.md), [API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-content-embed-kit/capi-contentembed.md))

### Form

Adds a field indicating the widget update reason to the onUpdateForm callback. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-form-kit/js-apis-app-form-formInfo.md#formupdatereason24))

### DFX

- HiDebug adds support for registering a memory dump listener, which exports an application memory snapshot when memory usage is high or when manually triggered through the hidumper command. ([Guide](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/dfx/hidebug-guidelines.md#exporting-memory-snapshots), [API Reference](https://gitcode.com/OpenHarmony/docs/blob/master/en/application-dev/reference/apis-performance-analysis-kit/capi-hidebug-h.md#oh_hidebug_registermemdumplistener))

- When an application exits abnormally due to a SIGPIPE exception, the Debug version of the application can enable SIGPIPE signal call stack printing to help locate the issue. ([Guide](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/dfx/cppcrash-guidelines.md#what-should-i-do-if-the-app-exits-due-to-a-sigpipe-exception))

HiProfiler introduces a file cache mode (use_file_cache_mode), which improves the collection performance of memory allocation information by persisting cached data to disk.

- HiDebug introduces a resource collection capability that collects application process resource allocation stacks to the sandbox on demand, covering categories such as file descriptors, threads, Native/GPU memory, and global handles, to help locate resource leaks. ([Guide](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/dfx/hidebug-guidelines.md))

- HiDebug adds support for obtaining physical memory usage information of an application process. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-performance-analysis-kit/js-apis-hidebug.md#hidebuggetrssinfo24))

- HiDebug adds support for changing the dumped heap snapshot from thread-level to process-level. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-performance-analysis-kit/js-apis-hidebug.md#hidebugsetprocdumpinsharedoom24))

- HiDebug introduces a Trace collection request API that includes kernel information. ([ArkTS API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-performance-analysis-kit/js-apis-hidebug.md#hidebugrequesttrace24), [C API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-performance-analysis-kit/capi-hidebug-h.md#oh_hidebug_requesttrace))

- HiAppEvent introduces an application freeze warning event and provides the capability to subscribe to the event. ([Guide](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/dfx/hiappevent-watcher-appfreezewarning-events.md))

### Multimodal Input

- Introduces the input event injection module, which provides the capability to simulate keyboard and mouse input events. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-input-kit/js-apis-inputeventclient.md))

- Enhances C API input events by providing events such as input event pressure and XY coordinates relative to the upper-left corner of the window. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-input-kit/capi-oh-input-manager-h.md#oh_input_settoucheventpressure))

### Notification

- Adds support for querying part of the information in the wantAgent field of the current application's notifications. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-notification-kit/js-apis-notificationManager.md#notificationmanagergetnotificationparameters24))

- Adds support for using files in the application sandbox as custom notification ringtones. ([Guide](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/notification/notification-customized-ringtone.md))

- Adds fields such as whether to enable lock screen notifications. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-notification-kit/js-apis-notificationManager.md#notificationsetting20))

- Adds support for opening the application's notification settings screen in a half-modal manner. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/apis-notification-kit/js-apis-notificationManager.md#notificationmanageropennotificationsettingswithresult))

### NDK

JSVM adds support for creating ArrayBuffer objects from external memory. ([API Reference](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/common/capi-jsvm-h.md#oh_jsvm_createarraybufferfromexternalmemory))

### Others

Adds support for the Unified SDK. The Unified SDK is a standardized development tool suite for the OpenHarmony ecosystem. It extends the capabilities of the OpenHarmony SDK and provides developers with multi-dimensional development capabilities, including far-field communication, basic voice, sharing services, basic vision, desktop extension, file preview, push services, and unified scanning services. For details, see [HarmonyOS SDK for OpenHarmony](https://gitcode.com/harmonyos-sdk-for-openharmony/docs/blob/6.1-release/README.md).

## System Application Updates

### New System Applications

The following system applications are introduced for the UNISOC P7885 chip development board:

#### [File Management](https://gitcode.com/openharmony/applications_filepicker)

- Supports browsing external storage.

- Supports accessing the gallery from within the file manager.

- Supports the file picker (selection, suffix filtering, and batch authorization).

- Supports saving files through the path picker.

- Supports opening, sharing, renaming, copying, moving, and favoriting files.

- Supports recently deleted, file properties, and list/grid views.

- Supports image/video thumbnail preview.

#### [Clock](https://gitcode.com/openharmony/applications_clock)

Supports world clock and timer.

#### [Calculator](https://gitcode.com/openharmony/applications_calculator)

Supports standard calculator/scientific calculator.

#### [Calendar](https://gitcode.com/openharmony/applications_calendar)

- Supports calendar cards and calendar view.

- Supports viewing schedules, viewing a specified date, viewing account schedules, and dark mode.

- Supports creating schedules and editing schedules and important days.

- Supports schedule search, schedule management, and calendar account management.

- Supports reminder notifications for regular schedules and important schedules.

- Supports calendar settings.

#### [OOBE](https://gitcode.com/openharmony/applications_startup_guide)

- Supports the welcome page.

- Supports language selection: welcome and language settings, and region settings.

- Supports region selection: welcome and language settings, and region settings.

- Supports agreements and declarations: the End User License Agreement and basic service declaration, and the data and privacy declaration.

- Supports the agreements and declarations page.

- Supports network selection: WLAN configuration.

- Supports enhanced services: cloud applications, enhanced services, and user experience improvement.

#### [Tips](https://gitcode.com/openharmony/applications_tips)

- Supports quick start.

- Supports Tips cards.

#### [Sound Recorder](https://gitcode.com/openharmony/applications_sound_recorder)

- Supports basic recording functions, including foreground recording and background recording.

- Supports recording status and control, including foreground pause/resume/stop and save recording, recording waveform, remaining recording time, background system notifications, background lock-screen notifications, and concurrent call and recording.

- Supports playback status and control of historical recordings, including foreground/background playback, pause and resume on the list/playback page, progress bar dragging, waveform and dragging on the playback page, large and small cards in the background playback control center, system notifications, and variable-speed playback.

- Supports m4a, wav, and amr playback formats.

- Supports recording markers, including adding markers, marker jumping, and marker following.

- Supports recording file management, including list swipe-left/multi-select/playback page deletion, list swipe-left/long-press rename, and recording file search and sorting (by time/name, with time from most recent to oldest).

- Supports all playback, management, and editing functions of ordinary recordings.

- Supports recording cards. The large card can start/stop/pause/resume recording and edit, and the small card can start/stop recording. Data is synchronized between the large and small cards.

- Supports microphone permission control.

#### [SIM Card Management](https://gitcode.com/openharmony/applications_simcardmanagement)

- Supports dual-SIM management, including editing the information (name and number) of SIM 1 and SIM 2, enabling/disabling SIM cards, and SIM card protection.

- Supports default mobile data selection.

- Supports default dialing card settings.

### Updated System Applications

For the Unisoc P7885 chip development board, the following system applications are updated based on the 7.0 Release version:

#### [Home](https://gitcode.com/openharmony/window_scene_board)

- Supports numeric password/swipe unlock, brute-force attack prevention, and lock screen clock and cards.

- Supports 4×4 home screen icon layout, Dock bar, home screen icon badges, app shortcuts, and home screen edit mode.

- Supports full management of cards, card stacks, and folders.

- Supports recent tasks (lock, one-tap cleanup, and swipe to delete).

- Supports the status bar, control center, and gesture/three-button navigation.

- Supports the notification center (list, sections, grouped notifications, and pin/mute).

- Supports live notifications (capsule/card).

- Supports system dialogs (power off/low battery) and the volume panel.

- Supports split screen and floating windows (smart multi-window).

- Supports window task management (start/stop, multitasking, task chains, and persistent recovery).

- Supports the wallpaper library, static wallpaper settings, and Do Not Disturb mode.

- Supports in-settings toggles, the control center home page, and the control center secondary page.

- Supports time fences.

- Supports notification Do Not Disturb and the application whitelist.

- Supports call Do Not Disturb, general Do Not Disturb policies, Do Not Disturb for specified contacts, and repeated-call ringing.

- Supports linking to the system dark mode.

- Supports status bar reminders and live reminders.

- Supports preset modes: Do Not Disturb, Sleep, Study, and Work.

- Supports custom modes, custom names, custom icons, custom colors, creation from preset templates, custom creation, and mode deletion.

#### [Settings](https://gitcode.com/openharmony/applications_settings)

- Supports global search within Settings.

- Supports WLAN, Bluetooth, and mobile networks.

- Supports wallpapers, brightness, dark mode (including scheduled), and font and display size.

- Supports sound modes, the volume panel, and ringtones for calls, messages, and notifications.

- Supports notification and status bar management.

- Supports app management, lock screen password, battery, and storage.

- Supports system navigation, language and input method, date and time, reset, and developer options.

- Supports complete device information (IMEI, serial number, RAM, etc.).

- Supports scheduled power-off.

- Supports settings suggestions.

- Supports SIM card management.

- Supports software updates.

- Supports system user management and account addition.

- Supports enlarged display, screen magnification, and zoom area switching.

- Supports color inversion.

- Supports color correction.

- Supports high-contrast text.

- Supports reduced motion.

- Supports mono audio and volume balance.

- Supports screen touch, with configurable press duration and ignore of repeated taps.

- Supports accessibility shortcuts.

#### [Camera](https://gitcode.com/openharmony/applications_camera)

- Supports front/rear photo capture and front/rear video recording.

- Supports the camera Picker (photo only / video only / photo + video).

- Supports the camera settings page and the toolbox entry.

#### [Gallery](https://gitcode.com/openharmony/applications_photos)

- Supports photo browsing, full-image browsing, full-image gestures, and full-image components.

- Supports grid operations, full-image menu operations, card operations, and album operations.

- Supports image editing and gallery settings.

- Supports full-image video playback and photo page browsing.

- Supports the gallery Picker.

#### [Contacts](https://gitcode.com/openharmony/applications_contacts)

- Supports dialer search and quick actions on results (details, blocklist, copy, mark, create/save contact, send message).

- Supports call logs (all/missed) and long-press management (multi-select, delete, mark, add to blocklist, etc.).

- Supports contact search, alphabetical index, and smart/custom groups.

- Supports creating/editing/viewing contacts (complete fields such as avatar, multiple numbers, email, address, and birthday).

- Supports favorite contacts with sorting and batch management.

- Supports contact import/export, SIM card import, recently deleted, and duplicate contact merging.

- Supports per-contact ringtones (local/video/none).

- Supports service cards (quick dial, missed calls, home screen shortcuts).

- Supports the contact Picker.

#### [SMS](https://gitcode.com/openharmony/applications_mms)

- Supports SMS sending, long messages, and emojis.

- Supports group sending, forwarding, and resending on failure.

- Supports deleting conversations by swiping left, long pressing, or swiping to multi-select.

- Supports notification bar integration, marking as read, and replying from notifications.

- Supports copying, forwarding, and selecting text on the detail page.

- Displays contact avatars in the list and detail views.

- Supports message favorites and delivery reports.

#### [Call](https://gitcode.com/openharmony/applications_call)

- Supports voice incoming and outgoing calls, answering/hanging up/rejecting, muting, speaker, and audio device switching.

- Supports emergency dialing, SOS by pressing the power button repeatedly, and emergency location display.

- Supports emergency contacts and automatic help requests.

- Supports full-screen/banner incoming call display and ringtone/vibration.

- Supports settings such as mobile data, APN, and data roaming.

- Supports airplane mode dialing prompts and proximity-light-based accidental touch prevention.

## Version Mapping

**Table 1** Software and tool version mapping

| Software | Version | Remarks | 
| -------- | -------- | -------- |
| OpenHarmony | 7.0 Release | NA | 
| Public SDK | Ohos_sdk_public 26.0.0.38 (API Version 26.0.0 Release) | Provided for application developers. It does not include system APIs that require system permissions. The SDK obtained by default through DevEco Studio is the Public SDK. | 
| HUAWEI DevEco Studio (optional) | 26.0.0 Release | Recommended for OpenHarmony application development.<br />*Software is being uploaded*. | 
| HUAWEI DevEco Device Tool (optional) | 4.0 Release | Recommended as the integrated development environment for OpenHarmony smart devices.<br />[Click here to obtain](https://device.harmonyos.com/en/develop/ide#download). | 
| HarmonyOS SDK for OpenHarmony | 7.0 Release | A standardized development tool suite provided for the OpenHarmony ecosystem, extending the capabilities of the OpenHarmony SDK.<br />For details, see [HarmonyOS SDK for OpenHarmony](https://gitcode.com/harmonyos-sdk-for-openharmony/docs/blob/master/README.md) |

### Prerequisites

1. Register an account with GitCode.

2. Register an SSH public key with GitCode. For details, see the [GitCode Help Center](https://docs.gitcode.com/en/docs/help/home/user_center/security_management/ssh/).

3. Install the [Git client](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and [git-lfs](https://gitcode.com/gh_mirrors/gi/git-lfs?source_module=search_result_repo), and configure the user information.

   ```shell
   git config --global user.name "yourname"
   git config --global user.email "your-email-address"
   git config --global credential.helper store
   ```

4. Run the following command to install the repo tool from GitCode.

   In the following command, the installation path is "~/bin" as an example. Create the required directory as needed.

   ```shell
   mkdir ~/bin
   curl https://raw.gitcode.com/gitcode-dev/repo/raw/main/repo-py3 -o ~/bin/repo
   chmod a+x ~/bin/repo
   pip3 install -i https://repo.huaweicloud.com/repository/pypi/simple requests
   ```

5. Add repo to the environment variables.

   ```shell
   vim ~/.bashrc               # Edit the environment variables.
   export PATH=~/bin:$PATH     # Add the repo path to the end of the environment variables.
   source ~/.bashrc            # Apply the environment variables.
   ```

### Obtaining Source Code via repo

**Method 1 (Recommended)**

Acquire the source code using repo + SSH (a public key must be registered; see the [GitCode Help Center](https://docs.gitcode.com/en/docs/help/home/user_center/security_management/ssh/)).

- Obtain the source code from the version branch. This gives you the latest source code of the version branch, including changes merged into the branch after the version release.

   ```shell
   repo init -u git@gitcode.com:openharmony/manifest.git -b OpenHarmony-7.0-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

- Obtain the source code from the version release tag. This gives you source code that is exactly the same as that at the time of the version release.

   ```shell
   repo init -u git@gitcode.com:openharmony/manifest.git -b refs/tags/OpenHarmony-v7.0-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

**Method 2**

Download the source code via repo + HTTPS.

- Obtain the source code from the version branch. This gives you the latest source code of the version branch, including changes merged into the branch after the version release.

   ```shell
   repo init -u https://gitcode.com/openharmony/manifest -b OpenHarmony-7.0-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

- Obtain the source code from the version release tag. This gives you source code that is exactly the same as that at the time of the version release.

   ```shell
   repo init -u https://gitcode.com/openharmony/manifest -b refs/tags/OpenHarmony-v7.0-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

### Obtaining Source Code from a Mirror Site

**Table 2** Source code paths

| Version Source Code | **Version Information** | **Download Site** | **SHA256 Checksum** | **Package Size** |
|---------------------------------------|------------|------------------------------------------------------------|------------------------------------------------------------|--------|
| Full code (standard, lightweight, and small systems)        | 7.0 Release    | [site](https://repo.huaweicloud.com/openharmony/os/7.0-Release/code-v7.0-Release.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/7.0-Release/code-v7.0-Release.tar.gz.sha256) | 57.3 GB |
| Hi3861 solution (binary)        | 7.0 Release    | [site](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_pegasus_20260829.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_pegasus_20260829.tar.gz.sha256) | 28.9 MB |
| Hi3863 solution (binary)        | 7.0 Release    | [site](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_pegasus_3863_20260829.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_pegasus_3863_20260829.tar.gz.sha256) | 6.7 MB |
| Hi3861 64K solution (binary)        | 7.0 Release    | [site](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_pegasus_64k_20260829.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_pegasus_64k_20260829.tar.gz.sha256) | 8.0 MB |
| Hi3863 64K solution (binary)        | 7.0 Release    | [site](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_pegasus_3863_64k_20260829.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_pegasus_3863_64k_20260829.tar.gz.sha256) | 8.0 MB |
| Hi3516 solution - LiteOS (binary) | 7.0 Release    | [site](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_taurus_LiteOS_20260829.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_taurus_LiteOS_20260829.tar.gz.sha256) | 362.4 MB |
| Hi3516 solution - Linux (binary)  | 7.0 Release    | [site](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_taurus_Linux_20260829.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/7.0-Release/hispark_taurus_Linux_20260829.tar.gz.sha256) | 239.8 MB |
| RK3568 standard system solution (binary) ROM package        | 7.0 Release    | [site](https://repo.huaweicloud.com/openharmony/os/7.0-Release/dayu200_standard_arm32_rom_20260829.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/7.0-Release/dayu200_standard_arm32_rom_20260829.tar.gz.sha256) | 3.7 GB |
| RK3568 standard system solution (binary) XTS package        | 7.0 Release    | [site](https://repo.huaweicloud.com/openharmony/os/7.0-Release/dayu200_standard_arm32_xts_20260829.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/7.0-Release/dayu200_standard_arm32_xts_20260829.tar.gz.sha256) | 4.9 GB |
| P7885 standard system solution (binary) ROM package        | 7.0 Release    | [site](https://repo.huaweicloud.com/openharmony/os/7.0-Release/dayu600_standard_arm32_rom_20260829.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/7.0-Release/dayu600_standard_arm32_rom_20260829.tar.gz.sha256) | 5.2 GB |
| P7885 standard system solution (binary) XTS package        | 7.0 Release    | [site](https://repo.huaweicloud.com/openharmony/os/7.0-Release/dayu600_standard_arm32_xts_20260829.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/7.0-Release/dayu600_standard_arm32_xts_20260829.tar.gz.sha256) | 5.0 GB |
| Standard system Public SDK package (Mac)             | 26.0.0.38 | [site](https://repo.huaweicloud.com/openharmony/os/7.0-Release/ohos-sdk-mac-public_20260829.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/7.0-Release/ohos-sdk-mac-public_20260829.tar.gz.sha256) | 1.3 GB |
| Standard system Public SDK package (Mac-M1)             | 26.0.0.38  | [site](https://repo.huaweicloud.com/openharmony/os/7.0-Release/L2-SDK-MAC-M1-PUBLIC_20260829.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/7.0-Release/L2-SDK-MAC-M1-PUBLIC_20260829.tar.gz.sha256) | 1.3 GB |
| Standard system Public SDK package (Windows/Linux/ohos)   | 26.0.0.38   | [site](https://repo.huaweicloud.com/openharmony/os/7.0-Release/ohos-sdk-windows_linux-public_20260829.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/7.0-Release/ohos-sdk-windows_linux-public_20260829.tar.gz.sha256) | 3.4 GB |

## Fixed Defect List

**Table 3** Fixed defects

| ISSUE | Issue Description | 
| ------- | ------- |
| [468](https://gitcode.com/openharmony/systemabilitymgr_safwk/issues/468) | The foundation process has a memory leak under Wukong stress testing, with memory usage increasing by about 100 MB over 5 days. |
| [329](https://gitcode.com/openharmony/applications_contacts/issues/329)<br />[192](https://gitcode.com/openharmony/telephony_telephony_data/issues/192) |
| [193](https://gitcode.com/openharmony/telephony_telephony_data/issues/193) | The time for the first launch of the Contacts application exceeds the baseline requirement. |
| [73886](https://gitcode.com/openharmony/arkui_ace_engine/issues/73886) | The boot completion latency is long and does not meet the baseline requirement. |
| [633](https://gitcode.com/openharmony/applications_systemui/issues/633) | The com.ohos.systemui process has a relatively high probability of appfreeze caused by a THREAD_BLOCK_6S fault. This issue is not reproduced in the new version. |
| [263](https://gitcode.com/openharmony/device_soc_rockchip/issues/263) | The render_service process has a low probability occurrence of sysfreeze caused by SERVICE_BLOCK, with the crash stack being libmali-bifrost-g52-g7p0-ohos.so. This issue is not reproduced in the new version. |
| [772](https://gitcode.com/openharmony/applications_photos/issues/772) | The time for the first launch of the Gallery application exceeds the baseline requirement. |

## Known Issues

**Table 4** List of remaining defects

| ISSUE | Issue Description | Impact | Planned Resolution Date | 
| ------- | ------- | ------- | ------- |
| [793](https://gitcode.com/openharmony/applications_photos/issues/793) | The com.ohos.photos process has a low probability occurrence of cppcrash, with the crash stack being libimage_effect_impl.so | The Gallery shows a black screen when entering edit mode, and recovers after exiting and re-entering edit mode. | OpenHarmony7.1 |
| [6750](https://gitcode.com/openharmony/web_webview/issues/6750) | The com.ohos.note:render process has a low probability occurrence of cppcrash, with the crash stack being libarkweb_engine.so | The Notes application shows a white screen, and recovers after restarting the application. | OpenHarmony7.1 |
| [472](https://gitcode.com/openharmony/communication_bluetooth_service/issues/472) | The bluetooth_service process has a low probability occurrence of cppcrash, with the crash stack being libbtstack.z.so | The Bluetooth service restarts automatically, and users have no obvious perception. | OpenHarmony7.1 |

<!--no_check-->