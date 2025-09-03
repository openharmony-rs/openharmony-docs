# @ohos.bundle.defaultAppManager (默认应用管理)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->

本模块提供查询默认应用的能力，支持查询当前应用是否是默认应用。

> **说明：**
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { defaultAppManager } from '@kit.AbilityKit';
```

## ApplicationType

默认应用的应用类型。

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

| 名称   | 值 | 说明                                   |
| -------- | -------------------------------------- | -------------------------------------- |
| BROWSER  | 'Web Browser' | 默认浏览器。                            |
| IMAGE    | 'Image Gallery' | 默认图片查看器。                         |
| AUDIO    | 'Audio Player' | 默认音频播放器。                         |
| VIDEO    | 'Video Player' | 默认视频播放器。                         |
| PDF      | 'PDF Viewer' | 默认PDF文档查看器。                      |
| WORD     | 'Word Viewer' | 默认WORD文档查看器。                     |
| EXCEL    | 'Excel Viewer' | 默认EXCEL文档查看器。                    |
| PPT      | 'PPT Viewer' | 默认PPT文档查看器。                      |
| EMAIL<sup>12+</sup>    | 'Email' | 默认邮件。                      |

## defaultAppManager.isDefaultApplication

isDefaultApplication(type: string): Promise\<boolean>

根据系统已定义的应用类型或者[UniformDataType](../apis-arkdata/js-apis-data-uniformTypeDescriptor.md)类型判断当前应用是否是该类型的默认应用，使用Promise异步回调。

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**参数：**

| 参数名         | 类型     | 必填   | 说明                                      |
| ----------- | ------ | ---- | --------------------------------------- |
| type  | string | 是    | 要查询的应用类型，取[ApplicationType](#applicationtype)或者[UniformDataType](../apis-arkdata/js-apis-data-uniformTypeDescriptor.md)类型中的值。                           |

**返回值：**

| 类型                        | 说明                 |
| ------------------------- | ------------------ |
| Promise\<boolean> | Promise形式返回当前应用是否是默认应用，true表示是默认应用，false表示不是默认应用。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                    |
| -------- | ---------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801 | Capability not supported. |

**示例：**

```ts
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

defaultAppManager.isDefaultApplication(defaultAppManager.ApplicationType.BROWSER)
  .then((data) => {
    console.info('Operation successful. IsDefaultApplication ? ' + JSON.stringify(data));
  }).catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  });
```

## defaultAppManager.isDefaultApplication

isDefaultApplication(type: string, callback: AsyncCallback\<boolean>): void

根据系统已定义的应用类型或者[UniformDataType](../apis-arkdata/js-apis-data-uniformTypeDescriptor.md)类型判断当前应用是否是该类型的默认应用，使用callback异步回调。

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**参数：**

| 参数名         | 类型                              | 必填   | 说明                                      |
| ----------- | ------------------------------- | ---- | --------------------------------------- |
| type  | string                          | 是    | 要查询的应用类型，取[ApplicationType](#applicationtype)或者[UniformDataType](../apis-arkdata/js-apis-data-uniformTypeDescriptor.md)类型中的值。                            |
| callback    | AsyncCallback\<boolean> | 是    | 程序启动作为入参的[回调函数](../apis-basic-services-kit/js-apis-base.md#asynccallback)，返回当前应用是否是默认应用，true表示是默认应用，false表示不是默认应用。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                    |
| -------- | ---------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801 | Capability not supported. |

**示例：**

```ts
import { defaultAppManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

defaultAppManager.isDefaultApplication(defaultAppManager.ApplicationType.BROWSER, (err: BusinessError, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. IsDefaultApplication ? ' + JSON.stringify(data));
});
```

## defaultAppManager.isDefaultApplicationSync<sup>10+</sup>

isDefaultApplicationSync(type: string): boolean

以同步方法根据系统已定义的应用类型或者[UniformDataType](../apis-arkdata/js-apis-data-uniformTypeDescriptor.md)类型判断当前应用是否是该类型的默认应用，使用boolean形式返回结果。

**系统能力：** SystemCapability.BundleManager.BundleFramework.DefaultApp

**参数：**

| 参数名 | 类型   | 必填 | 说明                                     |
| -------| ------ | ---- | --------------------------------------- |
|  type  | string | 是   | 要查询的应用类型，取[ApplicationType](#applicationtype)或者[UniformDataType](../apis-arkdata/js-apis-data-uniformTypeDescriptor.md)类型中的值。   |

**返回值：**

| 类型    | 说明                 |
| ------- | -------------------- |
| boolean | 返回当前应用是否是默认应用，true表示是默认应用，false表示不是默认应用。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                    |
| -------- | ---------------------------------------------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801 | Capability not supported. |

**示例：**

```ts
import { defaultAppManager } from '@kit.AbilityKit';

try {
  let data = defaultAppManager.isDefaultApplicationSync(defaultAppManager.ApplicationType.BROWSER)
  console.info('Operation successful. IsDefaultApplicationSync ? ' + JSON.stringify(data));
} catch(error) {
  console.error('Operation failed. Cause: ' + JSON.stringify(error));
};
```