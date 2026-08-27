# CreateAppCloneParam（系统接口）

创建分身应用可指定的参数信息。

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { installer } from '@kit.AbilityKit';
```

## appIndex

```TypeScript
appIndex?: number
```

指定创建分身应用的索引值。默认值：当前可用的最小索引值。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: number
```

指定创建分身应用所在的用户ID，可以通过 [getOsAccountLocalId接口](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) 获取。默认值：调用方所在用户。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。
