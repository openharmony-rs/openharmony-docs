# getSeniorModeStateForApp（系统接口）

## 导入模块

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## getSeniorModeStateForApp

```TypeScript
function getSeniorModeStateForApp(bundleName: string, appIndex?: int): Promise<boolean>
```

查询应用“长辈模式”的状态。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.READ_ACCESSIBILITY_CONFIG

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-config-function getSeniorModeStateForApp(bundleName: string, appIndex?: int): Promise<boolean>--><!--Device-config-function getSeniorModeStateForApp(bundleName: string, appIndex?: int): Promise<boolean>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 查询“长辈模式”的应用包名。 |
| appIndex | int | 否 | 应用包的分身索引标识。 <br>取值范围：大于等于0的整数。缺省时，appIndex默认为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示应用已启用“长辈模式”；返回false表示应用未启用“长辈模式”。 |

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

config.getSeniorModeStateForApp('com.example.myapplication', 0).then((data: boolean) => {
  console.info(`Succeeded in getting seniorModeState for app, data: ${data}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get seniorModeState for app. Code: ${err.code}, message: ${err.message}`);
});
```

