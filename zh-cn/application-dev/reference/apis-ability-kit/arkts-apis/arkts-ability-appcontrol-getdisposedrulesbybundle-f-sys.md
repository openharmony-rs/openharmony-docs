# getDisposedRulesByBundle（系统接口）

## 导入模块

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

<a id="getdisposedrulesbybundle"></a>
## getDisposedRulesByBundle

```TypeScript
function getDisposedRulesByBundle(bundleName: string): Array<DisposedRuleConfiguration>
```

获取指定应用程序包设置的所有拦截规则。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS or ohos.permission.GET_DISPOSED_APP_STATUS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-appControl-function getDisposedRulesByBundle(bundleName: string): Array<DisposedRuleConfiguration>--><!--Device-appControl-function getDisposedRulesByBundle(bundleName: string): Array<DisposedRuleConfiguration>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示设置拦截规则的应用程序包的包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;DisposedRuleConfiguration&gt; | 指定应用程序包已设置的拦截规则。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied. A non-system application is not allowed to call a system API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.example.myapplication';

try {
  let data = appControl.getDisposedRulesByBundle(bundleName);
  console.info('getDisposedRulesByBundle successfully. Data: ' + JSON.stringify(data));
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('getDisposedRulesByBundle failed ' + message);
}

```

