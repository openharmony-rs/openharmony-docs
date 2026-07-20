# AppSchema（系统接口）

应用数据库模式。

**起始版本：** 11

<!--Device-cloudExtension-export interface AppSchema--><!--Device-cloudExtension-export interface AppSchema-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudExtension } from '@kit.ArkData';
```

## bundleName

```TypeScript
bundleName: string
```

应用包名。

**类型：** string

**起始版本：** 11

<!--Device-AppSchema-bundleName: string--><!--Device-AppSchema-bundleName: string-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## databases

```TypeScript
databases: Array<Database>
```

应用的数据库信息。

**类型：** Array&lt;Database&gt;

**起始版本：** 11

<!--Device-AppSchema-databases: Array<Database>--><!--Device-AppSchema-databases: Array<Database>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## version

```TypeScript
version: number
```

数据库模式的版本。

**类型：** number

**起始版本：** 11

<!--Device-AppSchema-version: int--><!--Device-AppSchema-version: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

