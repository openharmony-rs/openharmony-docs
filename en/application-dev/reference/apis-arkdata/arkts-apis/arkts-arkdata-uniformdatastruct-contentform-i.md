# ContentForm

```TypeScript
interface ContentForm
```

Defines the content card typed data, which is used to share content card information across applications. Typical usage scenarios include sharing article cards in news applications, sharing product cards in e-commerce applications, and sharing content previews in social applications.

**Since:** 14

<!--Device-uniformDataStruct-interface ContentForm--><!--Device-uniformDataStruct-interface ContentForm-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## Modules to Import

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## appIcon

```TypeScript
appIcon?: Uint8Array
```

Application icon data in the content card. The default value is empty.

**Type:** Uint8Array

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContentForm-appIcon?: Uint8Array--><!--Device-ContentForm-appIcon?: Uint8Array-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## appName

```TypeScript
appName?: string
```

Application name in the content card. The default value is an empty string.

**Type:** string

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContentForm-appName?: string--><!--Device-ContentForm-appName?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## description

```TypeScript
description?: string
```

Description information in the content card. The default value is an empty string.

**Type:** string

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContentForm-description?: string--><!--Device-ContentForm-description?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## linkUri

```TypeScript
linkUri?: string
```

Redirect hyperlink corresponding to the content card, which must comply with the URI format specification. The default value is an empty string.

**Type:** string

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContentForm-linkUri?: string--><!--Device-ContentForm-linkUri?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## thumbData

```TypeScript
thumbData?: Uint8Array
```

Image data corresponding to the content card. The default value is empty.

**Type:** Uint8Array

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContentForm-thumbData?: Uint8Array--><!--Device-ContentForm-thumbData?: Uint8Array-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## title

```TypeScript
title: string
```

Title of the content widget.

**Type:** string

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContentForm-title: string--><!--Device-ContentForm-title: string-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'general.content-form'
```

Uniform data type, which has a fixed value of **general.content-form**.

**Type:** 'general.content-form'

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-ContentForm-readonly uniformDataType: 'general.content-form'--><!--Device-ContentForm-readonly uniformDataType: 'general.content-form'-End-->

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
