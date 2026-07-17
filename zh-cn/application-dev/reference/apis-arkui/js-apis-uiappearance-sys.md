# @ohos.uiAppearance (用户界面外观)(系统接口)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fangzhiyuan1-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @gouyuanyuan-->
<!--Adviser: @Brilliantry_Rui-->

用户界面外观提供管理系统外观的基础能力，包括深浅色模式配置、字体大小缩放比例和字体粗细缩放比例设置，适用于需要统一管理应用深浅色主题切换、适配用户字体偏好以提升阅读体验等场景，可解决系统外观配置分散、用户个性化需求无法统一响应等问题。

> **说明：**
>
> - 从API version 10开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.uiAppearance (用户界面外观)](js-apis-uiappearance.md)。


## 导入模块

```ts
import { uiAppearance } from '@kit.ArkUI';
```


## uiAppearance.setDarkMode

setDarkMode(mode: DarkMode, callback: AsyncCallback\<void>): void

设置系统深浅色模式，修改系统级配色方案配置。设置后，所有跟随系统配色方案的应用将自动切换至对应模式。使用callback异步回调。

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

**系统能力：** SystemCapability.ArkUI.UiAppearance

**系统接口：** 此接口为系统接口。

**参数：** 

| 参数名 | 类型 | 必填 | 说明 |
| -- | -- | -- | -- |
| mode | [DarkMode](js-apis-uiappearance.md#darkmode) | 是 | 指定系统的深浅色模式配置。 |
| callback | [AsyncCallback](../apis-basic-services-kit/js-apis-base.md#asynccallback)\<void>| 是 | 设置深浅色模式结果的回调。调用成功时，error为undefined；调用失败时，error为错误对象。 |

**错误码：**

错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[用户界面外观服务错误码](errorcode-uiappearance.md)。

| 错误码ID | 错误信息 |
| -- | -- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| 500001 | Internal error. |

**示例：** 

```ts
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  uiAppearance.setDarkMode(uiAppearance.DarkMode.ALWAYS_DARK, (error) => {
    if (error) {
      console.error(`Set dark-mode failed. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Set dark-mode successfully.');
  });
} catch (error) {
  let err = error as BusinessError;
  console.error(`Set dark-mode failed. Code: ${err.code}, message: ${err.message}`);
}
```


## uiAppearance.setDarkMode

setDarkMode(mode: DarkMode): Promise\<void>;

设置系统深浅色模式，修改系统级配色方案配置。设置后，所有跟随系统配色方案的应用将自动切换至对应模式。使用Promise异步回调。

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

**系统能力：** SystemCapability.ArkUI.UiAppearance

**系统接口：** 此接口为系统接口。

**参数：** 

| 参数名 | 类型 | 必填 | 说明 |
| -- | -- | -- | -- |
| mode | [DarkMode](js-apis-uiappearance.md#darkmode) | 是 | 指定系统的深浅色模式配置。 |

**返回值：**

| 类型   | 说明                           |
| ------ | ------------------------------ |
| Promise\<void> | Promise对象，无返回结果。|

**错误码：**

错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[用户界面外观服务错误码](errorcode-uiappearance.md)。

| 错误码ID | 错误信息 |
| -- | -- |
| 201 | Permission denied. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| 500001 | Internal error. |

**示例：** 

```ts
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  uiAppearance.setDarkMode(uiAppearance.DarkMode.ALWAYS_DARK).then(() => {
    console.info('Set dark-mode successfully.');
  }).catch((error: BusinessError) => {
    console.error(`Set dark-mode failed. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  let err = error as BusinessError;
  console.error(`Set dark-mode failed. Code: ${err.code}, message: ${err.message}`);
}
```


## uiAppearance.setFontScale<sup>12+</sup>

setFontScale(fontScale: number): Promise\<void>

设置系统字体大小缩放比例，修改系统级字体缩放配置。设置后，系统将通知所有运行中的应用按新的缩放比例调整字体显示。使用Promise异步回调。

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

**系统能力：** SystemCapability.ArkUI.UiAppearance

**系统接口：** 此接口为系统接口。

**参数：** 

| 参数名 | 类型 | 必填 | 说明 |
| -- | -- | -- | -- |
| fontScale | number | 是 | 字体大小缩放比例。<br/> 取值范围：(0, 5.0]，超出范围会抛出异常401。<br/> 取值原则：1.0为基准值表示正常字体大小，大于1.0放大字体，小于1.0缩小字体。 |

**返回值：** 

| 类型 | 说明 |
| -- | -- |
| Promise\<void> | Promise对象，无返回结果。|

**错误码：**

错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[用户界面外观服务错误码](errorcode-uiappearance.md)。

> **说明：**
>
> 在未申请`ohos.permission.UPDATE_CONFIGURATION`权限时，应用安装将失败，不会返回202错误码。

| 错误码ID | 错误信息 |
| -- | -- |
| 201 | Permission denied. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed. |
| 500001 | Internal error. |

**示例：** 

```ts
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let fontScale = 1.5;

try {
  uiAppearance.setFontScale(fontScale).then(() => {
    console.info('Set fontScale successfully.');
  }).catch((error: BusinessError) => {
    console.error(`Set fontScale failed. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  let err = error as BusinessError;
  console.error(`Set fontScale failed. Code: ${err.code}, message: ${err.message}`);
}
```


## uiAppearance.setFontWeightScale<sup>12+</sup>

setFontWeightScale(fontWeightScale: number): Promise\<void>

设置系统字体粗细缩放比例，修改系统级字体粗细缩放配置。设置后，系统将通知所有运行中的应用按新的缩放比例调整字体粗细显示。使用Promise异步回调。

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

**系统能力：** SystemCapability.ArkUI.UiAppearance

**系统接口：** 此接口为系统接口。

**参数：** 

| 参数名 | 类型 | 必填 | 说明 |
| -- | -- | -- | -- |
| fontWeightScale | number | 是 | 字体粗细缩放比例。<br/> 取值范围：(0, 5.0]，超出范围会抛出异常401。<br/> 取值原则：1.0为基准值表示正常字体粗细，大于1.0加粗字体，小于1.0变细字体。 |

**返回值：** 

| 类型 | 说明 |
| -- | -- |
| Promise\<void> | Promise对象，无返回结果。|

**错误码：**

错误码详细介绍请参考[通用错误码](../errorcode-universal.md)和[用户界面外观服务错误码](errorcode-uiappearance.md)。

> **说明：**
>
> 在未申请`ohos.permission.UPDATE_CONFIGURATION`权限时，应用安装将失败，不会返回202错误码。

| 错误码ID | 错误信息 |
| -- | -- |
| 201 | Permission denied. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameters types. 3. Parameter verification failed.  |
| 500001 | Internal error. |

**示例：** 

```ts
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let fontWeightScale = 1;

try {
  uiAppearance.setFontWeightScale(fontWeightScale).then(() => {
    console.info('Set fontWeightScale successfully.');
  }).catch((error: BusinessError) => {
    console.error(`Set fontWeightScale failed. Code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  let err = error as BusinessError;
  console.error(`Set fontWeightScale failed. Code: ${err.code}, message: ${err.message}`);
}
```
