# @ohos.uiAppearance (用户界面外观)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fangzhiyuan1-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @gouyuanyuan-->
<!--Adviser: @Brilliantry_Rui-->

用户界面外观提供获取系统外观的基础能力，包括获取深浅色模式、字体大小缩放比例、字体粗细缩放比例，适用于需要根据系统外观配置动态调整应用界面风格（如深浅色主题切换）、以及适配系统字体大小和粗细缩放设置的场景，帮助应用保持与系统外观的一致性，提升用户体验。

> **说明：**
>
> 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```ts
import { uiAppearance } from '@kit.ArkUI';
```


## DarkMode

深浅色模式枚举，用于配置系统的深色或浅色模式。


**系统能力：** SystemCapability.ArkUI.UiAppearance

| 名称 | 值 | 说明 |
| -- | -- | -- |
| ALWAYS_DARK | 0 | 表示系统始终为深色模式。 |
| ALWAYS_LIGHT | 1 | 表示系统始终为浅色模式。 |

## uiAppearance.getDarkMode

getDarkMode(): DarkMode

获取系统当前的深浅色模式配置。适用于需要根据系统外观模式动态适配应用UI主题的场景，例如应用内实现深色/浅色主题风格自动切换。

<!--Del-->
> **说明：**
>
> 该接口在API version 19及之前版本中为系统接口。开发者使用该接口时需要申请[ohos.permission.UPDATE_CONFIGURATION](../../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_configuration)权限。
<!--DelEnd-->

**系统能力：** SystemCapability.ArkUI.UiAppearance

**返回值：** 

| 类型 | 说明 |
| -- | -- |
|[DarkMode](#darkmode) | 系统当前的深浅色模式配置。 |

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
  let err = error as BusinessError;
  console.error(`Get dark-mode failed. Code: ${err.code}, message: ${err.message}`);
}
```


## uiAppearance.getFontScale

getFontScale(): number

获取系统当前的字体大小缩放比例。该比例为系统设置中用户配置的字体大小相对于默认字体大小的倍数，取值范围请参考系统字体大小设置。开发者可基于该比例值调整应用内字体大小，以适配用户的字体偏好设置。

<!--Del-->
> **说明：**
>
> 该接口在API version 19及之前版本中为系统接口。开发者使用该接口时需要申请[ohos.permission.UPDATE_CONFIGURATION](../../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_configuration)权限。
<!--DelEnd-->

**系统能力：** SystemCapability.ArkUI.UiAppearance

**返回值：** 

| 类型 | 说明 |
| -- | -- |
| number | 系统当前的字体大小缩放比例，1.0表示默认字体大小，大于1.0表示放大，小于1.0表示缩小。 |

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
  let err = error as BusinessError;
  console.error(`Get fontScale failed. Code: ${err.code}, message: ${err.message}`);
}
```


## uiAppearance.getFontWeightScale

getFontWeightScale(): number

获取系统当前的字体粗细缩放比例。该比例为系统设置中用户配置的字体粗细相对于默认字体粗细的倍数，取值范围请参考系统字体粗细设置。开发者可基于该比例值调整应用内字体粗细，以适配用户的字体粗细偏好设置。

<!--Del-->
> **说明：**
>
> 该接口在API version 19及之前版本中为系统接口。开发者使用该接口时需要申请[ohos.permission.UPDATE_CONFIGURATION](../../security/AccessToken/permissions-for-system-apps.md#ohospermissionupdate_configuration)权限。
<!--DelEnd-->

**系统能力：** SystemCapability.ArkUI.UiAppearance

**返回值：** 

| 类型 | 说明 |
| -- | -- |
| number | 系统当前的字体粗细缩放比例，1.0表示默认字体粗细，大于1.0表示加粗，小于1.0表示变细。 |

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
  console.info('Get fontWeightScale ' + fontWeightScale);
} catch (error) {
  let err = error as BusinessError;
  console.error(`Get fontWeightScale failed. Code: ${err.code}, message: ${err.message}`);
}
```
