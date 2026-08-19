# updateFormSize（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## updateFormSize

```TypeScript
function updateFormSize(formId: string, newDimension: formInfo.FormDimension, newRect: formInfo.Rect): void
```

调整卡片尺寸。

**起始版本：** 23

**需要权限：** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function updateFormSize(formId: string, newDimension: formInfo.FormDimension, newRect: formInfo.Rect): void--><!--Device-formHost-function updateFormSize(formId: string, newDimension: formInfo.FormDimension, newRect: formInfo.Rect): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |
| newDimension | formInfo.FormDimension | 是 | 卡片尺寸，例如 Dimension_1_2，表示 1 x 2 卡片。 |
| newRect | formInfo.Rect | 是 | 卡片位置信息，包括卡片左上角顶点的xy坐标和卡片的宽高。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501001](../errorcode-form.md#16501001-卡片id不存在) | The ID of the form to be operated does not exist. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | caller is not system app. |
| [16501012](../errorcode-form.md#16501012-卡片尺寸错误) | The dimension parameter is incorrect |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string = '12400633174999288';
  let newDimension = formInfo.FormDimension.Dimension_1_2;
  let newRect: formInfo.Rect = {
    left: 1,
    top: 2,
    width: 100,
    height: 100
  };
  formHost.updateFormSize(formId, newDimension, newRect);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string = '12400633174999288';
  let newDimension = formInfo.FormDimension.Dimension_1_2;
  let newRect: formInfo.Rect = {left: 1, top: 2, width: 100, height: 100};
  formHost.updateFormSize(formId, newDimension, newRect);
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

