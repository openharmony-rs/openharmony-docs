# applyQuickFix（系统接口）

## 导入模块

```TypeScript
import { quickFixManager } from '@kit.AbilityKit';
```

<a id="applyquickfix"></a>
## applyQuickFix

```TypeScript
function applyQuickFix(hapModuleQuickFixFiles: Array<string>, callback: AsyncCallback<void>): void
```

快速修复的补丁安装接口。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.INSTALL_BUNDLE

<!--Device-quickFixManager-function applyQuickFix(hapModuleQuickFixFiles: Array<string>, callback: AsyncCallback<void>): void--><!--Device-quickFixManager-function applyQuickFix(hapModuleQuickFixFiles: Array<string>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.QuickFix

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapModuleQuickFixFiles | Array&lt;string&gt; | 是 | 快速修复补丁文件（补丁文件需包含有效的文件路径）。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当快速修复的补丁安装成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [18500002](../errorcode-ability.md#18500002-指定的补丁包无效) | Invalid patch package. |
| [18500008](../errorcode-ability.md#18500008-快速修复内部错误) | Internal error. |

**示例：**

```TypeScript
import { quickFixManager } from '@kit.AbilityKit';

try {
  let hapModuleQuickFixFiles = ['/data/storage/el2/base/entry.hqf'];
  quickFixManager.applyQuickFix(hapModuleQuickFixFiles, (error) => {
    if (error) {
      console.error( `applyQuickFix failed with error: ${error}`);
    } else {
      console.info(`applyQuickFix success`);
    }
  });
} catch (paramError) {
  console.error(`error.code: ${paramError.code}, error.message: ${paramError.message}`);
}

```


<a id="applyquickfix-1"></a>
## applyQuickFix

```TypeScript
function applyQuickFix(hapModuleQuickFixFiles: Array<string>): Promise<void>
```

快速修复的补丁安装接口。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.INSTALL_BUNDLE

<!--Device-quickFixManager-function applyQuickFix(hapModuleQuickFixFiles: Array<string>): Promise<void>--><!--Device-quickFixManager-function applyQuickFix(hapModuleQuickFixFiles: Array<string>): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.QuickFix

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hapModuleQuickFixFiles | Array&lt;string&gt; | 是 | 快速修复补丁文件（补丁文件需包含有效的文件路径）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [18500002](../errorcode-ability.md#18500002-指定的补丁包无效) | Invalid patch package. |
| [18500008](../errorcode-ability.md#18500008-快速修复内部错误) | Internal error. |

**示例：**

```TypeScript
import { quickFixManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let hapModuleQuickFixFiles = ['/data/storage/el2/base/entry.hqf'];

try {
  quickFixManager.applyQuickFix(hapModuleQuickFixFiles).then(() => {
    console.info(`applyQuickFix success`);
  }).catch((error: BusinessError) => {
    console.error(`applyQuickFix err: ${error}`);
  });
} catch (paramError) {
  console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
}

```

