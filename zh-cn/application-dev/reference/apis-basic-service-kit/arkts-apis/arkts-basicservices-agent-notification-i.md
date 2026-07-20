# Notification

通知栏自定义信息。

**起始版本：** 15

<!--Device-agent-interface Notification--><!--Device-agent-interface Notification-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## 导入模块

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## text

```TypeScript
text?: string
```

通知栏自定义正文。若不设置则使用默认显示方式。text长度上限为3072B。

**类型：** string

**起始版本：** 15

<!--Device-Notification-text?: string--><!--Device-Notification-text?: string-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## title

```TypeScript
title?: string
```

通知栏自定义标题。若不设置则使用默认显示方式。title长度上限为1024B。

**类型：** string

**起始版本：** 15

<!--Device-Notification-title?: string--><!--Device-Notification-title?: string-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## visibility

```TypeScript
visibility?: number
```

设置任务的通知栏显示方式，通过[VISIBILITY常量](docroot://reference/apis-basic-services-kit/js-apis-request.md#常量-1)的位运算方式决定显示方式，任务通知的显示方式，包括如下几种：

- 仅显示完成通知，参数为VISIBILITY_COMPLETION或1，任务完成/失败后展示对应通知。  
- 仅显示进度通知，参数为VISIBILITY_PROGRESS或2，任务在进行中显示进度通知，当任务下载成功/失败后会直接退出进度通知，不会显示完成通知。  
- 显示进度通知/完成通知，参数为VISIBILITY_COMPLETION | VISIBILITY_PROGRESS或3，任务在进行中显示进度通知，当任务下载成功/失败后会退出进度通知，并显示完成通知。

若不设置该参数，则根据gauge字段来判断；若无gauge字段，则仅显示完成通知。

The value should be an integer.

**类型：** number

**起始版本：** 21

<!--Device-Notification-visibility?: int--><!--Device-Notification-visibility?: int-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## wantAgent

```TypeScript
wantAgent?: WantAgent
```

通知参数，用于实现点击任务通知后跳转的功能。默认值为空。

**类型：** WantAgent

**起始版本：** 22

<!--Device-Notification-wantAgent?: WantAgent--><!--Device-Notification-wantAgent?: WantAgent-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

