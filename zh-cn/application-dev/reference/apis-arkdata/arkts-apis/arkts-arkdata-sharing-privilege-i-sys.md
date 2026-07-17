# Privilege（系统接口）

指定的端云共享数据的权限。

**起始版本：** 11

<!--Device-sharing-interface Privilege--><!--Device-sharing-interface Privilege-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## creatable

```TypeScript
creatable?: boolean
```

被共享者是否可创建新的共享数据。true表示可创建，false表示不可创建，默认不可创建。

**类型：** boolean

**起始版本：** 11

<!--Device-Privilege-creatable?: boolean--><!--Device-Privilege-creatable?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

## deletable

```TypeScript
deletable?: boolean
```

被共享者是否可删除共享的数据。true表示可删除，false表示不可删除，默认不可删除。

**类型：** boolean

**起始版本：** 11

<!--Device-Privilege-deletable?: boolean--><!--Device-Privilege-deletable?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

## readable

```TypeScript
readable?: boolean
```

被共享者是否可读取共享的数据。true表示可读取，false表示不可读取，默认不可读取

**类型：** boolean

**起始版本：** 11

<!--Device-Privilege-readable?: boolean--><!--Device-Privilege-readable?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

## shareable

```TypeScript
shareable?: boolean
```

被共享者是否可将共享的数据再次共享给其他参与者。true表示可再次共享，false表示不可再次共享，默认不可再次共享。

**类型：** boolean

**起始版本：** 11

<!--Device-Privilege-shareable?: boolean--><!--Device-Privilege-shareable?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

## writable

```TypeScript
writable?: boolean
```

被共享者是否可修改共享的数据。true表示可修改，false表示不可修改，默认不可修改。

**类型：** boolean

**起始版本：** 11

<!--Device-Privilege-writable?: boolean--><!--Device-Privilege-writable?: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**系统接口：** 此接口为系统接口。

