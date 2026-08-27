# onPublishFormCrossBundleControl（系统接口）

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## onPublishFormCrossBundleControl

```TypeScript
function onPublishFormCrossBundleControl(callback: formInfo.PublishFormCrossBundleControlCallback): void
```

订阅跨应用加桌管控。

**起始版本：** 23

**需要权限：** ohos.permission.PUBLISH_FORM_CROSS_BUNDLE_CONTROL

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | formInfo.PublishFormCrossBundleControlCallback | 是 | 跨应用加桌管控的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |

**示例**

```TypeScript
import { formProvider, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formProvider.onPublishFormCrossBundleControl((info: formInfo.PublishFormCrossBundleInfo) => {
    return true;
  });
  console.info(`onPublishFormCrossBundleControl success`);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
