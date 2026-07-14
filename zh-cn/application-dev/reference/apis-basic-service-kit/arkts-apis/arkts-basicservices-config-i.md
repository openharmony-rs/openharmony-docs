# Config

上传/下载任务的配置信息。

**起始版本：** 10

**系统能力：** SystemCapability.Request.FileTransferAgent

## action

```TypeScript
action: Action
```

任务操作选项。

- UPLOAD表示上传任务。
- DOWNLOAD表示下载任务。

**类型：** Action

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## begins

```TypeScript
begins?: number
```

文件起点，单位为字节（B），通常情况下用于断点续传。默认值为0，取值为闭区间，表示从头开始传输。

- 下载时，请求读取服务器开始下载文件时的起点位置（HTTP协议中设置"Range"选项）。
- 上传时，读取需上传的文件的起点位置。

**类型：** number

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## data

```TypeScript
data?: string | Array<FormItem>
```

- 下载时，data为字符串类型，通常情况下使用json格式（object将被转换为json文本），默认为空。
- 上传时，data是表单项数组Array<
[FormItem](arkts-basicservices-formitem-i.md)>。从API version
15开始，创建单个任务可以上传最多100个文件。默认为空。

**类型：** string | Array<FormItem>

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## description

```TypeScript
description?: string
```

任务的详细信息，其最大长度为1024个字符，默认值为空字符串。

**类型：** string

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## ends

```TypeScript
ends?: number
```

文件终点，单位为字节（B），通常情况下用于断点续传。默认值为-1，取值为闭区间，表示传输到整个文件末尾结束。

- 下载时，请求读取服务器开始下载文件时的结束位置（HTTP协议中设置"Range"选项）。
- 上传时，读取需上传的文件的结束位置。

**类型：** number

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## extras

```TypeScript
extras?: object
```

配置的附加功能，默认为空。

**类型：** object

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## gauge

```TypeScript
gauge?: boolean
```

后台任务的过程进度通知策略，仅应用于后台任务，默认值为false。

- false：代表仅完成或失败的通知。
- true：发出每个进度已完成或失败的通知。

**类型：** boolean

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## headers

```TypeScript
headers?: object
```

添加要包含在任务中的HTTP协议标志头。

- 上传请求，默认的Content-Type为"multipart/form-data"。
- 下载请求，默认的Content-Type为"application/json"。

**类型：** object

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## index

```TypeScript
index?: number
```

任务的路径索引，通常情况下用于任务断点续传，默认为0。

**类型：** number

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## metered

```TypeScript
metered?: boolean
```

是否允许在按流量计费的网络中工作，默认为false。

- true：是
- false：否

**类型：** boolean

**默认值：** false

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## method

```TypeScript
method?: string
```

上传或下载HTTP的标准方法，包括GET、POST和PUT，不区分大小写。

- 上传时，使用PUT或POST，默认值为PUT。
- 下载时，使用GET或POST，默认值为GET。

**类型：** string

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## minSpeed

```TypeScript
minSpeed?: MinSpeed
```

最低限速自定义设置，默认不启用最低限速。

**类型：** MinSpeed

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

## mode

```TypeScript
mode?: Mode
```

任务模式，默认为后台任务。从API version 20开始，下载到用户文件场景必须为request.agent.Mode.FOREGROUND。

**类型：** Mode

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## multipart

```TypeScript
multipart?: boolean
```

是否使用单个请求进行上传，单个请求上传时必定使用multipart/form-data。

- false：每个文件使用一个请求传输。
- true：使用多文件单请求上传。

默认值为false。

**类型：** boolean

**起始版本：** 15

**系统能力：** SystemCapability.Request.FileTransferAgent

## network

```TypeScript
network?: Network
```

网络选项，当前支持无线网络WIFI和蜂窝数据网络CELLULAR，默认为ANY（WIFI或CELLULAR）。

**类型：** Network

**默认值：** Network.ANY

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## notification

```TypeScript
notification?: Notification
```

通知栏自定义设置。默认值为`{}`。

**类型：** Notification

**起始版本：** 15

**系统能力：** SystemCapability.Request.FileTransferAgent

## overwrite

```TypeScript
overwrite?: boolean
```

下载过程中路径已存在时的解决方案选择，默认为false。

- true，覆盖已存在的文件。
- false，下载失败。

从API version 20开始，下载到用户文件场景必须为true。

设置为 `true` 时，不建议创建多个任务同时往同一个文件下载内容，会导致文件内容混乱。

**类型：** boolean

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## precise

```TypeScript
precise?: boolean
```

- 如果设置为true，在上传/下载无法获取文件大小时任务失败。
- 如果设置为false，将文件大小设置为-1时任务继续。

默认值为false。

**类型：** boolean

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## priority

```TypeScript
priority?: number
```

任务的优先级。前台任务的优先级比后台任务高。任务模式相同的情况下，该配置项的数字越小优先级越高，默认值为0。

**类型：** number

**起始版本：** 11

**系统能力：** SystemCapability.Request.FileTransferAgent

## proxy

```TypeScript
proxy?: string
```

设置代理地址，其最大长度为512个字符，默认为空。

代理地址格式:"http://<domain or address>:<port>"

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.Request.FileTransferAgent

## redirect

```TypeScript
redirect?: boolean
```

是否允许重定向，默认为true。

- true：是
- false：否

**类型：** boolean

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## retry

```TypeScript
retry?: boolean
```

是否为后台任务启用自动重试，仅应用于后台任务，默认为true。

- true：是
- false：否

**类型：** boolean

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## roaming

```TypeScript
roaming?: boolean
```

是否允许在漫游网络中工作，默认为true。

- true：是
- false：否

**类型：** boolean

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## saveas

```TypeScript
saveas?: string
```

保存下载文件的路径，包括如下几种：

- 相对路径，位于调用方的缓存路径下，如"./xxx/yyy/zzz.html"、"xxx/yyy/zzz.html"。
- internal协议路径，支持"internal://"及其子路径，internal为调用方（传入的context）对应路径，"internal://cache"对应context.cacheDir。如"
internal://cache/path/to/file.txt"。
- 应用沙箱目录，只支持到base及其子目录下，如"/data/storage/el1/base/path/to/file.txt"。
- file协议路径，支持应用文件和用户文件，应用文件必须匹配应用包名，只支持到base及其子目录下，如"file://com.example.test/data/storage/el2/base/file.txt"。用户
文件必须为调用方创建好的用户文件uri。

从API version 20开始，除[下载网络资源文件至用户文件](../../../../basic-services/request/app-file-upload-download.md#下载网络资源文件至用户文件)外
，其他可默认为调用方（即传入的context）对应的缓存路径。默认文件名从url的最后一个"/"后截取。

**类型：** string

**默认值：** ./

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## timeout

```TypeScript
timeout?: Timeout
```

超时时间自定义设置，连接超时时间默认60秒，总超时时间默认604800秒（1周）。当retry参数为true时，
[timeout](arkts-basicservices-timeout-i.md)事件会触发立即重试，导致
[timeout](arkts-basicservices-timeout-i.md)在外部观察中被重试动作所掩盖，但
内部[timeout](arkts-basicservices-timeout-i.md)条件已实际触发。若需显性观察
[timeout](arkts-basicservices-timeout-i.md)事件，需关闭retry参数。

**类型：** Timeout

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

## title

```TypeScript
title?: string
```

任务标题，其最大长度为256个字符，默认值为小写的 upload 或 download，与上面的 action 保持一致。

**类型：** string

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## token

```TypeScript
token?: string
```

任务令牌。查询带有token的任务需提供token并通过
[request.agent.touch](arkts-basicservices-touch-f.md#touch-1)查询，否则无
法查询到指定任务。其最小为8个字节，最大为2048个字节。默认为空。

**类型：** string

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

## url

```TypeScript
url: string
```

资源地址。从API 6到API 14，最大长度为2048个字符；从API 15开始，最大长度为8192个字符。支持
[HTTP拦截](../../../../basic-services/request/app-file-upload-download.md#http拦截)功能。

**类型：** string

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Request.FileTransferAgent

