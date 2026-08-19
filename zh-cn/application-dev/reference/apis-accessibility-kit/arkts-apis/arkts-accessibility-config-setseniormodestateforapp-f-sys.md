# setSeniorModeStateForApp（系统接口）

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## setSeniorModeStateForApp

```TypeScript
function setSeniorModeStateForApp(appSeniorModeInfos: Array<AppSeniorModeInfo>): Promise<void>
```

设置应用“长辈模式”的状态。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.WRITE_ACCESSIBILITY_CONFIG

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-config-function setSeniorModeStateForApp(appSeniorModeInfos: Array<AppSeniorModeInfo>): Promise<void>--><!--Device-config-function setSeniorModeStateForApp(appSeniorModeInfos: Array<AppSeniorModeInfo>): Promise<void>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appSeniorModeInfos | Array&lt;[AppSeniorModeInfo](arkts-accessibility-config-appseniormodeinfo-i-sys.md)&gt; | 是 | 修改应用的“长辈模式”的状态信息，数组中每个对象包含bundleName、appIndex、 seniorModeState三个属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9300008](../errorcode-accessibility.md#9300008-应用分身索引不合法) | The appIndex is invalid. Possible causes: <br>1.The appIndex is out of the valid range. <br>2.The application corresponding to the appIndex does not exist. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. <br>The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. <br>A non-system application calls a system API. |
| [9300000](../errorcode-accessibility.md#9300000-无障碍系统服务工作异常) | System abnormality. |

**示例**

```TypeScript
import { config } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let infos: config.AppSeniorModeInfo[] = [{
  bundleName: 'com.example.myapplication',
  appIndex: 0,
  seniorModeState: true
}];

config.setSeniorModeStateForApp(infos).then(() => {
  console.info(`Succeeded in setting seniorModeState for App.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to set seniorModeState for app. Code: ${err.code}, message: ${err.message}`);
});
```

