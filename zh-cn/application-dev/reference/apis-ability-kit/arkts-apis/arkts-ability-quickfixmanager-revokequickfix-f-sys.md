# revokeQuickFix（系统接口）

## 导入模块

```TypeScript
import { quickFixManager } from '@kit.AbilityKit';
```

<a id="revokequickfix"></a>
## revokeQuickFix

```TypeScript
function revokeQuickFix(bundleName: string, callback: AsyncCallback<void>): void
```

撤销快速修复的接口，使用callback方式返回结果。

**起始版本：** 10

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED and ohos.permission.INSTALL_BUNDLE

<!--Device-quickFixManager-function revokeQuickFix(bundleName: string, callback: AsyncCallback<void>): void--><!--Device-quickFixManager-function revokeQuickFix(bundleName: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.QuickFix

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 需要撤销补丁的应用Bundle名称。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当撤销快速修复成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [18500001](../errorcode-ability.md#18500001-指定的包名无效) | The bundle does not exist or no patch has been applied. |
| [18500009](../errorcode-ability.md#18500009-该应用当前有正在处理的快速修复任务) | The application has an ongoing quick fix task. |

**示例：**

```TypeScript
import { quickFixManager } from '@kit.AbilityKit';

let bundleName = 'com.example.myapplication';

quickFixManager.revokeQuickFix(bundleName, (err) => {
  if (err.code) {
    console.error(`revokeQuickFix ${bundleName} failed, err code: ${err.code}, err msg: ${err.message}.`);
  }
});

```


<a id="revokequickfix-1"></a>
## revokeQuickFix

```TypeScript
function revokeQuickFix(bundleName: string): Promise<void>
```

撤销快速修复的接口。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED and ohos.permission.INSTALL_BUNDLE

<!--Device-quickFixManager-function revokeQuickFix(bundleName: string): Promise<void>--><!--Device-quickFixManager-function revokeQuickFix(bundleName: string): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.QuickFix

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 需要撤销补丁的应用Bundle名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [18500001](../errorcode-ability.md#18500001-指定的包名无效) | The bundle does not exist or no patch has been applied. |
| [18500009](../errorcode-ability.md#18500009-该应用当前有正在处理的快速修复任务) | The application has an ongoing quick fix task. |

**示例：**

```TypeScript
import { quickFixManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.example.myapplication';

quickFixManager.revokeQuickFix(bundleName).then(() => {
  console.info(`revokeQuickFix ${bundleName} success.`);
}).catch((err: BusinessError) => {
  console.error(`revokeQuickFix ${bundleName} failed, err code: ${err.code}, err msg: ${err.message}.`);
});

```

