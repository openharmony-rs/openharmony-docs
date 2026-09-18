# Notification

Describes the custom information of the notification bar.

**Since:** 15

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## text

```TypeScript
text?: string
```

Custom body text, with a maximum of 3072 bytes. The default text is used if this parameter is not set.

**Type:** string

**Since:** 15

**System capability:** SystemCapability.Request.FileTransferAgent

## title

```TypeScript
title?: string
```

Custom title, with a maximum of 1024 bytes. The default title is used if this parameter is not set.

**Type:** string

**Since:** 15

**System capability:** SystemCapability.Request.FileTransferAgent

## visibility

```TypeScript
visibility?: number
```

Task visibility mode for the notification bar, which is determined by bitwise operations on the [VISIBILITY constant](../../../reference/apis-basic-services-kit/js-apis-request.md#constants-1). The options are as follows:  
- Only the completion notification is displayed. The parameter is **VISIBILITY_COMPLETION** or **1**. The  
corresponding notification is displayed after the task is complete or fails.  
- Only the progress notification is displayed when the task is in progress. The parameter is  
**VISIBILITY_PROGRESS** or **2**. Completion notification is not displayed when the download task is complete or fails.  
- The progress notification and completion notification are displayed. The parameter is VISIBILITY_COMPLETION |  
VISIBILITY_PROGRESS or **3**. The progress notification is displayed when the task is in progress. When the download task is complete or fails, the completion notification is displayed as well. If this parameter is not set, the **gauge** field is used for determination. If there is no **gauge** field, only the completion notification is displayed. The value should be an integer.

**Type:** number

**Since:** 21

**System capability:** SystemCapability.Request.FileTransferAgent

## wantAgent

```TypeScript
wantAgent?: WantAgent
```

Notification parameter, which is used to implement redirection after a task notification is tapped. The default value is empty.

**Type:** [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-t.md)

**Since:** 22

**System capability:** SystemCapability.Request.FileTransferAgent
