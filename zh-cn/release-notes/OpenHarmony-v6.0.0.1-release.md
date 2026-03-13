# OpenHarmony 6.0.0.1 Release

## 版本概述

当前版本在OpenHarmony 6.0 Release的基础上，主要修复了linux kernel等开源组件的安全漏洞，增强了系统安全性。修复了部分功能和系统稳定性的issue，增强了系统稳定性。


## 配套关系

**表1** 版本软件和工具配套关系

| 软件 | 版本 | 备注 |
| -------- | -------- | -------- |
| OpenHarmony | 6.0.0.1 Release | NA |
| Public SDK | Ohos_sdk_public 6.0.0.48 (API Version 20 Release) | 面向应用开发者提供，不包含需要使用系统权限的系统接口。通过DevEco Studio默认获取的SDK为Public SDK。 |
| HUAWEI DevEco Studio（可选） | 6.0.0 Release | OpenHarmony应用开发推荐使用。<br />*待发布后提供*。 |
| HUAWEI DevEco Device Tool（可选） | 4.0 Release | OpenHarmony智能设备集成开发环境推荐使用。<br />[请点击这里获取](https://device.harmonyos.com/cn/develop/ide#download)。 |


## 源码获取


### 前提条件

1. 注册码云gitee帐号。

2. 注册码云SSH公钥，请参考[码云帮助中心](https://gitcode.com/help/articles/4191)。

3. 安装[git客户端](https://gitcode.com/link?target=https%3A%2F%2Fgit-scm.com%2Fbook%2Fzh%2Fv2%2F%25E8%25B5%25B7%25E6%25AD%25A5-%25E5%25AE%2589%25E8%25A3%2585-Git)和[git-lfs](https://gitcode.com/vcs-all-in-one/git-lfs?_from=gitee_search#downloading)并配置用户信息。
   ```bash
   git config --global user.name "yourname"
   git config --global user.email "your-email-address"
   git config --global credential.helper store
   ```

4. 安装码云repo工具，可以执行如下命令。
   ```bash
   curl -s https://gitcode.com/oschina/repo/raw/fork_flow/repo-py3 > /usr/local/bin/repo  #如果没有权限，可下载至其他目录，并将其配置到环境变量中chmod a+x /usr/local/bin/repo
   pip3 install -i https://repo.huaweicloud.com/repository/pypi/simple requests
   ```


### 通过repo获取

**方式一（推荐）**

通过repo + ssh 下载（需注册公钥，请参考[码云帮助中心](https://gitcode.com/help/articles/4191)）。

- 从版本分支获取源码。可获取该版本分支的最新源码，包括版本发布后在该分支的合入。
   ```bash
   repo init -u git@gitcode.com:openharmony/manifest.git -b OpenHarmony-6.0-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```
   
- 从版本发布Tag节点获取源码。可获取与版本发布时完全一致的源码。
   ```bash
   repo init -u git@gitcode.com:openharmony/manifest.git -b refs/tags/OpenHarmony-v6.0.0.1-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

**方式二**

通过repo + https 下载。

- 从版本分支获取源码。可获取该版本分支的最新源码，包括版本发布后在该分支的合入。
   ```bash
   repo init -u https://gitcode.com/openharmony/manifest -b OpenHarmony-6.0-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```
   
- 从版本发布Tag节点获取源码。可获取与版本发布时完全一致的源码。
   ```bash
   repo init -u https://gitcode.com/openharmony/manifest -b refs/tags/OpenHarmony-v6.0.0.1-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```


### 从镜像站点获取

**表2** 获取源码路径

| 版本源码                                | **版本信息** | **下载站点**                                                 | **SHA256校验码**                                             | **软件包容量** | 备注 |
| --------------------------------------- | ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | -------- | --------------------------------------- |
| 全量代码（标准、轻量和小型系统）        | 6.0.0.1 Release | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/code-v6.0.0.1-Release-20251216.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/code-v6.0.0.1-Release-20251216.tar.gz.sha256) | 55.1 GB | 建议：编译前请执行如下命令排除环境干扰：1) repo forall -c 'git reset --hard;git clean -fdx;git lfs pull'<br/>2) ./build/prebuilts_download.sh -skip-ssl |
| Hi3861解决方案（二进制）        | 6.0.0.1 Release | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/hispark_pegasus.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/hispark_pegasus.tar.gz.sha256) | 28.7 MB | / |
| Hi3516解决方案-LiteOS（二进制） | 6.0.0.1 Release | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/hispark_taurus_LiteOS.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/hispark_taurus_LiteOS.tar.gz.sha256) | 353.3 MB | / |
| Hi3516解决方案-Linux（二进制）  | 6.0.0.1 Release | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/hispark_taurus_Linux.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/hispark_taurus_Linux.tar.gz.sha256) | 234.8 MB | / |
| RK3568标准系统解决方案（二进制）ROM包        | 6.0.0.1 Release | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/dayu200_standard_arm32_rom.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/dayu200_standard_arm32_rom.tar.gz.sha256) | 3.6 GB | / |
| RK3568标准系统解决方案（二进制）XTS包        | 6.0.0.1 Release | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/dayu200_standard_arm32_xts.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/dayu200_standard_arm32_xts.tar.gz.sha256) | 4.1 GB | / |
| 标准系统Public SDK包（Mac）             | 6.0.0.48 | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/ohos-sdk-mac-public.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/ohos-sdk-mac-public.tar.gz.sha256) | 1.0 GB | / |
| 标准系统Public SDK包（Mac-M1）             | 6.0.0.48  | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/L2-SDK-MAC-M1-PUBLIC.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/L2-SDK-MAC-M1-PUBLIC.tar.gz.sha256) | 1.2 GB | / |
| 标准系统Public SDK包（Windows/Linux）   | 6.0.0.48   | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/ohos-sdk-windows_linux-public.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.1-Release/ohos-sdk-windows_linux-public.tar.gz.sha256) | 3.0 GB | / |

## 更新说明

API接口无变化。

## 修复缺陷和安全问题列表

**表3** 修复缺陷ISSUE列表

| ISSUE单                                                      | 描述                                                         |
| :----------------------------------------------------------- | ------------------------------------------------------------ |
| [280](https://gitcode.com/openharmony/resourceschedule_device_standby/issues/280) | 出现 resource_schedule_service由于SERVICE_BLOCK出现sysfreeze，卡在libstandby_service.z.so |
| [1698](https://gitcode.com/openharmony/hiviewdfx_faultloggerd/issues/1698) | 出现进程multimodalinput下的OS_DfxWatchdog线程出现cppcrash，崩溃栈：libunwinder.z.so |
| [12365](https://gitcode.com/openharmony/window_window_manager/issues/12365) | 【程序访问控制】不可透传窗口遮挡位置/粘贴控件时授权失败      |
| [7191](https://gitcode.com/openharmony/multimedia_media_library/issues/7191) | 出现进程com.ohos.medialibrary.medialibrarydata下的OS_IPC_1_1483线程出现cppcrash，崩溃栈：libmedialibrary_data_extension.z.so |
| [1688](https://gitcode.com/openharmony/hiviewdfx_faultloggerd/issues/1688) | 出现进程camera_host下的OS_DfxWatchdog线程出现cppcrash，崩溃栈：libunwinder.z.so |
| [341](https://gitcode.com/openharmony/applications_notes/issues/341) | 出现进程com.ohos.note出现jscrash，栈名：confirm              |
| [828](https://gitcode.com/openharmony/applications_settings/issues/828) | 出现com.ohos.settings由于THREAD_BLOCK_6S出现appfreeze        |
| [613](https://gitcode.com/openharmony/applications_systemui/issues/613) | 进程com.ohos.systemui出现jscrash，栈名：createDataShare      |
| [6157](https://gitcode.com/openharmony/drivers_peripheral/issues/6157) | 出现进程camera_host下的OS_IPC_2_2781线程出现cppcrash，崩溃栈：libcamera_host_vdi_impl_1.0.z.so |
| [1485](https://gitcode.com/openharmony/resourceschedule_resource_schedule_service/issues/1485) | 出现进程resource_schedule_service下的OS_FFRT_2_3线程出现cppcrash，崩溃栈：Not mapped |
| [11717](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/11717) | 出现进程com.ohos.mms下的OS_IPC_10_16215线程出现cppcrash，崩溃栈：libark_jsruntime.so |
| [11961](https://gitcode.com/openharmony/window_window_manager/issues/11961) | 【窗口】粘贴控件被输入法遮挡授权失败                         |
| [11960](https://gitcode.com/openharmony/window_window_manager/issues/11960) | 【窗口】粘贴控件被子窗口遮挡授权失败                         |
| [64924](https://gitcode.com/openharmony/arkui_ace_engine/issues/64924) | 出现进程com.ohos.mms下的OS_IPC_4_16933线程出现cppcrash，崩溃栈：libace_compatible.z.so |
| [539](https://gitcode.com/openharmony/hiviewdfx_hilog/issues/539) | 出现进程locationhub下的OS_FFRT_Delay线程出现cppcrash，崩溃栈：libhilog.so |
| [295](https://gitcode.com/openharmony/applications_mms/issues/295) | 出现进程com.ohos.mms下出现jscrash，栈名：deleteAction        |
| [296](https://gitcode.com/openharmony/applications_mms/issues/296) | 出现进程com.ohos.mms下出现jscrash，栈名：anonymous           |
| [63972](https://gitcode.com/openharmony/arkui_ace_engine/issues/63972) | 出现进程com.ohos.contacts下的m.ohos.contacts线程出现cppcrash，崩溃栈：libace_compatible.z.so |
| [744](https://gitcode.com/openharmony/applications_photos/issues/744) | 出现进程com.ohos.photos下出现jscrash，栈名：onPhotoChanged   |
| [96](https://gitcode.com/openharmony/update_update_app/issues/96) | 【升级子系统】软件更新点击下载安装包时，app闪退              |
| [4923](https://gitcode.com/openharmony/multimedia_player_framework/issues/4923) | 出现进程/system/bin/bootanimation下的OS_IPC_1_598线程出现cppcrash，崩溃栈：libmedia_foundation.z.so |

**表4** 修复安全问题列表

| 漏洞单号                                                     | 漏洞描述                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [CVE-2025-40049](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8072) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2024-38594](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8072) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2024-47674](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8072) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2023-53673](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2023-53520](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-39902](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2023-53482](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2023-53596](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2023-53594](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2023-53491](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2022-49054](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-40016](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-40064](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-40105](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-40102](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-40035](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-40021](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-40054](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-40077](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-39902](https://gitcode.com/openharmony/kernel_linux_6.6/issues/176) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2022-50552](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2023-53588](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2023-53577](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-39931](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-39913](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-39905](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2022-50445](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-39806](https://gitcode.com/openharmony/kernel_linux_6.6/issues/176) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-39913](https://gitcode.com/openharmony/kernel_linux_6.6/issues/176) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-39914](https://gitcode.com/openharmony/kernel_linux_6.6/issues/176) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-39931](https://gitcode.com/openharmony/kernel_linux_6.6/issues/176) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-39946](https://gitcode.com/openharmony/kernel_linux_6.6/issues/176) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-38732](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-39702](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8063) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-39994](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-39683](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-38694](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8050) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-39689](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8050) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-39730](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8050) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-38680](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8050) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-39760](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8050) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-38702](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8050) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-39724](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2023-53221](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8056) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |
| [CVE-2025-39749](https://gitcode.com/openharmony/kernel_linux_5.10/issues/8050) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_5.10存在漏洞 |

## 遗留缺陷列表

**表5** 遗留问题列表

| ISSUE | 问题描述 | 影响 | 计划解决日期 |
| -------- | -------- | -------- | -------- |
| [23366](https://gitcode.com/openharmony/xts_acts/issues/23366) | 6.0release XTS执行测试，web部分套件执行失败-xts_acts-AtomGit | 个别认证项失败 | 2025年12月30日 |
