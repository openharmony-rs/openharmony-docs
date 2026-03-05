# Interface (AVMusicTemplateDescriptor)(系统接口)
<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @ccfriend; @liao_qian-->
<!--Designer: @ccfriend-->
<!--Tester: @chenmingxi1_huawei-->
<!--Adviser: @w_Machine_cc-->

在媒体应用创建音频模板后，调用[avMusicTemplate.getAllAVMusicTemplateDescriptors](js-apis-avsession-avMusicTemplate-sys.md#avmusictemplategetallavmusictemplatedescriptors)后，返回音频模板描述的实例。控制器可查看音频模板唯一标识，应用的包名和用户ID。

> **说明：**
>
> - 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { avMusicTemplate } from '@kit.AVSessionKit';
```

## 属性

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

| 名称       | 类型   | 只读 | 可选 | 说明               |
| ---------- | ------ | ---- | ---- | ------------------ |
| sessionId  | string | 否   | 否   | 音频模板唯一标识。 |
| bundleName | string | 否   | 否   | 应用的包名。       |
| userId     | number | 否   | 否   | 用户ID。           |

**示例：**

```ts
let sessionId: string = currentAVSession.sessionId;
let sessionType: avSession.AVSessionType = currentAVSession.sessionType;
```

