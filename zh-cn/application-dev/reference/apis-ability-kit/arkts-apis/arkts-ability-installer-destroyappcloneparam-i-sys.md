# DestroyAppCloneParam（系统接口）

```TypeScript
export interface DestroyAppCloneParam
```

删除分身应用可指定的参数信息。

**起始版本：** 15

<!--Device-installer-export interface DestroyAppCloneParam--><!--Device-installer-export interface DestroyAppCloneParam-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { installer } from '@kit.AbilityKit';
```

## parameters

```TypeScript
parameters?: Array<Parameters>
```

指定删除分身应用扩展参数，默认值为空，不支持CLI沙箱应用。Parameters.key取值支持：</br> - "ohos.bms.param.clone.isKeepData"：从API version 21开始支持，若对应value值为"true"，表示删除分身时会保留分身的用户数据，否则不会保留分身的用户数据。

**类型：** Array&lt;Parameters&gt;

**起始版本：** 15

<!--Device-DestroyAppCloneParam-parameters?: Array<Parameters>--><!--Device-DestroyAppCloneParam-parameters?: Array<Parameters>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: number
```

指定删除分身应用或CLI沙箱应用所在的用户ID，可以通过[getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)获取。默认值：调用方所在用户。

**类型：** number

**起始版本：** 15

<!--Device-DestroyAppCloneParam-userId?: int--><!--Device-DestroyAppCloneParam-userId?: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。
