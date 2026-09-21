# DownloadConfig

```TypeScript
interface DownloadConfig
```

Defines the download task configuration.

**Since:** 6

**System capability:** SystemCapability.MiscServices.Download

## Modules to Import

```TypeScript
import { request } from '@kit.BasicServicesKit';
```

## background

```TypeScript
background?: boolean
```

Whether to enable the background task notification. When this parameter is enabled, the download status is displayed in the notification panel. The value **true** means the parameter is enabled, and **false** means the opposite. The default value is **false**.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.MiscServices.Download

## description

```TypeScript
description?: string
```

Description of the download session. The default value is an empty string.

**Type:** string

**Since:** 6

**System capability:** SystemCapability.MiscServices.Download

## enableMetered

```TypeScript
enableMetered?: boolean
```

Whether download is allowed on a metered connection. The value **true** means the download is allowed, and **false** means the opposite. The default value is **false**.

> **NOTE:** 
> 
> In general cases, a mobile data connection is metered, while a Wi-Fi connection is not.

**Type:** boolean

**Since:** 6

**System capability:** SystemCapability.MiscServices.Download

## enableRoaming

```TypeScript
enableRoaming?: boolean
```

Whether download is allowed on a roaming network. The value **true** means the download is allowed, and **false** means the opposite. The default value is **false**.

**Type:** boolean

**Since:** 6

**System capability:** SystemCapability.MiscServices.Download

## filePath

```TypeScript
filePath?: string
```

Path where the downloaded file is stored. The default value is the cache directory of the caller (that is, the input **context**). The default file name is the part truncated from the last slash (/) in the URL.

- In the FA model, use the [Context.getCacheDir](../../../reference/apis-ability-kit/js-apis-inner-app-context.md#contextgetcachedir) method to obtain the application storage path.  
- In the Stage model, use the **AbilityContext** class in [Context (Context Base Class of the Stage Model)](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) to obtain the file path.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.MiscServices.Download

## header

```TypeScript
header?: Object
```

HTTPS flag header to be included in the download request. The default value is empty.

**Type:** Object

**Since:** 6

**System capability:** SystemCapability.MiscServices.Download

## networkType

```TypeScript
networkType?: number
```

Network type that can be used for download. The allowed network type is determined by bitwise operation of [network type constants](../../../reference/apis-basic-services-kit/js-apis-request.md#constants). The following settings are supported:

- Only the cellular network is supported. The parameter is **NETWORK_MOBILE** or **0x00000001**.  
- Only WLAN is supported. The parameter is **NETWORK_WIFI** or **0x00010000**.  
- Both cellular network and WLAN are supported, which is the default settings. The parameter is  
**NETWORK_MOBILE **

**Type:** number

**Since:** 6

**System capability:** SystemCapability.MiscServices.Download

## title

```TypeScript
title?: string
```

Download task name. The default value is **download**.

**Type:** string

**Since:** 6

**System capability:** SystemCapability.MiscServices.Download

## url

```TypeScript
url: string
```

Resource URL. From API version 6 to 14, the value contains a maximum of 2048 characters; since API version 15, the value contains a maximum of 8192 characters. [Intercepting HTTP](../../../basic-services/request/app-file-upload-download.md#intercepting-http) is supported.

**Type:** string

**Since:** 6

**System capability:** SystemCapability.MiscServices.Download
