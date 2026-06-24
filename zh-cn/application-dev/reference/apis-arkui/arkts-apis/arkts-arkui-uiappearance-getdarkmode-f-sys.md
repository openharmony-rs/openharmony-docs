# getDarkMode（系统接口）

## getDarkMode

```TypeScript
function getDarkMode(): DarkMode
```

��ȡϵͳ��ǰ����ɫģʽ���á�

<!--Del-->

> **˵����**

> �ýӿ���API version 19��֮ǰ�汾��Ϊϵͳ�ӿڡ�������ʹ�øýӿ�ʱ��Ҫ����
> [ohos.permission.UPDATE_CONFIGURATION](../../../../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_configuration)
> Ȩ�ޡ�

<!--DelEnd-->

**起始版本：** 20

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

**系统能力：** SystemCapability.ArkUI.UiAppearance

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DarkMode | current dark-mode. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied.&lt;br&gt;**适用版本：** 10 - 19 |
| [500001](../../errorcode-universal.md#500001-Internal) | Internal error. |

**示例：**

```TypeScript
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let darkMode = uiAppearance.getDarkMode();
  console.info('Get dark-mode ' + darkMode);
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('Get dark-mode failed, ' + message);
}

```

