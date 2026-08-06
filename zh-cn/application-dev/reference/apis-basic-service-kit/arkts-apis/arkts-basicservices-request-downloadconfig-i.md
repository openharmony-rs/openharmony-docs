# DownloadConfig

下载任务的配置信息。

**起始版本：** 6

**ArkTS模式：** ArkTS-Dyn起始版本为6；ArkTS-Sta起始版本为23。

<!--Device-request-interface DownloadConfig--><!--Device-request-interface DownloadConfig-End-->

**系统能力：** SystemCapability.MiscServices.Download

## background

```TypeScript
background?: boolean
```

后台任务通知开关，启用后可在通知中显示下载状态。true表示启用，false表示禁用。默认值为false。

**类型：** boolean

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-DownloadConfig-background?: boolean--><!--Device-DownloadConfig-background?: boolean-End-->

**系统能力：** SystemCapability.MiscServices.Download

## description

```TypeScript
description?: string
```

设置下载会话的描述。默认值为空字符串。

**类型：** string

**起始版本：** 6

**ArkTS模式：** ArkTS-Dyn起始版本为6；ArkTS-Sta起始版本为23。

<!--Device-DownloadConfig-description?: string--><!--Device-DownloadConfig-description?: string-End-->

**系统能力：** SystemCapability.MiscServices.Download

## enableMetered

```TypeScript
enableMetered?: boolean
```

表示设置是否允许在按流量计费的连接下下载任务的配置信息。true表示允许，false表示不允许。默认值为false。 > **说明：** > > Wi-Fi为非计费网络，数据流量为计费网络。

**类型：** boolean

**起始版本：** 6

**ArkTS模式：** ArkTS-Dyn起始版本为6；ArkTS-Sta起始版本为23。

<!--Device-DownloadConfig-enableMetered?: boolean--><!--Device-DownloadConfig-enableMetered?: boolean-End-->

**系统能力：** SystemCapability.MiscServices.Download

## enableRoaming

```TypeScript
enableRoaming?: boolean
```

表示设置是否允许在漫游网络中下载任务的配置信息。true表示允许，false表示不允许。默认值为false。

**类型：** boolean

**起始版本：** 6

**ArkTS模式：** ArkTS-Dyn起始版本为6；ArkTS-Sta起始版本为23。

<!--Device-DownloadConfig-enableRoaming?: boolean--><!--Device-DownloadConfig-enableRoaming?: boolean-End-->

**系统能力：** SystemCapability.MiscServices.Download

## filePath

```TypeScript
filePath?: string
```

设置下载路径。默认为调用方（即传入的context）对应的缓存路径。默认文件名从url的最后一个"/"后截取。 - FA模型下使用 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_方法获取应用 存储路径。 - Stage模型下使用[Context (Stage模型的上下文基类)]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_中AbilityContext的类获取文件路径。

**类型：** string

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-DownloadConfig-filePath?: string--><!--Device-DownloadConfig-filePath?: string-End-->

**系统能力：** SystemCapability.MiscServices.Download

## header

```TypeScript
header?: Object
```

添加要包含在下载请求中的HTTPS标志头。默认值为空。

**类型：** Object

**起始版本：** 6

**ArkTS模式：** ArkTS-Dyn起始版本为6；ArkTS-Sta起始版本为23。

<!--Device-DownloadConfig-header?: Object--><!--Device-DownloadConfig-header?: Object-End-->

**系统能力：** SystemCapability.MiscServices.Download

## networkType

```TypeScript
networkType?: int
```

设置允许下载的网络类型，通过 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_的位运算方式决定允许 的网络类型，支持如下几种设置方式: - 仅支持蜂窝网络下载，参数为NETWORK\_MOBILE或0x00000001 - 仅支持WLAN网络下载，参数为NETWORK\_WIFI或0x00010000 - 参数默认值，支持蜂窝/WLAN网络下载，参数为NETWORK\_MOBILE | NETWORK\_WIFI或0x00010001。 当参数为NETWORK\_MOBILE | NETWORK\_WIFI时，enableMetered和enableRoaming参数不生效。

**类型：** int

**起始版本：** 6

**ArkTS模式：** ArkTS-Dyn起始版本为6；ArkTS-Sta起始版本为23。

<!--Device-DownloadConfig-networkType?: int--><!--Device-DownloadConfig-networkType?: int-End-->

**系统能力：** SystemCapability.MiscServices.Download

## title

```TypeScript
title?: string
```

设置下载任务名称。默认值为download。

**类型：** string

**起始版本：** 6

**ArkTS模式：** ArkTS-Dyn起始版本为6；ArkTS-Sta起始版本为23。

<!--Device-DownloadConfig-title?: string--><!--Device-DownloadConfig-title?: string-End-->

**系统能力：** SystemCapability.MiscServices.Download

## url

```TypeScript
url: string
```

资源地址。从API 6到API 14，最大长度为2048个字符；从API 15开始，最大长度为8192个字符。支持 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_功能。

**类型：** string

**起始版本：** 6

**ArkTS模式：** ArkTS-Dyn起始版本为6；ArkTS-Sta起始版本为23。

<!--Device-DownloadConfig-url: string--><!--Device-DownloadConfig-url: string-End-->

**系统能力：** SystemCapability.MiscServices.Download

