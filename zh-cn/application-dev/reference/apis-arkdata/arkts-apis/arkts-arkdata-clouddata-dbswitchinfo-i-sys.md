# DBSwitchInfo（系统接口）

端云协同数据库开关配置信息。

**起始版本：** 23

<!--Device-cloudData-interface DBSwitchInfo--><!--Device-cloudData-interface DBSwitchInfo-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## enable

```TypeScript
enable: boolean
```

数据库是否启用端云协同开关。true为启用端云协同开关，false为不启用该开关。

**类型：** boolean

**起始版本：** 23

<!--Device-DBSwitchInfo-enable: boolean--><!--Device-DBSwitchInfo-enable: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

## tableInfo

```TypeScript
tableInfo?: Record<string, boolean>
```

表级别的端云协同开关配置信息。键为表名，值为该表的开关状态。true为打开该表的端云协同开关，false为关闭该表开关。当未配置该参数时，默认按照数据库级开关状态enable生效。

**类型：** Record<string, boolean>

**起始版本：** 23

<!--Device-DBSwitchInfo-tableInfo?: Record<string, boolean>--><!--Device-DBSwitchInfo-tableInfo?: Record<string, boolean>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Config

**系统接口：** 此接口为系统接口。

