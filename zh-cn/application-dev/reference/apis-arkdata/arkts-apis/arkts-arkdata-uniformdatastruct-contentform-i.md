# ContentForm

内容卡片类型数据，用于跨应用共享内容卡片信息。典型使用场景包括：资讯应用分享文章卡片、电商应用分享商品卡片、社交应用分享内容预览等。

**起始版本：** 14

<!--Device-uniformDataStruct-interface ContentForm--><!--Device-uniformDataStruct-interface ContentForm-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## appIcon

```TypeScript
appIcon?: Uint8Array
```

内容卡片中的应用图标数据。默认值为空。

**类型：** Uint8Array

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContentForm-appIcon?: Uint8Array--><!--Device-ContentForm-appIcon?: Uint8Array-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## appName

```TypeScript
appName?: string
```

内容卡片中应用的应用名。默认值为空字符串。

**类型：** string

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContentForm-appName?: string--><!--Device-ContentForm-appName?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## description

```TypeScript
description?: string
```

内容卡片中的描述信息。默认值为空字符串。

**类型：** string

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContentForm-description?: string--><!--Device-ContentForm-description?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## linkUri

```TypeScript
linkUri?: string
```

内容卡片对应的跳转超链接，需符合URI格式规范。默认值为空字符串。

**类型：** string

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContentForm-linkUri?: string--><!--Device-ContentForm-linkUri?: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## thumbData

```TypeScript
thumbData?: Uint8Array
```

内容卡片对应的图片数据。默认值为空。

**类型：** Uint8Array

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContentForm-thumbData?: Uint8Array--><!--Device-ContentForm-thumbData?: Uint8Array-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## title

```TypeScript
title: string
```

内容卡片的标题。

**类型：** string

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContentForm-title: string--><!--Device-ContentForm-title: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uniformDataType

```TypeScript
readonly uniformDataType: 'general.content-form'
```

统一数据类型标识为内容卡片类型数据，固定为“general.content-form”。

**类型：** 'general.content-form'

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContentForm-readonly uniformDataType: 'general.content-form'--><!--Device-ContentForm-readonly uniformDataType: 'general.content-form'-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

