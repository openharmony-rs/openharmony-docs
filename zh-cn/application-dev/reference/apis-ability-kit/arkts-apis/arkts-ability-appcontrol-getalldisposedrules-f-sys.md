# getAllDisposedRules（系统接口）

## getAllDisposedRules

```TypeScript
function getAllDisposedRules(): Array<DisposedRuleConfiguration>
```

��ȡ��ǰ�û��������õ��������ع���

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_DISPOSED_APP_STATUS or ohos.permission.GET_DISPOSED_APP_STATUS

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;DisposedRuleConfiguration&gt; | Ӧ�������õ����ع��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission denied. A non-system application is not allowed to call a system API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. |

**示例：**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = appControl.getAllDisposedRules();
  console.info('getAllDisposedRules successfully. Data: ' + JSON.stringify(data));
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('getAllDisposedRules failed ' + message);
}

```

