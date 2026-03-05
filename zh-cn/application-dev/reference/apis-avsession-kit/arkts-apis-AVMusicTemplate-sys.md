# 模块描述
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_gyH0B0hP-->
<!--Designer: @ccfriend-->
<!--Tester: @chen-gong1-->
<!--Adviser: @w_Machine_cc-->

音频模板控制器，可用于向接入音频模板的媒体应用查询数据，然后进行统一风格的页面展示，并下发页面操作指令。

该模块提供如下功能：

- [AVMusicTemplateController](arkts-apis-avsession-AVMusicTemplateController-sys.md): 音频模板控制器，可用于与接入音频模板的媒体应用数据交互。
- [AVMusicTemplateDescriptor](arkts-apis-avsession-AVMusicTemplateDescriptor-sys.md): 音频模板描述，包含音频模板唯一标识，应用的包名和用户ID信息。

> **说明：**
>
> 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { aVMusicTemplate } from '@kit.AVSessionKit';
```