# OpenHarmony 6.1.1 LTS

## 版权和许可声明

本项目贡献依据 **《开发者原创声明》（DCO）** 授权给开放原子开源基金会。本项目是由许多开源软件组件组成的汇编作品，该汇编作品的版权归开放原子开源基金会所有。开放原子开源基金会根据Apache 2.0开源许可协议（以下简称 **Apache 2.0** ）向您提供该汇编作品的授权。

在遵守Apache 2.0，以及本项目包含的开源软件组件适用的对应开源许可协议的前提下，您方可使用本项目。您可以通过以下网址获取Apache 2.0副本：
**[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0#/session/_blank)**

除非适用法律要求或书面约定，依据适用的开源许可协议分发的软件均按“原样”提供，且不附带任何（明示或默示）形式的保证或条件。有关适用的开源许可协议的具体授权和限制，请参见其原文。

## 版本概述

OpenHarmony在6.1 LTS版本的基础上，更新发布6.1.1 LTS版本，在小型系统进行了相关增强。

#### **[小型系统支持JS应用不同页面之间切换的动效](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-LTS/zh-cn/device-dev/quick-start/application-adapter/quickstart-lite-router-page-transition.md)**

- 支持JS页面淡入淡出、上下滑动、页面左右滑动等场景的切换动效
- 支持JS应用不同页面之间切换的缩放动效

#### **[小型系统图形UI组件，Flex CSS布局等能力增强](https://gitcode.com/openharmony/docs/blob/OpenHarmony-6.1-LTS/zh-cn/device-dev/quick-start/application-adapter/README-CN.md)**

- 支持过渡、路径、专场等动画能力
- 支持对角线以及0度，45度，90度以及135度方向的线性渐变能力
- 支持SVG基础形状/路劲/渐变渲染能力、支持SVG多层叠加/同心圆/文本绘制以及SVG动画渲染能力，等
- Flex 支持容器方向控制、主轴对齐控制、交叉轴对齐、换行、子项伸缩等css能力适配
- Slider组件能力适配：刻度值数组，背景色/前景色管理、刻度标识大小，刻度值文字显示，扩展区域点击，等


#### **[小型系统分布式互联互通能力](https://gitcode.com/openharmony/communication_dsoftbus/blob/master/README_zh.md)**

- 小型设备支持分布式软总线同局域网设备与L2设备互通
- 分布式软总线发现小型化，支持动态裁剪资源优化，支持同局域网发现协议扩展厂商自定义字段
- 支持动态裁剪资源优化，包括软总线连接小型化、组网小型化，决策中心小型化，等
- 支持设备hichain依赖HUKS算法能力适配、支持IS凭据管理及认证能力，等
- DM支持设备发布和发现功能，支持设备上下线监听功能




## 配套关系

**表1** 版本软件和工具配套关系

| 软件 | 版本 | 备注 | 
| -------- | -------- | -------- |
| OpenHarmony | 6.1.1 LTS | NA | 
| Public SDK | Ohos_sdk_public 6.1.0.35 (API Version 23 Release) | 面向应用开发者提供，不包含需要使用系统权限的系统接口。通过DevEco Studio默认获取的SDK为Public SDK。 | 
| HarmonyOS SDK for OpenHarmony | 6.1 Release | 面向OpenHarmony生态提供的标准化开发工具套件，扩展了OpenHarmony SDK的能力。<br />详见[HarmonyOS SDK for OpenHarmony](https://gitcode.com/harmonyos-sdk-for-openharmony/docs/blob/6.1-release/README.md) | 
| HUAWEI DevEco Studio（可选） | 6.1.0 Release | OpenHarmony应用开发推荐使用。<br />[请点击这里获取](https://developer.huawei.com/consumer/cn/download/)。 | 
| HUAWEI DevEco Device Tool（可选） | 4.0 Release | OpenHarmony智能设备集成开发环境推荐使用。<br />[请点击这里获取](https://device.harmonyos.com/cn/develop/ide#download)。 | 


### 前提条件

1. 注册gitcode账号。

2. 注册gitcode的SSH公钥，请参考[gitcode帮助中心](https://docs.gitcode.com/docs/help/home/user_center/security_management/ssh)。

3. 安装[git客户端](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)和[git-lfs](https://gitcode.com/gh_mirrors/gi/git-lfs?source_module=search_result_repo)并配置用户信息。
  
   ```shell
   git config --global user.name "yourname"
   git config --global user.email "your-email-address"
   git config --global credential.helper store
   ```

4. 执行如下命令安装gitcode的repo工具。

   下述命令中的安装路径以"~/bin"为例，请用户自行创建所需目录。
  
   ```shell
   mkdir ~/bin
   curl https://raw.gitcode.com/gitcode-dev/repo/raw/main/repo-py3 -o ~/bin/repo
   chmod a+x ~/bin/repo
   pip3 install -i https://repo.huaweicloud.com/repository/pypi/simple requests
   ```

5. 将repo添加到环境变量。

   ```shell
   vim ~/.bashrc               # 编辑环境变量
   export PATH=~/bin:$PATH     # 在环境变量的最后添加一行repo路径信息
   source ~/.bashrc            # 应用环境变量
   ```


### 通过repo获取

**方式一（推荐）**

通过repo + ssh 下载（需注册公钥，请参考[gitcode帮助中心](https://docs.gitcode.com/docs/help/home/user_center/security_management/ssh)）。

- 从版本分支获取源码。可获取该版本分支的最新源码，包括版本发布后在该分支的合入。
   ```shell
   repo init -u git@gitcode.com:openharmony/manifest.git -b OpenHarmony-6.1-LTS --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```
   
- 从版本发布Tag节点获取源码。可获取与版本发布时完全一致的源码。
   ```shell
   repo init -u git@gitcode.com:openharmony/manifest.git -b refs/tags/OpenHarmony-v6.1.1-LTS --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

**方式二**

通过repo + https 下载。

- 从版本分支获取源码。可获取该版本分支的最新源码，包括版本发布后在该分支的合入。
   ```shell
   repo init -u https://gitcode.com/openharmony/manifest -b OpenHarmony-6.1-LTS --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```
   
- 从版本发布Tag节点获取源码。可获取与版本发布时完全一致的源码。
   ```shell
   repo init -u https://gitcode.com/openharmony/manifest -b refs/tags/OpenHarmony-v6.1.1-LTS --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```


### 前提条件

1. 注册gitcode账号。

2. 注册gitcode的SSH公钥，请参考[gitcode帮助中心](https://docs.gitcode.com/docs/help/home/user_center/security_management/ssh)。

3. 安装[git客户端](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)和[git-lfs](https://gitcode.com/gh_mirrors/gi/git-lfs?source_module=search_result_repo)并配置用户信息。
  
   ```shell
   git config --global user.name "yourname"
   git config --global user.email "your-email-address"
   git config --global credential.helper store
   ```

4. 执行如下命令安装gitcode的repo工具。

   下述命令中的安装路径以"~/bin"为例，请用户自行创建所需目录。
  
   ```shell
   mkdir ~/bin
   curl https://raw.gitcode.com/gitcode-dev/repo/raw/main/repo-py3 -o ~/bin/repo
   chmod a+x ~/bin/repo
   pip3 install -i https://repo.huaweicloud.com/repository/pypi/simple requests
   ```

5. 将repo添加到环境变量。

   ```shell
   vim ~/.bashrc               # 编辑环境变量
   export PATH=~/bin:$PATH     # 在环境变量的最后添加一行repo路径信息
   source ~/.bashrc            # 应用环境变量
   ```


### 通过repo获取

**方式一（推荐）**

通过repo + ssh 下载（需注册公钥，请参考[码云帮助中心](https://gitcode.com/help/articles/4191)）。

- 从版本分支获取源码。可获取该版本分支的最新源码，包括版本发布后在该分支的合入。
   ```
   repo init -u git@gitcode.com:openharmony/manifest.git -b OpenHarmony-6.1-LTS --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```
   
- 从版本发布Tag节点获取源码。可获取与版本发布时完全一致的源码。
   ```
   repo init -u git@gitcode.com:openharmony/manifest.git -b refs/tags/OpenHarmony-v6.1.1-LTS --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

**方式二**

通过repo + https 下载。

- 从版本分支获取源码。可获取该版本分支的最新源码，包括版本发布后在该分支的合入。
   ```
   repo init -u https://gitcode.com/openharmony/manifest -b OpenHarmony-6.1-LTS --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```
   
- 从版本发布Tag节点获取源码。可获取与版本发布时完全一致的源码。
   ```
   repo init -u https://gitcode.com/openharmony/manifest -b refs/tags/OpenHarmony-v6.1.1-LTS --no-repo-verify
   repo sync -c
   repo forall -c 'git lfs pull'
   ```

### 从镜像站点获取

**表2** 获取源码路径

| 版本源码 | **版本信息** | **下载站点** | **SHA256校验码** | **软件包容量** |
|---------------------------------------|------------|------------------------------------------------------------|------------------------------------------------------------|--------|
| 全量代码（标准、轻量和小型系统）        | 6.1.1 LTS    | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/code-v6.1-LTS.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/code-v6.1-LTS.tar.gz.sha256) | 69.3 GB |
| Hi3861解决方案（二进制）        | 6.1.1 LTS    | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_pegasus.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_pegasus.tar.gz.sha256) | 28.8 MB |
| Hi3863解决方案（二进制）        | 6.1.1 LTS    | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_pegasus_3863.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_pegasus_3863.tar.gz.sha256) | 8.0 MB |
| Hi3861 64K解决方案（二进制）        | 6.1.1 LTS    | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_pegasus_64k.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_pegasus_64k.tar.gz.sha256) | 7.9 MB |
| Hi3863 64K解决方案（二进制）        | 6.1.1 LTS    | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_pegasus_3863_64k.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_pegasus_3863_64k.tar.gz.sha256) | 3.0 MB |
| Hi3516解决方案-LiteOS（二进制） | 6.1.1 LTS    | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_taurus_LiteOS.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_taurus_LiteOS.tar.gz.sha256) | 359.7 MB |
| Hi3516解决方案-Linux（二进制）  | 6.1.1 LTS    | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_taurus_Linux.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/hispark_taurus_Linux.tar.gz.sha256) | 238.5 MB |
| RK3568标准系统解决方案（二进制）ROM包        | 6.1.1 LTS    | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/dayu200_standard_arm32_rom.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/dayu200_standard_arm32_rom.tar.gz.sha256) | 4.0 GB |
| RK3568标准系统解决方案（二进制）XTS包        | 6.1.1 LTS    | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/dayu200_standard_arm32_xts.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/dayu200_standard_arm32_xts.tar.gz.sha256) | 4.4 GB |
| P7885标准系统解决方案（二进制）ROM包        | 6.1.1 LTS    | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/dayu600_standard_arm32_rom.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/dayu600_standard_arm32_rom.tar.gz.sha256) | 6.0 GB |
| P7885标准系统解决方案（二进制）XTS包        | 6.1.1 LTS    | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/dayu600_standard_arm32_xts.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/dayu600_standard_arm32_xts.tar.gz.sha256) | 4.5 GB |
| 标准系统Public SDK包（Mac）             | 6.1.0.43 | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/ohos-sdk-mac-public.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/ohos-sdk-mac-public.tar.gz.sha256) | 1.3 GB |
| 标准系统Public SDK包（Mac-M1）             | 6.1.0.43  | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/L2-SDK-MAC-M1-PUBLIC.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/L2-SDK-MAC-M1-PUBLIC.tar.gz.sha256) | 1.2 GB |
| 标准系统Public SDK包（Windows/Linux）   | 6.1.0.43   | [站点](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/ohos-sdk-windows_linux-public.tar.gz) | [SHA256校验码](https://repo.huaweicloud.com/openharmony/os/6.1-LTS/ohos-sdk-windows_linux-public.tar.gz.sha256) | 3.0 GB |

## 遗留缺陷列表

**表4** 遗留缺陷列表

| ISSUE | 问题描述 | 影响 | 计划解决时间或版本 | 
| -------- | -------- | -------- | -------- |
| [13048](https://gitcode.com/openharmony/multimedia_audio_framework/issues/13048) | 进程audio_server有低概率因libaudio_policy_service.z.so导致cppcrash。 | 进程会自动重启 | 7.0版本 |
| [51](https://gitcode.com/openharmony/device_soc_unisoc/issues/51) | 测试过程中P7885开发板低概率出现白屏，显示`abnormal mode: init-mmc-fat failed Please check SD card`。原因为测试用例进入到updater模式导致。 | 不进入updater模式可规避此问题。<br />P7885开发板计划在7.1版本适配updater模式。 | 7.1版本 |
| [24762](https://gitcode.com/openharmony/graphic_graphic_2d/issues/24762) | P7885开发板配套Vulkan版本为1.2，测试套件要求Vulkan版本高于1.3，导致部分测试用例执行失败。 | 不影响正常使用，兼容性认证时建议申请豁免。<br />P7885开发板计划在7.1版本升级Vulkan版本。 | 7.1版本 |
