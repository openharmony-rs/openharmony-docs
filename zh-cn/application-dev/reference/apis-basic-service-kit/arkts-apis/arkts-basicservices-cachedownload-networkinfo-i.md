# NetworkInfo

预下载的网络信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-cacheDownload-interface NetworkInfo--><!--Device-cacheDownload-interface NetworkInfo-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## dnsServers

```TypeScript
readonly dnsServers: string[]
```

下载资源时使用的dns服务器列表。

**类型：** string[]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-NetworkInfo-readonly dnsServers: string[]--><!--Device-NetworkInfo-readonly dnsServers: string[]-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

## ip

```TypeScript
readonly ip?: string
```

下载资源时url的ip地址。当dns解析失败时，ip为undefined。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-NetworkInfo-readonly ip?: string--><!--Device-NetworkInfo-readonly ip?: string-End-->

**系统能力：** SystemCapability.Request.FileTransferAgent

