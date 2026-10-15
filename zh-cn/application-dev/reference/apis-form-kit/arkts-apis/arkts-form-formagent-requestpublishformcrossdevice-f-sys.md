# requestPublishFormCrossDevice（系统接口）

## 导入模块

```TypeScript
import { formAgent } from '@kit.FormKit';
```

## requestPublishFormCrossDevice

```TypeScript
function requestPublishFormCrossDevice(peerServiceInfo: formInfo.PeerFormHostServiceInfo, want: Want,
    formBindingData?: formBindingData.FormBindingData): Promise<formInfo.PublishFormCrossDeviceResult>
```

请求发布一张卡片到远端设备的卡片使用方服务。使用Promise异步回调。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.AGENT_REQUIRE_FORM

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-formAgent-function requestPublishFormCrossDevice(peerServiceInfo: formInfo.PeerFormHostServiceInfo, want: Want,    formBindingData?: formBindingData.FormBindingData): Promise<formInfo.PublishFormCrossDeviceResult>--><!--Device-formAgent-function requestPublishFormCrossDevice(peerServiceInfo: formInfo.PeerFormHostServiceInfo, want: Want,    formBindingData?: formBindingData.FormBindingData): Promise<formInfo.PublishFormCrossDeviceResult>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| peerServiceInfo | [formInfo.PeerFormHostServiceInfo](arkts-form-forminfo-peerformhostserviceinfo-i-sys.md) | 是 | 远端卡片使用方服务信息。 |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 发布请求，需包含以下字段。<br>bundleName: 目标卡片所属应用的bundleName <br>abilityName: 目标卡片所属应用的Ability <br>parameters: <br>- ohos.extra.param.key.form_dimension: 目标卡片规格<br>- ohos.extra.param.key.form_name: 目标卡片名<br>- ohos.extra.param.key.module_name: 目标卡片的模块名称 |
| formBindingData | [formBindingData.FormBindingData](arkts-form-formbindingdata-formbindingdata-i.md) | 否 | 用于更新的卡片数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[formInfo.PublishFormCrossDeviceResult](arkts-form-forminfo-publishformcrossdeviceresult-i-sys.md)&gt; | Promise对象，返回跨设备发布卡片的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permissions denied. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | The application is not a system application. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16501020](../errorcode-form.md#16501020-远端卡片服务不可用) | Remote form service is unavailable. |
| [16501021](../errorcode-form.md#16501021-远端卡片应用未安装或版本过低) | The peer form application is not installed or the version is too old. |
| [16501002](../errorcode-form.md#16501002-卡片数量达到上限) | The number of forms exceeds the maximum allowed. |
| [16501017](../errorcode-form.md#16501017-无空间发布卡片) | There is no space to publish the form. |
| [16501018](../errorcode-form.md#16501018-卡片不支持发布) | This form does not support publishing. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16501008](../errorcode-form.md#16501008-等待卡片加桌超时) | Waiting for the form addition to the desktop timed out. |

<!--Del-->
**示例**

```TypeScript
import { formBindingData, formAgent, formInfo } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let want: Want = {
  bundleName: 'com.ohos.exampledemo',
  abilityName: 'FormAbility',
  parameters: {
    'ohos.extra.param.key.form_dimension': 2,
    'ohos.extra.param.key.form_name': 'widget',
    'ohos.extra.param.key.module_name': 'entry'
  }
};
let peerServiceInfo: formInfo.PeerFormHostServiceInfo = {
  serviceName: 'serviceName',
  serviceDisplayName: 'serviceDisplayName',
  displayId: '0',
  deviceId: 'deviceId',
  networkId: 'networkId',
  serviceId: 'serviceId'
};
let param: Record<string, string> = {
  'temperature': '22c',
  'time': '22:00'
};
let obj: formBindingData.FormBindingData = formBindingData.createFormBindingData(param);
try {
  formAgent.requestPublishFormCrossDevice(peerServiceInfo, want, obj).then((data: formInfo.PublishFormCrossDeviceResult) => {
    console.info(`formAgent requestPublishFormCrossDevice success, form ID is: ${data.formId}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

<!--DelEnd-->
