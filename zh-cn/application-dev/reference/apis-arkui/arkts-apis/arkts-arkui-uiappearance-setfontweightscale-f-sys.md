# setFontWeightScale（系统接口）

## 导入模块

```TypeScript
import { uiAppearance } from '@kit.ArkUI';
```

<a id="setfontweightscale"></a>
## setFontWeightScale

```TypeScript
function setFontWeightScale(fontWeightScale: number): Promise<void>
```

设置系统字体粗细。

**起始版本：** 12

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-uiAppearance-function setFontWeightScale(fontWeightScale: number): Promise<void>--><!--Device-uiAppearance-function setFontWeightScale(fontWeightScale: number): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.UiAppearance

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontWeightScale | number | 是 | indicates the font-weight-scale to set |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [500001](../errorcode-uiappearance.md#500001-内部错误) | Internal error. |

**示例：**

```TypeScript
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

