# OpenHarmony 6.1 LTS

<!-- md-trans-meta sourceCommit=b197786926e8b2f2d5451df4faf322684110f7b0 translatedAt=2026-09-17T04:28:36.268Z pushedAt=2026-09-17T09:23:12.618Z -->

## Copyright and License Notice

Contributions to this project are licensed to the OpenAtom Foundation under ***Developer Certificate of Origin (DCO)***. This project is a compilation of many open source software components, and the copyright of this compilation belongs to the OpenAtom Foundation. The OpenAtom Foundation grants you a license to this compilation under the Apache 2.0 open source license (hereinafter referred to as **Apache 2.0**).

You may use this project only in compliance with Apache 2.0 and the corresponding open source licenses applicable to the open source software components contained in this project. You can obtain a copy of Apache 2.0 at the following URL:
**[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0#/session/_blank)**

Unless required by applicable law or agreed to in writing, software distributed under the applicable open source license is provided on an "AS IS" basis, without warranties or conditions of any kind, either express or implied. For the specific grants and restrictions under the applicable open source license, please refer to the original license text.

## Version Overview

OpenHarmony releases version 6.1 LTS based on version 6.1 Release. Compared with 6.1 Release, version 6.1 LTS introduces a new development board, the "Unisoc P7885 chip development board", for the standard system, and adds and enhances a series of capabilities as well as adapts preinstalled applications for this development board.

### New Capabilities



- For the UNISOC P7885 chip development board, the following capabilities are introduced:

  - Supports 5G cellular communication, providing network registration, calling, SMS, and data functions.

  - Supports unified rendering.

  - Supports GNSS satellite status reporting, which can identify and report satellite data such as GPS, BeiDou, and GLONASS.

  - Adapts the NearLink driver, supports NearLink SLE 1.0, and supports NearLink pairing, connection, and data transmission.

  - Onboard adaptation of six types of sensors: accelerometer, gyroscope, magnetometer, proximity sensor, ambient light sensor, and motor.

  - Onboard 36-pin standard PCI-E interface, with the external board supporting USB + Gigabit Ethernet interfaces or other standard PCI-E cards.

### New Preinstalled Applications

The following preinstalled applications are added for the Unisoc P7885 chip development board:

#### [File Management](https://gitcode.com/openharmony/applications_filepicker)

- Supports browsing external storage.

- Supports accessing the gallery from the file manager.

- Supports the file Picker (selection, suffix filtering, and batch authorization).

- Supports saving files via the path Picker.

- Supports opening, sharing, renaming, copying, moving, and favoriting files.

- Supports views such as recently deleted, file properties, and list/grid layouts.

#### [Clock](https://gitcode.com/openharmony/applications_clock)

- Supports world clock and timer.

#### [Calculator](https://gitcode.com/openharmony/applications_calculator)

- Supports standard calculator/scientific calculator.

### Updated Preinstalled Applications

For the Unisoc P7885 chip development board, the following preinstalled applications have been updated based on the 6.1 Release version:

#### [Home](https://gitcode.com/openharmony/window_scene_board)

- Supports numeric password/swipe unlock, brute-force attack prevention, and lock screen clock and cards.

- Supports a 4x4 home screen icon layout, the Dock, home screen icon badges, app shortcuts, and home screen edit mode.

- Supports full management of cards, card stacks, and folders.

- Supports recent tasks (locking, one-tap cleanup, and swipe-to-delete).

- Supports the status bar, control center, and gesture/three-key navigation.

- Supports the notification center (list, grouping, group notifications, and pinning/muting).

- Supports live notifications (capsule/card).

- Supports system dialogs (power off/low battery) and the volume panel.

- Supports split screen and floating windows (smart multi-window).

- Supports window task management (start/stop, multitasking, task chain, and persistent recovery).

- Supports wallpaper library, static wallpaper settings, and Do Not Disturb mode.

#### [Settings](https://gitcode.com/openharmony/applications_settings)

- Supports global search within Settings.

- Supports WLAN, Bluetooth, and mobile networks.

- Supports wallpaper, brightness, dark mode (including scheduling), font, and display size.

- Supports sound mode, volume panel, and ringtones for calls, messages, and notifications.

- Supports notification and status bar management.

- Supports app management, lock screen password, battery, and storage.

- Supports system navigation, language and input method, date and time, reset, and developer options.

- Supports complete device information (IMEI, serial number, RAM, etc.).

#### [Camera](https://gitcode.com/openharmony/applications_camera)

- Supports front/rear photo capture and front/rear video recording.

- Supports the camera Picker (photo only/video only/photo + video).

- Supports the camera settings page and the Treasure Box entry.

#### [Gallery](https://gitcode.com/openharmony/applications_photos)

- Supports photo browsing, full-screen image browsing, full-screen image gestures, and full-screen image components.

- Supports grid operations, full-screen image menu operations, card operations, and album operations.

- Supports image editing and gallery settings.

- Supports full-screen video playback and photo page browsing.

- Supports the gallery Picker.

#### [Contacts](https://gitcode.com/openharmony/applications_contacts)

- Supports dial pad search and quick actions on results (details, blocklist, copy, mark, create/save contact, send message).

- Supports call logs (all/missed) and long-press management (multi-select, delete, mark, add to blocklist, etc.).

- Supports contact search, alphabetical index, and smart/custom groups.

- Supports contact creation/editing/details (complete fields such as avatar, multiple numbers, email, address, and birthday).

- Supports favorite contacts, sorting, and batch management.

- Supports contact import/export, SIM card import, recently deleted, and duplicate contact merging.

- Supports per-contact ringtones (local/video/none).

- Supports service widgets (quick dial, missed calls, home screen shortcuts).

- Supports the contact Picker.

#### [SMS](https://gitcode.com/openharmony/applications_mms)

- Supports SMS sending, long messages, and emojis.

- Supports group sending, forwarding, and resending after failure.

- Supports deleting multiple conversations by swiping left, long pressing, or sliding to multi-select.

- Supports notification bar integration, marking as read, and replying from notifications.

- Supports operations such as copying, forwarding, and text selection on the details page.

- Supports displaying contact avatars in the list and details.

- Supports message favorites and delivery reports.

#### [Call](https://gitcode.com/openharmony/applications_call)

- Supports voice incoming and outgoing calls, answering/ending/rejecting, muting, speaker, and audio device switching.

- Supports emergency dialing, SOS by pressing the power key repeatedly, and emergency location display.

- Supports emergency contacts and automatic help requests.

- Supports full-screen/banner incoming call display and ringtone/vibration.

- Supports settings such as mobile data, APN, and data roaming.

- Supports airplane mode dialing prompts and proximity sensor-based accidental touch prevention.

### Others

Adds support for the unified SDK. The unified SDK is a standardized development tool suite provided for the OpenHarmony ecosystem. It extends the capabilities of the OpenHarmony SDK and provides developers with multi-dimensional development capabilities such as far-field communication, basic voice, sharing services, basic vision, desktop extension, file preview, push services, and unified scanning services. See [HarmonyOS SDK for OpenHarmony](https://gitcode.com/harmonyos-sdk-for-openharmony/docs/blob/6.1-release/README.md) for details.

## Version Mapping

**Table 1** Software and tool version mapping

| Software | Version | Remarks | 
| -------- | -------- | -------- |
| OpenHarmony | 6.1 LTS | NA | 
| Public SDK | Ohos_sdk_public 6.1.0.35 (API Version 23 Release) | Provided for application developers. It does not include system APIs that require system permissions. The SDK obtained by default through DevEco Studio is the Public SDK. | 
| HarmonyOS SDK for OpenHarmony | 6.1 Release | A standardized development tool suite provided for the OpenHarmony ecosystem. It extends the capabilities of the OpenHarmony SDK.<br />See [HarmonyOS SDK for OpenHarmony](https://gitcode.com/harmonyos-sdk-for-openharmony/docs/blob/6.1-release/README.md) for details. | 
| HUAWEI DevEco Studio (optional) | 6.1.0 Release | Recommended for OpenHarmony application development.<br />[Click here to obtain it](https://developer.huawei.com/consumer/en/download/). | 
| HUAWEI DevEco Device Tool (optional) | 4.0 Release | Recommended as the integrated development environment for OpenHarmony smart devices.<br />[Click here to obtain](https://device.harmonyos.com/en/develop/ide#download). |

### Prerequisites

1. Register an account with GitCode.

2. Register an SSH public key with GitCode. For details, see the [GitCode help center](https://docs.gitcode.com/en/docs/help/home/user_center/security_management/ssh/).

3. Install the [Git client](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and [git-lfs](https://gitcode.com/gh_mirrors/gi/git-lfs?source_module=search_result_repo), and configure the user information.

   ```shell
   git config --global user.name "yourname"
   git config --global user.email "your-email-address"
   git config --global credential.helper store
   ```

4. Run the following command to install the repo tool of GitCode.

   In the following command, the installation path "~/bin" is used as an example. Create the required directory as needed.

   ```shell
   mkdir ~/bin
   curl https://raw.gitcode.com/gitcode-dev/repo/raw/main/repo-py3 -o ~/bin/repo
   chmod a+x ~/bin/repo
   pip3 install -i https://repo.huaweicloud.com/repository/pypi/simple requests
   ```

5. Add repo to the environment variables.

   ```shell
   vim ~/.bashrc               # Edit the environment variables.
   export PATH=~/bin:$PATH     # Add the repo path information to the end of the environment variables.
   source ~/.bashrc            # Apply the environment variables.
   ```

### Obtaining Source Code via repo

**Method 1 (Recommended)**

Download via repo + SSH (a public key must be registered; for details, see the [GitCode help center](https://docs.gitcode.com/en/docs/help/home/user_center/security_management/ssh/)).

- Obtain the source code from the version branch. This gives you the latest source code of the version branch, including changes merged into the branch after the version release.

   ```shell
   repo init -u git@gitcode.com:openharmony/manifest.git -b OpenHarmony-6.1-LTS --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

- Obtain the source code from the version release tag. This gives you source code that is exactly the same as that at the time of the version release.

   ```shell
   repo init -u git@gitcode.com:openharmony/manifest.git -b refs/tags/OpenHarmony-v6.1-LTS --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

**Method 2**

Download the source code via repo + HTTPS.

- Obtain the source code from the version branch. This gives you the latest source code of the version branch, including changes merged into the branch after the version release.

   ```shell
   repo init -u https://gitcode.com/openharmony/manifest -b OpenHarmony-6.1-LTS --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

- Obtain the source code from the version release tag. This gives you source code that is exactly the same as that at the time of the version release.

   ```shell
   repo init -u https://gitcode.com/openharmony/manifest -b refs/tags/OpenHarmony-v6.1-LTS --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

### Prerequisites

1. Register an account with GitCode.

2. Register an SSH public key with GitCode. For details, please refer to the [GitCode help center](https://docs.gitcode.com/en/docs/help/home/user_center/security_management/ssh/).

3. Install the [git client](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and [git-lfs](https://gitcode.com/gh_mirrors/gi/git-lfs?source_module=search_result_repo), and configure the user information.

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
   export PATH=~/bin:$PATH     # Add a line of repo path information to the end of the environment variables.
   source ~/.bashrc            # Apply the environment variables.
   ```

### Obtaining Source Code via repo

**Method 1 (Recommended)**

Download the source code via repo + SSH (you need to register a public key first).

- Obtain the source code from the version branch. This gives you the latest source code of the version branch, including changes merged into the branch after the version release.

   ```
   repo init -u git@gitcode.com:openharmony/manifest.git -b OpenHarmony-6.1-LTS --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

- Obtain the source code from the version release tag. This gives you source code that is exactly the same as that at the time of the version release.

   ```
   repo init -u git@gitcode.com:openharmony/manifest.git -b refs/tags/OpenHarmony-v6.1-LTS --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

**Method 2**

Download the source code via repo + HTTPS.

- Obtain the source code from the version branch. This gives you the latest source code of the version branch, including changes merged into the branch after the version release.

   ```
   repo init -u https://gitcode.com/openharmony/manifest -b OpenHarmony-6.1-LTS --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

- Obtain the source code from the version release tag. This gives you source code that is exactly the same as that at the time of the version release.

   ```
   repo init -u https://gitcode.com/openharmony/manifest -b refs/tags/OpenHarmony-v6.1-LTS --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

### Obtaining Source Code from a Mirror Site

**Table 2** Source code paths

| Version Source Code | **Version Information** | **Download Site** | **SHA256 Checksum** | **Package Size** |
|---------------------------------------|------------|------------------------------------------------------------|------------------------------------------------------------|--------|
| Full code (standard, lightweight, and small systems)        | 6.1 LTS    | [site](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/code-v6.1-LTS.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/code-v6.1-LTS.tar.gz.sha256) | 69.3 GB |
| Hi3861 solution (binary)        | 6.1 LTS    | [site](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_pegasus.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_pegasus.tar.gz.sha256) | 28.8 MB |
| Hi3863 solution (binary)        | 6.1 LTS    | [site](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_pegasus_3863.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_pegasus_3863.tar.gz.sha256) | 8.0 MB |
| Hi3861 64K solution (binary)        | 6.1 LTS    | [site](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_pegasus_64k.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_pegasus_64k.tar.gz.sha256) | 7.9 MB |
| Hi3863 64K solution (binary)        | 6.1 LTS    | [site](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_pegasus_3863_64k.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_pegasus_3863_64k.tar.gz.sha256) | 3.0 MB |
| Hi3516 solution - LiteOS (binary) | 6.1 LTS    | [site](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_taurus_LiteOS.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_taurus_LiteOS.tar.gz.sha256) | 359.7 MB |
| Hi3516 solution - Linux (binary)  | 6.1 LTS    | [site](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_taurus_Linux.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_taurus_Linux.tar.gz.sha256) | 238.5 MB |
| RK3568 standard system solution (binary) ROM package        | 6.1 LTS    | [site](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/dayu200_standard_arm32_rom.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/dayu200_standard_arm32_rom.tar.gz.sha256) | 4.0 GB |
| RK3568 standard system solution (binary) XTS package        | 6.1 LTS    | [site](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/dayu200_standard_arm32_xts.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/dayu200_standard_arm32_xts.tar.gz.sha256) | 4.4 GB |
| P7885 standard system solution (binary) ROM package        | 6.1 LTS    | [site](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/dayu600_standard_arm32_rom.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/dayu600_standard_arm32_rom.tar.gz.sha256) | 6.0 GB |
| P7885 standard system solution (binary) XTS package        | 6.1 LTS    | [site](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/dayu600_standard_arm32_xts.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/dayu600_standard_arm32_xts.tar.gz.sha256) | 4.5 GB |
| Standard system Public SDK package (Mac)             | 6.1.0.35 | [site](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/ohos-sdk-mac-public.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/ohos-sdk-mac-public.tar.gz.sha256) | 1.3 GB |
| Standard system Public SDK package (Mac-M1)             | 6.1.0.35  | [site](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/L2-SDK-MAC-M1-PUBLIC.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/L2-SDK-MAC-M1-PUBLIC.tar.gz.sha256) | 1.2 GB |
| Standard system Public SDK package (Windows/Linux)   | 6.1.0.35   | [site](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/ohos-sdk-windows_linux-public.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/ohos-sdk-windows_linux-public.tar.gz.sha256) | 3.0 GB |

## Known Issues

**Table 4** Known issues

| Issue | Issue Description | Impact | Planned Resolution Date or Version |
| -------- | -------- | -------- | -------- |
| [13048](https://gitcode.com/openharmony/multimedia_audio_framework/issues/13048) | The audio_server process crashes in rare cases due to a cppcrash caused by libaudio_policy_service.z.so. | The process restarts automatically. | Version 7.0 |
| [51](https://gitcode.com/openharmony/device_soc_unisoc/issues/51) | During testing, the P7885 development board displays a white screen in rare cases, showing `abnormal mode: init-mmc-fat failed Please check SD card`. This is caused by the test case entering updater mode. | This issue can be avoided by not entering updater mode.<br />The P7885 development board is planned to support updater mode in version 7.1. | Version 7.1 |
| [24762](https://gitcode.com/openharmony/graphic_graphic_2d/issues/24762) | The Vulkan version bundled with the P7885 development board is 1.2, while the test suite requires a Vulkan version higher than 1.3, causing some test cases to fail. | Normal use is not affected. It is recommended to apply for an exemption during compatibility certification.<br />The P7885 development board is planned to upgrade its Vulkan version in version 7.1. | Version 7.1 |