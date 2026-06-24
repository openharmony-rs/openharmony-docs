# setFontScale（系统接口）

## setFontScale

```TypeScript
function setFontScale(fontScale: number): Promise<void>
```

����ϵͳ�����С��

**起始版本：** 12

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

**系统能力：** SystemCapability.ArkUI.UiAppearance

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontScale | number | 是 | indicates the font-scale to set |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [500001](../../errorcode-universal.md#500001-Internal) | Internal error. |

**示例：**

```TypeScript
import { uiAppearance } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

let fontScale = 10;

try {
    uiAppearance.setFontScale(fontScale).then(() => {
      console.info('Set fontScale successfully.');
    }).catch((error:Error) => {
      console.error('Set fontScale failed, ' + error.message);
    });
} catch (error) {
    let message = (error as BusinessError).message;
    console.error('Set fontScale failed, ' + message);
}

```

