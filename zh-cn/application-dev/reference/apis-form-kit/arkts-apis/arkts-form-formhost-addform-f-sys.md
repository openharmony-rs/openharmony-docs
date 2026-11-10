# addForm（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## addForm

```TypeScript
function addForm(want: Want): Promise<formInfo.RunningFormInfo>
```

添加主题卡片。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.REQUIRE_FORM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-formHost-function addForm(want: Want): Promise<formInfo.RunningFormInfo>--><!--Device-formHost-function addForm(want: Want): Promise<formInfo.RunningFormInfo>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 查询卡片状态时携带的want信息。需要包含bundle名、ability名、module名、卡片名、卡片规格等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | Promise对象。返回符合条件的卡片信息，包括卡片名称、尺寸等。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permissions denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | [Sync/Async] Parameter error. Possible causes:         1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |

<!--Del-->
**示例**

```TypeScript
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let want: Want = {
    'bundleName': 'com.huawei.hmsapp.thememanager',
    'abilityName': 'ThemeFaCardUIExtAbility',
    'parameters': {
      'ohos.extra.param.key.form_dimension': 4,
      'ohos.extra.param.key.form_is_theme': true,
      'ohos.extra.param.key.form_location': 0,
      'ohos.extra.param.key.module_name': 'entry',
      'ohos.extra.param.key.form_name': 'widget',
      'themeFormId': '0',
      'themeId': '2181824853'
    }
  };
  formHost.addForm(want).then((data: formInfo.RunningFormInfo) => {
    console.info(`formHost addForm, formId: ${data.formId}`);
  }).catch((error: BusinessError) => {
    console.error(`formHost addForm error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

<!--DelEnd-->
