# CreateAppCloneParam（系统接口）

创建分身应用可指定的参数信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-installer-export interface CreateAppCloneParam--><!--Device-installer-export interface CreateAppCloneParam-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## appIndex

```TypeScript
appIndex?: int
```

指定创建分身应用的索引值。默认值：当前可用的最小索引值。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CreateAppCloneParam-appIndex?: int--><!--Device-CreateAppCloneParam-appIndex?: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: int
```

指定创建分身应用所在的用户ID，可以通过 [getOsAccountLocalId接口](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId) 获取。默认值：调用方所在用户。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CreateAppCloneParam-userId?: int--><!--Device-CreateAppCloneParam-userId?: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

