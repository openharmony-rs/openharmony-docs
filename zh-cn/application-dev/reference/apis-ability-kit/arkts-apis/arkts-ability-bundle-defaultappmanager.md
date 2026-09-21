# @ohos.bundle.defaultAppManager

本模块提供查询默认应用的能力，支持查询当前应用是否是默认应用。

**起始版本：** 9

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

## 导入模块

```TypeScript
import { defaultAppManager } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [isDefaultApplication](arkts-ability-defaultappmanager-isdefaultapplication-f.md#isdefaultapplication) | 根据系统已定义的应用类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md)类型判断当前应用是否是该类型的默认应用。使用callback异步回调。 |
| [isDefaultApplication](arkts-ability-defaultappmanager-isdefaultapplication-f.md#isdefaultapplication-1) | 根据系统已定义的应用类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型判断当前应用是否是该类型的默认应用。使用Promise异步回调。 |
| [isDefaultApplicationSync](arkts-ability-defaultappmanager-isdefaultapplicationsync-f.md) | 以同步方法根据系统已定义的应用类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-data-uniformtypedescriptor.md)类型判断当前应用是否是该类型的默认应用，使用boolean形式返回结果。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getDefaultApplication](arkts-ability-defaultappmanager-getdefaultapplication-f-sys.md#getdefaultapplication) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型获取默认应用信息。使用callback异步回调。 |
| [getDefaultApplication](arkts-ability-defaultappmanager-getdefaultapplication-f-sys.md#getdefaultapplication-1) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型获取默认应用信息。使用callback异步回调。 |
| [getDefaultApplication](arkts-ability-defaultappmanager-getdefaultapplication-f-sys.md#getdefaultapplication-2) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型获取默认应用信息。使用Promise异步回调。 |
| [getDefaultApplicationCandidates](arkts-ability-defaultappmanager-getdefaultapplicationcandidates-f-sys.md) | 查询可被设置为指定类型默认应用的应用列表。当前仅支持**BROWSER**类型的查询。未被授予ohos.permission.DEFAULT_WEB_BROWSER权限的应用将从结果中排除。 |
| [getDefaultApplicationSync](arkts-ability-defaultappmanager-getdefaultapplicationsync-f-sys.md) | 以同步方法根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型获取默认应用信息，使用BundleInfo返回结果。 |
| [resetDefaultApplication](arkts-ability-defaultappmanager-resetdefaultapplication-f-sys.md#resetdefaultapplication) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型重置默认应用。使用callback异步回调。 |
| [resetDefaultApplication](arkts-ability-defaultappmanager-resetdefaultapplication-f-sys.md#resetdefaultapplication-1) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型重置默认应用。使用callback异步回调。 |
| [resetDefaultApplication](arkts-ability-defaultappmanager-resetdefaultapplication-f-sys.md#resetdefaultapplication-2) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型重置默认应用。使用Promise异步回调。 |
| [resetDefaultApplicationSync](arkts-ability-defaultappmanager-resetdefaultapplicationsync-f-sys.md) | 以同步方法根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型重置默认应用。 |
| [setDefaultApplication](arkts-ability-defaultappmanager-setdefaultapplication-f-sys.md#setdefaultapplication) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型设置默认应用。使用callback异步回调。将应用设置为默认浏览器时，目标应用必须已被授予ohos.permission.DEFAULT_WEB_BROWSER权限，否则返回错误码18000001。 [since 26.0.1] |
| [setDefaultApplication](arkts-ability-defaultappmanager-setdefaultapplication-f-sys.md#setdefaultapplication-1) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型设置默认应用。使用callback异步回调。将应用设置为默认浏览器时，目标应用必须已被授予ohos.permission.DEFAULT_WEB_BROWSER权限，否则返回错误码18000001。 [since 26.0.1] |
| [setDefaultApplication](arkts-ability-defaultappmanager-setdefaultapplication-f-sys.md#setdefaultapplication-2) | 根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型设置默认应用。使用Promise异步回调。将应用设置为默认浏览器时，目标应用必须已被授予ohos.permission.DEFAULT_WEB_BROWSER权限，否则返回错误码18000001。 [since 26.0.1] |
| [setDefaultApplicationForAppClone](arkts-ability-defaultappmanager-setdefaultapplicationforappclone-f-sys.md) | 以同步方法将分身应用设置为打开相应type类型的默认应用。将应用设置为默认浏览器时，目标应用必须已被授予ohos.permission.DEFAULT_WEB_BROWSER权限，否则返回错误码18000001。 [since 26.0.1] |
| [setDefaultApplicationSync](arkts-ability-defaultappmanager-setdefaultapplicationsync-f-sys.md) | 以同步方法根据系统已定义的应用类型或者符合媒体类型格式（type/subtype）的文件类型或者[UniformDataType](../../apis-arkdata/arkts-apis/arkts-arkdata-uniformtypedescriptor-uniformdatatype-e.md)类型设置默认应用。将应用设置为默认浏览器时，目标应用必须已被授予ohos.permission.DEFAULT_WEB_BROWSER权限，否则返回错误码18000001。 [since 26.0.1] |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ApplicationType](arkts-ability-defaultappmanager-applicationtype-e.md) | 默认应用的应用类型。 |
