# OpenHarmony 6.0.0.1 Release

## Version Description

OpenHarmony 6.0.0.1 Release provides enhanced system security over OpenHarmony 6.0 Release by rectifying certain known vulnerabilities in open-source components such as Linux kernel, and system stability issues.


## Version Mapping

**Table 1** Version mapping of software and tools

| Software/Tool| Version| Remarks|
| -------- | -------- | -------- |
| OpenHarmony | 6.0.0.1 Release | N/A|
| Public SDK | Ohos_sdk_public 6.0.0.48 (API Version 20 Release) | This toolkit is intended for application developers and does not contain system APIs that require system permissions. The SDK obtained by default through DevEco Studio is the Public SDK.|
| (Optional) HUAWEI DevEco Studio| 6.0.0 Release | Recommended for OpenHarmony application development.<br>*To be provided after release.*|
| (Optional) HUAWEI DevEco Device Tool| 4.0 Release | Recommended for application development for OpenHarmony smart devices.<br>[Click here](https://device.harmonyos.com/en/develop/ide#download).|


## Source Code Acquisition


### Prerequisites

1. Register your account with GitCode.

2. Register an SSH public key for access to GitCode.

3. Install the [git client](https://gitcode.com/link?target=https%3A%2F%2Fgit-scm.com%2Fbook%2Fzh%2Fv2%2F%25E8%25B5%25B7%25E6%25AD%25A5-%25E5%25AE%2589%25E8%25A3%2585-Git) and [git-lfs](https://gitcode.com/vcs-all-in-one/git-lfs?_from=gitee_search#downloading), and configure user information.
   ```bash
   git config --global user.name "yourname"
   git config --global user.email "your-email-address"
   git config --global credential.helper store
   ```

4. Install the **repo** tool.
   ```bash
   curl -s https://gitcode.com/oschina/repo/raw/fork_flow/repo-py3 > /usr/local/bin/repo  #If you do not have the permission, download the tool to another directory and add that directory to environment variables. chmod a+x /usr/local/bin/repo
   pip3 install -i https://repo.huaweicloud.com/repository/pypi/simple requests
   ```


### Acquiring Source Code Using the repo Tool

**Method 1 (recommended)**

Use the **repo** tool to download the source code over SSH. (You must have an SSH public key for access to GitCode.)

- Obtain the source code from the version branch. You can obtain the latest source code of the specified version branch, which includes all changes up to the time you run the commands.
   ```bash
   repo init -u git@gitcode.com:openharmony/manifest.git -b OpenHarmony-6.0-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```
   
- Obtain the source code from the version tag, which is the same as that released with the version.
   ```bash
   repo init -u git@gitcode.com:openharmony/manifest.git -b refs/tags/OpenHarmony-v6.0.0.1-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

**Method 2**

Use the **repo** tool to download the source code over HTTPS.

- Obtain the source code from the version branch. You can obtain the latest source code of the specified version branch, which includes all changes up to the time you run the commands.
   ```bash
   repo init -u https://gitcode.com/openharmony/manifest -b OpenHarmony-6.0-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```
   
- Obtain the source code from the version tag, which is the same as that released with the version.
   ```bash
   repo init -u https://gitcode.com/openharmony/manifest -b refs/tags/OpenHarmony-v6.0.0.1-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```


### Acquiring Source Code from Mirrors

**Table 2** Mirrors for acquiring source code

| Source Code                               | **Version**| **Mirror**                                                | **SHA-256 Checksum**                                            | **Software Package Size**| Remarks|
| --------------------------------------- | ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | -------- | --------------------------------------- |
| Full code base (for mini, small, and standard systems)       | 6.0.0.1 Release | [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/code-v6.0.0.1-Release-20251216.tar.gz)| [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/code-v6.0.0.1-Release-20251216.tar.gz.sha256)| 55.1 GB | Suggestion: Before compilation, run the following commands to eliminate environmental interference: 1. **repo forall -c 'git reset --hard;git clean -fdx;git lfs pull'**<br>2. **./build/prebuilts_download.sh -skip-ssl **|
| Hi3861 solution (binary)       | 6.0.0.1 Release | [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/hispark_pegasus.tar.gz)| [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/hispark_pegasus.tar.gz.sha256)| 28.7 MB | / |
| Hi3516 solution-LiteOS (binary)| 6.0.0.1 Release | [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/hispark_taurus_LiteOS.tar.gz)| [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/hispark_taurus_LiteOS.tar.gz.sha256)| 353.3 MB | / |
| Hi3516 solution-Linux (binary) | 6.0.0.1 Release | [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/hispark_taurus_Linux.tar.gz)| [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/hispark_taurus_Linux.tar.gz.sha256)| 234.8 MB | / |
| RK3568 standard system solution (binary) ROM package       | 6.0.0.1 Release | [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/dayu200_standard_arm32_rom.tar.gz)| [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/dayu200_standard_arm32_rom.tar.gz.sha256)| 3.6 GB | / |
| RK3568 standard system solution (binary) XTS package       | 6.0.0.1 Release | [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/dayu200_standard_arm32_xts.tar.gz)| [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/dayu200_standard_arm32_xts.tar.gz.sha256)| 4.1 GB | / |
| Public SDK package for the standard system (macOS)            | 6.0.0.48 | [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/ohos-sdk-mac-public.tar.gz)| [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/ohos-sdk-mac-public.tar.gz.sha256)| 1.0 GB | / |
| Public SDK package for the standard system (macOS-M1)            | 6.0.0.48  | [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/L2-SDK-MAC-M1-PUBLIC.tar.gz)| [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/L2-SDK-MAC-M1-PUBLIC.tar.gz.sha256)| 1.2 GB | / |
| Public SDK package for the standard system (Windows/Linux)  | 6.0.0.48   | [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/ohos-sdk-windows_linux-public.tar.gz)| [Download](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/ohos-sdk-windows_linux-public.tar.gz.sha256)| 3.0 GB | / |

## What's New

N/A

## Fixed Bugs and Security Issues

**Table 3** Resolved issues

| Issue No.                                                     | Description                                                        |
| :----------------------------------------------------------- | ------------------------------------------------------------ |
| [280](https://gitcode.com/openharmony/resourceschedule_device_standby/issues/280) | **sysfreeze** occurred in **resource_schedule_service** due to **SERVICE_BLOCK**, stuck at **libstandby_service.z.so**.|
| [1698](https://gitcode.com/openharmony/hiviewdfx_faultloggerd/issues/1698) | **cppcrash** occurred in the **OS_DfxWatchdog** thread under the **multimodalinput** process, crash stack: **libunwinder.z.so**|
| [12365](https://gitcode.com/openharmony/window_window_manager/issues/12365) | [Program access control] Authorization failed when the non-transparent window occludes the position/pastes the control.     |
| [7191](https://gitcode.com/openharmony/multimedia_media_library/issues/7191) | **cppcrash** occurred in the **OS_IPC_1_1483** thread under the **com.ohos.medialibrary.medialibrarydata** process, crash stack: **libmedialibrary_data_extension.z.so**|
| [1688](https://gitcode.com/openharmony/hiviewdfx_faultloggerd/issues/1688) | **cppcrash** occurred in the **OS_DfxWatchdog** thread under the **camera_host** process, crash stack: **libunwinder.z.so**|
| [341](https://gitcode.com/openharmony/applications_notes/issues/341) | **jscrash** occurred in the **com.ohos.note** process, crash stack: **confirm**             |
| [828](https://gitcode.com/openharmony/applications_settings/issues/828) | **appfreeze** occurred in **com.ohos.settings** due to **THREAD_BLOCK_6S**       |
| [613](https://gitcode.com/openharmony/applications_systemui/issues/613) | **jscrash** occurred in the **com.ohos.systemui** process, crash stack: **createDataShare**     |
| [6157](https://gitcode.com/openharmony/drivers_peripheral/issues/6157) | **cppcrash** occurred in the **OS_IPC_2_2781** thread under the **camera_host** process, crash stack: **libcamera_host_vdi_impl_1.0.z.so**|
| [1485](https://gitcode.com/openharmony/resourceschedule_resource_schedule_service/issues/1485) | **cppcrash** occurred in the **OS_FFRT_2_3** thread under the **resource_schedule_service** process, crash stack: **Not mapped**|
| [11717](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/11717) | **cppcrash** occurred in the **OS_IPC_10_16215** thread under the **com.ohos.mms** process, crash stack: **libark_jsruntime.so**|
| [11961](https://gitcode.com/openharmony/window_window_manager/issues/11961) | [Window] Authorization failed when the paste control is occluded by the input method.                        |
| [11960](https://gitcode.com/openharmony/window_window_manager/issues/11960) | [Window] Authorization failed when the paste control is occluded by a child window.                        |
| [64924](https://gitcode.com/openharmony/arkui_ace_engine/issues/64924) | **cppcrash** occurred in the **OS_IPC_4_16933** thread under the **com.ohos.mms** process, crash stack: **libace_compatible.z.so**|
| [539](https://gitcode.com/openharmony/hiviewdfx_hilog/issues/539) | **cppcrash** occurred in the **OS_FFRT_Delay** thread under the **locationhub** process, crash stack: **libhilog.so**|
| [295](https://gitcode.com/openharmony/applications_mms/issues/295) | **jscrash** occurred in the **com.ohos.mms** process, stack name: **deleteAction**       |
| [296](https://gitcode.com/openharmony/applications_mms/issues/296) | **jscrash** occurred in the **com.ohos.mms** process, stack name: **anonymous**          |
| [63972](https://gitcode.com/openharmony/arkui_ace_engine/issues/63972) | **cppcrash** occurred in the **m.ohos.contacts** thread under the **com.ohos.contacts** process, crash stack: **libace_compatible.z.so**|
| [744](https://gitcode.com/openharmony/applications_photos/issues/744) | **jscrash** occurred in the **com.ohos.photos** process, stack name: **onPhotoChanged**  |
| [96](https://gitcode.com/openharmony/update_update_app/issues/96) | [Subsystem upgrade] The application crashes when the user clicks to download the installation package during software update.             |
| [4923](https://gitcode.com/openharmony/multimedia_player_framework/issues/4923) | **cppcrash** occurred in the **OS_IPC_1_598** thread under **/system/bin/bootanimation** process, crash stack: **libmedia_foundation.z.so**|

**Table 4** Fixed security vulnerabilities

| Vulnerability Ticket No.                                                    | Description                                                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [CVE-2025-40049](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8072) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2024-38594](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8072) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2024-47674](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8072) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2023-53673](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2023-53520](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-39902](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2023-53482](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2023-53596](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2023-53594](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2023-53491](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2022-49054](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-40016](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-40064](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-40105](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-40102](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-40035](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-40021](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-40054](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-40077](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-39902](https://gitcode.com/openharmony/kernel_linux_6.6/issues/176) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_6.6. |
| [CVE-2022-50552](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2023-53588](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2023-53577](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-39931](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-39913](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-39905](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2022-50445](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-39806](https://gitcode.com/openharmony/kernel_linux_6.6/issues/176) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_6.6. |
| [CVE-2025-39913](https://gitcode.com/openharmony/kernel_linux_6.6/issues/176) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_6.6. |
| [CVE-2025-39914](https://gitcode.com/openharmony/kernel_linux_6.6/issues/176) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_6.6. |
| [CVE-2025-39931](https://gitcode.com/openharmony/kernel_linux_6.6/issues/176) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_6.6. |
| [CVE-2025-39946](https://gitcode.com/openharmony/kernel_linux_6.6/issues/176) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_6.6. |
| [CVE-2025-38732](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-39702](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-39994](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-39683](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-38694](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8050) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-39689](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8050) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-39730](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8050) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-38680](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8050) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-39760](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8050) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-38702](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8050) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-39724](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2023-53221](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|
| [CVE-2025-39749](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8050) | [Vulnerability] [OpenHarmony-6.0-Release] A vulnerability exists in kernel_linux_5.10.|

## Known Issues

**Table 5** Known issues

| Issue No.| Description| Impact| To Be Resolved By|
| -------- | -------- | -------- | -------- |
| [23366](https://gitcode.com/openharmony/xts_acts/issues/23366) | Web suite execution failed during 6.0 Release XTS testing -xts_acts-AtomGit.| Failure of individual certification items.| 2025-12-30|
