# @ohos.bundle.defaultAppManager

本模块提供查询默认应用的能力，支持查询当前应用是否是默认应用。

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [isDefaultApplication](arkts-ability-isdefaultapplication-f.md#isdefaultapplication-1) | 根据系统已定义的应用类型或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor)类型判断当前应用是否是该类型的默认应用。使用callback异步回调。 |
| [isDefaultApplication](arkts-ability-isdefaultapplication-f.md#isdefaultapplication-2) | 根据系统已定义的应用类型或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型判断当前应用是否是该类型的默认应用。使用Promise异步回调。 |
| [isDefaultApplicationSync](arkts-ability-isdefaultapplicationsync-f.md#isdefaultapplicationsync-1) | 以同步方法根据系统已定义的应用类型或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor)类型判断当前应用是否是该类型的默认应用，使用boolean形式返回结果。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getDefaultApplication](arkts-ability-getdefaultapplication-f-sys.md#getdefaultapplication-1) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型获取默认应用信息。使用callback异步回调。 |
| [getDefaultApplication](arkts-ability-getdefaultapplication-f-sys.md#getdefaultapplication-2) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型获取默认应用信息。使用callback异步回调。 |
| [getDefaultApplication](arkts-ability-getdefaultapplication-f-sys.md#getdefaultapplication-3) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型获取默认应用信息。使用Promise异步回调。 |
| [getDefaultApplicationSync](arkts-ability-getdefaultapplicationsync-f-sys.md#getdefaultapplicationsync-1) | 以同步方法根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型获取默认应用信息，使用BundleInfo返回结果。 |
| [resetDefaultApplication](arkts-ability-resetdefaultapplication-f-sys.md#resetdefaultapplication-1) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型重置默认应用。使用callback异步回调。 |
| [resetDefaultApplication](arkts-ability-resetdefaultapplication-f-sys.md#resetdefaultapplication-2) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型重置默认应用。使用callback异步回调。 |
| [resetDefaultApplication](arkts-ability-resetdefaultapplication-f-sys.md#resetdefaultapplication-3) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型重置默认应用。使用Promise异步回调。 |
| [resetDefaultApplicationSync](arkts-ability-resetdefaultapplicationsync-f-sys.md#resetdefaultapplicationsync-1) | 以同步方法根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型重置默认应用。 |
| [setDefaultApplication](arkts-ability-setdefaultapplication-f-sys.md#setdefaultapplication-1) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型设置默认应用。使用callback异步回调。 |
| [setDefaultApplication](arkts-ability-setdefaultapplication-f-sys.md#setdefaultapplication-2) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型设置默认应用。使用callback异步回调。 |
| [setDefaultApplication](arkts-ability-setdefaultapplication-f-sys.md#setdefaultapplication-3) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型设置默认应用。使用Promise异步回调。 |
| [setDefaultApplicationForAppClone](arkts-ability-setdefaultapplicationforappclone-f-sys.md#setdefaultapplicationforappclone-1) | 以同步方法将分身应用设置为打开相应type类型的默认应用。 |
| [setDefaultApplicationSync](arkts-ability-setdefaultapplicationsync-f-sys.md#setdefaultapplicationsync-1) | 以同步方法根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](@ohos.data.uniformTypeDescriptor:uniformTypeDescriptor.UniformDataType)类型设置默认应用。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ApplicationType](arkts-ability-applicationtype-e.md) | 默认应用的应用类型。 |

