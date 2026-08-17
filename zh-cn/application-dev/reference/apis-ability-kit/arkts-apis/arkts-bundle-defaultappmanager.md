# @ohos.bundle.defaultAppManager

本模块提供查询默认应用的能力，支持查询当前应用是否是默认应用。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace defaultAppManager--><!--Device-unnamed-declare namespace defaultAppManager-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [isDefaultApplication](arkts-ability-defaultappmanager-isdefaultapplication-f.md#isdefaultapplication) | 根据系统已定义的应用类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-data-uniformtypedescriptor.md#ohosdatauniformtypedescriptor标准化数据定义与描述)类型判断当前应用是否是该类型的默认应用。使用 callback异步回调。 |
| [isDefaultApplication](arkts-ability-defaultappmanager-isdefaultapplication-f.md#isdefaultapplication) | 根据系统已定义的应用类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#uniformdatatype)类型判断当前 应用是否是该类型的默认应用。使用Promise异步回调。 |
| [isDefaultApplicationSync](arkts-ability-defaultappmanager-isdefaultapplicationsync-f.md#isdefaultapplicationsync) | 以同步方法根据系统已定义的应用类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-data-uniformtypedescriptor.md#ohosdatauniformtypedescriptor标准化数据定义与描述)类型判断当前应用是否是该类型的默认 应用，使用boolean形式返回结果。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getDefaultApplication](arkts-ability-defaultappmanager-getdefaultapplication-f-sys.md#getdefaultapplication) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#uniformdatatype)类型获取默认应用信息。使用 callback异步回调。 |
| [getDefaultApplication](arkts-ability-defaultappmanager-getdefaultapplication-f-sys.md#getdefaultapplication系统接口) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#uniformdatatype)类型获取默认应用信息。使用 callback异步回调。 |
| [getDefaultApplication](arkts-ability-defaultappmanager-getdefaultapplication-f-sys.md#getdefaultapplication系统接口) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#uniformdatatype)类型获取默认应用信息。使用Promise 异步回调。 |
| [getDefaultApplicationSync](arkts-ability-defaultappmanager-getdefaultapplicationsync-f-sys.md#getdefaultapplicationsync) | 以同步方法根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#uniformdatatype)类型获取默认应用信息，使用 BundleInfo返回结果。 |
| [resetDefaultApplication](arkts-ability-defaultappmanager-resetdefaultapplication-f-sys.md#resetdefaultapplication) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#uniformdatatype)类型重置默认应用。使用callback异 步回调。 |
| [resetDefaultApplication](arkts-ability-defaultappmanager-resetdefaultapplication-f-sys.md#resetdefaultapplication系统接口) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#uniformdatatype)类型重置默认应用。使用callback异 步回调。 |
| [resetDefaultApplication](arkts-ability-defaultappmanager-resetdefaultapplication-f-sys.md#resetdefaultapplication系统接口) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#uniformdatatype)类型重置默认应用。使用Promise异步 回调。 |
| [resetDefaultApplicationSync](arkts-ability-defaultappmanager-resetdefaultapplicationsync-f-sys.md#resetdefaultapplicationsync) | 以同步方法根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#uniformdatatype)类型重置默认应用。 |
| [setDefaultApplication](arkts-ability-defaultappmanager-setdefaultapplication-f-sys.md#setdefaultapplication) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#uniformdatatype)类型设置默认应用。使用callback异 步回调。 |
| [setDefaultApplication](arkts-ability-defaultappmanager-setdefaultapplication-f-sys.md#setdefaultapplication系统接口) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#uniformdatatype)类型设置默认应用。使用callback异 步回调。 |
| [setDefaultApplication](arkts-ability-defaultappmanager-setdefaultapplication-f-sys.md#setdefaultapplication系统接口) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#uniformdatatype)类型设置默认应用。使用Promise异步 回调。 |
| [setDefaultApplicationForAppClone](arkts-ability-defaultappmanager-setdefaultapplicationforappclone-f-sys.md#setdefaultapplicationforappclone) | 以同步方法将分身应用设置为打开相应type类型的默认应用。 |
| [setDefaultApplicationSync](arkts-ability-defaultappmanager-setdefaultapplicationsync-f-sys.md#setdefaultapplicationsync) | 以同步方法根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者 [UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md#uniformdatatype)类型设置默认应用。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md) | 默认应用的应用类型。 |

