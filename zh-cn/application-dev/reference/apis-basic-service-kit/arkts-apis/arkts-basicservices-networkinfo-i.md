# NetworkInfo

预下载的网络信息。

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

## dnsServers

```TypeScript
readonly dnsServers: string[]
```

下载资源时使用的dns服务器列表。

**类型：** string[]

**起始版本：** 20

**系统能力：** SystemCapability.Request.FileTransferAgent

## ip

```TypeScript
readonly ip?: string
```

下载资源时url的ip地址。当dns解析失败时，ip为undefined。

**类型：** string

**起始版本：** 23

**系统能力：** SystemCapability.Request.FileTransferAgent

