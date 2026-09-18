# Config

Provides the configuration information of an upload or download task.

**Since:** 10

**System capability:** SystemCapability.Request.FileTransferAgent

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## action

```TypeScript
action: Action
```

Task action.

- **UPLOAD**: Upload tasks.  
- **DOWNLOAD**: Download tasks.

**Type:** [Action](arkts-basicservices-agent-action-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## begins

```TypeScript
begins?: number
```

File start point of the task, in bytes. It is usually used for resumable transfers. The default value is **0**. The value is a closed interval.

- For the download task, the value is obtained by sending an HTTP range request to read the start position when  
the server starts to download files.  
- For the upload task, the value is obtained at the start position of the upload.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## data

```TypeScript
data?: string | Array<FormItem>
```

- For the download task, the value is a string, typically in JSON format (an object will be converted to a JSON  
string); the default value is null.  
- For the upload task, the value is Array&lt;[FormItem](arkts-basicservices-agent-formitem-i.md)&gt;. Since API version 15, a maximum of 100 files can be uploaded in a single task. This parameter is left empty by default.

**Type:** string &#124; Array&lt;[FormItem](arkts-basicservices-agent-formitem-i.md)&gt;

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## description

```TypeScript
description?: string
```

Task description. The value contains a maximum of 1024 characters. The default value is a null string.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## ends

```TypeScript
ends?: number
```

File end point of the task, in bytes. It is usually used for resumable transfers. The default value is **-1**. The value is a closed interval.

- For the download task, the value is obtained by sending an HTTP range request to read the end position when  
the server starts to download files.  
- For the upload task, the value is obtained at the end position of the upload.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## extras

```TypeScript
extras?: object
```

Additional information of the task. This parameter is left empty by default.

**Type:** object

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## gauge

```TypeScript
gauge?: boolean
```

Whether to send progress notifications. This parameter applies only to background tasks. The default value is **false**.

- **false**: Progress notifications are not sent. This means that a notification is sent only to indicate the  
result of the total task.  
- **true**: Progress notifications are sent to indicate the result of each file.

**Type:** boolean

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## headers

```TypeScript
headers?: object
```

HTTP headers to be included in the task.

- For the upload task, the default **Content-Type** is **multipart/form-data**.  
- For the download task, the default **Content-Type** is **application/json**.

**Type:** object

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## index

```TypeScript
index?: number
```

Path index of the task. It is usually used for resumable transfers. The default value is **0**.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## metered

```TypeScript
metered?: boolean
```

Whether the task is allowed on a metered network. The default value is **false**.

- **true**: allowed  
- **false**: not allowed

**Type:** boolean

**Default:** false

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## method

```TypeScript
method?: string
```

Standard HTTP method for the task. The value can be **GET**, **POST**, or **PUT**, which is case-insensitive.

- For the upload task, use **PUT** or **POST**. The default value is **PUT**.  
- For the download task, use **GET** or **POST**. The default value is **GET**.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## minSpeed

```TypeScript
minSpeed?: MinSpeed
```

Minimum speed, which is disabled by default.

**Type:** [MinSpeed](arkts-basicservices-agent-minspeed-i.md)

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent

## mode

```TypeScript
mode?: Mode
```

Task mode. The default mode is background. Since API version 20, the task mode for downloading files to the user file folder must be set to **request.agent.Mode.FOREGROUND**.

**Type:** [Mode](arkts-basicservices-agent-mode-e.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## multipart

```TypeScript
multipart?: boolean
```

Whether to use a single request to upload multiple files. If yes, **multipart/form-data** must be used.

- **false**: A single request is used to upload one file.  
- **true**: A single request is used to upload multiple files.

The default value is **false**.

**Type:** boolean

**Since:** 15

**System capability:** SystemCapability.Request.FileTransferAgent

## network

```TypeScript
network?: Network
```

Network used for the task. The default value is **ANY** (Wi-Fi or cellular).

**Type:** [Network](arkts-basicservices-agent-network-e.md)

**Default:** Network.ANY

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## notification

```TypeScript
notification?: Notification
```

Custom settings for the notification bar. The default value is **{}**.

**Type:** [Notification](arkts-basicservices-agent-notification-i.md)

**Since:** 15

**System capability:** SystemCapability.Request.FileTransferAgent

## overwrite

```TypeScript
overwrite?: boolean
```

Whether to overwrite an existing file during the download. The default value is **false**.

- **true**: Overwrite the existing file.  
- **false**: Do not overwrite the existing file. In this case, the download fails.

Since API version 20, the overwrite mode for downloading files to the user file folder must be set to **true**.

In this case, do not create multiple tasks to download content to the same file at a time. Otherwise, the file content will be disordered.

**Type:** boolean

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## precise

```TypeScript
precise?: boolean
```

- If this parameter is set to **true**, the task fails when the file size cannot be obtained.  
- If this parameter is set to **false**, the task continues when the file size is set to **-1**.

The default value is **false**.

**Type:** boolean

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## priority

```TypeScript
priority?: number
```

Priority of the task. The priority of a foreground task is higher than that of a background task. For tasks in the same mode, a smaller value indicates a higher priority.

Default value: **0**

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Request.FileTransferAgent

## proxy

```TypeScript
proxy?: string
```

Proxy address. The value contains a maximum of 512 characters.

It is in the format of **http://&lt;***domain or address***&gt;:&lt;***port***&gt;**. By default, this parameter is left empty.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Request.FileTransferAgent

## redirect

```TypeScript
redirect?: boolean
```

Whether redirection is allowed. The default value is **true**.

- **true**: allowed  
- **false**: not allowed

**Type:** boolean

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## retry

```TypeScript
retry?: boolean
```

Whether automatic retry is enabled for the task. This parameter is only applicable to background tasks. The default value is **true**.

- **true**: enabled  
- **false**: not allowed

**Type:** boolean

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## roaming

```TypeScript
roaming?: boolean
```

Whether the task is allowed on a roaming network. The default value is **true**.

- **true**: allowed  
- **false**: not allowed

**Type:** boolean

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## saveas

```TypeScript
saveas?: string
```

Path for storing downloaded files. The options are as follows:

- Relative path, which is in the cache directory of the caller, for example, **./xxx/yyy/zzz.html** or  
**xxx/yyy/zzz.html**.  
- Internal protocol path, which can be **internal://** or its subdirectory. **internal** indicates the cache  
directory of the caller (that is, the input **context**), and **internal://cache** corresponds to **context.cacheDir**, for example, **internal://cache/path/to/file.txt**.  
- Application sandbox path. Only the **base** directory and its subdirectories are supported, for example,  
**./data/storage/el1/base/path/to/file.txt**.  
- File protocol path, which can be the path of an application file or a user file. For the application file,  
the application bundle name must be matched and only the **base** directory and its subdirectories are supported, for example, **file://com.example.test/data/storage/el2/base/file.txt**. For the user file, its path must be the user file URI created by the caller.

Since API version 20, the default file path can be the cache path of the caller (that is, the passed context), except for [downloading network resource files to the user file](../../../basic-services/request/app-file-upload-download.md#downloading-network-resource-files-to-the-user-file). The default file name is the part truncated from the last slash (/) in the URL.

**Type:** string

**Default:** ./

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

**Test API:** This API is used only in automated test scripts.

## timeout

```TypeScript
timeout?: Timeout
```

Custom timeout interval. The default connection timeout interval is 60 seconds, and the default total timeout interval is 604800 seconds (one week). If retry is set to **true**, the [timeout](arkts-basicservices-agent-timeout-i.md) event triggers immediate retry, which will obscure the timeout event itself. As a result, the internal [timeout](arkts-basicservices-agent-timeout-i.md) condition has been triggered but the [timeout](arkts-basicservices-agent-timeout-i.md) event is not observable. Set **retry** to **false** to explicitly observe the [timeout](arkts-basicservices-agent-timeout-i.md) event.

**Type:** Timeout

**Since:** 20

**System capability:** SystemCapability.Request.FileTransferAgent

## title

```TypeScript
title?: string
```

Task title. The value contains a maximum of 256 characters. The default value is **upload** or **download** in lowercase. Set the value to that of **action**.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## token

```TypeScript
token?: string
```

Task token. To query a task with a token, you need to provide the token and use [request.agent.touch](arkts-basicservices-agent-touch-f.md). Otherwise, the specified task cannot be queried. The value contains 8 to 2048 bytes. This parameter is left empty by default.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent

## url

```TypeScript
url: string
```

Resource URL. From API version 6 to 14, the value contains a maximum of 2048 characters; since API version 15, the value contains a maximum of 8192 characters. [Intercepting HTTP](../../../basic-services/request/app-file-upload-download.md#intercepting-http) is supported.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Request.FileTransferAgent
