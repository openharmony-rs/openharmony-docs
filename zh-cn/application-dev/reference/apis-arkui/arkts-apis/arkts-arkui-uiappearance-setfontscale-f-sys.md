# setFontScale（系统接口）

## 导入模块

```TypeScript
import { uiAppearance } from '@kit.ArkUI';
```

## setFontScale

```TypeScript
function setFontScale(fontScale: number): Promise<void>
```

设置系统字体大小。

**起始版本：** 12

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-uiAppearance-function setFontScale(fontScale: number): Promise<void>--><!--Device-uiAppearance-function setFontScale(fontScale: number): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.UiAppearance

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontScale | number | 是 | indicates the font-scale to set |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | the promise returned by the function |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [500001](../errorcode-uiappearance.md#500001-内部错误) | Internal error. |

**示例：**

```TypeScript
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

