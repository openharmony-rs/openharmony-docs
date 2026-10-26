# publishFormToDesktop

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## publishFormToDesktop

```TypeScript
function publishFormToDesktop(formInfo: FormInfo): string
```

卡片加桌。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.ENTERPRISE_REQUEST_PUBLISH_FORM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function publishFormToDesktop(formInfo: FormInfo): string--><!--Device-applicationManager-function publishFormToDesktop(formInfo: FormInfo): string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formInfo | [FormInfo](arkts-mdm-applicationmanager-forminfo-i.md) | 是 | 卡片信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 卡片ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
| 9201047 | Form count limit reached or insufficient home screen space to add forms. |
| 9201049 | The form does not exist. |
| 9201050 | The form type is not supported. |
| 9201051 | Failed to add the form to the desktop. |

**示例**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { formInfo, formProvider } from '@kit.FormKit';

async function publishFormToDesktop() {
  // 需根据实际情况进行替换
  let filter: formInfo.FormInfoFilter = {
    moduleName: 'entry'
  };
  // 此处调用formProvider.getFormsInfo接口查询应用自己的卡片信息，不是必须执行的步骤,按需使用
  let formsInfos: Array<formInfo.FormInfo> = await formProvider.getFormsInfo(filter);
  if (formsInfos.length == 0) {
    return;
  }
  // 需根据实际情况进行替换
  let form: applicationManager.FormInfo = {
    bundleName: formsInfos[0].bundleName,
    moduleName: formsInfos[0].moduleName,
    abilityName: formsInfos[0].abilityName,
    name: formsInfos[0].name,
    dimension: formsInfos[0].defaultDimension
  }
  try {
    let result: string = applicationManager.publishFormToDesktop(form);
    console.info(`Succeeded in publishing form to desktop, result : ${JSON.stringify(result)}`);
  } catch(err) {
    console.error(`Failed to publish form to desktop. Code: ${err.code}, message: ${err.message}`);
  }
}
```
