# OpenHarmony 6.1 LTS

## 版权和许可声明

本项目贡献依据 **《开发者原创声明》（DCO）** 授权给开放原子开源基金会。本项目是由许多开源软件组件组成的汇编作品，该汇编作品的版权归开放原子开源基金会所有。开放原子开源基金会根据Apache 2.0开源许可协议（以下简称 **Apache 2.0** ）向您提供该汇编作品的授权。

在遵守Apache 2.0，以及本项目包含的开源软件组件适用的对应开源许可协议的前提下，您方可使用本项目。您可以通过以下网址获取Apache 2.0副本：
**[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0#/session/_blank)**

除非适用法律要求或书面约定，依据适用的开源许可协议分发的软件均按“原样”提供，且不附带任何（明示或默示）形式的保证或条件。有关适用的开源许可协议的具体授权和限制，请参见其原文。

## 版本概述

OpenHarmony在6.1 Release版本的基础上，更新发布6.1 LTS版本。相比6.1 Release，6.1 LTS版本，在标准系统能力方面引入了一款新的开发板“展锐P7885芯片开发板”，并针对这款开发板进行一系列能力新增和增强，以及预置应用的适配；在轻量系统和小型系统的能力无新增。

### 新增能力

- 新增对统一SDK的支持。统一SDK是面向OpenHarmony生态提供的标准化开发工具套件，扩展了OpenHarmony SDK的能力，为开发者提供远场通信、基础语音、分享服务、基础视觉、桌面拓展、文件预览、推送服务、统一扫码服务等多维度开发能力。详见[HarmonyOS SDK for OpenHarmony](https://gitcode.com/harmonyos-sdk-for-openharmony/docs/blob/master/README.md)

- 针对展锐P7885芯片开发板，新增如下能力：

  - 支持5G蜂窝通信能力，提供驻网、通话、短信、数据功能。
  - 支持统一渲染。
  - 支持GNSS卫星状态信息上报，可识别并上报GPS、北斗、GLONASS等卫星数据。
  - 适配星闪驱动，支持星闪SLE 1.0，支持星闪配对连接和数据传输。
  - 板载适配6类传感器：加速度计、陀螺仪、磁力计、接近传感器、环境光传感器、马达。
  - 板载36 PIN标准PCI-E接口，外接板支持USB+千兆以太网接口或者其他标准PCI-E板卡。

### 新增预制应用  

针对展锐P7885芯片开发板，新增如下预置应用：

#### [文件管理](https://gitcode.com/openharmony/applications_filepicker)

- 支持外置存储浏览。
- 支持文管内访问图库。
- 支持文件Picker（选择、后缀过滤、批量授权）。
- 支持通过路径Picker保存文件。
- 支持文件的打开、分享、重命名、复制、移动、收藏。
- 支持最近删除、文件属性、列表/宫格等视图。

#### [时钟](https://gitcode.com/openharmony/applications_clock)

- 支持世界时钟/计时器。

#### [计算器](https://gitcode.com/openharmony/applications_calculator)

- 支持标准计算器/科学计算器。


### 更新预制应用

针对展锐P7885芯片开发板，如下预置应用在6.1 Release版本的基础上进行了更新：

#### [桌面](https://gitcode.com/openharmony/window_scene_board)

- 支持数字密码/滑动解锁、防暴力破解、锁屏时钟与卡片。
- 支持4×4桌面图标布局、Dock栏、桌面图标角标、应用快捷方式、桌面编辑模式。
- 支持卡片/卡片堆叠/文件夹的完整管理。
- 支持最近任务（锁定、一键清理、滑动删除）。
- 支持状态栏、控制中心、手势/三键导航。
- 支持通知中心（列表、分区、组通知、置顶/静默）。
- 支持实况通知（胶囊/卡片）。
- 支持系统弹框（关机/低电量）、音量面板。
- 支持分屏、悬浮窗（智慧多窗）。
- 支持窗口任务管理（启停、多任务、任务链、持久化恢复）。
- 支持壁纸库、静态壁纸设置、免打扰模式。

#### [设置](https://gitcode.com/openharmony/applications_settings)

- 支持设置内全局搜索。
- 支持WLAN/蓝牙/移动网络。
- 支持壁纸、亮度、深色模式（含定时）、字体与显示大小。
- 支持声音模式、音量面板、来电/信息/通知铃声。
- 支持通知和状态栏管理。
- 支持应用管理、锁屏密码、电池、存储。
- 支持系统导航、语言与输入法、日期时间、重置、开发者选项。
- 支持关于设备完整信息（IMEI、序列号、运行内存等）。

#### [相机](https://gitcode.com/openharmony/applications_camera)

- 支持前/后置拍照、前/后置录像。
- 支持相机Picker（仅拍照/仅录像/拍照+录像）。
- 支持相机设置页、百宝箱入口。

#### [图库](https://gitcode.com/openharmony/applications_photos)

- 支持照片浏览/大图浏览/大图手势/大图组件。
- 支持宫格操作/大图菜单操作/卡片操作/相册操作。
- 支持图片编辑/图库设置。
- 支持大图视屏播放/照片页浏览。
- 支持图库Picker。


#### [联系人](https://gitcode.com/openharmony/applications_contacts)

- 支持拨号盘搜索及结果快捷操作（详情、黑名单、复制、标记、新建/保存联系人、发短信）。
- 支持通话记录（全部/未接）及长按管理（多选、删除、标记、加入黑名单等）。
- 支持联系人搜索、字母索引、智能/自定义群组。
- 支持联系人新建/编辑/详情（头像、多号码、邮箱、地址、生日等完整字段）。
- 支持收藏联系人及排序、批量管理。
- 支持黑/白名单、黄页查询。
- 支持联系人导入/导出、SIM 卡导入、最近删除、重复联系人合并。
- 支持单人铃声（本地/视频/无铃声）。
- 支持服务卡片（快捷拨打、未接来电、桌面快捷方式）。
- 支持联系人Picker。

#### [短信](https://gitcode.com/openharmony/applications_mms)

- 支持短信发送，长短信、表情。
- 支持群发、转发、失败重发。
- 支持会话列表左滑/长按/滑动多选删除。
- 支持通知栏整合、标记已读、通知回复。
- 支持详情页复制、转发、选择文本等操作。
- 支持列表与详情展示联系人头像。
- 支持信息收藏、送达报告。

#### [通话](https://gitcode.com/openharmony/applications_call)

- 支持语音来去电、接听/挂断/拒接、静音、扬声器、音频设备切换。
- 支持紧急拨号、SOS 连按电源键、紧急位置展示。
- 支持紧急联系人及自动求助。
- 支持来电全屏/横幅、铃声/振动。
- 支持号码归属地/黄页/标记。
- 支持移动数据、APN、数据漫游、网络模式设置。
- 支持飞行模式拨号提示、接近光防误触。

## 配套关系

**表1** 版本软件和工具配套关系

| 软件 | 版本 | 备注 | 
| -------- | -------- | -------- |
| OpenHarmony |  | NA | 
| Public SDK |  | 面向应用开发者提供，不包含需要使用系统权限的系统接口。通过DevEco Studio默认获取的SDK为Public SDK。 | 
| 统一SDK |  | 面向OpenHarmony生态提供的标准化开发工具套件，扩展了OpenHarmony SDK的能力。 |
| HUAWEI DevEco Studio（可选） | 6.1.0 Release | OpenHarmony应用开发推荐使用。<br />*待发布后提供*。 | 
| HUAWEI DevEco Device Tool（可选） | 4.0 Release | OpenHarmony智能设备集成开发环境推荐使用。<br />[请点击这里获取](https://device.harmonyos.com/cn/develop/ide#download)。 | 


## 源码获取


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




### 从镜像站点获取



## 修复缺陷列表

**表3** 修复缺陷ISSUE列表

| ISSUE单 | 问题描述 | 
| ------- | ------- |


## 遗留缺陷列表

**表4** 遗留缺陷列表

| ISSUE | 问题描述 | 影响 | 计划解决日期 | 
| -------- | -------- | -------- | -------- |

