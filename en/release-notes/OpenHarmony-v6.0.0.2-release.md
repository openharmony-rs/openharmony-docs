# OpenHarmony 6.0.0.2 Release

<!-- md-trans-meta sourceCommit=34bc44ee002fd40552914869d77189df9fa2a4fa translatedAt=2026-09-17T04:24:14.136Z pushedAt=2026-09-17T09:21:55.838Z -->

## Version Overview

Based on OpenHarmony 6.0 Release, this version mainly fixes security vulnerabilities in open-source components such as the Linux kernel, enhancing system security. It also fixes issues related to certain functions and system stability, improving system stability.


## Version Mapping

**Table 1** Software and tool version mapping

| Software | Version | Remarks |
| -------- | -------- | -------- |
| OpenHarmony | 6.0.0.2 Release | NA |
| Public SDK | Ohos_sdk_public 6.0.0.49 (API Version 20 Release) | Provided for application developers. It does not include system APIs that require system permissions. The SDK obtained by default through DevEco Studio is the Public SDK. |
| HUAWEI DevEco Studio (optional) | 6.0.0 Release | Recommended for OpenHarmony application development.<br />*To be provided after release*. |
| HUAWEI DevEco Device Tool (optional) | 4.0 Release | Recommended as the integrated development environment for OpenHarmony smart devices.<br />[Click here to obtain](https://device.harmonyos.com/en/develop/ide#download). |


## Source Code Acquisition


### Prerequisites

1. Register a GitCode account.

2. Register an SSH public key on GitCode.

3. Install the [Git client](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and [git-lfs](https://gitcode.com/vcs-all-in-one/git-lfs?_from=gitee_search#downloading), and configure the user information.
   ```bash
   git config --global user.name "yourname"
   git config --global user.email "your-email-address"
   git config --global credential.helper store
   ```

4. Install the GitCode repo tool by running the following command.
   ```bash
   curl -s https://gitcode.com/oschina/repo/raw/fork_flow/repo-py3 > /usr/local/bin/repo  #If you do not have the permission, download it to another directory and configure it in the environment variables.
   chmod a+x /usr/local/bin/repo
   pip3 install -i https://repo.huaweicloud.com/repository/pypi/simple requests
   ```


### Obtaining Source Code via repo

**Method 1 (Recommended)**

Download the source code via repo + SSH (you need to register a public key first).

- Obtain the source code from the version branch. This gives you the latest source code of the version branch, including changes merged into the branch after the version release.
   ```bash
   repo init -u git@gitcode.com:openharmony/manifest.git -b OpenHarmony-6.0-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

- Obtain the source code from the version release tag. This gives you source code that is exactly the same as that at the time of the version release.
   ```bash
   repo init -u git@gitcode.com:openharmony/manifest.git -b refs/tags/OpenHarmony-v6.0.0.2-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

**Method 2**

Download the source code via repo + HTTPS.

- Obtain the source code from the version branch. This gives you the latest source code of the version branch, including changes merged into the branch after the version release.
   ```bash
   repo init -u https://gitcode.com/openharmony/manifest -b OpenHarmony-6.0-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

- Obtain the source code from the version release tag. This gives you source code that is exactly the same as that at the time of the version release.
   ```bash
   repo init -u https://gitcode.com/openharmony/manifest -b refs/tags/OpenHarmony-v6.0.0.2-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```


### Obtaining Source Code from a Mirror Site

**Table 2** Source code paths

| Version Source Code                                | **Version Information** | **Download Site**                                                 | **SHA256 Checksum**                                             | **Package Size** | Remarks |
| --------------------------------------- | ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | -------- | --------------------------------------- |
| Full code (standard, lightweight, and small systems)        | 6.0.0.2 Release | [site](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/code-v6.0.0.2-Release.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/code-v6.0.0.2-Release.tar.gz.sha256) | 57.2 GB | / |
| Hi3861 solution (binary)        | 6.0.0.2 Release | [site](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/hispark_pegasus.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/hispark_pegasus.tar.gz.sha256) | 28.7 MB | / |
| Hi3516 solution - LiteOS (binary) | 6.0.0.2 Release | [site](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/hispark_taurus_LiteOS.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/hispark_taurus_LiteOS.tar.gz.sha256) | 353.3 MB | / |
| Hi3516 solution - Linux (binary)  | 6.0.0.2 Release | [site](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/hispark_taurus_Linux.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/hispark_taurus_Linux.tar.gz.sha256) | 234.8 MB | / |
| RK3568 standard system solution (binary) ROM package        | 6.0.0.2 Release | [site](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/dayu200_standard_arm32_rom.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/dayu200_standard_arm32_rom.tar.gz.sha256) | 3.6 GB | / |
| RK3568 standard system solution (binary) XTS package        | 6.0.0.2 Release | [site](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/dayu200_standard_arm32_xts.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/dayu200_standard_arm32_xts.tar.gz.sha256) | 4.1 GB | / |
| Standard system Public SDK package (Mac)             | 6.0.0.49 | [site](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/ohos-sdk-mac-public.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/ohos-sdk-mac-public.tar.gz.sha256) | 1.3 GB | / |
| Standard system Public SDK package (Mac-M1)             | 6.0.0.49  | [site](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/L2-SDK-MAC-M1-PUBLIC.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/L2-SDK-MAC-M1-PUBLIC.tar.gz.sha256) | 1.2 GB | / |
| Standard system Public SDK package (Windows/Linux)   | 6.0.0.49   | [site](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/ohos-sdk-windows_linux-public.tar.gz) | [SHA256 checksum](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/ohos-sdk-windows_linux-public.tar.gz.sha256) | 3.0 GB | / |

## Update Notes

There are no API changes.

## Fixed Defects and Security Issues

**Table 3** Fixed defects

| ISSUE                                                      | Description                                                         |
| :----------------------------------------------------------- | ------------------------------------------------------------ |
| [886](https://gitcode.com/openharmony/print_print_fwk/issues/886) | A path traversal vulnerability exists in the GetPPDFile function                             |
| [87](https://gitcode.com/openharmony/applications_filepicker/issues/87) | The DownloadAuth.ets page is not registered in main_pages.json, causing the related logic to be unavailable |
| [12590](https://gitcode.com/openharmony/window_window_manager/issues/12590) | In landscape mode, the left half of the screen does not respond to clicks, and the mouse cursor moves in the wrong direction             |
| [12343](https://gitcode.com/openharmony/window_window_manager/issues/12343) | On rk3568, after modifying the display configuration and setting screen rotation, the touch function becomes abnormal             |
| [759](https://gitcode.com/openharmony/applications_photos/issues/759) | A jscrash occurred once in the com.ohos.photos process, with the stack name: getGeometryTransitionId |
| [2178](https://gitcode.com/openharmony/distributedhardware_device_manager/issues/2178) | A cppcrash occurred once in the OS_FFRT_2_4 thread under the device_manager process, with the crash stack: libdevicemanagerserviceimpl.z.so |

**Table 4** Fixed Security Issue List

| Vulnerability ID                                                     | Vulnerability Description                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [CVE-2025-8732](https://gitcode.com/openharmony/third_party_libxml2/issues/305) | [Vulnerability][OpenHarmony-6.0-Release] third_party_libxml2 has a vulnerability |
| [CVE-2024-36933](https://gitcode.com/openharmony/kernel_linux_6.6/issues/206) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2024-36886](https://gitcode.com/openharmony/kernel_linux_6.6/issues/206) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68337](https://gitcode.com/openharmony/kernel_linux_6.6/issues/233) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-71077](https://gitcode.com/openharmony/kernel_linux_6.6/issues/237) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68282](https://gitcode.com/openharmony/kernel_linux_6.6/issues/237) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-71113](https://gitcode.com/openharmony/kernel_linux_6.6/issues/224) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2024-27399](https://gitcode.com/openharmony/kernel_linux_6.6/issues/224) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-71154](https://gitcode.com/openharmony/kernel_linux_6.6/issues/222) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2026-1757](https://gitcode.com/openharmony/third_party_libxml2/issues/324) | [Vulnerability][OpenHarmony-6.0-Release] third_party_libxml2 has a vulnerability |
| [vul-1028052425900036096](https://gitcode.com/openharmony/kernel_liteos_a/issues/1055) | [Vulnerability][OpenHarmony-6.0-Release] kernel_liteos_a has a vulnerability   |
| [CVE-2025-39772](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-39782](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-39787](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-40149](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68769](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68773](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68774](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68776](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68777](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68780](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68782](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68783](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68787](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68788](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [vul-1028454419206770688](https://gitcode.com/openharmony/kernel_liteos_a/issues/1057) | [Vulnerability][OpenHarmony-6.0-Release] kernel_liteos_a has a vulnerability   |
| [CVE-2025-68795](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68796](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68797](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68799](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68800](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68801](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68804](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68808](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68320](https://gitcode.com/openharmony/kernel_linux_6.6/issues/195) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68809](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [CVE-2025-68813](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [vul-1034574030671187968](https://gitcode.com/openharmony/kernel_liteos_a/issues/1059) | [Vulnerability][OpenHarmony-6.0-Release] kernel_liteos_a has a vulnerability   |
| [CVE-2026-2441](https://gitcode.com/openharmony/web_webview/issues/6118) | [Vulnerability][OpenHarmony-6.0-Release] third_party_chromium has a vulnerability |
| [CVE-2025-68814](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | [Vulnerability][OpenHarmony-6.0-Release] kernel_linux_6.6 has a vulnerability  |
| [vul-993330609755525120](https://gitcode.com/openharmony/filemanagement_storage_service/issues/2100) | [Vulnerability][OpenHarmony-6.0-Release] filemanagement_storage_service has a vulnerability |
| [vul-1020139774691774464](https://gitcode.com/openharmony/filemanagement_storage_service/issues/2015) | [Vulnerability][OpenHarmony-6.0-Release] filemanagement_storage_service has a vulnerability |
| [vul-967294758072356864](https://gitcode.com/openharmony/multimedia_video_processing_engine/issues/35) | [Vulnerability][OpenHarmony-6.0-Release] multimedia_video_processing_engine has a vulnerability |
| [CVE-2025-14819](https://gitcode.com/openharmony/third_party_curl/issues/786) | [Vulnerability][OpenHarmony-6.0-Release] third_party_curl has a vulnerability  |
| [vul-1016519491300888576](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12596) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [CVE-2025-28164](https://gitcode.com/openharmony/third_party_libpng/issues/65) | [Vulnerability][OpenHarmony-6.0-Release] third_party_libpng has a vulnerability |
| [vul-967624164078784512](https://gitcode.com/openharmony/multimedia_audio_framework/issues/11328) | [Vulnerability][OpenHarmony-6.0-Release] multimedia_audio_framework has a vulnerability |
| [CVE-2026-0992](https://gitcode.com/openharmony/third_party_libxml2/issues/319) | [Vulnerability][OpenHarmony-6.0-Release] third_party_libxml2 has a vulnerability |
| [CVE-2026-0990](https://gitcode.com/openharmony/third_party_libxml2/issues/310) | [Vulnerability][OpenHarmony-6.0-Release] third_party_libxml2 has a vulnerability |
| [CVE-2026-0989](https://gitcode.com/openharmony/third_party_libxml2/issues/320) | [Vulnerability][OpenHarmony-6.0-Release] third_party_libxml2 has a vulnerability |
| [CVE-2026-22693](https://gitcode.com/openharmony/third_party_harfbuzz/issues/167) | [Vulnerability][OpenHarmony-6.0-Release] third_party_harfbuzz has a vulnerability |
| [CVE-2025-57812](https://gitcode.com/openharmony/third_party_cups-filters/issues/69) | [Vulnerability][OpenHarmony-6.0-Release] third_party_cups-filters has a vulnerability |
| [CVE-2025-69418](https://gitcode.com/openharmony/third_party_openssl/issues/738) | [Vulnerability][OpenHarmony-6.0-Release] third_party_openssl has a vulnerability |
| [vul-971258974047309824](https://gitcode.com/openharmony/web_webview/issues/5602) | [Vulnerability][OpenHarmony-6.0-Release] web_webview has a vulnerability       |
| [vul-988540061932851200](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12460) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [vul-992868940461903872](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12461) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [vul-992873011839242240](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12462) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [vul-992873706646671360](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12463) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [vul-992875157146046464](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12464) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [vul-992875715764424704](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12465) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [vul-992876332423581696](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12466) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [vul-992877023896539136](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12478) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [vul-992877687074721792](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12476) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [vul-1003373640709836800](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12554) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [vul-1001577650784833536](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12475) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [vul-1001578305113034752](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12468) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [vul-1015504664445063168](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12555) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [vul-1015504954808340480](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12475) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [vul-1015520885076922368](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12556) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [vul-1016587161425678336](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12584) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [vul-1016587498429616128](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12597) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |
| [CVE-2025-64720](https://gitcode.com/openharmony/third_party_libpng/issues/54) | [Vulnerability][OpenHarmony-6.0-Release] third_party_libpng has a vulnerability |
| [CVE-2025-66293](https://gitcode.com/openharmony/third_party_libpng/issues/56) | [Vulnerability][OpenHarmony-6.0-Release] third_party_libpng has a vulnerability |
| [vul-993331502148227072](https://gitcode.com/openharmony/security_device_auth/issues/979) | [Vulnerability][OpenHarmony-6.0-Release] security_device_auth has a vulnerability |
| [vul-988540830165766144](https://gitcode.com/openharmony/filemanagement_dfs_service/issues/2902) | [Vulnerability][OpenHarmony-6.0-Release] filemanagement_dfs_service has a vulnerability |
| [CVE-886107548950728704](https://gitcode.com/openharmony/sensors_medical_sensor/issues/70) | [Vulnerability][OpenHarmony-6.0-Release] Sensors_medical_sensor has a vulnerability |
| [vul-965035802218205184](https://gitcode.com/openharmony/kernel_liteos_a/issues/1030) | [Vulnerability][OpenHarmony-6.0-Release] kernel_liteos_a has a vulnerability   |
| [vul-980577404705574912](https://gitcode.com/openharmony/security_certificate_manager/issues/571) | [Vulnerability][OpenHarmony-6.0-Release] security_certificate_manager has a vulnerability |
| [vul-978760839278366720](https://gitcode.com/openharmony/security_certificate_manager/issues/571) | [Vulnerability][OpenHarmony-6.0-Release] security_certificate_manager has a vulnerability |
| [vul-968657437634596864](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12558) | [Vulnerability][OpenHarmony-6.0-Release] arkcompiler_ets_runtime has a vulnerability |

## Known Issues

**Table 5** Known issues

| ISSUE | Issue Description | Impact | Planned Resolution Date |
| -------- | -------- | -------- | -------- |
|   NA  |   NA    |   NA   |     NA       |

## Other Notes
Some hyphenation resource files for certain languages in the third-party library `third_party_tex-hyphen` are subject to the GPL/LGPL open source licenses. Using these resource files in an application may expose the application source code to the risk of passive open-sourcing. Therefore, it is recommended that you delete the following resource files in actual product use:

- hyph-cs.tex [Czech]
- hyph-id.tex [Indonesian]
- hyph-lv.tex [Latvian]
- hyph-mk.tex [Macedonian]
- hyph-sk.tex [Slovak]
- hyph-sr-cyrl.tex [Serbian Cyrillic]

After deleting these resource files, when the application processes text layout for the above languages, the automatic word-breaking function using the hyphen "-" will be unavailable because the corresponding ".tex" hyphenation rule files are missing. If you need to continue supporting word breaking for these languages, it is recommended that you look for a third-party hyphenation algorithm library based on permissive licenses such as MIT, Apache 2.0, or BSD.
