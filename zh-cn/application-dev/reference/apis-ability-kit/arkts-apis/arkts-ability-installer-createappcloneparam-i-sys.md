# CreateAppCloneParam（系统接口）

```TypeScript
export interface CreateAppCloneParam
```

创建分身应用可指定的参数信息。

**起始版本：** 12

<!--Device-installer-export interface CreateAppCloneParam--><!--Device-installer-export interface CreateAppCloneParam-End-->

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

<!--Device-CreateAppCloneParam-appIndex?: int--><!--Device-CreateAppCloneParam-appIndex?: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## parameters

```TypeScript
parameters?: Array<Parameters>
```

创建分身应用扩展参数，默认值为空。Parameters.key取值支持：</br>- "ohos.bms.param.disableInstallEventReport"：value值建议为string类型的"true"或"false"。若对应value值为"true"，表示分身创建完成后不发送安装广播事件；若对应value值为"false"或其他非"true"的值，则正常发送安装广播。不传入该键时，正常发送安装广播（默认行为）。</br>- "ohos.bms.param.bundleEnableState"：value值建议为string类型的"true"或"false"。若对应value值为"true"，表示分身创建后处于启用状态（enabled为true）；若对应value值为"false"或其他非"true"的值，表示分身创建后处于禁用状态（enabled为false）。不传入该键时，表示分身创建后处于启用状态（enabled为true，默认行为）。</br> </br>。

**类型：** Array&lt;Parameters&gt;

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CreateAppCloneParam-parameters?: Array<Parameters>--><!--Device-CreateAppCloneParam-parameters?: Array<Parameters>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: number
```

指定创建分身应用所在的用户ID，可以通过[getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)获取。默认值：调用方所在用户。

**类型：** number

**起始版本：** 12

<!--Device-CreateAppCloneParam-userId?: int--><!--Device-CreateAppCloneParam-userId?: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。
