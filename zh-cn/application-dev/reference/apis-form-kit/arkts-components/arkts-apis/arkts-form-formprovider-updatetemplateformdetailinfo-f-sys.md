# updateTemplateFormDetailInfo（系统接口）

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## updateTemplateFormDetailInfo

```TypeScript
function updateTemplateFormDetailInfo(templateFormInfo: Array<formInfo.TemplateFormDetailInfo>): Promise<void>
```

更新当前设备上指定的模板卡片静态配置信息。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| templateFormInfo | Array&lt;[formInfo.TemplateFormDetailInfo](arkts-form-forminfo-templateformdetailinfo-i-sys.md)&gt; | 是 | 指定的模板卡片静态配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16501013](../errorcode-form.md#16501013-系统不支持当前操作) | The system does not support the current operation. |

**示例**

```TypeScript
import { formProvider, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const templateFormInfo: formInfo.TemplateFormDetailInfo[] = [{
    bundleName: 'com.example.ohos.formjsdemo',
    moduleName: 'entry',
    abilityName: 'EntryAbility',
    formName: 'widget',
    dimension: 2,
    detailId: 'detailId',
    displayName: 'displayName',
    description: 'description',
  }];
  formProvider.updateTemplateFormDetailInfo(templateFormInfo).then(() => {
    console.info('updateTemplateFormDetailInfo succeed.');
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
