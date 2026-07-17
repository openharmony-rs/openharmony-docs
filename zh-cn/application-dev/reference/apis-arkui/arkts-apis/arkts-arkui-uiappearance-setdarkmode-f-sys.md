# setDarkMode（系统接口）

## 导入模块

```TypeScript
import { uiAppearance } from '@kit.ArkUI';
```

## setDarkMode

```TypeScript
function setDarkMode(mode: DarkMode, callback: AsyncCallback<void>): void
```

设置系统深色模式。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-uiAppearance-function setDarkMode(mode: DarkMode, callback: AsyncCallback<void>): void--><!--Device-uiAppearance-function setDarkMode(mode: DarkMode, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.ArkUI.UiAppearance

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [DarkMode](arkts-arkui-uiappearance-darkmode-e-sys.md) | 是 | indicates the dark-mode to set |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | the callback of setDarkMode |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [500001](../errorcode-uiappearance.md#500001-内部错误) | Internal error. |

**示例：**

```TypeScript
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


## setDarkMode

```TypeScript
function setDarkMode(mode: DarkMode): Promise<void>
```

设置系统深色模式。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-uiAppearance-function setDarkMode(mode: DarkMode): Promise<void>--><!--Device-uiAppearance-function setDarkMode(mode: DarkMode): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.UiAppearance

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [DarkMode](arkts-arkui-uiappearance-darkmode-e-sys.md) | 是 | indicates the dark-mode to set |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [500001](../errorcode-uiappearance.md#500001-内部错误) | Internal error. |

**示例：**

```TypeScript
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

