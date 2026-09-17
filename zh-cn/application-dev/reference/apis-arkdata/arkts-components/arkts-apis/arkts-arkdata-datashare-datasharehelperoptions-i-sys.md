# DataShareHelperOptions（系统接口）

指定[DataShareHelper](arkts-arkdata-datashare-datasharehelper-i-sys.md)的可选参数，包含是否在代理模式下，以及非静默访问的启动等待时间。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## isProxy

```TypeScript
isProxy?: boolean
```

默认为false，如果为true，则要创建的[DataShareHelper](arkts-arkdata-datashare-datasharehelper-i-sys.md)处于代理模式，所有操作都不会打开数据提供者APP，除非数据库不存在，当数据库不存在时，[createDataShareHelper](arkts-arkdata-datashare-createdatasharehelper-f-sys.md)会启动数据提供者创建数据库。

**类型：** boolean

**默认值：** false

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## waitTime

```TypeScript
waitTime?: number
```

启动数据提供者进程的等待时间（单位：秒），默认值为2秒。取值需大于0。

**类型：** number

**默认值：** 2

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。
