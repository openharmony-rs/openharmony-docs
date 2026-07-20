# EventClassifyInfo（系统接口）

事件信息。

**起始版本：** 9

<!--Device-update-export interface EventClassifyInfo--><!--Device-update-export interface EventClassifyInfo-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## eventClassify

```TypeScript
eventClassify: EventClassify
```

事件类型，用于指定要监听的事件分类。可取值：TASK（任务事件）。

**类型：** EventClassify

**起始版本：** 9

<!--Device-EventClassifyInfo-eventClassify: EventClassify--><!--Device-EventClassifyInfo-eventClassify: EventClassify-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## extraInfo

```TypeScript
extraInfo: string
```

额外信息，用于传递扩展数据。默认值为空字符串，表示无额外信息。长度范围[0, 128]，单位：字符。有效字符包括字母、数字、下划线、连字符和空格，超出范围或包含无效字符时抛出异常。

**类型：** string

**起始版本：** 9

<!--Device-EventClassifyInfo-extraInfo: string--><!--Device-EventClassifyInfo-extraInfo: string-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

