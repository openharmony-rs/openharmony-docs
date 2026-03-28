# OpenHarmony 6.0.0.2 Release

## 版本概述

当前版本在OpenHarmony 6.0 Release的基础上，主要修复了linux kernel等开源组件的安全漏洞，增强了系统安全性。修复了部分功能和系统稳定性的issue，增强了系统稳定性。


## 配套关系

**表1** 版本软件和工具配套关系

| 软件 | 版本 | 备注 |
| -------- | -------- | -------- |
| OpenHarmony | 6.0.0.2 Release | NA |
| Public SDK | Ohos_sdk_public 6.0.0.49 (API Version 20 Release) | 面向应用开发者提供，不包含需要使用系统权限的系统接口。通过DevEco Studio默认获取的SDK为Public SDK。 |
| HUAWEI DevEco Studio（可选） | 6.0.0 Release | OpenHarmony应用开发推荐使用。<br />*待发布后提供*。 |
| HUAWEI DevEco Device Tool（可选） | 4.0 Release | OpenHarmony智能设备集成开发环境推荐使用。<br />[请点击这里获取](https://device.harmonyos.com/cn/develop/ide#download)。 |


## 源码获取


### 前提条件

1. 注册码云gitcode帐号。

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
   repo init -u git@gitcode.com:openharmony/manifest.git -b refs/tags/OpenHarmony-v6.0.0.2-Release --no-repo-verify
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
   repo init -u https://gitcode.com/openharmony/manifest -b refs/tags/OpenHarmony-v6.0.0.2-Release --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```


### 从镜像站点获取

**表2** 获取源码路径

| 版本源码                                | **版本信息** | **下载站点**                                                 | **SHA256校验码**                                             | **软件包容量** | 备注 |
| --------------------------------------- | ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | -------- | --------------------------------------- |
| 全量代码（标准、轻量和小型系统）        | 6.0.0.2 Release | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/code-v6.0.0.2-Release.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/code-v6.0.0.2-Release.tar.gz.sha256) | 57.2 GB | / |
| Hi3861解决方案（二进制）        | 6.0.0.2 Release | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/hispark_pegasus.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/hispark_pegasus.tar.gz.sha256) | 28.7 MB | / |
| Hi3516解决方案-LiteOS（二进制） | 6.0.0.2 Release | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/hispark_taurus_LiteOS.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/hispark_taurus_LiteOS.tar.gz.sha256) | 353.3 MB | / |
| Hi3516解决方案-Linux（二进制）  | 6.0.0.2 Release | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/hispark_taurus_Linux.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/hispark_taurus_Linux.tar.gz.sha256) | 234.8 MB | / |
| RK3568标准系统解决方案（二进制）ROM包        | 6.0.0.2 Release | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/dayu200_standard_arm32_rom.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/dayu200_standard_arm32_rom.tar.gz.sha256) | 3.6 GB | / |
| RK3568标准系统解决方案（二进制）XTS包        | 6.0.0.2 Release | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/dayu200_standard_arm32_xts.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/dayu200_standard_arm32_xts.tar.gz.sha256) | 4.1 GB | / |
| 标准系统Public SDK包（Mac）             | 6.0.0.49 | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/ohos-sdk-mac-public.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/ohos-sdk-mac-public.tar.gz.sha256) | 1.3 GB | / |
| 标准系统Public SDK包（Mac-M1）             | 6.0.0.49  | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/L2-SDK-MAC-M1-PUBLIC.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/L2-SDK-MAC-M1-PUBLIC.tar.gz.sha256) | 1.2 GB | / |
| 标准系统Public SDK包（Windows/Linux）   | 6.0.0.49   | [站点](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/ohos-sdk-windows_linux-public.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.0.0.2-Release/ohos-sdk-windows_linux-public.tar.gz.sha256) | 3.0 GB | / |

## 更新说明

API接口无变化。

## 修复缺陷和安全问题列表

**表3** 修复缺陷ISSUE列表

| ISSUE单                                                      | 描述                                                         |
| :----------------------------------------------------------- | ------------------------------------------------------------ |
| [886](https://gitcode.com/openharmony/print_print_fwk/issues/886) | GetPPDFile函数中存在路径遍历漏洞                             |
| [87](https://gitcode.com/openharmony/applications_filepicker/issues/87) | DownloadAuth.ets页面未注册到main_pages.json导致相关逻辑不可用 |
| [12590](https://gitcode.com/openharmony/window_window_manager/issues/12590) | 横屏状态左半屏幕点击无响应，鼠标光标移动方向错误             |
| [12343](https://gitcode.com/openharmony/window_window_manager/issues/12343) | rk3568修改显示配置，设置屏幕旋转后，触摸功能异常             |
| [759](https://gitcode.com/openharmony/applications_photos/issues/759) | 出现1次 进程com.ohos.photos下出现jscrash，栈名：getGeometryTransitionId |
| [2178](https://gitcode.com/openharmony/distributedhardware_device_manager/issues/2178) | 出现1次  进程device_manager下的OS_FFRT_2_4线程出现cppcrash，崩溃栈：libdevicemanagerserviceimpl.z.so |

**表4** 修复安全问题列表

| 漏洞单号                                                     | 漏洞描述                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [CVE-2025-8732](https://gitcode.com/openharmony/third_party_libxml2/issues/305) | 【漏洞】【OpenHarmony-6.0-Release】third_party_libxml2存在漏洞 |
| [CVE-2024-36933](https://gitcode.com/openharmony/kernel_linux_6.6/issues/206) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2024-36886](https://gitcode.com/openharmony/kernel_linux_6.6/issues/206) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68337](https://gitcode.com/openharmony/kernel_linux_6.6/issues/233) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-71077](https://gitcode.com/openharmony/kernel_linux_6.6/issues/237) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68282](https://gitcode.com/openharmony/kernel_linux_6.6/issues/237) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-71113](https://gitcode.com/openharmony/kernel_linux_6.6/issues/224) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2024-27399](https://gitcode.com/openharmony/kernel_linux_6.6/issues/224) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-71154](https://gitcode.com/openharmony/kernel_linux_6.6/issues/222) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2026-1757](https://gitcode.com/openharmony/third_party_libxml2/issues/324) | 【漏洞】【OpenHarmony-6.0-Release】third_party_libxml2存在漏洞 |
| [vul-1028052425900036096](https://gitcode.com/openharmony/kernel_liteos_a/issues/1055) | 【漏洞】【OpenHarmony-6.0-Release】kernel_liteos_a存在漏洞   |
| [CVE-2025-39772](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-39782](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-39787](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-40149](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68769](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68773](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68774](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68776](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68777](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68780](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68782](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68783](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68787](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68788](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [vul-1028454419206770688](https://gitcode.com/openharmony/kernel_liteos_a/issues/1057) | 【漏洞】【OpenHarmony-6.0-Release】kernel_liteos_a存在漏洞   |
| [CVE-2025-68795](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68796](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68797](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68799](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68800](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68801](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68804](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68808](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68320](https://gitcode.com/openharmony/kernel_linux_6.6/issues/195) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68809](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [CVE-2025-68813](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [vul-1034574030671187968](https://gitcode.com/openharmony/kernel_liteos_a/issues/1059) | 【漏洞】【OpenHarmony-6.0-Release】kernel_liteos_a存在漏洞   |
| [CVE-2026-2441](https://gitcode.com/openharmony/web_webview/issues/6118) | 【漏洞】【OpenHarmony-6.0-Release】third_party_chromium存在漏洞 |
| [CVE-2025-68814](https://gitcode.com/openharmony/kernel_linux_6.6/issues/197) | 【漏洞】【OpenHarmony-6.0-Release】kernel_linux_6.6存在漏洞  |
| [vul-993330609755525120](https://gitcode.com/openharmony/filemanagement_storage_service/issues/2100) | 【漏洞】【OpenHarmony-6.0-Release】filemanagement_storage_service存在漏洞 |
| [vul-1020139774691774464](https://gitcode.com/openharmony/filemanagement_storage_service/issues/2015) | 【漏洞】【OpenHarmony-6.0-Release】filemanagement_storage_service存在漏洞 |
| [vul-967294758072356864](https://gitcode.com/openharmony/multimedia_video_processing_engine/issues/35) | 【漏洞】【OpenHarmony-6.0-Release】multimedia_video_processing_engine存在漏洞 |
| [CVE-2025-14819](https://gitcode.com/openharmony/third_party_curl/issues/786) | 【漏洞】【OpenHarmony-6.0-Release】third_party_curl存在漏洞  |
| [vul-1016519491300888576](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12596) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [CVE-2025-28164](https://gitcode.com/openharmony/third_party_libpng/issues/65) | 【漏洞】【OpenHarmony-6.0-Release】third_party_libpng存在漏洞 |
| [vul-967624164078784512](https://gitcode.com/openharmony/multimedia_audio_framework/issues/11328) | 【漏洞】【OpenHarmony-6.0-Release】multimedia_audio_framework存在漏洞 |
| [CVE-2026-0992](https://gitcode.com/openharmony/third_party_libxml2/issues/319) | 【漏洞】【OpenHarmony-6.0-Release】third_party_libxml2存在漏洞 |
| [CVE-2026-0990](https://gitcode.com/openharmony/third_party_libxml2/issues/310) | 【漏洞】【OpenHarmony-6.0-Release】third_party_libxml2存在漏洞 |
| [CVE-2026-0989](https://gitcode.com/openharmony/third_party_libxml2/issues/320) | 【漏洞】【OpenHarmony-6.0-Release】third_party_libxml2存在漏洞 |
| [CVE-2026-22693](https://gitcode.com/openharmony/third_party_harfbuzz/issues/167) | 【漏洞】【OpenHarmony-6.0-Release】third_party_harfbuzz存在漏洞 |
| [CVE-2025-57812](https://gitcode.com/openharmony/third_party_cups-filters/issues/69) | 【漏洞】【OpenHarmony-6.0-Release】third_party_cups-filters存在漏洞 |
| [CVE-2025-69418](https://gitcode.com/openharmony/third_party_openssl/issues/738) | 【漏洞】【OpenHarmony-6.0-Release】third_party_openssl存在漏洞 |
| [vul-971258974047309824](https://gitcode.com/openharmony/web_webview/issues/5602) | 【漏洞】【OpenHarmony-6.0-Release】web_webview存在漏洞       |
| [vul-988540061932851200](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12460) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [vul-992868940461903872](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12461) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [vul-992873011839242240](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12462) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [vul-992873706646671360](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12463) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [vul-992875157146046464](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12464) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [vul-992875715764424704](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12465) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [vul-992876332423581696](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12466) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [vul-992877023896539136](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12478) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [vul-992877687074721792](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12476) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [vul-1003373640709836800](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12554) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [vul-1001577650784833536](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12475) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [vul-1001578305113034752](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12468) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [vul-1015504664445063168](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12555) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [vul-1015504954808340480](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12475) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [vul-1015520885076922368](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12556) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [vul-1016587161425678336](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12584) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [vul-1016587498429616128](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12597) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |
| [CVE-2025-64720](https://gitcode.com/openharmony/third_party_libpng/issues/54) | 【漏洞】【OpenHarmony-6.0-Release】third_party_libpng存在漏洞 |
| [CVE-2025-66293](https://gitcode.com/openharmony/third_party_libpng/issues/56) | 【漏洞】【OpenHarmony-6.0-Release】third_party_libpng存在漏洞 |
| [vul-993331502148227072](https://gitcode.com/openharmony/security_device_auth/issues/979) | 【漏洞】【OpenHarmony-6.0-Release】security_device_auth存在漏洞 |
| [vul-988540830165766144](https://gitcode.com/openharmony/filemanagement_dfs_service/issues/2902) | 【漏洞】【OpenHarmony-6.0-Release】filemanagement_dfs_service存在漏洞 |
| [CVE-886107548950728704](https://gitcode.com/openharmony/sensors_medical_sensor/issues/70) | 【漏洞】【OpenHarmony-6.0-Release】Sensors_medical_sensor存在漏洞 |
| [vul-965035802218205184](https://gitcode.com/openharmony/kernel_liteos_a/issues/1030) | 【漏洞】【OpenHarmony-6.0-Release】kernel_liteos_a存在漏洞   |
| [vul-980577404705574912](https://gitcode.com/openharmony/security_certificate_manager/issues/571) | 【漏洞】【OpenHarmony-6.0-Release】security_certificate_manager存在漏洞 |
| [vul-978760839278366720](https://gitcode.com/openharmony/security_certificate_manager/issues/571) | 【漏洞】【OpenHarmony-6.0-Release】security_certificate_manager存在漏洞 |
| [vul-968657437634596864](https://gitcode.com/openharmony/arkcompiler_ets_runtime/issues/12558) | 【漏洞】【OpenHarmony-6.0-Release】arkcompiler_ets_runtime存在漏洞 |

## 遗留缺陷列表

**表5** 遗留问题列表

| ISSUE | 问题描述 | 影响 | 计划解决日期 |
| -------- | -------- | -------- | -------- |
|   NA  |   NA    |   NA   |     NA       |
