# getFontWeightScale（系统接口）

## getFontWeightScale

```TypeScript
function getFontWeightScale(): number
```

��ȡϵͳ��ǰ�������ϸ���ű�����

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
| number | current font-weight-scale. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied.&lt;br&gt;**适用版本：** 12 - 19 |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system<br/>API.&lt;br&gt;**适用版本：** 12 - 19 |
| [500001](../../errorcode-universal.md#500001-Internal) | Internal error. |

**示例：**

```TypeScript
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let fontWeightScale = uiAppearance.getFontWeightScale();
  console.info('Get fontWeightScale ' + fontWeightScale);
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('Get fontWeightScale failed, ' + message);
}

```

