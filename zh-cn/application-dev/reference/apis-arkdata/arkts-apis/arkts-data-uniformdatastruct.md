# @ohos.data.uniformDataStruct

本模块为统一数据管理框架（Unified Data Management Framework，UDMF）的组成部分，针对多对多跨应用数据共享的不同业务场景提供了部分标准化数据类型[UniformDataType](arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)对应的数据结构，方便不同应用间进行数据交互，减少数据类型适配的工作量。

**起始版本：** 12

<!--Device-unnamed-declare namespace uniformDataStruct--><!--Device-unnamed-declare namespace uniformDataStruct-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { uniformDataStruct } from '@kit.ArkData';
```

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ContentForm](arkts-arkdata-uniformdatastruct-contentform-i.md) | 内容卡片类型数据，用于跨应用共享内容卡片信息。典型使用场景包括：资讯应用分享文章卡片、电商应用分享商品卡片、社交应用分享内容预览等。 |
| [FileUri](arkts-arkdata-uniformdatastruct-fileuri-i.md) | 文件地址类型数据，用于描述文件的URI地址信息。创建FileUri对象后，可用于文件拖拽、文件共享等场景，支持通过uriAuthorizationPolicies控制文件访问权限，实现跨应用的文件数据传递和权限管理。 |
| [Form](arkts-arkdata-uniformdatastruct-form-i.md) | 系统定义的卡片类型数据，用于跨应用共享卡片信息。典型使用场景包括：卡片拖拽分享、卡片内容跨应用传输、桌面小组件数据共享等。 |
| [HTML](arkts-arkdata-uniformdatastruct-html-i.md) | HTML类型数据，用于描述超文本标记语言数据。创建HTML对象后，可在拖拽、复制粘贴等场景中传递富文本内容，支持跨应用的HTML格式数据交互，并可通过uriAuthorizationPolicies控制URI授权策略。 |
| [Hyperlink](arkts-arkdata-uniformdatastruct-hyperlink-i.md) | 超链接类型数据，用于描述和管理超链接信息。创建Hyperlink对象后，可用于拖拽、分享等场景，实现跨应用的超链接数据传递和跳转。 |
| [OpenHarmonyAppItem](arkts-arkdata-uniformdatastruct-openharmonyappitem-i.md) | 系统定义的桌面图标类型数据，用于跨应用共享桌面图标信息。典型使用场景包括：桌面启动器拖拽图标、应用商店分享应用图标或创建快捷方式等。 |
| [PixelMap](arkts-arkdata-uniformdatastruct-pixelmap-i.md) | 系统定义的像素图类型数据，用于描述图像像素数据。创建PixelMap对象后，可用于图像拖拽、图像共享等场景，实现跨应用的图像数据传递。 |
| [PlainText](arkts-arkdata-uniformdatastruct-plaintext-i.md) | 纯文本类型数据，用于描述和管理纯文本内容。创建PlainText对象后，可用于拖拽、复制粘贴等数据共享场景，实现跨应用的纯文本数据交互。 |

