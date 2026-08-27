# HTML

HTML类型数据，是[Text](arkts-arkdata-unifieddatachannel-text-c.md)的子类，用于描述超文本标记语言数据。

**继承/实现关系：** HTML extends [Text](arkts-arkdata-unifieddatachannel-text-c.md)

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## htmlContent

```TypeScript
set htmlContent(value: string)
```

html格式内容。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## plainContent

```TypeScript
plainContent?: string
```

去除html标签后的纯文本内容，非必填字段，默认值为空字符串。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## uriAuthorizationPolicies

```TypeScript
set uriAuthorizationPolicies(value: Array<UriPermission> | undefined)
```

用于拖拽场景的URI授权策略。默认值为READ（仅读授权），仅在img标签等场景下生效。只针对单个record使用，优先级最高，具体策略见 [UriPermission](arkts-arkdata-unifieddatachannel-uripermission-e.md)。

**类型：** Array&lt;[UriPermission](arkts-arkdata-unifieddatachannel-uripermission-e.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**示例**

```TypeScript
let html = new unifiedDataChannel.HTML();
html.htmlContent = '<div><p>标题</p></div>';
html.plainContent = 'This is plainContent';
// 从API 26.0.0版本开始，支持uri授权策略
html.uriAuthorizationPolicies = [
  unifiedDataChannel.UriPermission.WRITE
];
```
