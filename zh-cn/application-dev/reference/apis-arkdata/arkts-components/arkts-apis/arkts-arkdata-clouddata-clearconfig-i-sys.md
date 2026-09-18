# ClearConfig（系统接口）

端云协同数据库级清除规则。

**起始版本：** 23

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## dbInfo

```TypeScript
dbInfo: Record<string, DBActionInfo>
```

待清除数据的库信息及各库的清除规则。键为数据库名称，值为该数据库的清除规则。

**类型：** Record&lt;string, [DBActionInfo](arkts-arkdata-clouddata-dbactioninfo-i-sys.md)&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。
