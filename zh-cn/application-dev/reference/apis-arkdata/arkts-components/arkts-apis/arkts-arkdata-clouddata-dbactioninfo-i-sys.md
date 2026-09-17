# DBActionInfo（系统接口）

端云协同数据库级清除规则。

**起始版本：** 23

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## action

```TypeScript
action: ClearAction
```

数据库默认数据清除规则。

**类型：** [ClearAction](arkts-arkdata-clouddata-clearaction-e-sys.md)

**起始版本：** 23

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## tableInfo

```TypeScript
tableInfo?: Record<string, ClearAction>
```

待清除数据的表信息及各表的清除规则。键为表名称，值为该表的清除规则。当未配置该参数时，默认使用数据库的数据清除规则。

**类型：** Record&lt;string, [ClearAction](arkts-arkdata-clouddata-clearaction-e-sys.md)&gt;

**起始版本：** 23

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。
