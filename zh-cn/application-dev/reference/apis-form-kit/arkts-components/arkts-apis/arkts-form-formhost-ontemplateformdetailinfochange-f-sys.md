# onTemplateFormDetailInfoChange（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## onTemplateFormDetailInfoChange

```TypeScript
function onTemplateFormDetailInfoChange(callback: formInfo.TemplateFormDetailInfoCallback): void
```

订阅模板卡片静态配置信息变化。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [formInfo.TemplateFormDetailInfoCallback](arkts-form-forminfo-templateformdetailinfocallback-t-sys.md) | 是 | 回调函数，监控模板卡片静态配置信息变化。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |

**示例**

```TypeScript
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const callback: formInfo.TemplateFormDetailInfoCallback = (info: formInfo.TemplateFormDetailInfo[]) => {
    for (let templateFormDetailInfo of info) {
      console.info(`TemplateFormDetailInfoCallback bundleName: ${templateFormDetailInfo.bundleName}, moduleName: ${templateFormDetailInfo.moduleName}, formName: ${templateFormDetailInfo.formName}`);
    }
  };
  formHost.onTemplateFormDetailInfoChange(callback);
  console.info(`onTemplateFormDetailInfoChange success`);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
