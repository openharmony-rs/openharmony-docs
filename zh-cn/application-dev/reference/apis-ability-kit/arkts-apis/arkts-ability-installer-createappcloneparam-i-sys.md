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

## parameters

```TypeScript
parameters?: Array<Parameters>
```

扩展参数，Parameters类型的数组，默认值为空。Parameters.key取值支持：&lt;/br&gt;  
- "ohos.bms.param.disableInstallEventReport"：若对应value值为"true"，表示分身创建完成后不发送安装广播事件。  
若不传入该键或value值非"true"，则正常发送安装广播。&lt;/br&gt;  
- "ohos.bms.param.bundleEnableState"：若对应value值为"false"，表示分身创建后处于禁用状态（enabled为false）。  
若对应value值为"true"或不传入该键，表示分身创建后处于启用状态（enabled为true，默认行为）。

**类型：** Array&lt;Parameters&gt;

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: number
```

指定创建分身应用所在的用户ID，可以通过[getOsAccountLocalId接口](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)获取。默认值：调用方所在用户。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。
