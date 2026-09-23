# OpenHarmony 6.1 Release

<!-- md-trans-meta sourceCommit=22077c92b38b51e74abf174f8a6ba5e6cf1f639c translatedAt=2026-09-17T04:00:09.216Z pushedAt=2026-09-17T10:32:01.977Z -->

## Copyright and License Notice

The contributions to this project are licensed to the OpenAtom Foundation under the ***Developer Certificate of Origin (DCO)***. This project is a collective work composed of many open source software components, and the copyright of this collective work is owned by the OpenAtom Foundation. The OpenAtom Foundation grants you a license to this collective work under the Apache License 2.0 (hereinafter referred to as **Apache 2.0**).

You may use this project only in compliance with Apache 2.0 and the corresponding open source licenses applicable to the open source software components contained in this project. You can obtain a copy of Apache 2.0 at the following URL:
**[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0#/session/_blank)**

Unless required by applicable law or agreed to in writing, software distributed under the applicable open source license is provided on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. For the specific grants and restrictions under the applicable open source license, see the original text of the license.

## Version Overview

OpenHarmony 6.1 Release further enhances application development capabilities and supports finer-grained control over applications, such as measuring the UIAbility startup duration and obtaining the notification badge count. It improves the dynamic effect experience and optimizes the display of text in less common languages. It enhances system awareness capabilities: ArkWeb can obtain the status of web pages using the microphone and camera, and the input method can sense the screen state it is on. It enriches certificate management capabilities, and further enhances audio control and management capabilities, graphics processing capabilities, and more.

The key new and enhanced features of each module are described as follows:

### Application Framework

- Adds the launch time of a UIAbility to **LaunchParam** for startup time statistics. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-ability-kit/js-apis-app-ability-abilityConstant.md#launchparam))

- Adds the **allowSelfRedirect** configuration item to the [abilities tag in the module.json5 configuration file](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/quick-start/module-configuration-file.md#abilities), allowing an application to configure that it cannot be launched by itself through AppLinking.

### ArkUI



- Optimizes the display of text controls for minority languages.

- State management supports the capability to determine whether an object type is observable. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-arkui/js-apis-stateManagement.md#observedresult23))

- Optimizes the custom component lifecycle by adding the Attach&amp;Detach phases. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-arkui/arkui-ts/ts-custom-component-new-lifecycle.md))

- Navigation supports setting the color, margin, and visibility of the column divider. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-navigation.md#divider23))

### ArkWeb

- Adds support for setting and obtaining the microphone usage status of the current web page. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-arkweb/arkts-apis-webview-WebviewController.md#resumemicrophone23))

- Provides the capability to query the camera usage status of the current web page. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-arkweb/arkts-basic-components-web-events.md#oncameracapturestatechange23))

- Adds support for reporting selected text content. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-arkweb/arkts-basic-components-web-events.md#ontextselectionchange23))

- Adds support for disabling the password vault and smart fill features. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-arkweb/arkts-basic-components-web-attributes.md#enableautofill23))

- Adds support for launching autofill from context menu events. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-arkweb/arkts-basic-components-web-WebContextMenuResult.md#requestpasswordautofill23))

### Window

- The font engine supports variable fonts registered by applications for stepless adjustment.

- The font engine optimizes the display of minority languages.

### Bundle Management

- The packing tool supports incremental packing, which improves packing speed in certain scenarios (requires enabling so compression, and no major file changes compared with the previous packing). ([Guide](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/tools/packing-tool.md))

- Supports importing enterprise signing certificates on enterprise devices and using the imported enterprise signing certificates to verify the installation and running of enterprise applications, enhancing the application management capability of enterprise devices.

### Notifications

- Adds the capability to query the desktop badge number for precise updates of the desktop badge count. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-notification-kit/js-apis-notificationManager.md#notificationmanagergetbadgenumber22))

- Adds support for configuring whether banner notifications and lock screen notifications are enabled, allowing silent notifications in scenarios where user alerts are unnecessary to avoid disturbing users and degrading the experience. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-notification-kit/js-apis-inner-notification-notificationFlags.md#notificationflags-1))

- Adds support for notification overlay icons (overlayIcon), enabling customized notification icons for IM messages and improving the user experience of IM messages. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-notification-kit/js-apis-inner-notification-notificationRequest.md#notificationrequest-1))

### Distributed Data Management

UDMF adds the iWork UTD type. The UTD uniform identifiers configured in the system can be obtained through the extensions ".pages", ".key", and ".numbers". ([Guide](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/database/uniform-data-type-list.md))

### Audio

- Introduces NDK APIs for audio creation. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-audio-kit/capi-ohaudiosuite.md))

- Introduces APIs for obtaining the audio playback latency, allowing more accurate estimation of the playback latency before audio data is output for audio-video synchronization.

- Introduces NDK APIs for casting, allowing applications to integrate with system casting.

- Provides the interface capability for obtaining the audio/video playback source, enabling querying of the playback source information of audio/video applications.

- Introduces Menu-type casting APIs, supporting device switching for calling applications in cross-platform scenarios.

- Introduces casting for image applications.

- Introduces system-level desktop lyrics, allowing music applications to create and use system desktop lyrics.

- Introduces public APIs for system sound management and playback. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-audio-kit/js-apis-inner-multimedia-systemSoundPlayer.md))

- Audio session: introduces APIs for listening to mute playback suggestion notifications in mixed playback mode, improving the concurrent audio playback experience. ([Guide](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/media/audio/audio-session-management.md#enabling-mute-suggestion-notifications-for-mixed-playback))

### Security Foundation Platform

- Adds support for the companion device authentication system capability. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-user-authentication-kit/js-apis-useriam-companiondeviceauth-sys.md))

- Certificate management adds support for the following features ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-device-certificate-kit/js-apis-certManager.md)):

  - Supports the API for launching the certificate authorization dialog box, and directly returns an error code when no certificate is available.

  - Supports obtaining the Ukey hardware certificate management capability.

  - Provides the API for querying certificate credential details.

  - Provides the API for launching the dialog box for entering the Ukey PIN.

  - Provides a public API for launching the certificate credential installation UI, where users follow the wizard to complete credential installation.

  - The user certificate credential authorization UI supports selecting Ukey certificates and application private certificates.

- HUKS adds support for the following features:

  - Provides APIs for using and querying external hardware keys. ([Guide](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/security/UniversalKeystoreKit/huks-external-hardware-key-management-overview.md))

  - Supports key import in the form of SM2 digital envelopes. ([Guide-ArkTS](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/security/UniversalKeystoreKit/huks-import-envelop-key-arkts.md), [Guide-C/C++](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/security/UniversalKeystoreKit/huks-import-envelop-key-ndk.md))

- The certificate algorithm library adds support for the following features:

  - Supports ignoring the network-unreachable exception of the online certificate revocation check during certificate chain validation. ([Guide](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/security/DeviceCertificateKit/create-verify-cerchainvalidator-revocation-object.md#ignoring-the-network-unreachable-exception-during-online-certificate-revocation-check-in-certificate-chain-validation))

  - Supports downloading missing intermediate certificates during certificate chain validation. ([Guide](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/security/DeviceCertificateKit/allow-download-Intermediate-Cert.md))

### Graphics

- Canvas module: Drawing NDK adds the DrawPixelMapMesh API capability, and Drawing TS adds the drawVertics API capability.

- Completes the acquisition and switching of the fill type for the reverse state of Path.

- Completes the offset, flip, emptiness check, and self-update functions of Rect.

- Completes the region boundary, bounding box, type determination, translation, and containment relationship determination functions of Region.

- Completes the connection, rotation, skew operations, affine transformation, and rectangle mapping determination functions of Matrix.

- Provides NDK APIs for creating a Lattice.

- Completes the PathIterator/Typeface API capabilities.

- NativeWindow provides lock/unlock APIs to lock a buffer while obtaining it.

- NativeBuffer supports validating format and size information.

- NativeBuffer provides the capability to obtain the virtual address and OH_NativeBuffer_Config simultaneously.

- NativeBuffer provides cross-process buffer sharing, making it easier for developers to transfer buffers across processes.

### Language Runtime and Basic Libraries

- Provides an external string mechanism to avoid extra copying and allow the ArkTS side to directly read strings in the C++ layer. ([Guide](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/napi/use-napi-about-string.md#napi_create_external_string_utf16))

- Provides the sendable reference feature to support concurrent operations on string objects across multiple ArkTS threads. ([Guide](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/napi/use-napi-about-sendable-reference.md))

- Adds a new API to support dynamically enabling the multi-thread detection capability. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-arkts/js-apis-util.md#arktsvm23))

### Customization Service (MDM)

- New support for MDM application deployment in DA mode on PC-form devices. Developers can select the deployment mode more flexibly based on the actual usage scenarios of the device.

- A new EnterpriseAdminExtensionContext object is added to EnterpriseAdminExtensionAbility, providing the capability to launch pages in the background.

- Provides the capability to disable the UIAbility components of specified applications (both system applications and third-party applications are supported).

- Provides the capability to intercept system keys (power key, volume keys, BACK key, HOME key, and recent tasks key).

### Input Method Framework



- Introduces APIs for carrying screen information:

  - In multi-screen multi-focus scenarios, an application can obtain the keyboard information of the screen where it resides. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-ime-kit/js-apis-inputmethod-sys.md#ispanelshown23))

  - In multi-screen multi-focus scenarios, an application can show and hide the keyboard on the screen where it resides. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-ime-kit/js-apis-inputmethod-sys.md#inputmethodcontroller))

### Resource Scheduler

Adds a continuous task of the sports and health type. After user authorization, this type of continuous task can run in the background. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-backgroundtasks-kit/js-apis-resourceschedule-backgroundTaskManager.md#properties))

### Basic Communications

- Adds the capability to set the card presence detection interval when an application reads an NFC card in the foreground, allowing applications to process card information more flexibly. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-connectivity-kit/js-apis-nfcTag.md#tagon23))

- Adds the Bluetooth HID Device class APIs, supporting the Bluetooth HID Device capability. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-connectivity-kit/js-apis-bluetooth-hid.md#hidcreatehiddeviceprofile23))

- Adds the PartnerAgent APIs, supporting the launch of an application's PartnerAgentExtensionAbility process after a Bluetooth device is connected. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-connectivity-kit/js-apis-fusionConnectivity-partnerAgent.md))

### Sensor

A new field **isMockSensor** is added to sensor information to distinguish whether the device is a mock device. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-sensor-service-kit/js-apis-sensor.md))

### Multimodal Input

- Provides a common event to detect the opening and closing of the laptop lid.

- Provides an API to query whether the current device has an infrared emitter. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-input-kit/js-apis-infraredemitter.md#infraredemitterhasiremitter23))

### Power Management

- Adds the BACKGROUND_USER_IDLE running lock type for preventing sleep. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-basic-services-kit/js-apis-runninglock.md#runninglocktype))

- Adds APIs for registering and unregistering shutdown callbacks, allowing applications to detect an imminent shutdown on demand so that they can perform important processing actions in a timely manner. ([API Reference](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-Release/en/application-dev/reference/apis-basic-services-kit/js-apis-power-sys.md#powerregistershutdowncallback23))

### Testing and Certification Platform

- SP Host adds file descriptor (FD) leak analysis capabilities, supporting the capture and analysis of FD resource request/release call events and call stacks.

- SP Host adds support for displaying dynamic swimlane diagrams and call stack flame graphs for the request and release of ION memory, ASHMem memory, and so references.

- SP Host adds support for displaying dynamic swimlane diagrams and call stack flame graphs for the request and release of ArkTS objects and ArkWeb JS objects.

## Version Evolution

OpenHarmony 6.1 LTS is planned to be released before June 30 as the new recommended version for long-term maintenance and compatibility assessment of OpenHarmony.

## Version Mapping

**Table 1** Software and tool version mapping

| Software | Version | Remarks | 
| -------- | -------- | -------- |
| OpenHarmony | 6.1 Release | N/A | 
| Public SDK | Ohos_sdk_public 6.1.0.31 (API Version 23 Release) | Provided for application developers. It does not include system APIs that require system permissions. The SDK obtained by default through DevEco Studio is the Public SDK. | 
| HUAWEI DevEco Studio (optional) | 6.1.0 Release | Recommended for OpenHarmony application development.<br />*To be provided after release*. | 
| HUAWEI DevEco Device Tool (optional) | 4.0 Release | Recommended as the integrated development environment for OpenHarmony smart devices.<br />[Click here to obtain](https://device.harmonyos.com/en/develop/ide#download). |

## Source Code Acquisition

### Prerequisites

1. Register an account with GitCode.

2. Register an SSH public key with GitCode. For details, see the [GitCode Help Center](https://docs.gitcode.com/en/docs/help/home/user_center/security_management/ssh/).

3. Install the [git client](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and [git-lfs](https://gitcode.com/gh_mirrors/gi/git-lfs?source_module=search_result_repo), and configure user information.

   ```shell
   git config --global user.name "yourname"
   git config --global user.email "your-email-address"
   git config --global credential.helper store
   ```

4. Run the following command to install the repo tool of GitCode.

   In the following command, "~/bin" is used as an example installation path. Create the required directory as needed.

   ```shell
   mkdir ~/bin
   curl https://raw.gitcode.com/gitcode-dev/repo/raw/main/repo-py3 -o ~/bin/repo
   chmod a+x ~/bin/repo
   pip3 install -i https://repo.huaweicloud.com/repository/pypi/simple requests
   ```

5. Add repo to the environment variables.

   ```shell
   vim ~/.bashrc               # Edit the environment variables.
   export PATH=~/bin:$PATH     # Add a line of repo path information to the end of the environment variable.
   source ~/.bashrc            # Apply the environment variable.
   ```

### Obtaining Source Code via repo

**Method 1 (Recommended)**

Download the source code via repo + SSH (you need to register a public key first).

- Obtain the source code from the version branch. This gives you the latest source code of the version branch, including changes merged into the branch after the version release.

   ```
   repo init -u git@gitcode.com:openharmony/manifest.git -b OpenHarmony-6.1-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

- Obtain the source code from the version release tag. This gives you source code that is exactly the same as that at the time of the version release.

   ```
   repo init -u git@gitcode.com:openharmony/manifest.git -b refs/tags/OpenHarmony-v6.1-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

**Method 2**

Download the source code via repo + HTTPS.

- Obtain the source code from the version branch. This gives you the latest source code of the version branch, including changes merged into the branch after the version release.

   ```
   repo init -u https://gitcode.com/openharmony/manifest -b OpenHarmony-6.1-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

- Obtain the source code from the version release tag. This gives you source code that is exactly the same as that at the time of the version release.

   ```
   repo init -u https://gitcode.com/openharmony/manifest -b refs/tags/OpenHarmony-v6.1-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

### Obtaining Source Code from a Mirror Site

**Table 2** Source code paths

| Version Source Code | **Version Information** | **Download Site** | **SHA256 Checksum** | **Package Size** |
|---------------------------------------|------------|------------------------------------------------------------|------------------------------------------------------------|--------|
| Full code (standard, lightweight, and small systems)        | 6.1 Release    | [site](https://repo.huaweicloud.com/openharmony/os/6.1-Release/code-v6.1-Release.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-Release/code-v6.1-Release.tar.gz.sha256) | 64.2 GB |
| Hi3861 solution (binary)        | 6.1 Release    | [site](https://repo.huaweicloud.com/openharmony/os/6.1-Release/hispark_pegasus.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-Release/hispark_pegasus.tar.gz.sha256) | 28.8 MB |
| Hi3516 solution - LiteOS (binary) | 6.1 Release    | [site](https://repo.huaweicloud.com/openharmony/os/6.1-Release/hispark_taurus_LiteOS.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-Release/hispark_taurus_LiteOS.tar.gz.sha256) | 359.6 MB |
| Hi3516 solution - Linux (binary)  | 6.1 Release    | [site](https://repo.huaweicloud.com/openharmony/os/6.1-Release/hispark_taurus_Linux.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-Release/hispark_taurus_Linux.tar.gz.sha256) | 237.7 MB |
| RK3568 standard system solution (binary) ROM package        | 6.1 Release    | [site](https://repo.huaweicloud.com/openharmony/os/6.1-Release/dayu200_standard_arm32_rom.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-Release/dayu200_standard_arm32_rom.tar.gz.sha256) | 4.1 GB |
| RK3568 standard system solution (binary) XTS package        | 6.1 Release    | [site](https://repo.huaweicloud.com/openharmony/os/6.1-Release/dayu200_standard_arm32_xts.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-Release/dayu200_standard_arm32_xts.tar.gz.sha256) | 4.4 GB |
| Standard system Public SDK package (Mac)             | 6.1.0.31 | [site](https://repo.huaweicloud.com/openharmony/os/6.1-Release/ohos-sdk-mac-public.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-Release/ohos-sdk-mac-public.tar.gz.sha256) | 1.3 GB |
| Standard system Public SDK package (Mac-M1)             | 6.1.0.31  | [site](https://repo.huaweicloud.com/openharmony/os/6.1-Release/L2-SDK-MAC-M1-PUBLIC.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-Release/L2-SDK-MAC-M1-PUBLIC.tar.gz.sha256) | 1.2 GB |
| Standard system Public SDK package (Windows/Linux)   | 6.1.0.31   | [site](https://repo.huaweicloud.com/openharmony/os/6.1-Release/ohos-sdk-windows_linux-public.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-Release/ohos-sdk-windows_linux-public.tar.gz.sha256) | 2.3 GB |

## Resolved Issues

**Table 3** Fixed defects

| ISSUE | Issue Description | 
| ------- | ------- |
| [19592](https://gitcode.com/openharmony/graphic_graphic_2d/issues/19592) | The frame rate when swiping the comment section in a Douyin-like app is 43 FPS, which does not meet the baseline requirement. |
| [588](https://gitcode.com/openharmony/applications_systemui/issues/588) | The process com.ohos.systemui experiences a memory leak under Wukong stress testing. |
| [296](https://gitcode.com/openharmony/applications_mms/issues/296)<br />[295](https://gitcode.com/openharmony/applications_mms/issues/295) | The process com.ohos.mms experiences a jscrash in rare cases caused by anonymous or deleteAction. |
| [527](https://gitcode.com/openharmony/hiviewdfx_hilog/issues/527) | The hilogd.server thread in the process /system/bin/hilogd experiences a cppcrash in rare cases. |
| [63972](https://gitcode.com/openharmony/arkui_ace_engine/issues/63972) | The m.ohos.contacts thread in the process com.ohos.contacts experiences a cppcrash in rare cases caused by libace_compatible.z.so. |

## Known Issues

**Table 4** Known Issues

| Issue | Issue Description | Impact | Planned Resolution Date | 
| -------- | -------- | -------- | -------- |
| [19617](https://gitcode.com/openharmony/graphic_graphic_2d/issues/19617) | The boot completion latency is slightly degraded compared with the previous version. | Slightly affects the user experience. | May 30, 2026 |
| [329](https://gitcode.com/openharmony/applications_contacts/issues/329)<br />[192](https://gitcode.com/openharmony/telephony_telephony_data/issues/192) | The frame rate when swiping the contacts list is lower than the baseline requirement.| Slightly affects the user experience. | May 30, 2026 |
| [193](https://gitcode.com/openharmony/telephony_telephony_data/issues/193) | The time to launch the Contacts app for the first time exceeds the baseline requirement. | Slightly affects the user experience. | May 30, 2026 |
| [73886](https://gitcode.com/openharmony/arkui_ace_engine/issues/73886) | The boot completion latency is long and does not meet the baseline requirement. | Slightly affects the user experience. | April 30, 2026 |
| [772](https://gitcode.com/openharmony/applications_photos/issues/772) | The time to launch the Gallery app for the first time exceeds the baseline requirement. | Slightly affects the user experience. | May 30, 2026 |
| [245](https://gitcode.com/openharmony/device_soc_rockchip/issues/245) | The process render_service experiences a sysfreeze in rare cases caused by SERVICE_BLOCK, with the blocking cause being a fault in libmali-bifrost-g52-g7p0-ohos.so | The keyboard and mouse lag for 1 to 2 seconds and become temporarily unresponsive, and recover automatically after 1 to 2 seconds. | June 30, 2026 |
| [246](https://gitcode.com/openharmony/device_soc_rockchip/issues/246) | RK3568 experiences a restart under Wukong stress testing (Kernel panic - not syncing: watchdog pretimeout event) | The system returns to normal after a restart. | June 30, 2026 |
| [248](https://gitcode.com/openharmony/device_soc_rockchip/issues/248) | The omx_msg_hdl thread in the process codec_host experiences a cppcrash in rare cases, with the crash stack being libomxvpu_dec.z.so. | The keyboard and mouse lag for 1 to 2 seconds and become temporarily unresponsive, and recover automatically after 1 to 2 seconds. | June 30, 2026 |
| [856](https://gitcode.com/openharmony/applications_settings/issues/856) | The process com.ohos.settings experiences a sysfreeze in rare cases caused by LIFECYCLE_TIMEOUT. | The issue is not reproduced during normal service usage and has a minor impact on users. | May 30, 2026 |
| [630](https://gitcode.com/openharmony/applications_systemui/issues/630) | The process com.ohos.systemui experiences a jscrash in rare cases, with the crash stack being subscriberCallBack. | The device screen goes black and recovers after a few seconds. | March 31, 2026 |
| [12339](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12339) | The main process com.ohos.systemui experiences a cppcrash in rare cases, with the crash stack being libark_jsruntime.so. | The device screen goes black and recovers after a few seconds. | March 31, 2026 |