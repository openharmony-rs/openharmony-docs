# Core File Kit（文件基础服务）<!--core-file-kit-->

<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @bao-yangyang; @maokelong95-->
<!--Designer: @Hun_Dun-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->

- Core File Kit简介
- 应用文件<!--app-file-->
  - 应用文件概述
  - 应用沙箱目录
  - 应用文件访问与管理<!--app-file-access-management-->
    - 应用文件访问(ArkTS)
    - 应用文件访问(C/C++)
    - 应用及文件系统空间统计
  <!--Del-->
  - 向应用沙箱推送文件（仅对系统应用开放）
  <!--DelEnd-->
  - 应用文件分享
  - 应用共享目录配置
  - 应用数据备份恢复<!--app-file-backup-restore-->
    - 应用数据备份恢复概述
    - 应用接入数据备份恢复<!--RP2--><!--RP2End-->
    <!--Del-->
    - 应用触发数据备份/恢复（仅对系统应用开放）
    <!--DelEnd-->
- 用户文件<!--user-files-->
  - 用户文件概述
  - 用户文件URI介绍
  - FileUri开发指导(C/C++)
  - 获取用户目录环境(C/C++)
  - 选择与保存用户文件<!--select-save-user-file-->
    - 选择用户文件
    - 保存用户文件
    - 授权持久化
    - 授权持久化(C/C++)
  - 获取并使用公共目录
  <!--Del-->
  - 开发用户文件管理器（仅对系统应用开放）
  - 管理外置存储设备（仅对系统应用开放）
  <!--DelEnd-->
- 分布式文件系统<!--distributed-fs-->
  - 分布式文件系统概述
  - 设置分布式文件数据等级
  - 跨设备文件共享和访问
  - 跨设备文件拷贝<!--RP1--><!--RP1End-->
- 文件压缩解压缩<!--compression-->
  - 压缩解压缩概述
  - 文件归档类压缩解压缩(C/C++)
  - 流式压缩解压缩(C/C++)
  - 缓冲区压缩解压缩(C/C++)
  <!--RP3--><!--RP3End-->