# ComponentDescription（系统接口）

组件描述文件。

**起始版本：** 9

<!--Device-update-export interface ComponentDescription--><!--Device-update-export interface ComponentDescription-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## componentId

```TypeScript
componentId: string
```

组件标识，用于唯一标识升级包中的组件。

使用场景：在获取版本描述信息(getNewVersionDescription)时需要传入componentId以获取对应组件的描述内容；在展示版本详情时可通过componentId区分不同组件。

获取方式：从版本检查结果的versionComponents数组中获取对应组件的componentId字段。

**类型：** string

**起始版本：** 9

<!--Device-ComponentDescription-componentId: string--><!--Device-ComponentDescription-componentId: string-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## descriptionInfo

```TypeScript
descriptionInfo: DescriptionInfo
```

描述文件信息。

**类型：** DescriptionInfo

**起始版本：** 9

<!--Device-ComponentDescription-descriptionInfo: DescriptionInfo--><!--Device-ComponentDescription-descriptionInfo: DescriptionInfo-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

