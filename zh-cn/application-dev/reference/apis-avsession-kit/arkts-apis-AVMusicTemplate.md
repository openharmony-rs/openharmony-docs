# 模块描述
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_gyH0B0hP-->
<!--Designer: @ccfriend-->
<!--Tester: @chen-gong1-->
<!--Adviser: @w_Machine_cc-->

音频模板提供数据写入和接收接口，目的是让媒体应用接入音频中心进行页面展示，并响应媒体中心的操作指令。

该模块提供以下媒体会话相关的常用功能：

- [AVMusicTemplate](arkts-apis-avsession-AVMusicTemplate.md): 音频模板，可用于与媒体中心进行数据交互。
- [AVMusicTemplateController](arkts-apis-avsession-AVMusicTemplateController-sys.md): 音频模板控制器，可用于查询音频模板页面数据，并下发页面操作指令。

> **说明：**
>
> 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { aVMusicTemplate } from '@kit.AVSessionKit';
```