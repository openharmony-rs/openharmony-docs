# @ohos.uiAppearance (用户界面外观)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @lushi871202-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->

用户界面外观提供获取系统外观的一些基础能力，包括获取深浅色模式、字体大小缩放比例、字体粗细缩放比例。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 从API version 20开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。


## 导入模块

```ts
import { uiAppearance } from '@kit.ArkUI';
```


## DarkMode

深色模式枚举。

**系统能力：** SystemCapability.ArkUI.UiAppearance

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

| 名称 | 值 | 说明 |
| -- | -- | -- |
| ALWAYS_DARK | 0 | 系统始终为深色。  |
| ALWAYS_LIGHT | 1 | 系统始终为浅色。 |

## uiAppearance.getDarkMode

getDarkMode(): DarkMode

获取系统当前的深色模式配置。

<!--Del-->
> **说明：**
>
> 该接口在API version 19及之前版本中为系统接口。开发者使用该接口时需要申请[ohos.permission.UPDATE_CONFIGURATION](../../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_configuration)权限。
<!--DelEnd-->

**系统能力**：SystemCapability.ArkUI.UiAppearance

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

**返回值：** 

| 类型 | 说明 |
| -- | -- |
|[DarkMode](#darkmode) | 系统当前的深色模式配置。 |

**错误码：**

错误码详细介绍请参考[用户界面外观服务错误码](errorcode-uiappearance.md)。

| 错误码ID | 错误信息 |
| -- | -- |
| 500001 | Internal error. |

**示例：** 

```ts
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


## uiAppearance.getFontScale

ArkTS-Dyn: getFontScale(): number

ArkTS-Sta: getFontScale(): double

获取系统当前的字体大小缩放比例。

<!--Del-->
> **说明：**
>
> 该接口在API version 19及之前版本中为系统接口。开发者使用该接口时需要申请[ohos.permission.UPDATE_CONFIGURATION](../../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_configuration)权限。
<!--DelEnd-->

**系统能力**：SystemCapability.ArkUI.UiAppearance

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

**返回值：** 

| 类型 | 说明 |
| -- | -- |
| ArkTS-Dyn: number<br/>ArkTS-Sta: double | 系统当前的字体大小缩放比例。 |

**错误码：**

错误码详细介绍请参考[用户界面外观服务错误码](errorcode-uiappearance.md)。

| 错误码ID | 错误信息 |
| -- | -- |
| 500001 | Internal error. |

**示例：** 

```ts
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let fontScale = uiAppearance.getFontScale();
  console.info('Get fontScale ' + fontScale);
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('Get fontScale failed, ' + message);
}
```


## uiAppearance.getFontWeightScale

ArkTS-Dyn: getFontWeightScale(): number

ArkTS-Sta: getFontWeightScale(): double

获取系统当前的字体粗细缩放比例。

<!--Del-->
> **说明：**
>
> 该接口在API version 19及之前版本中为系统接口。开发者使用该接口时需要申请[ohos.permission.UPDATE_CONFIGURATION](../../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_configuration)权限。
<!--DelEnd-->

**系统能力**：SystemCapability.ArkUI.UiAppearance

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

**返回值：** 

| 类型 | 说明 |
| -- | -- |
| ArkTS-Dyn: number<br/>ArkTS-Sta: double | 系统当前的字体粗细缩放比例。 |

**错误码：**

错误码详细介绍请参考[用户界面外观服务错误码](errorcode-uiappearance.md)。

| 错误码ID | 错误信息 |
| -- | -- |
| 500001 | Internal error. |

**示例：** 

```ts
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let fontWeightScale = uiAppearance.getFontWeightScale();
  console.info('Get fontScale ' + fontWeightScale);
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('Get fontWeightScale failed, ' + message);
}
```