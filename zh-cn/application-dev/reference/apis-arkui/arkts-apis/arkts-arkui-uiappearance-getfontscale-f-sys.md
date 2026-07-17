# getFontScale（系统接口）

## 导入模块

```TypeScript
import { uiAppearance } from '@kit.ArkUI';
```

## getFontScale

```TypeScript
function getFontScale(): number
```

获取系统当前的字体大小缩放比例。

<!--Del-->

> **说明：**

> 该接口在API version 19及之前版本中为系统接口。开发者使用该接口时需要申请  
> [ohos.permission.UPDATE_CONFIGURATION](../../../../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_configuration)  
> 权限。

<!--DelEnd-->

**起始版本：** 20

**需要权限：** 
- API版本12 - 19：ohos.permission.UPDATE_CONFIGURATION

<!--Device-uiAppearance-function getFontScale(): number--><!--Device-uiAppearance-function getFontScale(): number-End-->

**系统能力：** SystemCapability.ArkUI.UiAppearance

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | current font-scale. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 12 - 19 |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12 - 19 |
| [500001](../errorcode-uiappearance.md#500001-内部错误) | Internal error. |

**示例：**

```TypeScript
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let fontScale = uiAppearance.getFontScale();
  console.info('Get fontScale ' + fontScale);
} catch (error) {
  let err = error as BusinessError;
  console.error(`Get fontScale failed. Code: ${err.code}, message: ${err.message}`);
}

```

