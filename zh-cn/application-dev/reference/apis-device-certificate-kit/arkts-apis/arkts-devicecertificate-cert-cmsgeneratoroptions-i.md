# CmsGeneratorOptions

表示生成CMS消息的配置选项。

**起始版本：** 18

<!--Device-cert-interface CmsGeneratorOptions--><!--Device-cert-interface CmsGeneratorOptions-End-->

**系统能力：** SystemCapability.Security.Cert

## 导入模块

```TypeScript
import { cert } from '@kit.DeviceCertificateKit';
```

## contentDataFormat

```TypeScript
contentDataFormat?: CmsContentDataFormat
```

内容数据的格式。默认为CmsContentDataFormat.BINARY。

**类型：** CmsContentDataFormat

**默认值：** CmsContentDataFormat.BINARY

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CmsGeneratorOptions-contentDataFormat?: CmsContentDataFormat--><!--Device-CmsGeneratorOptions-contentDataFormat?: CmsContentDataFormat-End-->

**系统能力：** SystemCapability.Security.Cert

## isDetached

```TypeScript
isDetached?: boolean
```

Cms最终数据是否不包含原始数据。默认为false。true为不包含，false为包含。

**类型：** boolean

**默认值：** false

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CmsGeneratorOptions-isDetached?: boolean--><!--Device-CmsGeneratorOptions-isDetached?: boolean-End-->

**系统能力：** SystemCapability.Security.Cert

## outFormat

```TypeScript
outFormat?: CmsFormat
```

Cms最终数据的输出格式。默认为DER。

**类型：** CmsFormat

**默认值：** CmsFormat.DER

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CmsGeneratorOptions-outFormat?: CmsFormat--><!--Device-CmsGeneratorOptions-outFormat?: CmsFormat-End-->

**系统能力：** SystemCapability.Security.Cert

